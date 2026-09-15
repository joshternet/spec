# RFC-JOSH-0001: Josh Identity

**Status:** Draft
**Category:** Foundational
**Created:** August 22, 2026
**Author:** Joshua Morris
**Organization:** Joshternet
**License:** CC BY 4.0

## Abstract

This document defines the identity model used by the Joshternet.

Josh identity is based on voluntary self-identification.

A person's name, spelling, nickname, language, transliteration, ancestry, etymology, or historical relationship to the name Joshua MUST NOT determine whether that person identifies as a Josh.

A person may affirm Josh identity, explicitly decline Josh identity, or make no declaration at all.

Josh identity is separate from Joshternet participation.

A person who explicitly declares that they are not a Josh MAY still participate in the Joshternet.

**Joshness is declared, never derived.**

## 1. Purpose

The Joshternet exists primarily to connect Joshes and the independent places they maintain on the web.

The word "Josh" represents a broad family of names, spellings, nicknames, transliterations, and linguistic variants.

Attempting to determine Josh identity through a fixed list of names would be incomplete, culturally narrow, and inconsistent with the voluntary nature of the network.

This specification therefore defines Josh identity as something declared by the person represented.

Participation in the Joshternet does not itself make someone a Josh.

A non-Josh may participate, contribute, operate infrastructure, interact with Joshes, or otherwise take part in the network while continuing to identify as a non-Josh.

The protocol does not decide who is a Josh.

The person does.

## 2. Scope

This RFC defines:

* Josh identity states;
* voluntary self-identification;
* the distinction between identity and participation;
* non-Josh participation;
* identity authority;
* changes to identity over time;
* name and language considerations;
* privacy expectations related to Josh identity;
* requirements that dependent Joshternet specifications MUST preserve.

This RFC does not define machine-readable formats, serialization, network endpoints, discovery, registries, navigation, or transport mechanisms.

RFC-JOSH-0002 defines the current machine-readable mechanism used by a participating origin.

## 3. Normative Language

The key words **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** describe requirements placed upon conforming Joshternet specifications and implementations.

## 4. Identity and Participation

Joshternet implementations MUST distinguish between:

1. **Josh identity**
2. **Joshternet participation**

These concepts are independent.

A person may identify as a Josh without participating in the Joshternet.

A person may participate in the Joshternet without identifying as a Josh.

A person may participate without making any declaration regarding Josh identity.

A person may do neither.

Conceptually:

| Josh Identity | Participation | Meaning                                          |
| ------------- | ------------- | ------------------------------------------------ |
| Affirmed      | Active        | A Josh participating in the Joshternet           |
| Affirmed      | Inactive      | A Josh who is not currently participating        |
| Declined      | Active        | A non-Josh participating in the Joshternet       |
| Declined      | Inactive      | A non-Josh who is not participating              |
| Undeclared    | Active        | A participant who has not declared Josh identity |
| Undeclared    | Inactive      | No known Josh identity or active participation   |

Participation MUST NOT be interpreted as evidence of Josh identity.

Josh identity MUST NOT automatically imply participation.

RFC-JOSH-0002 defines how an origin currently declares active participation.

## 5. Josh Identity States

Josh identity has three states.

### 5.1 Affirmed

The person explicitly identifies as a Josh.

### 5.2 Declined

The person explicitly states that they do not identify as a Josh.

### 5.3 Undeclared

No Josh identity declaration is known.

These states are distinct.

**Undeclared does not mean Declined.**

**Declined does not mean Undeclared.**

**Participation does not mean Affirmed.**

## 6. Affirmed Josh Identity

A person has **Affirmed Josh Identity** when they voluntarily identify themselves as a Josh.

An affirmed Josh MAY use:

* Josh;
* Joshua;
* another spelling or variation of Joshua;
* a linguistic or transliterated form related to Joshua;
* a nickname;
* a name not traditionally associated with Joshua;
* any other name under which that person genuinely identifies as a Josh.

For example, each of the following fictional people could legitimately affirm Josh identity:

```text
Joshua Exampleton
Josh Exampleton
Joshuah Exampleton
Josué Exampleton
Yeshua Exampleton
```

The spelling does not determine their Joshness.

