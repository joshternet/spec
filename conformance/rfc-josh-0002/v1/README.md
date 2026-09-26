# RFC-JOSH-0002 Version 1 Conformance Suite

This directory contains the language-neutral conformance corpus for
RFC-JOSH-0002 version 1.

The suite exists to make the observable protocol behavior defined by
RFC-JOSH-0002 testable without depending on JoshBot, Go, a particular HTTP
library, a database schema, or any Joshternet registry implementation.

The corpus currently targets the RFC-JOSH-0002 semantics published at:

```text
ee57ea7c0b1427c100008ca41647ed4dbd50b05d
```

Canonical specification:

```text
rfcs/0002-well-known-josh.md
```

The specification remains authoritative. The conformance corpus provides test
vectors for it. A fixture that conflicts with RFC-JOSH-0002 is a defect in the
fixture, not a change to the protocol.

## Goals

The conformance suite is intended to:

- provide deterministic protocol examples;
- make version 1 behavior independently testable;
- allow implementations in different languages to use the same vectors;
- distinguish retrieval, declaration validity, participation, and Josh identity;
- preserve malformed JSON and other wire representations exactly as received;
- associate every expected result with the RFC-JOSH-0002 section that defines
  it;
- provide interoperability evidence without making JoshBot the definition of
  the protocol.

The suite does not define crawler scheduling, discovery, registries, retries,
robots policy, storage, publication, reporting, operator controls, or any other
JoshBot behavior outside RFC-JOSH-0002.

## Directory layout

Version 1 uses this structure:

```text
conformance/
└── rfc-josh-0002/
    └── v1/
        ├── README.md
        ├── schema.json
        └── fixtures/
            ├── ...
            └── ...
```

`README.md` defines the fixture contract and vocabulary.

`schema.json` provides machine-readable validation for fixture files.

`fixtures/` contains individual language-neutral test cases.

## Fixture format

Each fixture is one UTF-8 JSON document.

JSON is used for the fixture envelope because it is widely supported and does
not require a language-specific parser or serialization format.

Declaration response bodies are stored as JSON strings rather than nested JSON
values. This is intentional. Tests must be able to preserve representations
that cannot safely be represented as parsed fixture objects, including invalid
JSON and JSON containing duplicate member names.

A typical fixture has this shape:

```json
{
  "id": "affirmed",
  "description": "A valid version 1 declaration with affirmed Josh identity.",
  "role": "consumer",
  "conformance": "required",
  "rfc_sections": [
    "4",
    "5",
    "6",
    "7.1"
  ],
  "origin": "https://example.invalid",
  "exchanges": [
    {
      "request": {
        "method": "GET",
        "uri": "https://example.invalid/.well-known/josh"
      },
      "response": {
        "status": 200,
        "headers": [
          {
            "name": "Content-Type",
            "value": "application/json"
          }
        ],
        "body": "{\"version\":1,\"josh\":true}"
      }
    }
  ],
  "expected": {
    "declaration": "valid-v1",
    "participation": "declared",
    "identity": "affirmed"
  }
}
```

The exact fixture structure is enforced by `schema.json`.

## Top-level fields

### `id`

`id` is the stable identifier for the fixture.

It must be unique within the version 1 corpus.

Identifiers use lowercase ASCII words separated by hyphens.

Examples:

```text
affirmed
declined
missing-version
version-fraction
cross-origin-redirect
nondefault-port
```

Fixture filenames should match their identifiers:

```text
affirmed.json
cross-origin-redirect.json
```

### `description`

`description` briefly explains the protocol behavior exercised by the fixture.

It must describe the protocol case rather than an implementation detail.

### `role`

`role` identifies which side of the protocol the fixture primarily exercises.

The initial vocabulary is:

```text
consumer
publisher
```

Most response-classification fixtures exercise consumers.

Publisher fixtures may use the same protocol vectors to verify declaration
location, representation, and response behavior.

A fixture must not use an implementation name such as `joshbot` as its role.

### `conformance`

`conformance` describes how the fixture relates to RFC-JOSH-0002 normative
requirements.

The vocabulary is:

```text
required
recommended
optional-capability
```

`required` means the fixture exercises behavior required for conformance,
normally corresponding to a MUST or MUST NOT requirement or behavior necessary
to interpret the version 1 representation.

