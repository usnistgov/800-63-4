---
layout: default
title: Federation Assurance Level
navOrder: 3
navTitle: FAL
permalink: /sp800-63c/fal/
anchor: fal
section: 2
---

# Federation Assurance Level (FAL) {#fal}

*This section is normative.*

This section defines *federation assurance levels* (FALs) and the requirements for securing federation transactions at each FAL. In order to fulfill the requirements for a a given FAL, the federation transaction **SHALL** meet or exceed all requirements listed for that FAL.

Each FAL is characterized by a set of requirements that increase the security and complexity as the FAL increases. These requirements are listed here and expanded in other sections of this document:

Audience Restriction
: The assertion presented in the federation protocol is targeted to a specific RP and the RP can confirm that it is the intended audience of the assertion.

Injection Protection
: The RP is strongly protected from an attacker presenting an assertion in circumstances outside a current federation transaction request. (See [Sec. 3.10.1](3_federation.md#injection-protection) for details on injection protection.)

Trust Agreement Establishment
: The agreement to participate in a federation transaction for the purposes of creating an authenticated session for the subscriber at the RP. (See [Sec. 3.4](3_federation.md#trust-agreement) for details of the trust agreement.)

Identifier and Key Establishment
: The IdP and RP have exchanged identifiers and key material to allow for the verification of assertions and other artifacts during future federation transactions. (See [Sec. 3.5](3_federation.md#identifiers-keys) for details of key establishment.)

Presentation
: The assertion can be presented to the RP either on its own (as a bearer assertion) or in concert with an authenticator presented by the subscriber.

[Table 1](2_fal.md#table-1) provides a non-normative summary of aspects for each FAL. Each successive level subsumes and fulfills all requirements of lower levels (e.g., a federation process at FAL3 can be accepted at FAL2 or FAL1 since FAL3 satisfies all the requirements of these lower levels). Combinations not found in [Table 1](2_fal.md#table-1) are possible, and agencies can choose to implement stronger protections in one or more areas of requirements at a given FAL.

[Table 1. Federation Assertion Levels](2_fal.md#table-1){:name="table-1"}
{:latex-ignore="true"}

|Requirement|FAL1|FAL2|FAL3|
|:--:|----|----|----|
|Audience Restriction|Multiple RPs allowed per assertion, Single RP per assertion recommended|Single RP per assertion|Single RP per assertion|
|Injection Protection|Recommended for all transactions|Required; transaction begins at the RP|Required; transaction begins at the RP|
|Trust Agreement Establishment|Subscriber-driven or A priori|A priori|A priori|
|Identifier and Key Establishment|Dynamic or Static|Dynamic or Static|Static|
|Presentation|Bearer Assertion|Bearer Assertion|Holder-of-Key Assertion or Bound Authenticator|
{:latex-table="1" latex-caption="Federation Assurance Levels"}

While many different federation implementation options are possible, the FAL is intended to provide clear guidance representing increasingly secure deployment options. See [[SP800-63]](../_sp800-63/1_introduction.md#introduction){:latex-href="#ref-SP800-63"} for details on how to choose the most appropriate FAL.

> Note: In these guidelines, assertions, attribute bundles, and other elements of the federation protocol are protected by asymmetric digital signatures or symmetric MACs. When either asymmetric or symmetric cryptography is specifically required, the terms "sign" and "signature" will be qualified as appropriate to indicate the requirement. When either option is possible, the terms "sign" and "signature" are used without a qualifier.

## Common FAL Requirements {#falcommon}

At all FALs, all federation transactions **SHALL** comply with the requirements in [Sec. 3](3_federation.md#common) to deliver an assertion to the RP and create an authenticated session at the RP. Examples of assertions used in federation protocols include the ID Token in OpenID Connect [[OIDC]](references.md#ref-OIDC) and the Security Assertion Markup Language [[SAML]](references.md#ref-SAML) Assertion format.

At all FALs, the RP needs to trust the IdP to provide valid assertions representing the subscriber's authentication event and **SHALL** validate the assertion.

IdPs and RPs **SHALL** employ appropriately tailored security controls from the moderate baseline security controls defined in [[SP800-53]](references.md#ref-SP800-53) or an equivalent federal (e.g., [[FEDRAMP]](references.md#ref-FEDRAMP)) or industry standard that the organization has determined for the information systems, applications, and online services that these guidelines are used to protect. IdPs and RPs **SHALL** ensure that the minimum assurance-related controls for the appropriate systems, or equivalent, are satisfied. Additional security controls are discussed in [Sec. 3.10](3_federation.md#security-controls).

If no FAL is specified by the trust agreement or federation transaction, the requirements of this section still apply.

An IdP or RP can be capable of operating at multiple FALs simultaneously, depending on use case and needs. For example, an IdP could provide FAL3 federation transactions to a high-risk RP while providing FAL2 to an RP with a lower risk profile. Similarly, an RP could require FAL2 for normal actions but require the subscriber to re-authenticate with FAL3 for higher impact or more sensitive actions. This capability extends to other dimensions, as an IdP could simultaneously have access to subscriber accounts that have been proofed at any IAL and allow authentication at any AAL. However, an RP talking to that IdP could have restrictions on the lowest IAL and AAL it is willing to accept for access. As a consequence, it is imperative that the trust agreement establish the xALs allowed and required for different use cases.

## Federation Assurance Level 1 (FAL1) {#fal1}

FAL1 provides a basic level of protection for federation transactions, allowing for a wide range of use cases and deployment decisions.

At FAL1, the IdP **SHALL** sign the assertion using approved cryptography. The RP **SHALL** validate the signature using the key associated with the expected IdP. The signature protects the integrity of the assertion contents and allows for the IdP to be verified as the source of the assertion.

All assertions at FAL1 **SHALL** be audience-restricted to a specific RP or set of RPs, and the RP **SHALL** validate that it is one of the targeted RPs for the given assertion.

At FAL1, the trust agreement **MAY** be established by the subscriber during the federation transaction. Note that at FAL1, it is still possible for the trust agreement to be established a priori by the RP and IdP.

At FAL1, the federation protocol **SHOULD** apply injection protection as discussed in [Sec. 3.10.1](3_federation.md#injection-protection). The federation transaction **SHOULD** be initiated by the RP.

## Federation Assurance Level 2 (FAL2) {#fal2}

FAL2 provides a high level of protection for federation transactions, providing protections against a variety of attacks against federated systems. All the requirements for FAL1 apply at FAL2 except where overridden by more specific or stringent requirements here.

At FAL2, the assertion **SHALL** be strongly protected from injection attacks, as discussed in [Sec. 3.10.1](3_federation.md#injection-protection). The federation transaction **SHALL** be initiated by the RP.

At FAL2, the assertion **SHALL** audience restricted to a single RP.

At FAL2, an a priori trust agreement **SHALL** be established prior to the federation transaction taking place.

IdPs operated by or on behalf of federal agencies that present assertions at FAL2 or higher **SHALL** protect keys used for signing or encrypting those assertions with mechanisms validated at [[FIPS140]](references.md#ref-FIPS140) Level 1 or higher.

## Federation Assurance Level 3 (FAL3) {#fal3}

FAL3 provides a very high level of protection for federation transactions, establishing very high confidence that the subscriber asserted by the IdP is the subscriber present in the authenticated session. All the requirements at FAL1 and FAL2 apply at FAL3 except where overridden by more specific or stringent requirements here.

At FAL3, the RP **SHALL** verify that the subscriber is in control of an authenticator in addition to the assertion. This authenticator is either identified in a holder-of-key assertion as described in [Sec 3.14](3_federation.md#idp-managed-bound-authn) or is a bound authenticator as described in [Sec. 3.15](3_federation.md#bound-authn).

At FAL3, the trust agreement **SHALL** be established such that the IdP can identify and trust the RP to abide by all aspects of the trust agreement prior to any federation transaction taking place. To facilitate this, the key material used to authenticate the RP and IdP to each other is associated with the identifiers for the RP and IdP in a static fashion using a trusted mechanism. For example, a public key file representing the RP is uploaded to the IdP during a static registration process, and the RP downloads the IdP's public key from a URL indicated in the trust agreement. Alternatively, the trust agreement can dictate that the RP and IdP can upload their respective public keys to a federation authority and then download each other's keys from that same trusted authority.

IdPs operated by or on behalf of federal agencies that present assertions at FAL3 **SHALL** protect keys used for signing or encrypting those assertions with mechanisms validated at [[FIPS140]](references.md#ref-FIPS140) Level 1 or higher.

## Requesting and Processing xALs {#request-xals}

Since an IdP is capable of asserting the identities of many different subscribers with a variety of authenticators using a variety of federation parameters, the IAL, AAL, and FAL could vary across different federation transactions, even to the same RP.

IdPs **SHALL** support a mechanism for RPs to specify a set of minimum acceptable xALs as part of the trust agreement and **SHOULD** support the RP specifying a more strict minimum set at runtime as part of the federation transaction. When an RP requests a particular xAL, the IdP **SHOULD** fulfill that request, if possible, and **SHALL** indicate the resulting xAL in the assertion. For example, if the subscriber has an active session that was authenticated at AAL1, but the RP has requested AAL2, the IdP needs to prompt the subscriber for AAL2 authentication to step up the security of the session at the IdP during the subscriber's interaction at the IdP, if possible. The IdP sends the resulting AAL as part of the returned assertion, whether it is AAL1 (the step-up authentication was not met) or AAL2 (the step-up authentication was met successfully).

The IdP **SHALL** inform the RP of the following information for each federation transaction:

- The IAL of the subscriber account being presented to the RP, or an indication that no IAL claim is being made
- The AAL of the currently active session of the subscriber at the IdP, or an indication that no AAL claim is being made
- The FAL of the federation transaction

The RP gets this xAL information from a combination of the terms of the trust agreement as described in [Sec. 3.4](3_federation.md#trust-agreement) and information included in the assertion as described in [Sec. 4.9](4_generalidp.md#assertions) and [Sec. 5.8](5_subscriberidp.md#assertion-contents). If the xAL is unchanging for all messages between the IdP and RP, the xAL information **SHALL** be included in the terms of the trust agreement between the IdP and RP. If the xAL could be within a range of possible values specified by the trust agreement, the xAL information **SHALL** be included as part of the assertion contents.

The IdP **MAY** indicate that no claim is made to the IAL or AAL for a given federation transaction. In such cases, no default value is assigned to the resulting xAL by the RP. That is to say, a federation transaction without an IAL declaration in either the trust agreement or the assertion is functionally considered to have "no IAL" and the RP cannot assume the account meets "IAL1", the lowest numbered IAL described in this suite.

The RP **SHALL** determine the minimum IAL, AAL, and FAL it is willing to accept for access to any offered functionality. An RP **MAY** vary its functionality based on the IAL, AAL, and FAL of a specific federated authentication. For example, an RP can allow federation transactions at AAL2 for common functionality (e.g., viewing the status of a dam system) but require AAL3 be used for higher risk functionality (e.g., changing the flow rates of a dam system). Similarly, an RP could restrict management functionality to only certain subscriber accounts which have been identity proofed at IAL2, while allowing federation transactions from all subscriber accounts regardless of IAL.

In a federation process, only the IdP has direct access to the details of the subscriber account, which determines the applicable IAL, and the authentication event at the IdP, which determines the applicable AAL. Consequently, the IdP declares the IAL, AAL, and intended FAL for each federation transaction.

The RP **SHALL** ensure that it meets its obligations in the federation transaction for the FAL declared in the assertion. For example, the RP needs to ensure the presentation method meets the injection protection requirements at FAL2 and above, and that the appropriate bound authenticator is presented at FAL3.
