# RFC-JOSH-0002 Provisional IANA Registration Preparation

This document prepares the proposed provisional IANA Well-Known URI
registration for RFC-JOSH-0002.

It is non-normative.

RFC-JOSH-0002 remains the authority for the `/.well-known/josh` protocol. This
document audits the frozen version 1 specification against RFC 8615, records
current Well-Known URI registry guidance, and prepares the proposed
registration package before external technical review.

No registration request has been submitted as part of this work.

## Baseline

This preparation document uses the following protocol and process baselines:

| Artifact | Revision |
| --- | --- |
| RFC-JOSH-0002 | `ee57ea7c0b1427c100008ca41647ed4dbd50b05d` |
| Version 1 conformance corpus | `5728bf19b0d193db026cdb5f283ab998cc6bc03d` |
| Interoperability evidence | `aa4696f6839192a339425649f5dca04721e5c110` |
| JoshBot canonical-corpus integration | `dc68fae1379dc50a2eced056d37f6a1ee3f2ded1` |
| Well-Known URI registry request guidance | `8034e51a59d8d09784632df4686987bebd6d8110` |

The frozen RFC-JOSH-0002 specification is the protocol baseline for this
audit. The audit must not redefine the protocol.

If review exposes a genuine specification defect, that defect should be handled
as an explicit specification change rather than silently corrected in this
document.

The Well-Known URI registry request guidance is maintained separately from
RFC 8615. It represents current designated-expert process guidance and can
therefore impose practical review expectations beyond the minimum normative
requirements stated in RFC 8615.

## Registry status at preparation time

The IANA Well-Known URIs registry is defined by RFC 8615.

At the time this package was prepared:

- the registry procedure is `Specification Required`;
- registrations are reviewed by one or more designated experts;
- the current registry identifies Mark Nottingham as the designated expert;
- the registry contains permanent and provisional registrations;
- the registry was last updated on September 16, 2026;
- no `josh` URI suffix is registered.

The proposed registration therefore does not duplicate an existing `josh`
entry.

The intended initial status remains:

```text
provisional
```

RFC 8615 states that values not defined by Standards Track RFCs or other
recognized permanent open standards should normally be registered as
provisional.

## Current registry request process

The current Well-Known URI registry request process is maintained at:

```text
https://github.com/protocol-registries/well-known-uris
```

A new registration can currently be requested by:

1. filing an issue in that repository, which is the preferred method; or
2. sending a request to the `wellknown-uri-review@ietf.org` mailing list.

Approval through that review process precedes incorporation into the official
IANA registry.

The registry request guidance also adds practical considerations that matter
for this proposal and are not safe to infer solely from the text of RFC 8615.

Those considerations are documented below rather than treated as already
resolved.

## Proposed registration

The current candidate registration is:

```text
URI suffix:
josh

Change controller:
Joshua Morris, Joshternet, https://joshternet.org/

Specification document(s):
RFC-JOSH-0002: /.well-known/josh

Status:
provisional

Related information:
https://joshternet.org/
https://github.com/joshternet/spec
https://github.com/joshternet/joshbot
```

This is a preparation template, not a final submission.

Two fields in particular remain subject to external review:

```text
URI suffix
Specification document(s)
```

The current designated-expert guidance creates material review questions for
both.

## Candidate specification location

The frozen specification is publicly retrievable at an immutable Git commit.

Candidate rendered URI:

```text
https://github.com/joshternet/spec/blob/ee57ea7c0b1427c100008ca41647ed4dbd50b05d/rfcs/0002-well-known-josh.md
```

Candidate raw URI:

```text
https://raw.githubusercontent.com/joshternet/spec/ee57ea7c0b1427c100008ca41647ed4dbd50b05d/rfcs/0002-well-known-josh.md
```

Those locations provide immutable access to the exact specification revision
used by this preparation work.

However, immutability alone does not establish that the GitHub document will
be accepted as a suitable specification reference.

Current Well-Known URI registry guidance says that a stable specification
reference is required and that publication by a recognized open standards body
is preferred.