`recommended` means the fixture exercises a SHOULD or SHOULD NOT requirement.
A failure should be reported distinctly from failure of a required fixture.

`optional-capability` means RFC-JOSH-0002 permits but does not require the
behavior. A runner may skip the fixture when the implementation does not claim
the corresponding capability.

For example, RFC-JOSH-0002 Section 10 says consumers MAY follow same-origin
redirects. A consumer is therefore not nonconforming merely because it chooses
not to follow them.

A same-origin redirect fixture that requires following the redirect must use:

```json
{
  "conformance": "optional-capability",
  "capability": "same-origin-redirects"
}
```

An implementation claiming that capability must satisfy the associated
fixtures.

### `capability`

`capability` is present only when `conformance` is
`optional-capability`.

Capability names are suite-level identifiers and are not new protocol
requirements.

The initial capability vocabulary includes:

```text
same-origin-redirects
```

Additional capabilities may be introduced only when RFC-JOSH-0002 makes the
corresponding behavior optional.

### `rfc_sections`

`rfc_sections` contains one or more RFC-JOSH-0002 section numbers that directly
support the fixture's expected behavior.

Examples:

```json
[
  "3.1",
  "3.2"
]
```

```json
[
  "5",
  "6",
  "12"
]
```

Every fixture must contain at least one section reference.

Section references must point to RFC-JOSH-0002 itself. They must not point to
JoshBot source code, tests, issues, pull requests, or implementation
documentation.

### `origin`

`origin` is the RFC 6454 web origin being evaluated.

Examples:

```text
https://example.invalid
```

```text
https://example.invalid:8443
```

Paths, queries, and fragments are not part of the origin.

The fixture's request URI is specified separately so that URI construction can
be tested explicitly.

### `exchanges`

`exchanges` is the ordered sequence of network interactions expected for the
fixture.

Unless a fixture explicitly defines otherwise, the exchange sequence is exact.
A consumer must not issue additional declaration requests outside the sequence.

This allows the corpus to test requirements such as:

- using the same non-default port;
- not probing alternate ports;
- using the canonical `/.well-known/josh` path;
- omitting query parameters;
- omitting fragment identifiers;
- following only an explicitly represented redirect sequence.

Each exchange contains a `request` and exactly one of:

```text
response
failure
```

## Request

A request contains:

```json
{
  "method": "GET",
  "uri": "https://example.invalid/.well-known/josh"
}
```

### `method`

RFC-JOSH-0002 Section 9 requires consumers to use HTTP `GET`.

The version 1 corpus therefore uses:

```text
GET
```

for declaration retrieval.

### `uri`

`uri` is the complete declaration request URI expected on the wire.

This permits direct testing of the URI rules in Sections 3, 3.1, and 3.2.

For:

```text
https://example.invalid:8443
```

the expected initial declaration URI is:

```text
https://example.invalid:8443/.well-known/josh
```

The initial declaration URI must not contain:

- a trailing slash after `josh`;
- additional path components;
- a query;
- a fragment;
- a different port.

## Response

A response contains:

```json
{
  "status": 200,
  "headers": [
    {
      "name": "Content-Type",
      "value": "application/json"
    }
  ],
  "body": "{\"version\":1}"
}
```

### `status`

`status` is the HTTP response status code.

### `headers`

`headers` is an ordered array of HTTP field name and value pairs.

An array is used instead of a JSON object because HTTP fields may be repeated.

Header names are compared case-insensitively according to HTTP semantics.

A fixture may omit `headers` when no response field is relevant to the case.

RFC-JOSH-0002 associates the declaration with `application/json` and says a
publisher SHOULD return that Content-Type. It does not make the Content-Type
field a consumer-side prerequisite for interpreting an otherwise valid
representation.

Fixtures therefore include cases where a valid declaration is returned with a
missing or different Content-Type.

### `body`

`body` contains the response body exactly as text presented to the declaration
parser.

The body must not be parsed or normalized by the fixture loader before the
implementation under test receives it.

For example, this must remain possible:

```json
{
  "body": "{\"version\":1,\"version\":1}"
}
```

That representation contains duplicate JSON member names and is invalid under
RFC-JOSH-0002 Section 12.

Likewise, malformed JSON must remain malformed:

```json
{
  "body": "{\"version\":"
}
```

## Failure

Some retrieval attempts do not produce an HTTP response.