Their self-identification does.

A Joshternet implementation MUST NOT reject an affirmative identity solely because a person's name does not match an expected spelling or naming convention.

## 7. Declined Josh Identity

A person has **Declined Josh Identity** when they explicitly state that they do not identify as a Josh.

For example:

```text
Name: Yeshua Exampleton
Josh identity: Declined
```

Even if Yeshua Exampleton's name has a historical, linguistic, or etymological relationship to Joshua, that relationship does not override the person's declaration.

A declined identity MUST take precedence over:

* name matching;
* linguistic analysis;
* transliteration;
* etymology;
* naming databases;
* previously indexed information;
* directory assumptions;
* automated inference;
* third-party assertions.

The Joshternet does not get to explain to someone why they are technically a Josh.

## 8. Undeclared Josh Identity

A person has **Undeclared Josh Identity** when no identity declaration is known.

For example:

```text
Name: Joshua Exampleton
Josh identity: Undeclared
```

An implementation may recognize that the name Joshua is commonly associated with Josh.

It may not therefore claim that Joshua Exampleton identifies as a Josh.

Similarly:

```text
Name: Yeshua Exampleton
Josh identity: Undeclared
```

No conclusion about Josh identity should be drawn.

Undeclared means exactly that:

**No declaration is known.**

## 9. Non-Josh Participation

Declining Josh identity does not prohibit participation in the Joshternet.

A person MAY explicitly identify as a non-Josh while participating in the network.

Such a person is referred to by this specification as a **Non-Josh Participant**.

A Non-Josh Participant MAY:

* participate in Joshternet communities;
* contribute to Joshternet specifications;
* maintain Joshternet software;
* operate compatible infrastructure;
* interact with participating Joshes;
* link to Joshternet resources;
* navigate participating sites;
* contribute to projects built around the network;
* otherwise participate where permitted by the relevant specification or service.

A Non-Josh Participant MUST NOT be represented as a Josh solely because they participate.

The Joshternet exists primarily to connect Joshes.

It is not necessarily only for Joshes.

## 10. Joshing the Joshes

A Non-Josh Participant MAY knowingly participate in the Joshternet while explicitly maintaining a non-Josh identity.

Such participation may include interacting with, contributing to, or good-naturedly joshing the Joshes.

This does not change the participant's identity state.

Participation in a network named after Josh is not evidence of Joshness.

The amount of joshing involved is likewise not evidence of Joshness.

A conforming implementation MUST continue to respect a Declined identity regardless of how deeply a participant becomes involved in the Joshternet.

## 11. Name Variants

The Joshternet intentionally does not define an authoritative list of valid Josh names.

Names associated with the broader Josh name family may include forms such as:

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
* other spellings, transliterations, nicknames, and linguistic variants.

This list is illustrative.

It MUST NOT be interpreted as exhaustive.

A person does not need to appear on this list to identify as a Josh.

Appearing on this list does not make someone a Josh.

## 12. Joshness Is Not a Naming Algorithm

A conforming Joshternet implementation MUST NOT determine Josh identity solely by applying:

* regular expressions;
* string matching;
* phonetic matching;
* language detection;
* transliteration;
* etymological databases;
* genealogy;
* nickname databases;
* machine learning;
* artificial intelligence;
* another automated naming system.

Such mechanisms MAY be useful for identifying people who might be interested in the Joshternet.

They MUST NOT be used as authoritative evidence of Josh identity.

Discovery and identity are separate concerns.

## 13. Self-Identification

A Josh identity declaration MUST represent the preference of the person being represented.

Third parties MUST NOT affirm or decline Josh identity on behalf of another person without authorization.

Another Josh cannot appoint someone a Josh.

A registry cannot appoint someone a Josh.

A crawler cannot appoint someone a Josh.

An algorithm cannot appoint someone a Josh.

The Joshternet organization cannot appoint someone a Josh.

Joshness originates with the person.

## 14. Identity Authority

For purposes of the Joshternet, the most authoritative source of Josh identity is the person's own current declaration.

A Joshternet protocol MAY define a mechanism through which that declaration is published by infrastructure controlled by the participant.

RFC-JOSH-0002 defines the current version 1 mechanism for participating origins.