The guidance also says that specifications published by established open
source projects, community organizations, or commercial organizations can be
accepted when there is a reasonable plan for specification stability.

It further warns that specifications hosted on single-purpose websites or
GitHub repositories are not eligible without significant deployment and/or
community support, and specifically identifies single-owner GitHub repositories
as unsuitable references.

RFC-JOSH-0002 therefore has a real specification-reference review question.

The Joshternet project currently has evidence beyond an unpublished design:

- a public specification;
- a language-neutral conformance corpus;
- a production consumer;
- multiple live publishers;
- independently operated publishers;
- documented interoperability.

Whether that evidence is sufficient to satisfy the registry expert's
expectations for deployment and community support must be reviewed externally.

This document must not assume that the immutable GitHub URL is acceptable
merely because the content at that URL is stable.

## Candidate suffix

The requested suffix is:

```text
josh
```

RFC 8615 requires registered names to conform to the RFC 3986 `segment-nz`
production and recommends that application-specific names be correspondingly
precise rather than unnecessarily generic.

The value `josh` satisfies the syntax requirement.

Current registry guidance adds a practical concern.

The guidance says that a request to register a common name without broad
community discussion and support is likely to result in a recommendation to:

- choose a more specific name; or
- engage in broader community discussion first.

It identifies a single common word as an example of a name likely to face
objection unless submitted by a recognized standards organization or supported
by sufficient community review.

`josh` is intentionally the protocol's name and directly describes the
Joshternet declaration.

It is not intended as a generic identifier for:

- people;
- identity generally;
- profiles;
- metadata;
- social networking;
- discovery generally.

Nevertheless, it is a short bare name and a common personal name.

The suitability of `josh` itself must therefore be treated as an external
review question rather than as already settled.

This preparation work does not change the requested suffix preemptively.

## Current process implications

The current designated-expert guidance materially affects the roadmap.

It does not establish that `josh` will be rejected.

It does establish that we should not proceed directly from an internally
complete registration package to submission without wider technical review.

Before submission we need evidence addressing:

1. whether `josh` is sufficiently specific and supported to justify the bare
   name;
2. whether the current specification publication model is suitable;
3. whether the current deployment and independent implementation evidence
   demonstrates enough real use and community participation;
4. whether broader standards-community review should occur before requesting
   registration.

The registry guidance strongly recommends engagement with a broader community,
such as IETF DISPATCH or another appropriate standards-incubation process,
before registration.

It also discourages anticipatory registration requests from open source,
community, and commercial projects.

That guidance is consistent with the existing Joshternet roadmap decision to
perform external technical review before submitting anything to IANA.

## Related evidence

The registration package may provide the following as supporting information.

### Project

```text
https://joshternet.org/
```

This is the public Joshternet project and network site.

It is not the protocol specification.

### Canonical specification repository

```text
https://github.com/joshternet/spec
```

This repository contains the Joshternet RFCs, conformance suite,
interoperability evidence, and this IANA preparation material.

### Conformance suite

```text
https://github.com/joshternet/spec/tree/main/conformance/rfc-josh-0002/v1
```

The version 1 conformance suite is language-neutral and exercises the protocol
independently of JoshBot's internal types.

The reviewed corpus revision is:

```text
5728bf19b0d193db026cdb5f283ab998cc6bc03d
```

### Interoperability evidence

```text
https://github.com/joshternet/spec/tree/main/interoperability/rfc-josh-0002/v1
```

The interoperability record documents project-controlled and independently
operated publishers and JoshBot's current consumer behavior.

The current evidence includes independently operated publishers but not an
independently authored consumer.

That limitation should remain visible during external review.

### JoshBot

```text
https://github.com/joshternet/joshbot
```

JoshBot is one implementation and consumer of RFC-JOSH-0002.

JoshBot is not the specification and does not define the protocol.

## Conceptual boundaries

The registration package must keep four concepts separate.

```text
RFC-JOSH
    defines the Joshternet protocol.

IANA
    coordinates registration of the josh well-known URI suffix.

JoshBot
    is one implementation and consumer of the protocol.

Joshternet.org
    is one network and project site using the protocol.
```

