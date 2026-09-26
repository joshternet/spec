# RFC-JOSH-0002 External Technical Review Packet

This document is the external technical review packet for
RFC-JOSH-0002 version 1.

It is non-normative.

The purpose of this packet is to give reviewers one stable place to understand:

- what RFC-JOSH-0002 defines;
- what it deliberately does not define;
- which revision is under review;
- what conformance and interoperability evidence exists;
- which questions remain open;
- how review feedback will be classified and resolved.

This is not an IANA registration request.

This is not an Internet-Draft.

This document does not change RFC-JOSH-0002.

The protocol specification remains authoritative.

## Review status

```text
Protocol version:
RFC-JOSH-0002 version 1

Protocol status:
Joshternet Draft

Review stage:
External technical review

IANA status:
Not submitted

Requested IANA status:
Provisional, if later review supports submission

Internet-Draft:
Not currently published
```

## Review baseline

Review should be performed against the following revisions.

| Artifact                             | Revision                                   |
| ------------------------------------ | ------------------------------------------ |
| RFC-JOSH-0002                        | `ee57ea7c0b1427c100008ca41647ed4dbd50b05d` |
| Version 1 conformance corpus         | `5728bf19b0d193db026cdb5f283ab998cc6bc03d` |
| Interoperability evidence            | `aa4696f6839192a339425649f5dca04721e5c110` |
| IANA preparation audit               | `a4f85cf63eecd44ee6edc9e588ef0e16b870ca3f` |
| JoshBot canonical-corpus integration | `dc68fae1379dc50a2eced056d37f6a1ee3f2ded1` |

The external-review work began from specification repository commit:

```text
a4f85cf63eecd44ee6edc9e588ef0e16b870ca3f
```

If any protocol changes result from review, those changes must be documented
explicitly and the baseline above must be updated.

## Primary review question

The central technical question is:

> Can somebody implement `/.well-known/josh` correctly using only
> RFC-JOSH-0002?

A reviewer does not need to agree with the purpose of the Joshternet to answer
that question.

The goal of this review is protocol clarity and interoperability.

The goal is not to determine whether Joshternet is a good idea, whether the
project will become popular, or whether reviewers personally want to
participate.

## Registration review questions

The Phase 9 RFC 8615 audit identified three additional questions that require
external review before any IANA registration request.

### Question 1: Registered suffix

The proposed Well-Known URI suffix is:

```text
josh
```

Review question:

> Is `josh` sufficiently specific, deployed, and community-supported to justify
> registration as the bare Well-Known URI suffix under current registry
> guidance?

RFC 8615 requires the name to satisfy the registered-name syntax and discourages
unnecessarily generic names.

`josh` satisfies the syntax.

Current Well-Known URI registry guidance also warns that bare common words can
require broader community discussion or a more specific alternative.

The project is not asking reviewers to assume that the name is acceptable.

We specifically want feedback on whether:

- `josh` appropriately identifies this protocol;
- its scope is sufficiently narrow;
- existing deployments help justify the name;
- broader community review is sufficient;
- a more specific suffix should be considered.

### Question 2: Specification reference and governance

The protocol currently lives in the public Joshternet specification repository.

The frozen specification under review is available at:

```text
https://github.com/joshternet/spec/blob/ee57ea7c0b1427c100008ca41647ed4dbd50b05d/rfcs/0002-well-known-josh.md
```

Review question:

> Does the current Joshternet specification publication and governance model
> provide a suitable stable reference for the Well-Known URI registry?

The specification has:

- a frozen version 1 protocol revision;
- a public Git history;
- public issues and pull requests;
- a language-neutral conformance corpus;
- production deployment;
- independently operated publishers;
- documented interoperability evidence.

However, current registry guidance places additional scrutiny on specifications
hosted in project-controlled repositories and on single-owner publication
models.

Reviewers are specifically invited to comment on whether:

- the existing publication model is sufficient;
- additional governance or stability documentation would help;
- broader community ownership is necessary;
- an Internet-Draft should precede registration;
- another publication mechanism would be more appropriate.

The project has intentionally not moved the Internet-Draft step earlier without
review evidence that doing so would improve the standards path.

### Question 3: Web browser interaction

RFC-JOSH-0002 defines the associated media type as:

```text
application/json
```

Publishers SHOULD return that media type.

Consumers do not reject an otherwise valid version 1 representation solely
because another Content-Type was returned.

That behavior is deliberate and is covered by the canonical conformance corpus.

Review question:

> Should RFC-JOSH-0002 explicitly recommend publisher-side browser-safety
> response headers, particularly `X-Content-Type-Options: nosniff`, while
> preserving the existing consumer-side Content-Type leniency semantics?

RFC 8615 Section 4.2 discusses interaction between well-known resources and Web
browsers.

RFC-JOSH-0002 already:

- defines a passive JSON representation;
- requires no authentication;
- requires no client-side script execution;
- requires no confidential information;
- defines no cookies;
- defines no browser storage;
- defines no state-changing operation;
- limits authority to the serving origin.

It does not currently make an explicit recommendation about:

```text
X-Content-Type-Options: nosniff
```

or otherwise discuss MIME sniffing directly.

We want review of that gap without conflating publisher security guidance with
consumer declaration-validation rules.

## Specification under review

The canonical frozen specification is:

```text
RFC-JOSH-0002: /.well-known/josh
```

Immutable rendered copy:

```text
https://github.com/joshternet/spec/blob/ee57ea7c0b1427c100008ca41647ed4dbd50b05d/rfcs/0002-well-known-josh.md
```

Immutable raw copy:

```text
https://raw.githubusercontent.com/joshternet/spec/ee57ea7c0b1427c100008ca41647ed4dbd50b05d/rfcs/0002-well-known-josh.md
```

Current repository copy:

```text
https://github.com/joshternet/spec/blob/main/rfcs/0002-well-known-josh.md
```

Reviewers should use the immutable revision when evaluating the Phase 10
baseline.

## Protocol summary

RFC-JOSH-0002 defines one well-known resource:

```text
/.well-known/josh
```

A valid representation declares that the origin serving it participates in the
Joshternet.

Version 1 contains a required `version` member and an optional `josh` member.

Minimum participating origin:

```json
{
  "version": 1
}
```

Affirmed Josh identity:

```json
{
  "version": 1,
  "josh": true
}
```

Declined Josh identity:

```json
{
  "version": 1,
  "josh": false
}
```

An absent `josh` member represents undeclared Josh identity.

The protocol deliberately separates:

```text
participation
```

from:

```text
Josh identity
```

A valid declaration participates even when no Josh identity assertion is made.

## Core protocol behavior

### Origin scope

A declaration applies only to the RFC 6454 origin from which it is retrieved.

Scheme, host, and port all matter.

For:

```text
https://example.invalid/
```

the declaration is:

```text
https://example.invalid/.well-known/josh
```

For:

```text
https://example.invalid:8443/
```

the declaration is:

```text
https://example.invalid:8443/.well-known/josh
```

Consumers MUST NOT probe alternative ports looking for a declaration.

### URI form

The canonical URI path is:

```text
/.well-known/josh
```

Version 1 defines:

- no trailing slash;
- no additional path components;
- no query parameters;
- no fragment identifier.

### Schemes

RFC-JOSH-0002 defines use with:

```text
http
https
```

The exact scheme of the evaluated origin is preserved.

### Retrieval

Consumers use:

```text
GET
```

The declaration must be publicly retrievable without authentication or
client-side script execution.

### Representation

The representation is a JSON object conforming to RFC 8259.

Associated media type:

```text
application/json
```

### Version

Version 1 requires:

```json
{
  "version": 1
}
```