Those exchanges use `failure` instead of `response`.

Example:

```json
{
  "request": {
    "method": "GET",
    "uri": "https://example.invalid/.well-known/josh"
  },
  "failure": {
    "kind": "timeout"
  }
}
```

The initial retrieval failure vocabulary is:

```text
dns
tls
timeout
transport
```

These values describe protocol-relevant classes of retrieval failure rather
than language-specific exception types.

HTTP server errors such as `500` and `503` are represented as responses, not
transport failures.

RFC-JOSH-0002 Section 11 states that temporary retrieval failures, including
server errors, DNS failures, TLS failures, and timeouts, do not establish
intentional withdrawal.

## Expected result

`expected` separates declaration interpretation from participation and Josh
identity.

Example:

```json
{
  "expected": {
    "declaration": "valid-v1",
    "participation": "declared",
    "identity": "affirmed"
  }
}
```

These values are conformance-suite vocabulary. They are not additional
RFC-JOSH protocol fields.

### Declaration classification

The version 1 declaration vocabulary is:

```text
valid-v1
invalid
unsupported-version
absent
temporary-failure
cross-origin-redirect
```

#### `valid-v1`

The retrieved representation is a valid RFC-JOSH-0002 version 1 declaration.

Examples include:

```json
{"version":1}
```

```json
{"version":1,"josh":true}
```

```json
{"version":1,"josh":false}
```

#### `invalid`

A representation was retrieved but does not satisfy version 1 validation
requirements.

Examples include:

- malformed JSON;
- a top-level value that is not an object;
- missing `version`;
- `version: 1.0`;
- `version: 1e0`;
- invalid `josh` types;
- duplicate JSON member names.

#### `unsupported-version`

The representation declares an integer version that the version 1 consumer does
not support.

RFC-JOSH-0002 Section 6 says such a declaration must not be interpreted using
version 1 semantics.

This classification must remain distinct from `invalid`.

#### `absent`

The declaration resource is not currently published.

The initial version 1 corpus uses this classification for the explicit removal
responses identified by RFC-JOSH-0002 Section 11:

```text
404 Not Found
410 Gone
```

#### `temporary-failure`

The declaration state could not be determined because retrieval failed
temporarily.

Examples include:

- DNS failure;
- TLS failure;
- timeout;
- transport failure;
- temporary server error.

A temporary failure must remain distinct from `absent`.

#### `cross-origin-redirect`

The declaration request redirects to another origin.

RFC-JOSH-0002 Section 10 says a cross-origin redirect must not be treated as a
declaration for the original origin.

The suite keeps this case distinct so implementations can demonstrate that
origin authority was not extended across the redirect.

## Participation classification

The participation vocabulary is:

```text
declared
not-declared
indeterminate
```

### `declared`

A valid version 1 declaration was successfully retrieved for the origin.

RFC-JOSH-0002 Section 4 states that a valid `/.well-known/josh` resource
declares participation.

### `not-declared`

The observed result establishes that the origin is not declaring participation
through the version 1 protocol represented by the fixture.

Examples include:

- an invalid version 1 representation;
- `404 Not Found`;
- `410 Gone`;
- a cross-origin redirect that cannot speak for the original origin.

### `indeterminate`

The consumer cannot determine participation from the observation.

Examples include:

- a temporary retrieval failure;
- a declaration using an unsupported integer version that must not be
  interpreted with version 1 semantics.

`indeterminate` must not be silently converted to `not-declared`.

## Identity classification

The identity vocabulary is:

```text
affirmed
declined
undeclared
not-applicable
```

### `affirmed`

The valid version 1 declaration contains:

```json
{"josh":true}
```

as defined by RFC-JOSH-0002 Section 7.1.

### `declined`

The valid version 1 declaration contains:

```json
{"josh":false}
```

as defined by RFC-JOSH-0002 Section 7.2.

Declined identity remains a participating declaration.

### `undeclared`

The valid version 1 declaration omits `josh`, as defined by Section 7.3.

An absent `josh` member must not be interpreted as either `true` or `false`.

### `not-applicable`

No version 1 Josh identity can be interpreted from the fixture.

This is used for cases including:

- invalid declarations;
- unsupported versions;
- absent declarations;
- temporary retrieval failures;
- cross-origin redirects.

## Unknown members

RFC-JOSH-0002 Section 13 allows version 1 declarations to contain unknown
members.