Registration of `josh` would not make RFC-JOSH an IETF standard.

Registration would not make JoshBot an IETF reference implementation.

Registration would not make Joshternet.org authoritative over implementations
of the protocol.

Registration would not imply IETF or IANA endorsement of the Joshternet.

## RFC 8615 Section 3 audit

RFC 8615 Section 3 defines the general requirements for applications using
well-known URIs.

Each applicable requirement is audited below.

### Well-known URI path form

RFC 8615 defines a well-known URI as one whose path begins with:

```text
/.well-known/
```

RFC-JOSH-0002 Section 3 requires:

```text
/.well-known/josh
```

RFC-JOSH-0002 Section 3.2 identifies the registered suffix as:

```text
josh
```

and the canonical path as:

```text
/.well-known/josh
```

Status:

```text
covered
```

### Registered-name syntax

RFC 8615 requires a registered name to conform to the RFC 3986 `segment-nz`
production and therefore not contain `/`.

The proposed name is:

```text
josh
```

It is non-empty and contains no `/`.

Status:

```text
covered
```

### Name specificity

RFC 8615 discourages claiming unnecessarily generic names and recommends names
that are appropriately precise for the application.

The requested name is:

```text
josh
```

The name directly identifies the Joshternet declaration defined by
RFC-JOSH-0002.

The RFC itself narrowly limits the resource to Joshternet participation and
optional Josh identity.

From the protocol's own scope, the name is specific to the Joshternet
application.

Current designated-expert guidance nevertheless identifies bare common words as
names likely to require broader community discussion or greater specificity.

Because `josh` is both a short bare name and a common personal name, the
protocol-level rationale does not by itself settle the registry-level naming
question.

Status:

```text
syntax covered; name suitability requires external review
```

### Representation format

RFC 8615 requires the referenced specification to define the representation
obtained by dereferencing the well-known URI.

RFC-JOSH-0002 Section 5 requires the representation to be a JSON object
conforming to RFC 8259.

Version 1 defines:

```text
version
josh
```

with exact validation semantics defined in Sections 5 through 8 and Section 12.

Status:

```text
covered
```

### Associated media type

RFC 8615 requires the specification to define the associated media type or
media types.

RFC-JOSH-0002 Section 5 defines:

```text
application/json
```

as the associated media type.

Publishers SHOULD return:

```text
Content-Type: application/json
```

The protocol does not make the Content-Type response field a prerequisite for
consumer interpretation of an otherwise valid version 1 representation.

That behavior is intentional and is represented in the canonical conformance
suite.

Status:

```text
covered for RFC 8615 Section 3
```

Browser-security implications of Content-Type leniency are considered
separately in the Section 4.2 audit below.

### URI schemes

RFC 8615 requires the specification to define the URI schemes with which the
well-known URI is used.

RFC-JOSH-0002 Section 3.1 explicitly defines:

```text
http
https
```

RFC 8615 itself defines HTTP and HTTPS as schemes supporting well-known URIs.

Status:

```text
covered
```

### Default and alternative ports

RFC 8615 says applications typically use the default port for a scheme and
requires alternative-port use to be explicitly specified by the application.

RFC-JOSH-0002 Section 3.1 defines declaration retrieval using the exact scheme,
host, and port of the origin being evaluated.

For a non-default port such as:

```text
https://example.invalid:8443/
```

the declaration is:

```text
https://example.invalid:8443/.well-known/josh
```

Consumers MUST NOT probe alternate ports.

Status:

```text
covered
```

### Additional path components

RFC 8615 permits registrations to define additional path-component syntax.

RFC-JOSH-0002 Section 3.2 explicitly defines no additional path components.

The canonical path is exactly:

```text
/.well-known/josh
```

Status:

```text
covered
```

### Query syntax

RFC 8615 permits registrations to define query-string syntax.

RFC-JOSH-0002 Section 3.2 explicitly defines no query parameters for the
declaration URI.

Status:

```text
covered
```

### Fragment syntax

RFC 8615 permits registrations to define fragment syntax.

