# RFC-JOSH-0002: `/.well-known/josh`

**Status:** Draft
**Category:** Protocol
**Created:** August 22, 2026
**Author:** Joshua Morris
**Organization:** Joshternet

## Abstract

This document defines `/.well-known/josh`, the machine-readable resource used by an origin to declare participation in the Joshternet.

A valid resource at this location indicates participation.

The resource may also declare Josh identity using the semantics defined by RFC-JOSH-0001.

## 1. Scope

This RFC defines:

* the location of the Joshternet declaration;
* its JSON representation;
* the representation of Josh identity;
* retrieval and validation requirements;
* how publication and removal affect participation.

This RFC does not define discovery, registries, navigation, profiles, feeds, trust, reputation, or abuse handling.

## 2. Normative Language

The key words **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are to be interpreted as described by BCP 14 when they appear in uppercase.

## 3. Resource Location

A participating origin MUST publish its declaration at:

```text
/.well-known/josh
```

For:

```text
https://example.invalid/
```

the declaration is:

```text
https://example.invalid/.well-known/josh
```

The declaration applies only to the origin from which it is retrieved.

Different origins, including subdomains, publish their own declarations.

The canonical path does not include a trailing slash.

## 4. Participation

A valid `/.well-known/josh` resource declares that its origin participates in the Joshternet.

No separate participation property is defined.

An origin that does not publish a valid declaration is not declaring participation through this protocol.

Publication and removal of the resource do not change a person's Josh identity as defined by RFC-JOSH-0001.

## 5. Representation

The resource MUST contain a JSON object conforming to RFC 8259.

A version 1 declaration contains:

| Member    | Required | Type    |
| --------- | -------- | ------- |
| `version` | Yes      | integer |
| `josh`    | No       | boolean |

A server SHOULD return:

```text
Content-Type: application/json
```

## 6. Version

The `version` member MUST be present.

For this specification its value MUST be the integer:

```json
{
  "version": 1
}
```

A consumer that does not support the declared version MUST NOT interpret the declaration using version 1 semantics.

## 7. Josh Identity

The optional `josh` member expresses Josh identity according to RFC-JOSH-0001.

### 7.1 Affirmed

```json
{
  "version": 1,
  "josh": true
}
```

declares Affirmed Josh Identity.

### 7.2 Declined

```json
{
  "version": 1,
  "josh": false
}
```

declares Declined Josh Identity.

### 7.3 Undeclared

```json
{
  "version": 1
}
```

declares no Josh identity.

The absence of `josh` represents Undeclared Josh Identity.

Consumers MUST NOT interpret an absent `josh` member as either `true` or `false`.

## 8. Valid Values

When present, `josh` MUST be a JSON boolean.

The following are invalid:

```json
{
  "version": 1,
  "josh": "true"
}
```

```json
{
  "version": 1,
  "josh": 1
}
```

```json
{
  "version": 1,
  "josh": null
}
```

The `version` member MUST be the integer `1`.

## 9. Retrieval

Consumers MUST use HTTP `GET` to retrieve the declaration before interpreting its contents.

A valid declaration is normally returned with:

```text
200 OK
```

Normal HTTP caching behavior MAY be used.

Public Joshternet declarations MUST be retrievable without authentication or client-side script execution.

## 10. Redirects

A declaration SHOULD be served directly from `/.well-known/josh`.

Consumers MAY follow same-origin redirects.

A cross-origin redirect MUST NOT be treated as a declaration for the original origin.

## 11. Removal

An origin stops declaring participation by ceasing to publish a valid `/.well-known/josh` resource.

Responses including:

```text
404 Not Found
```

or:

```text
410 Gone
```

indicate that no declaration is currently published at that location.

Temporary retrieval failures, including server errors, DNS failures, TLS failures, and timeouts, do not establish intentional withdrawal.

Policies for stale or unreachable nodes are outside the scope of this RFC.

## 12. Validation

