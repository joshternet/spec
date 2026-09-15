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

Known operational implementations of RFC-JOSH-0002 version 1:

| Site | Identity | Status |
| --- | --- | --- |
| [joshuamorris.info](https://joshuamorris.info/) | Affirmed Josh Identity | Operational |
| [joshternet.org](https://joshternet.org/) | Undeclared Josh Identity | Operational |

Their Joshternet declarations are published at:

- `https://joshuamorris.info/.well-known/josh`
- `https://joshternet.org/.well-known/josh`

Both origins participate according to RFC-JOSH-0002. Their different identity states demonstrate that participation and Josh identity are separate.

Implementations are listed for reference only. Inclusion does not grant authority, special status, or precedence within the Joshternet.

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