RFC-JOSH-0002 Section 3.2 explicitly defines no fragment identifiers for the
declaration URI.

Status:

```text
covered
```

### HTTP method behavior

RFC 8615 permits registration specifications to define protocol-specific
details such as HTTP method handling.

RFC-JOSH-0002 Section 9 requires consumers to use:

```text
GET
```

before interpreting a declaration.

Status:

```text
covered
```

### Hostname discovery

RFC 8615 does not define how an application determines which hostname to use
for a well-known URI. The application must define that behavior.

RFC-JOSH-0002 does not perform hostname discovery.

A consumer evaluates a specific RFC 6454 origin and retrieves the declaration
using that origin's scheme, host, and port.

Status:

```text
covered
```

### Scope of discovered metadata

RFC 8615 requires applications to define the scope of information obtained from
the well-known URI.

RFC-JOSH-0002 repeatedly defines exact-origin scope.

Relevant sections include:

```text
Section 3
Section 3.1
Section 14
```

A declaration applies only to the origin serving it.

It does not automatically apply to:

- another subdomain;
- another hostname;
- another scheme;
- another port;
- an organizationally related origin.

Status:

```text
covered
```

### Rooted path hierarchy

RFC 8615 specifies that well-known URIs exist at the root of the path
hierarchy.

RFC-JOSH-0002 defines only:

```text
/.well-known/josh
```

It does not define forms such as:

```text
/foo/.well-known/josh
```

Status:

```text
covered
```

## RFC 8615 Section 3.1 registration-field audit

RFC 8615 Section 3.1 identifies the information required for a Well-Known URI
registration.

### URI suffix

Candidate value:

```text
josh
```

The value is syntactically valid.

The current registry's name-selection guidance creates a separate suitability
question because `josh` is a short bare name.

Status:

```text
syntactically ready; suitability requires external review
```

### Change controller

RFC-JOSH-0002 Section 20 currently states:

```text
Joshua Morris, Joshternet, https://joshternet.org/
```

RFC 8615 requires non-IETF registrations to identify the responsible party and
allows additional details such as an email address or home-page URI.

The existing value has the required responsible-party structure.

The exact wording and durable contact information should be reviewed before
submission so that future registry maintenance does not depend on a single
repository account.

Status:

```text
ready for external review
```

### Specification document

The frozen RFC-JOSH-0002 document defines the registered resource.

Immutable candidate URI:

```text
https://github.com/joshternet/spec/blob/ee57ea7c0b1427c100008ca41647ed4dbd50b05d/rfcs/0002-well-known-josh.md
```

The document is public and stable at that revision.

Current registry guidance, however, says that repository-hosted and
single-purpose specification references require meaningful deployment and/or
community support and specifically warns against single-owner GitHub
specifications.

The suitability of the current publication model must therefore be established
during external review rather than assumed.

Possible outcomes include:

- the current publication model is accepted based on deployment and community
  evidence;
- stronger project governance or specification-stability commitments are
  requested;
- broader community review is requested;
- an Internet-Draft or another standards-community publication path is brought
  forward in the roadmap;
- the designated expert recommends another stable specification publication
  mechanism.

This preparation document does not choose among those outcomes in advance.

Status:

```text
stable content exists; registry-reference suitability unresolved
```

### Status

Proposed value:

```text
provisional
```

RFC-JOSH-0002 remains a Joshternet Draft rather than a Standards Track RFC or
other recognized permanent open standard.

RFC 8615 says other values should normally be registered as provisional.

Status:

```text
ready
```

### Related information

Candidate related information includes:

```text
https://joshternet.org/
https://github.com/joshternet/spec
https://github.com/joshternet/joshbot
```

The conformance and interoperability records can also be supplied if useful to
the designated expert.

Status:

```text
ready for external review
```

## RFC 8615 Section 4 audit

RFC 8615 requires applications defining well-known URIs to consider security
issues associated with origin-wide resources.

The following audit maps those considerations to RFC-JOSH-0002.

## RFC 8615 Section 4 general security considerations

RFC 8615 calls out several general classes of risk.