The version value must use integer-number syntax.

These are not valid version 1 values:

```json
{
  "version": 1.0
}
```

```json
{
  "version": 1
}
```

An unsupported integer version must not be interpreted using version 1
semantics.

### Identity

When present:

```text
josh
```

must be a JSON boolean.

```json
{
  "version": 1,
  "josh": true
}
```

means:

```text
Affirmed Josh Identity
```

```json
{
  "version": 1,
  "josh": false
}
```

means:

```text
Declined Josh Identity
```

Absence of the member means:

```text
Undeclared Josh Identity
```

### Unknown members

Unknown members are allowed.

Consumers SHOULD ignore them unless another supported Joshternet specification
defines them.

Unknown members cannot redefine:

- version;
- Josh identity;
- participation by publication.

### Redirects

A declaration SHOULD be served directly.

Consumers MAY follow same-origin redirects.

A cross-origin redirect cannot declare participation for the original origin.

### Removal

A declaration is no longer published when a valid representation is no longer
available.

Responses such as:

```text
404 Not Found
```

and:

```text
410 Gone
```

mean that no declaration is currently published at that location.

Temporary failures do not prove intentional withdrawal.

Examples include:

- server errors;
- DNS failures;
- TLS failures;
- timeouts;
- transport errors.

### Invalid declarations

Version 1 is invalid when:

- the body is not valid JSON;
- the top-level JSON value is not an object;
- `version` is absent;
- `version` is not the integer `1`;
- `josh` is present but not a boolean;
- duplicate JSON member names are present.

## What RFC-JOSH-0002 does not define

The specification intentionally does not define:

- Web crawling;
- discovery;
- registries;
- search;
- navigation;
- profiles;
- feeds;
- social graphs;
- reputation;
- trust;
- moderation;
- abuse handling;
- legal identity;
- proof of personhood;
- ownership relationships between multiple origins;
- multi-person identity declarations.

Those behaviors are outside the scope of this review unless a reviewer believes
the omission makes the version 1 protocol ambiguous or unsafe.

JoshBot behavior outside declaration retrieval and interpretation is not part of
RFC-JOSH-0002.

## Security model

RFC-JOSH-0002 treats declaration contents as untrusted input.

Consumers SHOULD bound:

- response size;
- parsing resources;
- redirects;
- retrieval time.

Publishers SHOULD restrict creation and modification of the declaration to
parties authorized to speak for the origin.

The declaration is public.

Publishers MUST NOT include information requiring confidentiality.

Plain HTTP does not provide protection against modification by an on-path
attacker.

Consumers requiring authenticated transport SHOULD use HTTPS origins and
perform normal TLS certificate validation.

Automated consumers retrieving declarations from untrusted origins SHOULD
protect against:

- SSRF;
- loopback access;
- link-local access;
- private network access;
- reserved destinations;
- otherwise non-public destinations;
- DNS rebinding.

A declaration establishes only that the serving origin publishes that
declaration.

It does not establish:

- legal identity;
- trustworthiness;
- reputation;
- authority over another origin;
- authority within the Joshternet.

## Canonical conformance corpus

The language-neutral version 1 conformance corpus is located at:

```text
https://github.com/joshternet/spec/tree/main/conformance/rfc-josh-0002/v1
```

The corpus revision under review is:

```text
5728bf19b0d193db026cdb5f283ab998cc6bc03d
```

It currently contains 27 consumer fixtures.

The fixtures use protocol-neutral classifications rather than JoshBot internal
types.

Declaration classifications include:

```text
valid-v1
invalid
unsupported-version
absent
temporary-failure
cross-origin-redirect
```

Participation classifications include:

```text
declared
not-declared
indeterminate
```

Identity classifications include:

```text
affirmed
declined
undeclared
not-applicable
```

The optional capability currently represented is:

```text
same-origin-redirects
```

The corpus exercises behavior including:

- affirmed identity;
- declined identity;
- undeclared identity;
- malformed JSON;
- non-object JSON;
- missing version;
- malformed version values;
- unsupported versions;
- invalid `josh` values;
- duplicate members;
- unknown members;
- Content-Type leniency;
- `404 Not Found`;
- `410 Gone`;
- server failures;
- DNS failures;
- TLS failures;
- timeouts;
- transport failures;
- same-origin redirects;
- cross-origin redirects;
- non-default ports;
- prohibition on alternate-port probing;
- canonical declaration URI construction.

Reviewers who believe RFC-JOSH-0002 implies behavior different from the corpus
are encouraged to identify the exact specification section and fixture involved.

## Current consumer implementation

JoshBot is the current project-controlled consumer implementation.

Repository:

```text
https://github.com/joshternet/joshbot
```

Canonical-corpus integration revision:

```text
dc68fae1379dc50a2eced056d37f6a1ee3f2ded1
```

At that revision, JoshBot passes all 27 canonical version 1 fixtures, including
the optional same-origin redirect capability.

JoshBot is evidence of one implementation.

It is not the definition of RFC-JOSH-0002.

If JoshBot and the specification disagree, the disagreement must be
investigated rather than automatically resolving the specification in favor of
JoshBot.

## Interoperability evidence

The current interoperability record is:

```text
https://github.com/joshternet/spec/blob/aa4696f6839192a339425649f5dca04721e5c110/interoperability/rfc-josh-0002/v1/README.md
```

Current demonstrated relationships are:

```text
project publisher -> project consumer
independent publisher -> project consumer
```

Not yet demonstrated:

```text
publisher -> independent consumer
project consumer <-> independent consumer agreement
multiple independent consumers
```

The lack of an independently authored consumer is an explicit limitation of the
current evidence.

The project does not intend to manufacture a nominally independent second
consumer merely to increase an implementation count.

## Live publisher examples

The following deployments were directly observed on September 26, 2026.

### joshternet.org

```text
https://joshternet.org/.well-known/josh
```

Observed representation:

```json
{
  "version": 1
}
```

Interpretation:

```text
declaration: valid-v1
participation: declared
identity: undeclared
```

Operation:

```text
project-controlled
```

### joshuamorris.info

```text
https://joshuamorris.info/.well-known/josh
```

Observed representation:

```json
{
  "version": 1,
  "josh": true
}
```

Interpretation:

```text
declaration: valid-v1
participation: declared
identity: affirmed
```

Operation:

```text
project-controlled
```

### joshtronic.com

```text
https://joshtronic.com/.well-known/josh
```

Observed representation:

```json
{
  "version": 1,
  "josh": true
}
```

Observed Content-Type:

```text
application/octet-stream
```

Interpretation:

```text
declaration: valid-v1
participation: declared
identity: affirmed
```

Operation:

```text
independent
```

This deployment is particularly useful for reviewing the distinction between:

```text
publisher Content-Type recommendation
```

and:

```text
consumer validity requirements
```

### www.joshuabaker.com

```text
https://www.joshuabaker.com/.well-known/josh
```

Observed representation:

```json
{
  "version": 1,
  "josh": true
}
```

Observed Content-Type:

```text
application/json; charset=utf-8
```

Interpretation:

```text
declaration: valid-v1
participation: declared
identity: affirmed
```

Operation:

```text
independent
```

## IANA preparation audit

The Phase 9 preparation document is:

```text
https://github.com/joshternet/spec/blob/a4f85cf63eecd44ee6edc9e588ef0e16b870ca3f/iana/rfc-josh-0002/README.md
```

That audit maps RFC-JOSH-0002 against:

- RFC 8615 Section 3;
- RFC 8615 Section 3.1;
- RFC 8615 Section 4;
- RFC 8615 Sections 4.1 through 4.4;
- RFC 8615 designated-expert considerations;
- current Well-Known URI registry request guidance.

