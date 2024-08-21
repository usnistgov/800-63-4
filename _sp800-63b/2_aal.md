---
layout: default
title: Authentication Assurance Levels
navOrder: 3
navTitle: AAL
permalink: /sp800-63b/aal/
anchor: AAL_SEC4
section: 2
---

# Authentication Assurance Levels {#AAL_SEC4}

_This section is normative._

To satisfy the requirements of a given AAL and be recognized as a subscriber, a claimant **SHALL** authenticate to an RP or IdP as described in [[SP800-63C]](../_sp800-63c/1_introduction.md#introduction){:latex-href="#ref-SP800-63C"} with a process whose strength is equal to or greater than the requirements at that level. The authentication process results in an identifier that uniquely identifies the subscriber each time they authenticate to that RP. The identifier **MAY** be pseudonymous. Other attributes that identify the subscriber as a unique subject **MAY** also be provided.

Detailed normative requirements for authenticators and verifiers at each AAL are provided in [Sec. 3](#AAL_SEC5). See [[SP800-63] Sec. 3](../_sp800-63/3_DIRM.md#sec5){:latex-href="#ref-SP800-63"} for details on how to choose the most appropriate AAL.

Personal information collected during and after identity proofing (described in [[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"}) **MAY** be made available to the subscriber by the digital identity service through the subscriber account. The release or online availability of any personally identifiable information (PII) or other personal information by federal agencies requires multi-factor authentication in accordance with [[EO13681]](references.md#ref-EO13681). Therefore, federal agencies **SHALL** select a minimum of AAL2 when PII or other personal information is made available online.

At all AALs, pre-authentication checks **MAY** be used to lower the risk of misauthentication. For example, authentication from an unexpected geolocation or IP address block (e.g., a cloud service) might prompt the use of additional risk-based controls. Where used, CSPs or verifiers **SHALL** assess their pre-authentication checks for efficacy and to identify and mitigate potential disparate impacts on their user populations. CSPs or verifiers **SHALL** include pre-authentication checks in the authentication privacy risk assessment. Pre-authentication checks do not impact or change the AAL of a transaction or substitute for an authentication factor.

Throughout this document, [[FIPS140]](references.md#ref-FIPS140) requirements are satisfied by the latest edition of FIPS 140. Legacy FIPS 140 certifications **MAY** also be used while still valid.

## Authentication Assurance Level 1

AAL1 provides basic confidence that the claimant controls an authenticator bound to the subscriber account. AAL1 requires either single-factor or multi-factor authentication using a wide range of available authentication technologies. Verifiers **SHOULD** make multi-factor authentication options available at AAL1 and encourage their use. Successful authentication requires that the claimant prove possession and control of the authenticator through a secure authentication protocol.

### Permitted Authenticator Types

AAL1 authentication **SHALL** use any of the following authentication types, which are further defined in [Sec. 3](3_authenticators.md#AAL_SEC5):

* Password ([Sec. 3.1.1](3_authenticators.md#password)): A memorizable secret typically chosen by the subscriber
* Look-up secret ([Sec. 3.1.2](3_authenticators.md#lookupsecrets)): A secret determined by the claimant by looking up a prompted value in a list held by the subscriber
* Out-of-band device ([Sec. 3.1.3](3_authenticators.md#out-of-band)): A secret sent or received through a separate communication channel with the subscriber
* Single-factor one-time password (OTP) ([Sec. 3.1.4](3_authenticators.md#singlefactorOTP)): A one-time secret obtained from a device or application held by the subscriber
* Multi-factor OTP ([Sec. 3.1.5](3_authenticators.md#multifactorOTP)): A one-time secret obtained from a device or application held by the subscriber that requires activation by a second authentication factor
* Single-factor cryptographic authentication ([Sec. 3.1.6](3_authenticators.md#sfc)): Proof of possession and control via an authentication protocol of a cryptographic key held by the subscriber.
* Multi-Factor cryptographic authentication ([Sec. 3.1.7](3_authenticators.md#mfc)): Proof of possession and control via an authentication protocol of a cryptographic key held by the subscriber that requires activation by a second authentication factor

### Authenticator and Verifier Requirements {#aal1req}

Authenticators used at AAL1 **SHALL** use *approved cryptography*. In other words, they must use approved algorithms, but the implementation need not be validated under [[FIPS140]](references.md#ref-FIPS140).

Communication between the claimant and verifier **SHALL** occur via one or more authenticated protected channels.

Cryptography used by verifiers operated by or on behalf of federal agencies at AAL1 **SHALL** be validated to meet the requirements of [[FIPS140]](references.md#ref-FIPS140) Level 1.

### Reauthentication {#aal1reauth}

These guidelines provide for two types of timeouts, which are further described in [Sec. 5.2](5_session.md#sessionreauthn):

1. An overall timeout limits the duration of an authenticated session to a specified period following authentication or a previous reauthentication.
2. An inactivity timeout terminates a session that has not had activity from the subscriber for a specified period.

Periodic reauthentication of subscriber sessions **SHALL** be performed, as described in [Sec. 5.2](5_session.md#sessionreauthn). A definite reauthentication overall timeout **SHALL** be established, which **SHOULD** be no more than 30 days at AAL1. An inactivity timeout **MAY** be applied but is not required at AAL1.

## Authentication Assurance Level 2

AAL2 provides high confidence that the claimant controls one or more authenticators that are bound to the subscriber account. Proof of possession and control of two distinct authentication factors is required through the use of secure authentication protocols. Approved cryptographic techniques are required.

### Permitted Authenticator Types {#aal2types}

At AAL2, authentication **SHALL** use either a multi-factor authenticator or a combination of two single-factor authenticators. A multi-factor authenticator requires two factors to execute a single authentication event, such as a cryptographically secure device with an integrated biometric sensor that is required to activate the device. Authenticator requirements are specified in [Sec. 3](3_authenticators.md#AAL_SEC5).

When a multi-factor authenticator is used, any of the following **MAY** be used:

* Multi-factor Out-of-band authenticator ([Sec. 3.1.3.4](3_authenticators.md#mfooba))
* Multi-factor OTP ([Sec. 3.1.5](3_authenticators.md#multifactorOTP))
* Multi-factor cryptographic authentication ([Sec. 3.1.7](3_authenticators.md#mfc))

When a combination of two single-factor authenticators is used, the combination **SHALL** include a password ([Sec. 3.1.1](3_authenticators.md#password)) and one *physical authenticator* (i.e., "something you have") from the following list:

* Look-up secret ([Sec. 3.1.2](3_authenticators.md#lookupsecrets))
* Out-of-band device ([Sec. 3.1.3](3_authenticators.md#out-of-band))
* Single-factor OTP ([Sec. 3.1.4](3_authenticators.md#singlefactorOTP))
* Single-factor cryptographic authentication ([Sec. 3.1.6](3_authenticators.md#sfc))

A biometric characteristic is not recognized as an authenticator by itself. When biometric authentication meets the requirements in [Sec. 3.2.3](3_authenticators.md#biometric_use), a physical authenticator is authenticated along with the biometric. The physical authenticator then serves as "something you have," while the biometric match serves as "something you are." When a biometric comparison is used as an activation factor for a multi-factor authenticator, the authenticator itself serves as the physical authenticator.

### Authenticator and Verifier Requirements {#aal2req}

Authenticators used at AAL2 **SHALL** use approved cryptography. Cryptographic authenticators procured by federal agencies **SHALL** be validated to meet the requirements of [[FIPS140]](references.md#ref-FIPS140) Level 1. At least one authenticator used at AAL2 **SHALL** be replay-resistant, as described in [Sec. 3.2.7](3_authenticators.md#replay). Authentication at AAL2 **SHOULD** demonstrate authentication intent from at least one authenticator, as discussed in [Sec. 3.2.8](3_authenticators.md#intent).

Communication between the claimant and verifier **SHALL** occur via one or more authenticated protected channels.

Cryptography used by verifiers operated by or on behalf of federal agencies at AAL2 **SHALL** be validated to meet the requirements of [[FIPS140]](references.md#ref-FIPS140) Level 1.

When a biometric factor is used in authentication at AAL2, the performance requirements stated in [Sec. 3.2.3](3_authenticators.md#biometric_use) **SHALL** be met, and the verifier **SHALL** determine that the biometric sensor and subsequent processing meet these requirements.

Verifiers **SHALL** offer at least one phishing-resistant authentication option at AAL2, as described in [Sec. 3.2.5](3_authenticators.md#verifimpers). Federal agencies **SHALL** require their staff, contractors, and partners to use phishing-resistant authentication to access federal information systems. In all cases, verifiers **SHOULD** encourage the use of phishing-resistant authentication at AAL2 whenever practical since phishing is a significant threat vector.

### Reauthentication {#aal2reauth}

Periodic reauthentication of subscriber sessions **SHALL** be performed as described in [Sec. 5.2](5_session.md#sessionreauthn). A definite reauthentication overall timeout **SHALL** be established, which **SHOULD** be no more than 24 hours at AAL2. The inactivity timeout **SHOULD** be no more than 1 hour. When the inactivity timeout has occurred but the overall timeout has not yet occurred, the verifier **MAY** allow the subscriber to reauthenticate using only a successful password or biometric comparison in conjunction with the session secret.

## Authentication Assurance Level 3 {#aal3}

AAL3 provides very high confidence that the claimant controls authenticators that are bound to the subscriber account. Authentication at AAL3 is based on the proof of possession of a key through the use of a cryptographic protocol along with either an activation factor or a password. AAL3 authentication requires the use of a hardware-based authenticator that provides phishing resistance. Approved cryptographic techniques are required.

~~~
\clearpage
~~~
{:latex-literal="true"}

### Permitted Authenticator Types {#aal3types}

AAL3 authentication **SHALL** require one of the following authenticator combinations:

* Multi-factor cryptographic authentication ([Sec. 3.1.7](3_authenticators.md#mfc))
* Single-factor cryptographic authentication ([Sec. 3.1.6](3_authenticators.md#sfc)) used in conjunction with a password ([Sec. 3.1.1](3_authenticators.md#password))

### Authenticator and Verifier Requirements {#aal3req}

Authenticators used at AAL3 **SHALL** use approved cryptography. Communication between the claimant and verifier **SHALL** occur via one or more authenticated protected channels. The cryptographic authenticator used at AAL3 **SHALL** be hardware-based and **SHALL** provide phishing resistance, as described in [Sec. 3.2.5](3_authenticators.md#verifimpers). The cryptographic authentication protocol **SHALL** be replay-resistant as described in [Sec. 3.2.7](3_authenticators.md#replay). All authentication and reauthentication processes at AAL3 **SHALL** demonstrate authentication intent from at least one authenticator as described in [Sec. 3.2.8](3_authenticators.md#intent).

Multi-factor authenticators used at AAL3 **SHALL** be hardware cryptographic modules that are validated at [[FIPS140]](references.md#ref-FIPS140) Level 2 or higher overall with at least [[FIPS140]](references.md#ref-FIPS140) Level 3 physical security. Single-factor cryptographic authenticators used at AAL3 **SHALL** be validated at [[FIPS140]](references.md#ref-FIPS140) Level 1 or higher overall with at least [[FIPS140]](references.md#ref-FIPS140) Level 3 physical security. AAL3 protects the verifier from compromise through the use of public-key cryptography since the verifier does not possess the private key required to authenticate.

Cryptography used by verifiers at AAL3 **SHALL** be validated at [[FIPS140]](references.md#ref-FIPS140) Level 1 or higher.

Hardware-based authenticators and verifiers at AAL3 **SHOULD** resist relevant side-channel (e.g., timing and power-consumption analysis) attacks.

When a biometric factor is used in authentication at AAL3, the verifier **SHALL** determine that the biometric sensor and subsequent processing meet the performance requirements stated in [Sec. 3.2.3](3_authenticators.md#biometric_use).

### Reauthentication {#aal3reauth}

Periodic reauthentication of subscriber sessions **SHALL** be performed, as described in [Sec. 5.2](5_session.md#sessionreauthn). At AAL3, the overall timeout for reauthentication **SHALL** be no more than 12 hours. The inactivity timeout **SHOULD** be no more than 15 minutes. Unlike AAL2, AAL3 reauthentication requirements are the same as for initial authentication at AAL3.

~~~
\clearpage
~~~
{:latex-literal="true"}

## General Requirements

The following requirements apply to authentication at all AALs.

### Security Controls

The CSP **SHALL** employ appropriately tailored security controls from the moderate baseline security controls defined in [[SP800-53]](references.md#ref-SP800-53) or an equivalent federal (e.g., [[FEDRAMP]](references.md#ref-FEDRAMP)) or industry standard that the organization has chosen for the information systems, applications, and online services that these guidelines are used to protect. The CSP **SHALL** ensure that the minimum assurance-related controls for the appropriate system are satisfied.

### Records Retention Policy

The CSP **SHALL** comply with its respective records retention policies in accordance with applicable laws, regulations, and policies, including any National Archives and Records Administration (NARA) records retention schedules that may apply. If the CSP opts to retain records in the absence of mandatory requirements, the CSP **SHALL** conduct a risk management process, including assessments of privacy and security risks, to determine how long records should be retained and **SHALL** inform the subscriber of that retention policy.

### Privacy Requirements {#aal_privacy}

The CSP **SHALL** employ appropriately tailored privacy controls defined in [[SP800-53]](references.md#ref-SP800-53) or an equivalent industry standard.

If CSPs process attributes for purposes other than identity service (i.e., identity proofing, authentication, or attribute assertions), related fraud mitigation, or compliance with laws or legal process, CSPs **SHALL** implement measures to maintain predictability and manageability commensurate with the privacy risks that arise from the additional processing. Examples of such measures include providing clear notice, obtaining subscriber consent, and enabling the selective use or disclosure of attributes. When CSPs use consent measures, CSPs **SHALL NOT** make consent for the additional processing a condition of the identity service.

Regardless of whether the CSP is an agency or private-sector provider, the following requirements apply to a federal agency that offers or uses the authentication service:

1. The agency **SHALL** consult with their Senior Agency Official for Privacy (SAOP) and conduct an analysis to determine whether the collection of PII to issue or maintain authenticators triggers the requirements of the *Privacy Act of 1974* [[PrivacyAct]](references.md#ref-PrivacyAct) (see [Sec. 7.4](7_privacy.md#agency-privacy)).
2. The agency **SHALL** publish a System of Records Notice (SORN) to cover such collections, as applicable.
3. The agency **SHALL** consult with its SAOP and conduct an analysis to determine whether the collection of PII to issue or maintain authenticators triggers the requirements of the *E-Government Act of 2002* [[E-Gov]](references.md#ref-E-Gov).
4. The agency **SHALL** publish a Privacy Impact Assessment (PIA) to cover such collection, as applicable.

### Redress Requirements

The CSP and verifier **SHALL** provide mechanisms for the redress of subscriber complaints and for problems that arise from subscriber authentication processes as described in [Sec. 5.6 of SP 800-63](../_sp800-63/sec5_DIRM.md#redress){:latex-href="#ref-SP800-63"}. These mechanisms **SHALL** be easy for subscribers to find and use. The CSP **SHALL** assess the mechanisms for efficacy in resolving complaints or problems.

## Summary of Requirements

[Figure 1](2_aal.md#fig-1) provides a non-normative summary of the requirements for each of the AALs.

[Fig. 1. Summary of requirements by AAL](2_aal.md#fig-1){:name="fig-1"}
{:latex-ignore="true"}

![Informative table summarizing requirements of each AAL]({{site.baseurl}}/{{page.collection}}/images/AAL-requirements.png 'Summary of requirements by AAL'){:latex-src="AAL-requirements.pdf" latex-fig="1" latex-place="h"}