### Sensitive-data exposure

RFC-JOSH-0002 Section 17 states that declarations are publicly retrievable and
MUST NOT contain information requiring confidentiality.

Section 18 states that the protocol requires no personal information.

The minimum declaration is:

```json
{
  "version": 1
}
```

Status:

```text
covered
```

### Denial of service and load

RFC-JOSH-0002 Section 17 tells consumers to apply reasonable limits to:

- response size;
- parsing resources;
- redirects;
- retrieval time.

The protocol defines one declaration URI for an already selected origin and
explicitly prohibits probing alternate ports.

It does not define broad hostname discovery or service bootstrapping.

JoshBot's additional crawl budgets, retries, and operational controls are
implementation policy and are not relied on for protocol conformance.

Status:

```text
covered at protocol level
```

### Authentication

RFC 8615 identifies server and client authentication as security
considerations.

RFC-JOSH-0002 Section 9 requires declarations to be publicly retrievable
without authentication.

The declaration is therefore not an authenticated user resource.

Section 17 explains that declarations retrieved over plain HTTP do not receive
on-path integrity protection and that consumers requiring authenticated
transport SHOULD use HTTPS origins with normal TLS certificate validation.

Retrieving a declaration establishes only that the serving origin publishes the
representation.

It does not establish:

- legal identity;
- trustworthiness;
- reputation;
- authority over another origin;
- authority within the Joshternet.

Status:

```text
covered
```

### DNS rebinding and SSRF

RFC-JOSH-0002 Section 17 explicitly addresses automated retrieval from
untrusted or user-supplied origins.

Consumers SHOULD protect local network boundaries against SSRF and similar
attacks.

The section specifically calls out:

- loopback destinations;
- link-local destinations;
- private destinations;
- reserved destinations;
- otherwise non-public destinations;
- DNS rebinding between address validation and connection establishment.

Status:

```text
covered
```

### Limited write access affecting well-known resources

RFC-JOSH-0002 Section 17 states that operators SHOULD restrict creation or
modification of `/.well-known/josh` to parties authorized to speak for the
origin.

Status:

```text
covered
```

## RFC 8615 Section 4.1: Protecting Well-Known Resources

RFC 8615 warns that a well-known resource effectively speaks for an origin and
therefore requires careful write control.

RFC-JOSH-0002 Section 17 says:

```text
Because a declaration represents the origin serving it, server operators
SHOULD restrict the ability to create or modify /.well-known/josh to parties
authorized to speak for that origin.
```

The protocol also limits the declaration's authority to the exact serving
origin.

Status:

```text
covered
```

## RFC 8615 Section 4.2: Interaction with Web Browsing

RFC 8615 notes that HTTP and HTTPS well-known resources are accessible to Web
browsers and share an origin security boundary with other Web content.

Content elsewhere on the same origin can potentially interact with a
well-known resource.

RFC 8615 lists possible mitigations depending on the nature of the application,
including:

- avoiding sensitive information;
- careful handling of cookies and other shared origin capabilities;
- `X-Content-Type-Options: nosniff`;
- application-specific media types with strict client checking;
- Content Security Policy;
- Referrer Policy;
- avoiding compression of sensitive information.

Those examples are not universal protocol requirements. Their applicability
depends on the application being defined.

### Existing RFC-JOSH-0002 protections

RFC-JOSH-0002 already has several properties that reduce Section 4.2 risk.

The declaration:

- is a small JSON object;
- is retrieved using `GET`;
- must be retrievable without client-side script execution;
- requires no authentication;
- contains no required secrets or personal information;
- MUST NOT contain information requiring confidentiality;
- does not define cookies;
- does not define browser storage;
- does not define authentication tokens;
- does not define state-changing browser behavior;
- applies only to the exact serving origin.

### Content-Type leniency

RFC-JOSH-0002 associates the declaration with:

```text
application/json
```

and says a publisher SHOULD return that Content-Type.

Consumers do not reject an otherwise valid declaration solely because the
response uses another Content-Type.

This is intentional.

The canonical conformance corpus includes a Content-Type leniency fixture.

