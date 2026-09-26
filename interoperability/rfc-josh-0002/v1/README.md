# RFC-JOSH-0002 Version 1 Interoperability Evidence

This document records observed implementation and deployment evidence for
RFC-JOSH-0002 version 1.

It is non-normative. RFC-JOSH-0002 remains the authority for protocol
semantics. This document records what implementations have demonstrated; it
does not add requirements to the protocol.

## Reference revisions

The interoperability evidence in this document is evaluated against these
revisions:

| Artifact | Revision |
| --- | --- |
| RFC-JOSH-0002 | `ee57ea7c0b1427c100008ca41647ed4dbd50b05d` |
| Version 1 conformance corpus | `5728bf19b0d193db026cdb5f283ab998cc6bc03d` |
| JoshBot canonical-corpus integration | `dc68fae1379dc50a2eced056d37f6a1ee3f2ded1` |

The publisher observations below were made on September 26, 2026 at
approximately 06:42 UTC.

## What this evidence means

RFC-JOSH-0002 has two implementation roles that matter for interoperability.

A **publisher** controls an origin and publishes its declaration at that
origin's canonical `/.well-known/josh` URI.

A **consumer** retrieves and interprets that declaration according to
RFC-JOSH-0002.

An implementation is **project-controlled** when it is operated as part of the
Joshternet project or by the specification author for Joshternet development.

An implementation is **independent** when it is operated outside the Joshternet
project and is not being maintained as another Joshternet reference
implementation.

These categories are intentionally separate. An independent publisher does not
establish the existence of an independent consumer, and a project-controlled
consumer successfully reading an independent publisher is not the same thing as
two independently authored consumers agreeing with each other.

## Current implementation matrix

| Implementation | Role | Control | Version 1 evidence |
| --- | --- | --- | --- |
| `https://joshternet.org` | Publisher | Project-controlled | Live valid declaration |
| `https://joshuamorris.info` | Publisher | Project-controlled | Live valid declaration |
| `https://joshtronic.com` | Publisher | Independent | Live valid declaration accepted by JoshBot |
| `https://www.joshuabaker.com` | Publisher | Independent | Live valid declaration accepted by JoshBot |
| JoshBot | Consumer | Project-controlled | Canonical corpus and live publisher consumption |

At this stage there are independently operated RFC-JOSH-0002 publishers, but
there is not yet a known independently authored RFC-JOSH-0002 consumer.

That distinction should remain explicit in future interoperability claims.

## Publisher observations

### joshternet.org

Declaration URI:

```text
https://joshternet.org/.well-known/josh
```

Observed HTTP status:

```text
200
```

Observed Content-Type:

```text
application/json
```

Observed representation:

```json
{
  "version": 1
}
```

RFC-JOSH-0002 version 1 interpretation:

```text
declaration: valid-v1
participation: declared
identity: undeclared
```

This is a project-controlled publisher.

It also demonstrates the version 1 case where an origin participates without
making a Josh identity assertion.

### joshuamorris.info

Declaration URI:

```text
https://joshuamorris.info/.well-known/josh
```

Observed HTTP status:

```text
200
```

Observed Content-Type:

```text
application/json
```

Observed representation:

```json
{
  "version": 1,
  "josh": true
}
```

RFC-JOSH-0002 version 1 interpretation:

```text
declaration: valid-v1
participation: declared
identity: affirmed
```

This is a project-controlled publisher.

It demonstrates participation with an explicitly affirmed Josh identity.

### joshtronic.com

Declaration URI:

```text
https://joshtronic.com/.well-known/josh
```

Observed HTTP status:

```text
200
```

Observed Content-Type:

```text
application/octet-stream
```

Observed representation:

```json
{
  "version": 1,
  "josh": true
}
```

RFC-JOSH-0002 version 1 interpretation:

```text
declaration: valid-v1
participation: declared
identity: affirmed
```

This is an independent publisher.

The response is especially useful interoperability evidence because its media
type is `application/octet-stream` rather than `application/json`.

RFC-JOSH-0002 associates declarations with `application/json` and says
publishers SHOULD return that Content-Type, but it does not make that response
header a consumer-side prerequisite for interpreting an otherwise valid
declaration. The canonical version 1 conformance corpus contains an explicit
Content-Type leniency case for this behavior.

JoshBot accepts this declaration as valid version 1 participation, which
demonstrates that its consumer behavior follows the specification rather than
requiring a stricter implementation-specific media-type rule.

### www.joshuabaker.com

Declaration URI:

```text
https://www.joshuabaker.com/.well-known/josh
```

Observed HTTP status:

```text
200
```

Observed Content-Type:

```text
application/json; charset=utf-8
```

Observed representation:

```json
{
  "version": 1,
  "josh": true
}
```

RFC-JOSH-0002 version 1 interpretation:

```text
declaration: valid-v1
participation: declared
identity: affirmed
```

This is an independent publisher.

It demonstrates an independently operated origin publishing an affirmed
version 1 declaration using a JSON media type with a charset parameter.

## JoshBot consumer evidence

JoshBot is the current project-controlled RFC-JOSH-0002 consumer.

Its declaration verifier is tested against the language-neutral version 1
conformance corpus maintained in this repository.

The canonical corpus revision used by JoshBot is:

```text
5728bf19b0d193db026cdb5f283ab998cc6bc03d
```

JoshBot's integration of that corpus was merged at:

```text
dc68fae1379dc50a2eced056d37f6a1ee3f2ded1
```

At that revision JoshBot passes all 27 canonical consumer fixtures, including
the `same-origin-redirects` optional capability.

Those fixtures exercise:

- affirmed, declined, and undeclared identity;
- malformed and non-object JSON;
- missing and malformed version values;
- unsupported versions;
- invalid `josh` values;
- duplicate JSON members;
- unknown members;
- Content-Type leniency;
- `404 Not Found` and `410 Gone`;
- server, DNS, TLS, timeout, and transport failures;
- same-origin redirects;
- cross-origin redirects;
- non-default ports;
- prohibition on alternate-port probing;
- construction of the clean canonical `/.well-known/josh` URI.

The corpus is implementation-neutral. JoshBot maps its internal outcomes to the
neutral classifications defined by the corpus rather than exposing JoshBot
implementation details as protocol semantics.

## Live consumer and publisher interoperability

The public Joshternet registry is published in:

```text
https://github.com/joshternet/index-data
```

That repository is machine-managed registry data published by JoshBot.

On September 26, 2026 its `registry.json` contained all four origins documented
above:

```text
https://joshternet.org
https://joshtronic.com
https://joshuamorris.info
https://www.joshuabaker.com
```

The stored declarations matched the live representations observed from each
origin.

This provides end-to-end operational evidence that JoshBot has consumed and
accepted declarations from both project-controlled and independently operated
publishers.

In particular, the two independent publisher deployments demonstrate that
people outside the Joshternet project can publish representations understood by
the project's consumer without requiring implementation-specific changes to
RFC-JOSH-0002.

The evidence currently demonstrates:

```text
project publisher -> project consumer
independent publisher -> project consumer
```

It does not yet demonstrate:

```text
publisher -> independent consumer
project consumer <-> independent consumer agreement
multiple independent consumers
```

Those remain useful future interoperability milestones.

## Independent consumer status

No independently authored RFC-JOSH-0002 consumer is currently documented here.

This is a limitation of the present interoperability evidence, not a protocol
failure.

The Joshternet project should not create a nominally separate implementation
solely to increase an implementation count. A stronger test will occur when
another person or project reads RFC-JOSH-0002, implements a consumer
independently, and compares its results with the canonical conformance corpus
and real publisher deployments.

When such an implementation appears, this document should record:

- the implementation and maintainer;
- the implementation language or platform;
- the RFC-JOSH-0002 revision implemented;
- the canonical conformance corpus revision tested;
- which required and recommended fixtures pass;
- which optional capabilities are claimed;
- live origins used for interoperability testing;
- any disagreements with another implementation;
- any ambiguity or defect discovered in the specification.

A disagreement should be investigated as an interoperability problem first.

If independent implementation exposes a genuine ambiguity or protocol defect,
the specification should be corrected in this repository. JoshBot-specific
behavior must not silently become the protocol definition.

## Relationship to IANA registration

This document is supporting implementation evidence.

Multiple independent implementations are not being treated here as a formal
prerequisite for registration of the `josh` Well-Known URI suffix.

The registration path for Well-Known URIs is governed by RFC 8615 and the
IANA Well-Known URIs registry's Specification Required policy. The relevant
registration case depends on a suitable public specification and designated
expert review.

Independent implementation and deployment evidence is nevertheless useful. It
helps demonstrate that the specification can be understood outside its
reference implementation, that its wire behavior is interoperable, and that
the proposed identifier describes deployed behavior rather than only a design
on paper.

This evidence should therefore accompany later IANA preparation without being
presented as a requirement that RFC 8615 does not impose.

## Updating this record

This document is an evidence log, not a static claim of universal
interoperability.

Update it when:

- another independent publisher is meaningfully relevant to interoperability;
- an independent consumer implementation appears;
- an implementation runs a newer canonical conformance corpus;
- a real interoperability disagreement is discovered;
- an ambiguity in RFC-JOSH-0002 is exposed by implementation experience;
- evidence recorded here becomes stale or can no longer be reproduced.

Normal growth of the Joshternet registry does not require adding every
participant to this document.

The goal is to record distinct and useful implementation evidence, not to turn
this file into a directory of Joshternet members.
