# RFC-JOSH-0001: Josh Identity

**Status:** Draft
**Category:** Foundational
**Created:** August 22, 2026
**Author:** Joshua Morris
**Organization:** Joshternet

## Abstract

This document defines the identity model used by the Joshternet.

Joshternet identity is based on voluntary self-identification. A person's name, spelling, nickname, language, transliteration, ancestry, etymology, or historical relationship to the name Joshua MUST NOT determine whether that person identifies as a Josh.

A person may affirm Josh identity, explicitly decline Josh identity, or make no declaration at all.

Josh identity is separate from Joshternet participation.

A person who explicitly declares that they are not a Josh MAY still participate in the Joshternet.

These states and concepts are intentionally distinct.

**Joshness is declared, never derived.**

## 1. Purpose

The Joshternet exists primarily to connect Joshes and the independent places they maintain on the web.

The word "Josh" represents a broad family of names, spellings, nicknames, transliterations, and linguistic variants. Attempting to determine Josh identity through a fixed list of names would be incomplete, culturally narrow, and inconsistent with the voluntary nature of the network.

This specification therefore defines Josh identity as a declaration made by the person represented.

It also recognizes that participation in the Joshternet does not itself make someone a Josh.

A non-Josh may participate, contribute, operate compatible infrastructure, interact with Joshes, or otherwise take part in the network while explicitly maintaining that they are not a Josh.

The protocol does not decide who is a Josh.

The person does.

## 2. Identity and Participation

Joshternet implementations MUST distinguish between:

1. **Josh identity**
2. **Joshternet participation**

These concepts are independent.

A person may be:

| Josh Identity | Participating | Meaning                                                 |
| ------------- | ------------- | ------------------------------------------------------- |
| Affirmed      | Yes           | A Josh participating in the Joshternet                  |
| Affirmed      | No            | A Josh who is not participating                         |
| Declined      | Yes           | A non-Josh participating in the Joshternet              |
| Declined      | No            | A non-Josh who is not participating                     |
| Undeclared    | Yes           | A participant who has made no Josh identity declaration |
| Undeclared    | No            | No known identity or participation declaration          |

Participation MUST NOT be interpreted as evidence of Josh identity.

Josh identity MUST NOT automatically imply active participation.

## 3. Josh Identity States

Josh identity has three possible states:

| State          | Meaning                                                             |
| -------------- | ------------------------------------------------------------------- |
| **Affirmed**   | The person declares that they identify as a Josh.                   |
| **Declined**   | The person explicitly declares that they do not identify as a Josh. |
| **Undeclared** | No Josh identity declaration has been made.                         |

These states MUST NOT be treated as equivalent.

In particular:

**Undeclared does not mean Declined.**

**Declined does not mean Undeclared.**

And:

**Participating does not mean Affirmed.**

## 4. Affirmed Josh Identity

A person has **Affirmed Josh Identity** when they voluntarily declare themselves to be a Josh.

An affirmed Josh MAY use:

* Josh;
* Joshua;
* another spelling or variation of Joshua;
* a linguistic or transliterated form related to Joshua;
* a nickname derived from another name;
* another name entirely, provided that the person genuinely identifies themselves as a Josh.

A registry or implementation MUST NOT reject an affirmative declaration solely because the person's name does not match an expected spelling.

For example, each of the following fictional people could legitimately affirm Josh identity:

```text
Joshua Exampleton
Josh Exampleton
Joshuah Exampleton
Josué Exampleton
Yeshua Exampleton
```

Their spelling does not determine their Joshness.

Their declaration does.

## 5. Declined Josh Identity

A person has **Declined Josh Identity** when they explicitly state that they do not identify as a Josh.

A declined declaration MUST take precedence over:

* name matching;
* linguistic analysis;
* transliteration;
* etymology;
* previously indexed information;
* registry assumptions;
* third-party assertions.

For example:

```text
Name: Yeshua Exampleton
Josh identity: Declined
```

Even if an implementation determines that the name has a historical or linguistic relationship to Joshua, the person MUST NOT be represented as a Josh.

The network does not get to explain to someone why they are technically a Josh.

## 6. Non-Josh Participation

Declining Josh identity does not prohibit participation in the Joshternet.