Current interoperability evidence also includes an independently operated
publisher serving a valid declaration as:

```text
application/octet-stream
```

JoshBot correctly interprets that representation under the existing protocol.

Changing consumers to require `application/json` would therefore be a protocol
change and is not part of this audit.

### Remaining browser-interaction question

RFC-JOSH-0002 does not explicitly discuss MIME sniffing or recommend
publisher-side browser-safety response headers such as:

```text
X-Content-Type-Options: nosniff
```

RFC 8615 specifically identifies that header as one possible mitigation against
attacker-controlled content being interpreted as active browser content.

The protocol's passive JSON design and lack of secrets reduce the consequence
of this risk, but the frozen specification does not expressly document the
browser-interaction analysis.

Audit status:

```text
partial
```

Recommended handling:

```text
external security review required before IANA submission
```

This audit does not recommend changing the consumer-side Content-Type
leniency rule merely to address this point.

One possible specification clarification, if external review concludes it is
worthwhile, would be a publisher-side security recommendation to:

- serve the declaration using the associated `application/json` media type;
  and
- return `X-Content-Type-Options: nosniff`.

That would need to be proposed explicitly as an RFC-JOSH-0002 change and
reviewed against existing deployments and the conformance corpus.

It must not be introduced through this non-normative preparation document.

## RFC 8615 Section 4.3: Scoping Applications

RFC 8615 says applications must define both how the relevant well-known URI is
selected and the scope of information retrieved from it.

RFC-JOSH-0002 is explicit on both points.

The URI is constructed from the exact RFC 6454 origin being evaluated.

The declaration applies only to that exact origin.

RFC-JOSH-0002 explicitly rejects extending authority based on:

- subdomain relationships;
- shared hostnames;
- related domain names;
- organizational relationships;
- different ports;
- cross-origin redirects.

The protocol also does not use the well-known URI to bootstrap an unrelated
service on another hostname.

Status:

```text
covered
```

## RFC 8615 Section 4.4: Hidden Capabilities

RFC 8615 warns that server administrators may overlook `.well-known` paths and
that write access to such a path could unexpectedly grant control over an
origin-wide declaration.

RFC-JOSH-0002 Section 17 explicitly states that server operators SHOULD
restrict creation and modification of `/.well-known/josh` to parties
authorized to speak for the origin.

The declaration's effect is also deliberately narrow.

Control of the resource can declare only:

- Joshternet participation for that origin;
- an optional Josh identity state for that origin.

It cannot establish:

- legal identity;
- trust;
- reputation;
- authority over another origin;
- authority within the Joshternet.

Status:

```text
covered
```

## RFC 8615 Section 5.1 expert-review considerations

RFC 8615 says the designated experts' primary considerations when evaluating a
registration are:

1. conformance to Section 3;
2. availability and stability of the specifying document;
3. the considerations in Section 4.

### Section 3 conformance

Most Section 3 protocol requirements are covered.

One Section 3 issue remains subject to expert judgment:

```text
whether the bare name josh is sufficiently precise
```

Audit result:

```text
protocol mechanics covered; registered-name suitability requires review
```

### Specification availability and stability

RFC-JOSH-0002 is publicly available in the Joshternet specification repository.

The protocol baseline is pinned to:

```text
ee57ea7c0b1427c100008ca41647ed4dbd50b05d
```

The version 1 semantics have been frozen for IANA preparation.

A language-neutral conformance corpus exists.

JoshBot runs the canonical consumer corpus.

Independent publisher interoperability has been documented.

However, current registry guidance places additional weight on the publication
and governance context of non-standards-body specifications.

The specification currently lives in a project GitHub repository.

That means the following must be established through external review:

- whether the project demonstrates sufficient community support;
- whether deployment is sufficiently significant;
- whether the specification-stability plan is credible;
- whether the current GitHub-hosted document is an acceptable registry
  reference;
- whether a stronger publication path should precede registration.

Audit result:

```text
public and technically stable; registry-reference suitability unresolved
```

### Section 4 considerations