A fixture such as:

```json
{
  "version": 1,
  "josh": true,
  "example": "ignored"
}
```

must retain the version 1 meaning of the known members.

Unknown members must not change participation, version, or Josh identity
semantics.

## Content-Type

RFC-JOSH-0002 Section 5 associates the declaration with:

```text
application/json
```

and says publishers SHOULD return:

```text
Content-Type: application/json
```

The requirement is deliberately not expressed as a consumer MUST reject other
Content-Type values.

The corpus therefore includes valid declaration responses with:

- `Content-Type: application/json`;
- no Content-Type field;
- a different Content-Type field.

The representation itself remains subject to normal RFC-JOSH-0002 validation.

## Redirects

RFC-JOSH-0002 Section 10 distinguishes same-origin and cross-origin redirects.

Consumers MAY follow same-origin redirects.

Because following a same-origin redirect is optional, fixtures requiring that
behavior use:

```text
optional-capability
```

with:

```text
same-origin-redirects
```

A consumer that does not claim that capability may skip those fixtures.

A cross-origin redirect is different. RFC-JOSH-0002 requires that it not be
treated as a declaration for the original origin. Cross-origin authority tests
are therefore required consumer conformance cases.

## Ports

The declaration URI uses the same scheme, host, and port as the origin being
evaluated.

For:

```text
https://example.invalid:8443
```

the declaration URI is:

```text
https://example.invalid:8443/.well-known/josh
```

RFC-JOSH-0002 Section 3.1 explicitly states that consumers MUST NOT probe
alternate ports in an attempt to locate a declaration.

A fixture testing this rule contains only the request to port `8443`.

An additional request to port `443`, port `80`, or any other port fails that
fixture.

## URI cleanliness

The initial declaration request must use the canonical path:

```text
/.well-known/josh
```

RFC-JOSH-0002 Section 3.2 defines no trailing slash, additional path component,
query parameter, or fragment identifier for the declaration URI.

Fixtures covering this requirement compare the complete request URI rather than
only the pathname.

## Initial version 1 corpus

The initial corpus should cover at least:

- affirmed identity;
- declined identity;
- undeclared identity;
- invalid JSON;
- non-object JSON;
- missing `version`;
- fractional `version: 1.0`;
- exponent `version: 1e0`;
- unsupported integer version;
- string `josh`;
- numeric `josh`;
- null `josh`;
- duplicate `version`;
- duplicate `josh`;
- unknown members;
- valid JSON without Content-Type;
- valid JSON with a different Content-Type;
- `404 Not Found`;
- `410 Gone`;
- temporary HTTP server failure;
- DNS failure;
- TLS failure;
- timeout;
- same-origin redirect;
- cross-origin redirect;
- non-default port retrieval;
- prohibition on alternate-port probing;
- canonical declaration path;
- no declaration query;
- no declaration fragment.

Additional fixtures may be added when they exercise behavior already defined by
RFC-JOSH-0002.

Adding a fixture must not create new protocol semantics.

## Implementation integration

Implementations are expected to translate this neutral fixture vocabulary into
their own internal representations.

For example, JoshBot may have internal outcome names that differ from the
strings used by this corpus. That mapping belongs in JoshBot's conformance
adapter, not in these fixtures.

Other implementations should be able to consume the same corpus without
knowing anything about JoshBot.

A conforming runner should report, at minimum:

- fixture identifier;
- pass, fail, or skip;
- expected classification;
- observed classification;
- referenced RFC-JOSH-0002 sections.

Optional-capability fixtures may be reported as skipped when the corresponding
capability is not claimed.

Recommended fixtures should be reported separately from required conformance
failures.

## Versioning

This directory represents RFC-JOSH-0002 version 1 semantics.

Fixtures under `v1/` must not be silently changed to represent an incompatible
future protocol version.

An incompatible declaration representation requires a new protocol version as
defined by RFC-JOSH-0002 Section 19 and should receive a separate conformance
corpus.

Corrections that bring a fixture back into agreement with RFC-JOSH-0002 may be
made in place with normal repository history and review.

## Authority

RFC-JOSH-0002 defines the protocol.

This conformance suite demonstrates the protocol.

JoshBot is one consumer implementation.

Joshternet.org is one deployment of the protocol.

None of those roles should be treated as interchangeable.