A person MAY explicitly declare themselves to be a non-Josh while participating in the network.

Such a person is referred to by this specification as a **Non-Josh Participant**.

A Non-Josh Participant MAY:

* operate Joshternet-compatible infrastructure;
* contribute to specifications;
* maintain software or services;
* participate in discussions;
* interact with participating Joshes;
* link to or navigate the Joshternet;
* operate a compatible website or endpoint;
* otherwise participate in the network.

A Non-Josh Participant MUST NOT be represented as a Josh merely because they participate.

Conceptually:

```text
Josh identity: Declined
Joshternet participation: Active
```

is completely valid.

The Joshternet is primarily for connecting Joshes.

It is not necessarily only for Joshes.

## 7. Joshing the Joshes

A Non-Josh Participant MAY knowingly participate in the Joshternet while maintaining an explicit non-Josh identity.

Such participation may, among other legitimate purposes, consist of interacting with, contributing to, or good-naturedly joshing the Joshes.

This does not change their identity state.

Participation in a network named after Josh is not sufficient evidence of Joshness.

A conforming implementation MUST continue to respect an explicit Declined identity declaration regardless of the amount of joshing involved.

## 8. Undeclared Josh Identity

A person has **Undeclared Josh Identity** when no identity declaration has been made.

An undeclared person MUST NOT automatically be considered either an affirmed Josh or a declined Josh.

For example:

```text
Name: Joshua Exampleton
Josh identity: Undeclared
```

An implementation may reasonably suspect that Joshua Exampleton could identify as a Josh.

It may not claim that he does.

Similarly:

```text
Name: Yeshua Exampleton
Josh identity: Undeclared
```

No inference should be made.

Undeclared means exactly that: no declaration is known.

## 9. Name Variants

The Joshternet intentionally does not define an authoritative list of valid Josh names.

Names related to the Josh family may include forms such as:

* Josh;
* Joshua;
* Joshuah;
* Joshu;
* Joshue;
* Joshuwa;
* Josua;
* Joschua;
* Jozua;
* Josué;
* Josue;
* Yehoshua;
* Yeshua;
* Giosuè;
* other spellings, transliterations, nicknames, or linguistic variants.

This list is illustrative and MUST NOT be interpreted as exhaustive.

Identifying as a Josh MUST NOT depend upon appearing in this list.

Likewise, appearing in this list MUST NOT automatically make someone a Josh.

## 10. Self-Identification

A Josh identity declaration MUST represent the identity preference of the person being represented.

Third parties MUST NOT create an affirmative or declined Josh identity declaration on behalf of another person without that person's authorization.

A service MAY discover a website that appears to belong to someone named Josh.

It MAY identify that website as a potential candidate for discovery.

It MUST NOT convert that observation into an affirmative Josh identity declaration without an authoritative declaration from the person or a resource they control.

## 11. Authority

For purposes of the Joshternet, the authoritative source of Josh identity is the person's own declaration.

A declaration published through a mechanism defined by a Joshternet specification MAY be treated as authoritative when control of the associated website or endpoint has been reasonably established.

A registry is not an authority over Josh identity.

A crawler is not an authority over Josh identity.

A naming database is not an authority over Josh identity.

A search engine is not an authority over Josh identity.

Another Josh is not an authority over somebody else's Josh identity.

## 12. Participation

Joshternet participation is voluntary.

A person MAY participate regardless of whether their Josh identity is:

* Affirmed;
* Declined;
* Undeclared.

Likewise, a person MAY stop participating without changing their Josh identity.

For example:

```text
Josh identity: Affirmed
Joshternet participation: Inactive
```

may describe someone who still considers themselves a Josh but no longer wishes to maintain a Joshternet node.

Identity and network presence are not the same thing.

## 13. Changing Identity

A person MAY change their Josh identity state at any time.

A person may transition between:

```text
Undeclared -> Affirmed
Undeclared -> Declined
Affirmed   -> Declined
Declined   -> Affirmed
Affirmed   -> Undeclared
Declined   -> Undeclared
```

Implementations SHOULD respect the most recent authoritative declaration available.

Registries SHOULD remove or update stale identity information within a reasonable period after discovering a changed declaration.