Sections 4, 4.1, 4.3, and 4.4 are explicitly represented by existing
RFC-JOSH-0002 security and scope requirements.

Section 4.2 is substantially mitigated by the protocol's passive public JSON
design, but browser interaction is not explicitly addressed in the frozen
specification.

Audit result:

```text
partial
```

The browser-interaction question remains an external-review item.

## Current registry-guidance audit

RFC 8615 defines the registry itself.

The current designated-expert request guidance additionally describes the
practical expectations for submissions.

Those expectations are audited separately here so that they are not confused
with RFC 8615 normative requirements.

### Common or overly broad names

Current guidance warns that single common words are likely to face rejection or
a request for broader discussion unless there is sufficient justification and
community support.

Candidate:

```text
josh
```

Status:

```text
open review item
```

### Stable specification reference

A frozen Git commit provides content immutability.

Current registry guidance requires more than a technically stable URL when the
specification originates outside a recognized standards organization.

Status:

```text
open review item
```

### Community and deployment support

Current guidance permits specifications from open source projects, communities,
and commercial organizations when there is an appropriate stability plan and
sufficient evidence of deployment and/or community support.

Current Joshternet evidence includes:

- multiple deployed publishers;
- two independently operated publishers;
- a production consumer;
- a language-neutral conformance corpus;
- a public specification;
- public issue and pull-request development;
- interoperability evidence.

There is not yet a documented independently authored consumer.

Status:

```text
evidence exists; sufficiency requires external review
```

### Timing of registration

Current guidance says registration should generally occur once a document is
mature enough for wide review.

It explicitly says registration should not be used merely as a proposal for
standardization.

For open source, community, and commercial specifications, anticipatory
requests are discouraged and may be refused or delayed.

Status:

```text
do not submit yet
```

### Broader technical review

Current guidance strongly recommends engagement with a broader community before
registration and specifically names processes such as IETF DISPATCH and W3C
incubation as examples.

Joshternet's Phase 10 external-review stage therefore aligns with current
registry expectations and should occur before submission.

Status:

```text
required by project gate and strongly recommended by registry guidance
```

## Audit summary

| Topic | RFC-JOSH-0002 / project coverage | Result |
| --- | --- | --- |
| `/.well-known/` path form | Sections 3, 3.2 | Covered |
| `segment-nz` syntax | `josh` | Covered |
| Registered-name suitability | `josh` | External review required |
| Representation format | Section 5 | Covered |
| Associated media type | Section 5 | Covered |
| URI schemes | Section 3.1 | Covered |
| Alternative ports | Section 3.1 | Covered |
| Additional path syntax | Section 3.2 | Covered |
| Query syntax | Section 3.2 | Covered |
| Fragment syntax | Section 3.2 | Covered |
| Method behavior | Section 9 | Covered |
| Hostname/origin selection | Sections 3, 3.1 | Covered |
| Metadata scope | Sections 3, 14 | Covered |
| URI suffix registration field | Section 20 | Syntax ready, name review open |
| Change controller | Section 20 | Ready for review |
| Stable specification content | Frozen RFC-JOSH-0002 | Covered |
| Registry-reference suitability | Project-hosted specification | External review required |
| Provisional status | Section 20 | Ready |
| Sensitive information | Sections 17, 18 | Covered |
| Denial of service | Section 17 | Covered |
| Authentication | Sections 9, 17 | Covered |
| DNS rebinding / SSRF | Section 17 | Covered |
| Write authority | Section 17 | Covered |
| RFC 8615 §4.1 resource protection | Section 17 | Covered |
| RFC 8615 §4.2 Web browsing interaction | Section 17 / protocol design | Partial |
| RFC 8615 §4.3 application scope | Sections 3, 10, 14, 17 | Covered |
| RFC 8615 §4.4 hidden capabilities | Section 17 | Covered |
| Deployment evidence | Interoperability record | Exists |
| Independent publishers | Interoperability record | Exists |
| Independent consumer | None documented | Missing |
| Broader community review | Not yet performed | Required before project submission |
| Registration timing | Phase 9 preparation | Do not submit yet |

## Open review items