Inferred identity MUST NOT override explicit identity.

Third-party claims MUST NOT override explicit identity.

Participation MUST NOT override explicit identity.

## 15. Changing Identity

A person MAY change their Josh identity at any time.

Valid conceptual transitions include:

```text
Undeclared -> Affirmed
Undeclared -> Declined

Affirmed   -> Declined
Affirmed   -> Undeclared

Declined   -> Affirmed
Declined   -> Undeclared
```

A previous declaration MUST NOT permanently bind someone to a Josh identity.

Systems consuming Josh identity information SHOULD respect the most recent authoritative declaration available.

Joshness is voluntary.

Joshness is revocable.

## 16. Changing Participation

Participation MAY begin or end independently of Josh identity.

For example:

```text
Josh identity: Affirmed
Participation: Active
```

may later become:

```text
Josh identity: Affirmed
Participation: Inactive
```

without changing the person's Josh identity.

Likewise:

```text
Josh identity: Declined
Participation: Inactive
```

may later become:

```text
Josh identity: Declined
Participation: Active
```

without making that person a Josh.

Identity describes who someone says they are.

Participation describes whether they are taking part.

RFC-JOSH-0002 represents active participation through publication of its defined resource. It does not require an inactive participant to publish a declaration of inactivity.

## 17. Multiple Names

A person may use more than one name.

For example:

```text
Legal name: Joshua Exampleton
Display name: Josh
Professional name: J. Exampleton
```

Joshternet participation MUST NOT require publication of a legal name.

A participant SHOULD be able to control how their name is presented by services built on the Joshternet.

No particular version of a person's name determines Josh identity.

## 18. Display Names

A participant MAY use a display name.

A display name:

* does not need to contain "Josh";
* does not need to match a legal name;
* does not determine Josh identity;
* does not determine participation;
* SHOULD be treated as participant-controlled information.

For example:

```text
Josh identity: Affirmed
Display name: J. Exampleton
```

is valid.

Likewise:

```text
Josh identity: Declined
Display name: Alex Exampleton
Participation: Active
```

is valid.

This RFC does not require a particular protocol to publish a display name.

## 19. Internationalization

Joshternet implementations SHOULD support Unicode names.

They SHOULD NOT assume that names are written using:

* ASCII;
* the Latin alphabet;
* English spelling conventions;
* Western name ordering.

A participant MUST NOT be required to anglicize, shorten, translate, transliterate, or otherwise modify their name in order to participate.

Josh identity is independent of writing system.

## 20. Identity and Joshternet Nodes

Josh identity applies to a person.

A Joshternet Node is participating infrastructure as defined by RFC-JOSH-0000.

A single person MAY participate through multiple nodes.

A participating node does not, by itself, establish that its participant is a Josh.

RFC-JOSH-0002 defines the current version 1 mechanism by which an origin declares participation and may publish Josh identity.

Infrastructure has no Josh identity of its own.

## 21. Discovery Is Not Identity

Discovering a website, endpoint, or person does not establish Josh identity.

For example:

```text
Joshua Exampleton
https://example.invalid/
```

does not constitute an Affirmed Josh identity declaration.

A service MUST NOT represent someone as an affirmed Josh solely because their name appears Josh-related.

Where RFC-JOSH-0002 is used, the identity declaration published by the participating origin provides the applicable Josh identity state for that declaration.

Discovery remains a separate concern.

## 22. Participation Is Not Identity

The presence of a person in:

* a Joshternet discussion;
* a Joshternet repository;
* a Joshternet-compatible service;
* a Josh-related event;
* a Josh directory;
* another Joshternet community;

does not establish Josh identity.

People may participate for many reasons.

Some may simply be joshing.

## 23. Privacy

Josh identity SHOULD require as little personal information as possible.

A Joshternet specification MUST NOT require disclosure of:

* a legal name;
* physical address;
* precise location;
* phone number;
* date of birth;
* government identification;
* private email address;
* employer;
* family information;

solely to express Josh identity.

A Josh should be able to communicate conceptually:

```text
I am a Josh.
I want to participate.
```

A non-Josh should likewise be able to communicate:

```text
I am not a Josh.
I still want to participate.
```