The audit found that the mechanical protocol requirements are substantially
covered.

It identified the three external-review questions documented at the beginning
of this packet:

1. suffix suitability;
2. specification-reference suitability;
3. browser interaction.

Reviewers are encouraged to challenge the Phase 9 audit if they believe it
misreads RFC 8615 or current registry expectations.

## What useful review looks like

The most useful feedback identifies something concrete.

Examples include:

```text
Section 10 is ambiguous about whether redirects can change ports.
```

```text
Fixture X appears inconsistent with Section 6 because...
```

```text
Two independent implementations could reasonably interpret this sentence in
different ways.
```

```text
This security requirement cannot be implemented safely because...
```

```text
The proposed josh registration appears too broad under the registry guidance
because...
```

```text
The existing publication model does not provide sufficient change-control
stability because...
```

Reviewers do not need to provide a proposed fix.

Finding the ambiguity is useful by itself.

## Feedback classification

Review feedback should be classified before changes are made.

### `protocol-defect`

Use when the specification itself is:

- ambiguous;
- contradictory;
- incomplete in a way that affects interoperability;
- unsafe in a way requiring protocol changes;
- inconsistent with a normative dependency.

Example:

```text
Two conforming consumers can produce different outcomes from the same
declaration because the specification does not define X.
```

A `protocol-defect` can justify changing RFC-JOSH-0002.

### `conformance-defect`

Use when the canonical language-neutral conformance corpus disagrees with the
specification or fails to test behavior needed to demonstrate conformance.

Example:

```text
The specification requires X but no fixture covers it.
```

### `implementation-defect`

Use when an implementation such as JoshBot behaves differently from the
specification or canonical corpus.

Example:

```text
JoshBot classifies X as temporary-failure but the canonical fixture requires
invalid.
```

An implementation defect does not justify changing the protocol to match the
implementation.

### `registry-process`

Use for feedback about:

- suffix suitability;
- IANA registration procedure;
- change-controller expectations;
- specification-reference suitability;
- provisional versus permanent status;
- standards-incubation path;
- designated-expert expectations.

Registry-process feedback is not automatically a protocol defect.

### `security`

Use for a vulnerability, unsafe requirement, missing threat analysis, or
security consideration requiring deeper review.

Security feedback may ultimately become:

```text
protocol-defect
```

or:

```text
implementation-defect
```

depending on where the problem actually exists.

### `editorial`

Use when the technical meaning is already clear but wording, organization,
examples, or references could be improved.

Editorial feedback should not change protocol semantics.

### `optional-suggestion`

Use for an idea that might be useful but is not necessary for version 1
correctness or interoperability.

Examples include:

- additional metadata;
- new capabilities;
- discovery behavior;
- profile information;
- crawler features.

Version 1 intentionally follows YAGNI.

Optional ideas should normally become separate future work rather than expanding
RFC-JOSH-0002 during conformance review.

## Recording review feedback

External feedback should be recorded in the specification repository whenever
possible.

Each actionable review item should record:

```text
Source:
Reviewer:
Date:
Specification revision:
Category:
Specification section:
Conformance fixture, if applicable:
Summary:
Resolution:
Status:
```

Recommended status values:

```text
open
needs-investigation
accepted
rejected
deferred
resolved
```

A rejected review item should retain the reasoning for rejection.

A deferred item should explain why it is outside version 1 or current scope.

## Review resolution rules

Review should not cause opportunistic protocol expansion.

Use the following decision order.

### 1. Is there actually a specification problem?

If no:

```text
do not change RFC-JOSH-0002
```

### 2. Is the problem only in an implementation?

If yes:

```text
fix the implementation
```

### 3. Is the problem only in the conformance corpus?

If yes:

```text
fix or expand the corpus
```

### 4. Is the issue about the IANA process rather than protocol behavior?

If yes:

```text
handle it in the registration path
```