A previous declaration MUST NOT permanently bind a person to a Josh identity.

Joshness is voluntary and revocable.

## 14. Changing Participation

A person MAY begin or end Joshternet participation independently of their Josh identity.

For example:

```text
Josh identity: Declined
Participation: Active
```

may later become:

```text
Josh identity: Declined
Participation: Inactive
```

without changing the person's declared non-Josh identity.

Likewise:

```text
Josh identity: Affirmed
Participation: Inactive
```

may later become:

```text
Josh identity: Affirmed
Participation: Active
```

without requiring the person to reaffirm their Joshness.

## 15. Multiple Names

A person may use more than one name.

For example, a fictional participant might use:

```text
Legal name: Joshua Exampleton
Display name: Josh
Professional name: J. Exampleton
```

Joshternet implementations SHOULD allow the participant to control the name presented publicly.

Participation MUST NOT require publication of a legal name.

## 16. Display Names

A participant MAY provide a display name for use by Joshternet services.

A display name:

* does not need to contain the word Josh;
* does not need to match a legal name;
* does not determine Josh identity;
* does not determine participation;
* SHOULD be treated as participant-controlled public metadata.

For example:

```text
Josh identity: Affirmed
Display name: J. Exampleton
```

remains a valid affirmative Josh identity.

Likewise:

```text
Josh identity: Declined
Display name: Alex Exampleton
Participation: Active
```

remains a valid Non-Josh Participant.

## 17. Identity and Nodes

Josh identity applies to a person.

Network participation may be represented by a website or network endpoint.

A Josh MAY operate multiple participating endpoints.

A Non-Josh Participant MAY also operate compatible infrastructure or endpoints where permitted by the relevant specification.

The terminology and technical representation of participating endpoints are defined by other Joshternet RFCs.

This RFC does not require that every Joshternet-compatible endpoint be operated by a Josh.

## 18. Illustrative Declaration Semantics

The machine-readable format for Joshternet declarations is defined by **RFC-JOSH-0002**.

The following examples are conceptual only.

An affirmative Josh identity could correspond to:

```json
{
  "josh": true
}
```

An explicit non-Josh identity could correspond to:

```json
{
  "josh": false
}
```

An undeclared identity contains no Josh declaration:

```json
{
  "name": "Joshua Exampleton"
}
```

The absence of `josh` MUST NOT be interpreted as either `true` or `false`.

Identity and participation may also be represented independently.

Conceptually:

```json
{
  "josh": false,
  "participating": true
}
```

means:

```text
I do not identify as a Josh.
I am participating in the Joshternet.
```

Conversely:

```json
{
  "josh": true,
  "participating": false
}
```

means:

```text
I identify as a Josh.
I am not currently participating in the Joshternet.
```

These examples define semantics only.

RFC-JOSH-0002 defines the normative machine-readable representation.

## 19. Precedence

When conflicting identity information exists, Joshternet implementations SHOULD apply the following precedence:

```text
Current authoritative self-declaration
              |
              v
Older authoritative self-declaration
              |
              v
No declaration
```

Name analysis, directory listings, third-party claims, participation status, and inferred identity MUST NOT override an authoritative self-declaration.

In particular:

```text
josh: false
```

MUST override any inference that a person appears to have a Josh-related name.

Likewise:

```text
participating: true
```

MUST NOT override:

```text
josh: false
```

The participant remains a participating non-Josh.

## 20. Impersonation

A Joshternet declaration MUST NOT be treated as proof of a person's legal identity.

Joshternet identity establishes only the identity declaration associated with a participating endpoint.

Implementations SHOULD distinguish between:

* control of a website or endpoint;
* Josh identity;
* Joshternet participation;
* legal or real-world identity verification.

These are separate concerns.

The Joshternet is not intended to become a legal identity system.

## 21. Privacy

A Josh identity or participation declaration SHOULD require as little personal information as possible.

Participation MUST NOT require disclosure of:

* a legal name;
* physical address;
* precise location;
* phone number;
* date of birth;
* government-issued identification;
* private email address;
* employer;
* family information.

A Josh should be able to say:

```text
I am a Josh.
This is my website.
I want to participate in the Joshternet.
```

A non-Josh should likewise be able to say:

```text
I am not a Josh.
This is my website.
I still want to participate in the Joshternet.
```

Neither should require substantially more personal information.

## 22. Registry Behavior

Josh Registries MUST preserve the distinction between:

* Affirmed;
* Declined;
* Undeclared;

and SHOULD separately preserve participation state where that information is supported.

A registry MUST NOT list an undeclared person as a Josh solely because of their name.

A registry MUST NOT list a Declined participant as a Josh solely because they participate in the network.

A Non-Josh Participant MAY appear in services where non-Josh participation is relevant, but MUST be clearly distinguishable from affirmed Joshes.

Registries SHOULD avoid retaining information about people who have ceased participation except where retaining minimal information is necessary to prevent repeated rediscovery, unwanted enrollment, abuse, or other operational problems.

Such records SHOULD contain the minimum information necessary.

## 23. Crawlers and Discovery Services

A crawler MAY discover potential Josh-related websites.

Discovery alone does not establish Josh identity.

A crawler finding:

```text
Joshua Exampleton
https://example.invalid/
```

does not constitute an affirmative Josh declaration.

Likewise, discovering that a website participates in the Joshternet does not prove that its operator identifies as a Josh.

The crawler must locate an authoritative identity declaration before representing that person as an affirmed Josh.

## 24. Internationalization

Joshternet implementations SHOULD support Unicode names and SHOULD NOT assume that Josh-related names are written using ASCII or the Latin alphabet.

Implementations MUST NOT require participants to anglicize, transliterate, or otherwise modify their names in order to participate.

Josh identity is independent of writing system.

## 25. Humor Is Not Identity

The Joshternet is intentionally playful.

That does not make someone's identity a joke.

Implementations and community services SHOULD distinguish between humor about the existence of the Joshternet and humor directed at an individual person's name, language, culture, or identity.

Non-Josh Participants may even participate specifically because the entire concept amuses them.

That is permitted.

The network may be ridiculous.

Participation should still be respectful.

## 26. Security Considerations

Identity and participation declarations are self-published metadata and MUST be treated as untrusted input.

Implementations should account for:

* impersonation;
* forged declarations;
* domain takeover;
* stale declarations;
* malicious metadata;
* deceptive redirects;
* registry poisoning.

A future specification MAY define stronger mechanisms for establishing control of a participating endpoint.

## 27. Relationship to Other RFCs

This RFC defines the semantics of Josh identity and its relationship to Joshternet participation.

The initial related specifications are expected to include:

| RFC           | Relationship                                           |
| ------------- | ------------------------------------------------------ |
| RFC-JOSH-0000 | Defines the Joshternet and its foundational principles |
| RFC-JOSH-0001 | Defines Josh identity and participation semantics      |
| RFC-JOSH-0002 | Defines the machine-readable declaration               |
| RFC-JOSH-0003 | Defines discovery and registry behavior                |
| RFC-JOSH-0004 | Defines navigation between participating endpoints     |

If another Joshternet specification conflicts with the voluntary identity principles established here, this specification SHOULD take precedence unless explicitly superseded by a later foundational RFC.

## 28. Foundational Identity Rules

A conforming Joshternet implementation MUST preserve the following rules:

1. **Joshness is declared, never derived.**
2. Josh identity and Joshternet participation are separate concepts.
3. A person MAY affirm Josh identity.
4. A person MAY explicitly decline Josh identity.
5. A person MAY make no Josh identity declaration.
6. Undeclared identity MUST NOT be interpreted as Affirmed or Declined.
7. A person MAY participate in the Joshternet while declaring that they are not a Josh.
8. Participation MUST NOT be interpreted as evidence of Josh identity.
9. Name spelling MUST NOT determine Josh identity.
10. Name origin MUST NOT determine Josh identity.
11. A self-declaration MUST take precedence over inferred identity.
12. A participant MAY change or withdraw their declaration.
13. A participant MAY begin or end participation independently of their identity.
14. No implementation may appoint someone a Josh against their wishes.
15. `josh: false` MUST remain valid even when that person is actively participating in the Joshternet.

The Joshternet may connect the Joshes.

Non-Joshes may come along for the ride.

The network still does not get to decide who anyone is.