A version 1 declaration is invalid if:

* the response body is not valid JSON;
* the top-level JSON value is not an object;
* `version` is absent;
* `version` is not the integer `1`;
* `josh` is present but is not a boolean;
* duplicate JSON member names are present.

An invalid resource MUST NOT be interpreted as a valid Josh identity declaration.

## 13. Unknown Members

Version 1 declarations MAY contain members not defined by this RFC.

Consumers SHOULD ignore unknown members unless another supported Joshternet specification defines them.

Unknown members MUST NOT alter the meaning of `version`, `josh`, or participation by publication.

## 14. Origin Scope

A declaration speaks only for the origin serving it.

For example, a declaration at:

```text
https://example.invalid/.well-known/josh
```

does not declare participation for:

```text
https://www.example.invalid/
```

or:

```text
https://other.example.invalid/
```

unless those origins publish their own declarations.

## 15. Multiple Origins

A participant MAY publish declarations from more than one origin.

This RFC does not define a mechanism for asserting that multiple origins represent the same person.

## 16. Multiple Participants

Version 1 represents at most one Josh identity declaration per origin.

Multi-participant declarations are outside the scope of this RFC.

An origin that cannot appropriately represent a single Josh identity MAY participate without declaring Josh identity:

```json
{
  "version": 1
}
```

## 17. Security Considerations

Consumers MUST treat declaration contents as untrusted input.

Consumers SHOULD apply reasonable limits to response size and parsing resources.

Retrieving a declaration from an origin does not establish legal identity, trustworthiness, or authority beyond control of that origin.

The security and trust principles defined by RFC-JOSH-0000 and RFC-JOSH-0001 remain applicable.

## 18. Privacy Considerations

This protocol requires no personal information.

The minimum valid declaration is:

```json
{
  "version": 1
}
```

Additional personal or profile metadata is outside the scope of this RFC.

## 19. Extensibility

Version 1 intentionally defines only the minimum declaration necessary for Joshternet participation and Josh identity.

Additional metadata and capabilities SHOULD be defined by separate specifications rather than added to the core declaration without demonstrated need.

An incompatible future representation MUST use a new version number.

## 20. IANA Considerations

This specification proposes the well-known URI suffix:

```text
josh
```

for use under the `/.well-known/` namespace defined by RFC 8615.

This Draft does not claim that the suffix has been registered with IANA.

Registration SHOULD be pursued before this specification is represented as using a formally registered well-known URI.

## 21. Relationship to Other Joshternet RFCs

RFC-JOSH-0000 defines the Joshternet and participating node terminology.

RFC-JOSH-0001 defines Josh identity and participation semantics.

This RFC defines the version 1 machine-readable representation used by a participating origin.

Discovery, registries, navigation, and other network behavior are outside the scope of this RFC and may be defined by future Joshternet specifications.

## 22. Version 1 Summary

A version 1 declaration follows these rules:

1. The resource is located at `/.well-known/josh`.
2. A valid published resource declares participation.
3. `version` is required and MUST equal the integer `1`.
4. `josh` is optional.
5. `josh: true` represents Affirmed Josh Identity.
6. `josh: false` represents Declined Josh Identity.
7. An absent `josh` member represents Undeclared Josh Identity.
8. No separate participation property exists.
9. Removing the resource ends the origin's declaration of participation.
10. The declaration applies only to the origin serving it.

Minimum participating Joshternet Node:

```json
{
  "version": 1
}
```

Minimum Josh Node:

```json
{
  "version": 1,
  "josh": true
}
```

## 23. References

### Normative References

* RFC 8259 — The JavaScript Object Notation (JSON) Data Interchange Format.
* RFC 8615 — Well-Known Uniform Resource Identifiers (URIs).
* BCP 14 — Requirement terminology defined by RFC 2119 and RFC 8174.

### Joshternet References

* RFC-JOSH-0000 — The Joshternet.
* RFC-JOSH-0001 — Josh Identity.