### 5. Does the issue expose a genuine version 1 protocol defect?

If yes:

```text
open a dedicated specification issue
```

Then:

1. change the specification explicitly;
2. update the conformance corpus;
3. update affected implementations;
4. rerun the canonical corpus;
5. rerun interoperability evidence;
6. update the IANA audit;
7. update this review baseline.

No review comment should silently change protocol semantics.

## Initial review venues

Phase 10 starts with venues where the questions can receive focused technical
feedback.

### IndieWeb developer community

The IndieWeb community operates a dedicated developer discussion channel:

```text
#indieweb-dev
```

Discussion is bridged across the IndieWeb chat systems.

This venue is useful for:

- independent-site implementer feedback;
- Web deployment experience;
- origin and hosting considerations;
- practical publication experience;
- independent implementation interest.

This should be treated as a technical request for review, not promotion of the
Joshternet.

### Well-Known URI review community

RFC 8615 identifies:

```text
wellknown-uri-review@ietf.org
```

for Well-Known URI registration discussion.

The current registry request process also maintains:

```text
https://github.com/protocol-registries/well-known-uris
```

This venue is particularly relevant to:

- suitability of the bare `josh` suffix;
- specification-reference requirements;
- provisional registration expectations;
- RFC 8615 interpretation;
- browser interaction;
- whether wider standards incubation should precede registration.

During Phase 10, discussion can request technical guidance without pretending
that the project is already making its final registration request.

### Web and security implementers

Focused security review should specifically examine:

- RFC 8615 Section 4.2;
- Content-Type leniency;
- MIME sniffing;
- browser interaction;
- `X-Content-Type-Options`;
- origin authority;
- redirects;
- SSRF;
- DNS rebinding;
- public declaration semantics.

Reviewers should distinguish:

```text
publisher security recommendations
```

from:

```text
consumer conformance requirements
```

### IETF DISPATCH

DISPATCH is a possible later Phase 10 venue.

Its current charter provides a venue for feedback and next-step guidance on new
work in the relevant IETF areas.

Current DISPATCH guidance gives presentation precedence to proposals showing
evidence of interest through:

```text
active Internet-Drafts
```

and:

```text
mailing-list discussion
```

The Joshternet currently has neither an active RFC-JOSH-0002 Internet-Draft nor
DISPATCH list discussion.

For that reason, DISPATCH should not be treated as the first outreach step.

Earlier external review should help determine whether moving the Internet-Draft
track forward would materially improve the standards path.

## Outreach draft: IndieWeb developer discussion

This text is prepared for later manual posting.

It has not been posted by this repository change.

```text
Hi all. I’m looking for technical review of a very small Web protocol I’ve
been working on as part of the Joshternet.

RFC-JOSH-0002 defines /.well-known/josh, a JSON declaration that lets an
origin voluntarily declare participation and optionally declare Josh identity.

The protocol is frozen at version 1, has a language-neutral 27-case conformance
suite, one consumer implementation, and several live publishers including two
independently operated sites.

I’m not looking for feedback on whether the Joshternet itself is a good idea.
The question I’m trying to answer is much narrower:

Can somebody implement /.well-known/josh correctly using only the
specification?

I’d especially appreciate people looking for ambiguity around origin scope,
ports, redirects, JSON/version validation, removal behavior, and Web security.

The review packet is here:

https://github.com/joshternet/spec/tree/main/review/rfc-josh-0002

The frozen specification is linked from there, along with the conformance
fixtures and interoperability evidence.

If anything can reasonably be interpreted two different ways, I want to know
about it before taking the protocol any further.
```

## Outreach draft: Well-Known URI review

This text is prepared for later review and manual submission.

It is not an IANA registration request.

Suggested subject:

```text
Early review request: proposed /.well-known/josh protocol
```

Draft:

```text
Hello,

I’m seeking early technical feedback on a proposed Well-Known URI before making
any registration request.

RFC-JOSH-0002 defines:

    /.well-known/josh

as a small JSON declaration through which an origin can voluntarily declare
participation in the Joshternet and optionally express Josh identity.

Version 1 has been frozen for review. There is a language-neutral conformance
corpus with 27 consumer fixtures, a consumer implementation that runs that
corpus, and multiple live publishers, including independently operated
deployments.

I have completed a preliminary RFC 8615 audit and am deliberately asking for
review before requesting registration.

There are three questions I would particularly value guidance on:

1. The desired registered suffix is the bare name "josh". Given the current
   guidance regarding common names, is the protocol's narrow scope and existing
   deployment enough to make that a reasonable candidate, or should a more
   specific name be considered?

2. The specification is currently maintained publicly in the Joshternet GitHub
   organization with a frozen protocol revision, conformance suite, public
   change history, and interoperability evidence. Is that publication and
   governance model likely to be an acceptable specification reference, or
   would an Internet-Draft or another publication path be preferable before
   registration?

3. RFC-JOSH-0002 associates the declaration with application/json, while
   consumers intentionally do not reject an otherwise valid declaration solely
   because a different Content-Type was returned. Should the specification add
   an explicit publisher-side recommendation such as
   X-Content-Type-Options: nosniff to better address RFC 8615 Section 4.2
   without changing consumer-side Content-Type leniency?

The complete external-review packet is:

https://github.com/joshternet/spec/tree/main/review/rfc-josh-0002

The frozen protocol, conformance corpus, interoperability record, and RFC 8615
audit are all linked from that document.

I am not requesting registration yet. I’m trying to discover specification or
process problems before reaching that point.

Thank you for any technical feedback.
```

## Outreach draft: security review

This text is prepared for sharing with Web/security implementers.

```text
I’m looking for a security review of a very small Web protocol before moving
toward standards registration.

RFC-JOSH-0002 defines /.well-known/josh as a publicly retrievable JSON object.
It requires no authentication, contains no required personal information,
defines no state-changing behavior, and applies only to the exact RFC 6454
origin serving it.

The specification already discusses response-size/parser limits, redirect
limits, TLS, SSRF, private/local destinations, DNS rebinding, write authority,
cross-origin authority, and confidentiality.

The question I’m least satisfied with is RFC 8615 Section 4.2 browser
interaction.

The associated media type is application/json and publishers SHOULD return it,
but consumers intentionally accept an otherwise valid declaration even if the
server returns another Content-Type. That behavior is already represented in
the language-neutral conformance suite and in a real independent deployment.

I’d like review of whether the specification should explicitly recommend
publisher-side protections such as:

    X-Content-Type-Options: nosniff

without changing the consumer validation semantics.

I’d also appreciate review for any threat that the current Security
Considerations section has missed.

Review packet:

https://github.com/joshternet/spec/tree/main/review/rfc-josh-0002
```

## Future DISPATCH preparation

No DISPATCH request is being made during creation of this review packet.

If Phase 10 feedback indicates that IETF discussion would be useful, the
project should first decide whether to create an Internet-Draft from the frozen
RFC-JOSH-0002 specification.

A future DISPATCH proposal should have a clear answer to:

```text
What interoperability problem exists?
```

```text
What specification currently solves it?
```

```text
Who has implemented it?
```

```text
What independent interest exists?
```

```text
What action or guidance is being requested from the IETF?
```

DISPATCH should not be approached merely to obtain a badge of legitimacy for
the Joshternet.

Its value would be architectural and process guidance.

## Internet-Draft decision

The current roadmap places an Internet-Draft after provisional IANA
registration.

Phase 10 review may change that ordering.

Move the Internet-Draft work earlier if external review indicates that doing so
would materially improve:

- specification stability;
- governance credibility;
- standards-community participation;
- registered-name review;
- designated-expert confidence;
- interoperability review.

