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

Known implementations of Joshternet specifications:

| Site                                            | Specification           | Status      |
| ----------------------------------------------- | ----------------------- | ----------- |
| [joshuamorris.info](https://joshuamorris.info/) | RFC-JOSH-0002 version 1 | Operational |

The implementation publishes its Joshternet declaration at:

```text
https://joshuamorris.info/.well-known/josh
```

Implementations are listed for reference only.

Inclusion does not grant authority, special status, or precedence within the Joshternet.

## Development

Specifications are developed publicly through issues, discussion, and pull requests.

Future RFCs are added as they are developed rather than reserved in advance.

The Joshternet is currently in its **PRE-JOSH** phase while the foundational standards are being defined.
