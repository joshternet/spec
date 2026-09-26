# Joshternet Specifications

Open specifications for Josh identity, participation, and inter-Josh networking.

> **Specification status:** PRE-JOSH

This repository is the canonical home for the open standards that define the Joshternet.

The Joshternet is a decentralized network for connecting people who identify as Josh and the websites they call home. Non-Joshes may also participate without being represented as Joshes.

## Principles

The Joshternet is built around a few foundational ideas:

* **Joshness is declared, never derived.**
* Participation is voluntary.
* Identity and participation are separate.
* Participants retain control of their own websites and infrastructure.
* No Josh outranks another Josh.
* Participation does not imply trust.
* Open and boring web standards are preferred over proprietary infrastructure.
* Participation should not require a social network, centralized identity provider, or JavaScript.
* Implementations should remain simple enough for personal websites of any size or technology stack.

## Specifications

Joshternet standards are developed as Joshternet RFCs.

| RFC                                           | Title               | Status |
| --------------------------------------------- | ------------------- | ------ |
| [RFC-JOSH-0000](rfcs/0000-the-joshternet.md)  | The Joshternet      | Draft  |
| [RFC-JOSH-0001](rfcs/0001-josh-identity.md)   | Josh Identity       | Draft  |
| [RFC-JOSH-0002](rfcs/0002-well-known-josh.md) | `/.well-known/josh` | Draft  |

No RFCs have been accepted yet.

## Implementations

Known operational publishers of RFC-JOSH-0002 version 1:

| Site | Identity | Operation | Status |
| --- | --- | --- | --- |
| [joshuamorris.info](https://joshuamorris.info/) | Affirmed Josh Identity | Project-controlled | Operational |
| [joshternet.org](https://joshternet.org/) | Undeclared Josh Identity | Project-controlled | Operational |
| [joshtronic.com](https://joshtronic.com/) | Affirmed Josh Identity | Independent | Operational |
| [www.joshuabaker.com](https://www.joshuabaker.com/) | Affirmed Josh Identity | Independent | Operational |

Their Joshternet declarations are published at:

- `https://joshuamorris.info/.well-known/josh`
- `https://joshternet.org/.well-known/josh`
- `https://joshtronic.com/.well-known/josh`
- `https://www.joshuabaker.com/.well-known/josh`

All four origins currently publish valid RFC-JOSH-0002 version 1 declarations.

Their different deployments and identity states demonstrate that participation
is not tied to a particular hosting stack, operator, or Josh identity state.

Implementations are listed for reference only. Inclusion does not grant
authority, special status, or precedence within the Joshternet.

## Interoperability

The repository maintains non-normative implementation evidence separately from
the protocol specification.

See
[RFC-JOSH-0002 version 1 interoperability evidence](interoperability/rfc-josh-0002/v1/README.md)
for observed publisher deployments, JoshBot consumer conformance, independent
implementation status, and the limitations of the current interoperability
evidence.

The current evidence includes independently operated publishers and a
project-controlled consumer. No independently authored RFC-JOSH-0002 consumer
is currently documented.

The interoperability record does not define protocol behavior. RFC-JOSH-0002
remains authoritative.

## IANA preparation

RFC-JOSH-0002 is being prepared for a proposed provisional registration of the
`josh` suffix in the IANA Well-Known URIs registry.

The
[RFC-JOSH-0002 IANA registration preparation](iana/rfc-josh-0002/README.md)
document contains the proposed registration fields, the RFC 8615 audit, and the
remaining external-review questions.

That document is non-normative. It does not change RFC-JOSH-0002.

No IANA registration request has been submitted yet, and this repository does
not claim that `josh` is currently registered.

External technical review is required before a provisional registration request
is submitted.

## Related software

[JoshBot](https://github.com/joshternet/joshbot) is the Joshternet discovery, verification, and public registry crawler.

JoshBot verifies `/.well-known/josh` declarations and can produce deterministic public registry data. It is implementation infrastructure, not a specification, and its behavior does not define participation or Josh identity.

The first supported JoshBot release is [v1.0.0](https://github.com/joshternet/joshbot/releases/tag/v1.0.0).

## Development

Specifications are developed publicly through issues, discussion, and pull requests.

Future RFCs are added as they are developed rather than reserved in advance.

The Joshternet is currently in its **PRE-JOSH** phase while the foundational standards are being defined.

## License

The Joshternet specifications and repository documentation are licensed under the Creative Commons Attribution 4.0 International License (CC BY 4.0).

This permits others to share and adapt the specifications, including for commercial purposes, with attribution and an indication of changes.

See [LICENSE.md](LICENSE.md).