Neither should require substantially more personal information merely to establish those states.

## 24. Impersonation

Josh identity within the Joshternet is not proof of legal or real-world identity.

Implementations MUST distinguish between:

* Josh self-identification;
* control of a website or endpoint;
* participation in the Joshternet;
* legal identity verification.

These are separate concerns.

Someone claiming to be a Josh does not prove who that person is.

Someone proving control of a domain does not prove their legal name.

The Joshternet is not a legal identity system.

## 25. Trust

Josh identity does not imply trust.

Participation in the Joshternet does not imply trust.

An implementation MAY refuse to interact with, index, display, or otherwise trust a participant or endpoint for operational, security, safety, or abuse-related reasons.

Such a decision MUST NOT redefine that person's Josh identity.

Whether someone is a Josh and whether another participant chooses to interact with them are separate concerns.

**Interoperability does not require interaction.**

## 26. Security Considerations

Identity information MUST be treated as untrusted input.

Implementations should account for:

* impersonation;
* forged declarations;
* stale identity information;
* compromised websites;
* domain takeover;
* malicious metadata;
* registry poisoning;
* unauthorized third-party declarations.

Control of infrastructure and legal identity are separate concerns.

## 27. Humor Is Not Identity

The Joshternet is intentionally playful.

That does not make an individual person's identity a joke.

Implementations and communities SHOULD distinguish between humor about the Joshternet and humor directed at a person's:

* name;
* language;
* nationality;
* culture;
* identity.

Non-Joshes may participate specifically because the entire concept amuses them.

That is permitted.

The network may be ridiculous.

Participation should still be respectful.

## 28. Requirements for Dependent Specifications

Specifications that depend upon Josh identity MUST preserve the semantics defined by this RFC.

### 28.1 Three Identity States

They MUST preserve the distinction between:

* Affirmed;
* Declined;
* Undeclared.

### 28.2 Identity and Participation

They MUST NOT treat Josh identity and Joshternet participation as the same state.

### 28.3 Non-Josh Participation

They MUST permit the concept of a person participating while explicitly declining Josh identity.

### 28.4 No Inferred Joshness

They MUST NOT convert name analysis, participation, or other inferred information into authoritative Josh identity.

### 28.5 Revocability

They MUST allow newer authoritative identity information to supersede older identity information.

### 28.6 Internationalization

They MUST NOT require a particular Josh spelling, alphabet, language, or transliteration.

### 28.7 Trust Independence

They MUST NOT treat Josh identity as proof of trustworthiness.

RFC-JOSH-0002 defines the current machine-readable representation used by participating origins while preserving these requirements.

## 29. Relationship to Other Joshternet RFCs

RFC-JOSH-0000 defines the Joshternet and its foundational terminology.

RFC-JOSH-0001 defines Josh identity semantics.

RFC-JOSH-0002 defines the current version 1 machine-readable participation and identity declaration.

## 30. Foundational Identity Rules

A conforming Joshternet specification or implementation MUST preserve the following rules:

1. **Joshness is declared, never derived.**
2. Josh identity and Joshternet participation are separate concepts.
3. A person MAY affirm Josh identity.
4. A person MAY explicitly decline Josh identity.
5. A person MAY leave Josh identity undeclared.
6. Undeclared identity MUST NOT be interpreted as Affirmed or Declined.
7. A person MAY participate while explicitly declining Josh identity.
8. Participation MUST NOT be interpreted as evidence of Josh identity.
9. Name spelling MUST NOT determine Josh identity.
10. Name origin MUST NOT determine Josh identity.
11. Language MUST NOT determine Josh identity.
12. Automated inference MUST NOT override self-identification.
13. Current authoritative self-identification takes precedence over inferred identity.
14. A person MAY change or withdraw their identity declaration.
15. A person MAY begin or end participation independently of identity.
16. Josh identity MUST NOT imply trust.
17. A participant or service MAY decline interaction without redefining another person's identity.
18. No person, registry, crawler, service, organization, algorithm, or other Josh may appoint someone a Josh against their wishes.

The Joshternet may connect the Joshes.

Non-Joshes may come along for the ride.

It still does not get to decide who anyone is.