The Phase 9 audit identifies three material questions that must be taken into
external review.

### 1. Suffix suitability

```text
Is josh sufficiently specific, deployed, and community-supported to justify
registration as the bare well-known URI suffix?
```

Possible review outcomes include:

- `josh` is acceptable;
- more community review is requested;
- stronger deployment evidence is requested;
- a more specific suffix is recommended.

This document does not preselect an outcome.

### 2. Specification-reference suitability

```text
Does the current Joshternet specification publication and governance model
provide a suitable stable reference for the registry?
```

Possible review outcomes include:

- the frozen project specification is acceptable;
- stronger stability/governance documentation is requested;
- more community participation is requested;
- an Internet-Draft should be brought forward in the roadmap;
- another publication mechanism is recommended.

This document does not assume that an immutable GitHub URL alone satisfies the
registry.

### 3. Browser interaction

```text
Should RFC-JOSH-0002 explicitly recommend browser-safety response headers,
particularly X-Content-Type-Options: nosniff, while preserving the existing
consumer-side Content-Type leniency semantics?
```

This is a security-review question.

It should not be resolved by making consumers reject existing interoperable
publishers solely because they return a different Content-Type.

## External review gate

This package is not ready for IANA submission.

Before submitting the provisional registration, seek external review focused
on the protocol and registration rather than on whether reviewers personally
like the Joshternet idea.

The central implementation-review question remains:

> Can somebody implement `/.well-known/josh` correctly using only
> RFC-JOSH-0002?

The registration-specific questions are:

> Is `josh` an appropriate registered suffix?

> Is the specification publication model sufficiently stable and
> community-supported for the registry?

> Does RFC-JOSH-0002 adequately address RFC 8615's Web-browser interaction
> considerations?

Review should include, where practical:

- implementers familiar with Web protocols;
- IndieWeb technical participants;
- security reviewers;
- independent publisher implementers;
- potential independent consumer implementers;
- the `wellknown-uri-review` community;
- IETF DISPATCH or ART participants where appropriate.

The current registry guidance strongly favors wider community discussion before
registration, so this should be treated as substantive protocol review rather
than merely an announcement.

Any ambiguity discovered during review should be evaluated against:

1. RFC-JOSH-0002;
2. the canonical conformance corpus;
3. existing interoperability evidence;
4. RFC 8615;
5. current Well-Known URI registry request guidance.

Protocol defects should be fixed in the specification.

Implementation defects should be fixed in the implementation.

Registry-process concerns should be handled as registration-process concerns.

Those categories should not be conflated.

## Relationship to the Internet-Draft roadmap

The existing Joshternet roadmap treats conversion of RFC-JOSH-0002 into an
Internet-Draft as a later track rather than a prerequisite for provisional
registration.

This audit does not automatically change that decision.

However, current registry guidance places meaningful weight on specification
publication, community review, and standards-incubation context.

Phase 10 external review should therefore explicitly ask whether moving the
Internet-Draft step earlier would materially strengthen:

- specification-reference suitability;
- community review;
- change-control credibility;
- the case for retaining the bare `josh` suffix.

If external reviewers or the designated expert indicate that an Internet-Draft
would materially improve the registration path, the roadmap should be revised
deliberately rather than treating the earlier ordering as fixed.

## Submission gate

The provisional IANA request should not be submitted until:

- the suitability of the bare `josh` suffix has received external review;
- the specification-reference publication model has received external review;
- the Section 4.2 browser-interaction question has received security review;
- the proposed registration fields have been reviewed;
- the change-controller contact has been confirmed;
- broader community review has occurred;
- no unresolved protocol ambiguity remains;
- any specification changes resulting from review have been reflected in the
  conformance corpus;
- interoperability has been rerun after any protocol change;
- any decision to move the Internet-Draft track earlier has been resolved;
- the final specification URI is suitable for the registry.

Once those conditions are satisfied, the intended candidate request remains:

```text
/.well-known/josh
status: provisional
```

through the Well-Known URI registry request process.

The exact suffix, specification reference, and supporting material remain
subject to the external review documented above.