Do not move it earlier merely because an Internet-Draft sounds more official.

The decision should be based on evidence from review.

## Review checklist

A reviewer does not need to answer every question.

### Protocol mechanics

- Is the canonical declaration URI unambiguous?
- Is origin scope unambiguous?
- Are non-default ports unambiguous?
- Is prohibition of alternate-port probing clear?
- Are HTTP and HTTPS semantics clear?
- Are redirect rules clear?
- Are cross-origin redirects handled safely?
- Is the JSON representation sufficiently specified?
- Is version-number syntax clear?
- Is `josh` validation clear?
- Are unknown members handled clearly?
- Are duplicate members handled clearly?
- Are unsupported versions handled clearly?
- Are removal semantics clear?
- Are temporary failures distinguishable from removal?
- Is Content-Type behavior clear?
- Can two reasonable implementers classify the same response differently?

### Security

- Are resource limits sufficiently addressed?
- Is origin authority sufficiently constrained?
- Are write-authority concerns addressed?
- Are SSRF concerns addressed?
- Is DNS rebinding addressed?
- Is TLS behavior clear?
- Is cross-origin authority sufficiently constrained?
- Are browser interaction risks adequately discussed?
- Should `nosniff` be recommended?
- Does Content-Type leniency create an unexpected security problem?
- Does allowing unknown members introduce a meaningful risk?
- Is any sensitive information accidentally required or encouraged?

### Privacy

- Does the protocol actually remain usable without personal information?
- Does the identity declaration expose a privacy problem not addressed in the
  current specification?
- Are extension-member privacy risks adequately described?

### Interoperability

- Can a second consumer be implemented from the specification alone?
- Does the conformance corpus accurately represent the specification?
- Are any important normative behaviors missing fixtures?
- Are any fixtures stricter than the specification?
- Are any fixtures more permissive than the specification?
- Does existing deployment expose assumptions not stated in the RFC?

### Registry

- Is `josh` sufficiently specific?
- Is the requested scope consistent with the name?
- Is provisional status appropriate?
- Is the proposed change controller adequate?
- Is the current specification reference suitable?
- Is the specification mature enough for registration review?
- Should broader incubation happen first?
- Would an Internet-Draft materially improve the path?

## Review outcomes

Phase 10 does not require every reviewer to agree.

Possible outcomes include:

```text
no protocol changes required
```

```text
editorial clarification required
```

```text
conformance corpus correction required
```

```text
implementation correction required
```

```text
security clarification required
```

```text
protocol defect discovered
```

```text
registration process change required
```

```text
more implementation evidence needed
```

```text
Internet-Draft should move earlier
```

```text
registered suffix should be reconsidered
```

A negative review finding is useful evidence.

The purpose of review is to find weaknesses while they are still inexpensive
to correct.

## Phase 10 exit conditions

External technical review is complete enough to make the next standards
decision when:

- the packet has been shared with appropriate Web implementers;
- the protocol has received independent technical feedback;
- the three registration-specific questions have received meaningful review;
- security feedback has addressed RFC 8615 Section 4.2;
- all actionable feedback has been classified;
- genuine protocol defects have dedicated issues;
- implementation defects have dedicated implementation issues;
- conformance defects have dedicated corpus issues;
- registry-process concerns are documented separately;
- any accepted protocol changes have been reflected in the conformance corpus;
- interoperability has been rerun after any protocol change;
- the Internet-Draft ordering decision has been revisited;
- there are no known unresolved ambiguities that would prevent independent
  implementation.

Phase 10 does not itself submit the IANA registration.

After review, the project should make an explicit decision among:

```text
proceed toward provisional IANA registration
```

```text
move the Internet-Draft track earlier
```

```text
revise RFC-JOSH-0002 and repeat conformance/interoperability review
```

```text
gather additional independent implementation evidence
```

```text
reconsider the requested suffix
```

The decision should follow the evidence collected during review.
