---
layout: default
title: Security
navOrder: 7
navTitle: Security
permalink: /sp800-63c/security/
anchor: security
section: 6
---

# Security {#security}

*This section is informative.*

Since the federated authentication process involves coordination between multiple components, including the CSP, IdP, and RP, there are additional opportunities for attackers to compromise federated identity transactions and additional ramifications for successful attacks. This section summarizes many of the attacks and mitigations applicable to federation.

## Federation Threats

As in non-federated authentication, attackers' motivations are typically to gain access (or a greater level of access) to a resource or service provided by an RP. Attackers may also attempt to impersonate a subscriber. Rogue or compromised IdPs, RPs, user agents (e.g., browsers), and parties outside of a typical federation transaction are potential attackers. To accomplish their attack, they might intercept or modify assertions and assertion references. Furthermore, two or more entities may attempt to subvert federation protocols by directly compromising the integrity or confidentiality of the assertion data. For the purpose of these types of threats, any authorized parties who attempt to exceed their privileges are considered attackers.

In federated systems, successful attacks on the IdP can propagate through to the RPs that rely on that IdP for identity and security information. As a consequence, an attack against the IdP targeting one agency's RP could potentially proliferate to another agency's RP. Additionally, since a single subscriber account is made available to multiple RPs in a federated system, there are potential limitations on the tailoring to proofing strategies and the visibility into the proofing process that an IdP can offer to different RPs. However, these terms can vary in the trust agreements with each RP, if the IdP is able to support different use cases for different subscriber account populations. Furthermore, while the IdP can disclose different attributes to each RP, the subscriber account will need to contain the union of all attributes available to all RPs. This practice limits the damage of attacks against RPs but in turn makes the IdP a more compelling target for attackers.

[Table 2. Federation Threats](6_security.md#table-2){:name="table-2"}
{:latex-ignore="true"}

| Federation Threats/Attacks  | Description  | Examples |
|---------------------------------|------------------|--------------|
| Assertion Manufacture or Modification | The attacker generates a false assertion | Compromised IdP asserts identity of a claimant who has not properly authenticated |
| | The attacker modifies an existing assertion | Compromised proxy that changes AAL of an authentication assertion |
| Assertion Disclosure | Assertion visible to third party | Network monitoring reveals subscriber address of record to an outside party |
| Assertion Repudiation by the IdP | IdP later claims not to have signed transaction | User engages in fraudulent credit card transaction at RP, IdP claims not to have logged them in |
| Assertion Repudiation by the Subscriber | Subscriber claims not to have performed transaction | User agreement (e.g., contract) cannot be enforced |
| Assertion Redirect | Assertion can be used in unintended context | Compromised user agent passes assertion to attacker who uses it elsewhere |
| Assertion Reuse | Assertion can be used more than once with same RP | Intercepted assertion used by attacker to authenticate their own session |
| Assertion Substitution | Attacker uses an assertion intended for a different subscriber | Session hijacking attack between IdP and RP |
{:latex-table="2" latex-caption="Federation Threats" latex-columns="p@0.20\textwidth,p@0.35\textwidth,p@0.35\textwidth"}


## Federation Threat Mitigation Strategies

Mechanisms that assist in mitigating the above threats are identified in [Table 3](6_security.md#table-3).

[Table 3. Mitigating Federation Threats](6_security.md#table-3){:name="table-3"}
{:latex-ignore="true"}

| Federation Threat/Attack | Threat Mitigation Mechanisms | Normative Reference(s) |
|------------------------------|----------------------------------|---|
| Assertion Manufacture or Modification | Cryptographically sign the assertion at IdP and verify at RP | [3.5](3_federation.md#identifiers-keys), [3.12.2](3_federation.md#signed-assertion) |
| | Send assertion over an authenticated protected channel authenticating the IdP | [4.11](4_generalidp.md#presentation) |
| | Include a non-guessable random identifier in the assertion | [3.12.1](3_federation.md#assertion-id) |
| Assertion Disclosure | Send assertion over an authenticated protected channel authenticating the RP | [4.9](4_generalidp.md#assertions), [5.8](5_subscriberidp.md#assertion-contents) |
| | Encrypt assertion for a specific RP (may be accomplished by use of a mutually authenticated protected channel) | [3.12.3](3_federation.md#encrypted-assertion) |
| Assertion Repudiation by the IdP | Cryptographically sign the assertion at the IdP with a key that supports non-repudiation; verify signature at RP | [3.12.2](3_federation.md#signed-assertion) |
| Assertion Repudiation by the Subscriber | Issue holder-of-key assertions or assertions with bound authenticators; proof of possession of authenticator verifies subscriber's participation to the RP | [3.14](3_federation.md#idp-managed-bound-authn) [3.15](3_federation.md#bound-authn) |
| Assertion Redirect | Include identity of the RP ("audience") for which the assertion is issued in its signed content; RP verifies that they are intended recipient |  |
| Assertion Reuse | Include an issuance timestamp with short validity period in the signed content of the assertion; RP verifies validity | [4.9](4_generalidp.md#assertions), [5.8](5_subscriberidp.md#assertion-contents) |
| | RP keeps track of assertions consumed within a configurable time window to ensure that a given assertion is not used more than once. | [3.12.1](3_federation.md#assertion-id) |
| Assertion Substitution | Ensure that assertions contain a reference to the assertion request or some other nonce that was cryptographically bound to the request by the RP | [4.9](4_generalidp.md#assertions), [5.8](5_subscriberidp.md#assertion-contents) |
| | Send assertions in the same authenticated protected channel as the request, such as in the back-channel model |[4.11.1](4_generalidp.md#back-channel)|
{:latex-table="3" latex-caption="Mitigating Federation Threats" latex-columns="p@0.20\textwidth,p@0.55\textwidth,p@0.15\textwidth"}

