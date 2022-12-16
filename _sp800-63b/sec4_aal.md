---
layout: default
title: Authentication Assurance Levels
navOrder: 4
navTitle: AAL
permalink: /sp800-63b/aal/
anchor: AAL_SEC4
section: 4
---

# Authentication Assurance Levels {#AAL_SEC4}

_This section is normative._

To satisfy the requirements of a given AAL and be recognized as a subscriber, a claimant **SHALL** be authenticated with a process whose strength is equal to or greater than the requirements at that level. The result of an authentication process is an identifier that **SHALL** be used each time that subscriber authenticates to that RP. The identifier **MAY** be pseudonymous. Subscriber identifiers **SHOULD NOT** be reused for a different subject but **SHOULD** be reused when a previously enrolled subject is re-enrolled by the CSP. Other attributes that identify the subscriber as a unique subject **MAY** also be provided.

Detailed normative requirements for authenticators and verifiers at each AAL are provided in [Sec. 5](#AAL_SEC5).

See [[SP800-63]](../_sp800-63/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63"} Sec. 5 for details on how to choose the most appropriate AAL.

[[FIPS140]](references.md#ref-FIPS140) requirements are satisfied by FIPS 140-3 or newer revisions.

Personal information collected during and subsequent to identity proofing **MAY** be made available to the subscriber by the digital identity service. The release or online availability of any PII or other personal information, whether self-asserted or validated, by federal government agencies requires multi-factor authentication in accordance with [[EO13681]](references.md#ref-EO13681). Therefore, federal government agencies **SHALL** select a minimum of AAL2 when PII or other personal information is made available online.

## Authentication Assurance Level 1

AAL1 provides some assurance that the claimant controls an authenticator bound to the subscriber account. AAL1 requires either single-factor or multi-factor authentication using a wide range of available authentication technologies. Successful authentication requires that the claimant prove possession and control of the authenticator through a secure authentication protocol.

### Permitted Authenticator Types

AAL1 authentication **SHALL** occur by the use of any of the following authenticator types, which are defined in [Sec. 5](sec5_authenticators.md#AAL_SEC5):

* Memorized secret ([Sec. 5.1.1](sec5_authenticators.md#memsecret))
* Look-Up secret ([Sec. 5.1.2](sec5_authenticators.md#lookupsecrets))
* Out-of-band device ([Sec. 5.1.3](sec5_authenticators.md#out-of-band))
* Single-factor one-time password (OTP) device ([Sec. 5.1.4](sec5_authenticators.md#singlefactorOTP))
* Multi-factor OTP device ([Sec. 5.1.5](sec5_authenticators.md#multifactorOTP))
* Single-factor cryptographic software ([Sec. 5.1.6](sec5_authenticators.md#sfcs))
* Single-factor cryptographic device ([Sec. 5.1.7](sec5_authenticators.md#sfcd))
* Multi-factor cryptographic software ([Sec. 5.1.8](sec5_authenticators.md#mfcs))
* Multi-factor cryptographic device ([Sec. 5.1.9](sec5_authenticators.md#mfcd))

### Authenticator and Verifier Requirements {#aal1req}

Cryptographic authenticators used at AAL1 **SHALL** use approved cryptography. Software-based authenticators that operate within the context of an operating system **MAY**, where applicable, attempt to detect compromise (e.g., by malware) of the user endpoint in which they are running and **SHOULD NOT** complete the operation when such a compromise is detected.

Communication between the claimant and verifier **SHALL** be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to adversary-in-the-middle (AitM) attacks.

Verifiers operated by or on behalf of federal government agencies at AAL1 **SHALL** be validated to meet the requirements of [[FIPS140]](references.md#ref-FIPS140-2) Level 1.

### Reauthentication {#aal1reauth}

Periodic reauthentication of subscriber sessions **SHALL** be performed as described in [Sec. 7.2](sec7_session.md#sessionreauthn). At AAL1, reauthentication of the subscriber **SHOULD** be repeated at least once per 30 days during an extended usage session, regardless of user activity. The session **SHOULD** be terminated (i.e., logged out) when this time limit is reached.

### Security Controls

The CSP **SHALL** employ appropriately tailored security controls from the baseline security controls defined in [[SP800-53]](references.md#ref-SP800-53) or equivalent federal (e.g., [[FEDRAMP]](references.md#ref-FEDRAMP)) or industry standard that the organization has determined for the information systems, applications, and online services that these guidelines are used to protect. The CSP **SHALL** ensure that the minimum assurance-related controls for the appropriate systems, or equivalent, are satisfied.

###  Records Retention Policy {#aal1records}

The CSP **SHALL** comply with its respective records retention policies in accordance with applicable laws, regulations, and policies, including any National Archives and Records Administration (NARA) records retention schedules that may apply. If the CSP opts to retain records in the absence of any mandatory requirements, the CSP **SHALL** conduct a risk management process, including assessments of privacy and security risks, to determine how long records should be retained and **SHALL** inform the subscriber of that retention policy.

## Authentication Assurance Level 2

AAL2 provides high confidence that the claimant controls authenticators bound to the subscriber account. Proof of possession and control of two distinct authentication factors is required through secure authentication protocols. Approved cryptographic techniques are required at AAL2 and above.

### Permitted Authenticator Types {#aal2types}

At AAL2, authentication **SHALL** occur by the use of either a multi-factor authenticator or a combination of two single-factor authenticators. A multi-factor authenticator requires two factors to execute a single authentication event, such as a cryptographically secure device with an integrated biometric sensor that is required to activate the device. Authenticator requirements are specified in [Sec. 5](sec5_authenticators.md#AAL_SEC5).

When a multi-factor authenticator is used, any of the following **MAY** be used:

* Multi-Factor Out-of-Band Authenticator ([Sec. 5.1.3.4](sec5_authenticators.md#mfooba))
* Multi-Factor OTP Device ([Sec. 5.1.5](sec5_authenticators.md#multifactorOTP))
* Multi-Factor Cryptographic Software ([Sec. 5.1.8](sec5_authenticators.md#mfcs))
* Multi-Factor Cryptographic Device ([Sec. 5.1.9](sec5_authenticators.md#mfcd))

When a combination of two single-factor authenticators is used, the combination **SHALL** include a Memorized Secret authenticator ([Sec. 5.1.1](sec5_authenticators.md#memsecret)) and one physical authenticator (i.e., "something you have") from the following list:

* Look-Up Secret ([Sec. 5.1.2](sec5_authenticators.md#lookupsecrets))
* Out-of-Band Device ([Sec. 5.1.3](sec5_authenticators.md#out-of-band))
* Single-Factor OTP Device ([Sec. 5.1.4](sec5_authenticators.md#singlefactorOTP))
* Single-Factor Cryptographic Software ([Sec. 5.1.6](sec5_authenticators.md#sfcs))
* Single-Factor Cryptographic Device ([Sec. 5.1.7](sec5_authenticators.md#sfcd))

> Note: When biometric authentication meets the requirements in [Sec. 5.2.3](sec5_authenticators.md#biometric_use), the device has to be authenticated in addition to the biometric match. A biometric characteristic is recognized as a factor, but not recognized as an authenticator by itself. Therefore, when conducting authentication with a biometric characteristic, it is unnecessary to use two authenticators because the associated device serves as "something you have," while the biometric match serves as "something you are."

### Authenticator and Verifier Requirements {#aal2req}

Cryptographic authenticators used at AAL2 **SHALL** use approved cryptography. Authenticators procured by federal government agencies **SHALL** be validated to meet the requirements of [[FIPS140]](references.md#ref-FIPS140-2) Level 1. Software-based authenticators that operate within the context of an operating system **MAY**, where applicable, attempt to detect compromise (e.g., by malware) of the platform in which they are running. They **SHOULD NOT** complete the operation when such a compromise is detected. At least one authenticator used at AAL2 **SHALL** be replay resistant as described in [Sec. 5.2.8](sec5_authenticators.md#replay). Authentication at AAL2 **SHOULD** demonstrate authentication intent from at least one authenticator as discussed in [Sec. 5.2.9](sec5_authenticators.md#intent).

Communication between the claimant and verifier **SHALL** be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to AitM attacks.

Verifiers operated by or on behalf of federal government agencies at AAL2 **SHALL** be validated to meet the requirements of [[FIPS140]](references.md#ref-FIPS140-2) Level 1.

When a biometric factor is used in authentication at AAL2, the performance requirements stated in [Sec. 5.2.3](sec5_authenticators.md#biometric_use) **SHALL** be met, and the verifier **SHOULD** make a determination that the biometric sensor and subsequent processing meet these requirements.

OMB Memorandum [[M-22-09]](references.md#ref-M-22-09) requires federal government agencies to offer at least one phishing-resistant authenticator option to public users at AAL2. While phishing resistance as described in [Sec. 5.2.5](sec5_authenticators.md#verifimpers) is not generally required for authentication at AAL2, verifiers **SHOULD** encourage the use of phishing-resistant authenticators at AAL2 whenever practical since phishing is a significant threat vector.

### Reauthentication {#aal2reauth}

Periodic reauthentication of subscriber sessions **SHALL** be performed as described in [Sec. 7.2](sec7_session.md#sessionreauthn). At AAL2, authentication of the subscriber **SHALL** be repeated at least once per 12 hours during an extended usage session, regardless of user activity. Reauthentication of the subscriber **SHALL** be repeated following any period of inactivity lasting 30 minutes or longer. The session **SHALL** be terminated (i.e., logged out) when either of these time limits is reached.

Reauthentication of a session that has not yet reached its time limit **MAY** require only a memorized secret or a biometric in conjunction with the still-valid session secret. The verifier **MAY** prompt the user to cause activity just before the inactivity timeout.

### Security Controls

The CSP **SHALL** employ appropriately tailored security controls from the baseline security controls defined in [[SP800-53]](references.md#ref-SP800-53) or equivalent federal (e.g., [[FEDRAMP]](references.md#ref-FEDRAMP)) or industry standard that the organization has determined for the information systems, applications, and online services that these guidelines are used to protect. The CSP **SHALL** ensure that the minimum assurance-related controls for the appropriate systems, or equivalent, are satisfied.

### Records Retention Policy {#aal2records}

The CSP **SHALL** comply with its respective records retention policies in accordance with applicable laws, regulations, and policies, including any NARA records retention schedules that may apply. If the CSP opts to retain records in the absence of any mandatory requirements, the CSP **SHALL** conduct a risk management process, including assessments of privacy and security risks to determine how long records should be retained and **SHALL** inform the subscriber of that retention policy.

## Authentication Assurance Level 3 {#aal3}

AAL3 provides very high confidence that the claimant controls authenticators bound to the subscriber account. Authentication at AAL3 is based on proof of possession of a key through a cryptographic protocol. AAL3 authentication **SHALL** use a hardware-based authenticator and an authenticator that provides phishing resistance — the same device **MAY** fulfill both these requirements. In order to authenticate at AAL3, claimants **SHALL** prove possession and control of two distinct authentication factors through secure authentication protocols. Approved cryptographic techniques are required.

### Permitted Authenticator Types {#aal3types}

AAL3 authentication **SHALL** occur by the use of one of a combination of authenticators satisfying the requirements in [Sec. 4.3](#aal3). Possible combinations are:

* Multi-Factor Cryptographic Device ([Sec. 5.1.9](sec5_authenticators.md#mfcd))
* Single-Factor Cryptographic Device ([Sec. 5.1.7](sec5_authenticators.md#sfcd)) used in conjunction with a Memorized Secret ([Sec. 5.1.1](sec5_authenticators.md#memsecret))
* Multi-Factor OTP device (software or hardware) ([Sec. 5.1.5](sec5_authenticators.md#multifactorOTP)) used in conjunction with a Single-Factor Cryptographic Device ([Sec. 5.1.7](sec5_authenticators.md#sfcd))
* Multi-Factor OTP device (hardware only) ([Sec. 5.1.5](sec5_authenticators.md#multifactorOTP)) used in conjunction with a Single-Factor Cryptographic Software ([Sec. 5.1.6](sec5_authenticators.md#sfcs))
* Single-Factor OTP device (hardware only) ([Sec. 5.1.4](sec5_authenticators.md#singlefactorOTP)) used in conjunction with a Multi-Factor Cryptographic Software Authenticator ([Sec. 5.1.8](sec5_authenticators.md#mfcs))

### Authenticator and Verifier Requirements {#aal3req}

Communication between the claimant and verifier **SHALL** be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to AitM attacks. At least one cryptographic authenticator used at AAL3 **SHALL** be phishing resistant as described in [Sec. 5.2.5](sec5_authenticators.md#verifimpers) and **SHALL** be replay resistant as described in [Sec. 5.2.8](sec5_authenticators.md#replay). All authentication and reauthentication processes at AAL3 **SHALL** demonstrate authentication intent from at least one authenticator as described in [Sec. 5.2.9](sec5_authenticators.md#intent).

Multi-factor authenticators used at AAL3 **SHALL** be hardware cryptographic modules validated at [[FIPS140]](references.md#ref-FIPS140-2) Level 2 or higher overall with at least [[FIPS140]](references.md#ref-FIPS140-2) Level 3 physical security. Single-factor cryptographic devices used at AAL3 **SHALL** be validated at [[FIPS140]](references.md#ref-FIPS140-2) Level 1 or higher overall with at least [[FIPS140]](references.md#ref-FIPS140-2) Level 3 physical security.

Verifiers at AAL3 **SHALL** be validated at [[FIPS140]](references.md#ref-FIPS140-2) Level 1 or higher.

Verifiers at AAL3 **SHALL** be verifier compromise resistant as described in [Sec. 5.2.7](sec5_authenticators.md#verifier-secrets) with respect to at least one authentication factor.

Hardware-based authenticators and verifiers at AAL3 **SHOULD** resist relevant side-channel (e.g., timing and power-consumption analysis) attacks.

When a biometric factor is used in authentication at AAL3, the verifier **SHALL** make a determination that the biometric sensor and subsequent processing meet the performance requirements stated in [Sec. 5.2.3](sec5_authenticators.md#biometric_use).

### Reauthentication {#aal3reauth}

Periodic reauthentication of subscriber sessions **SHALL** be performed as described in [Sec. 7.2](sec7_session.md#sessionreauthn). At AAL3, authentication of the subscriber **SHALL** be repeated at least once per 12 hours during an extended usage session, regardless of user activity, as described in [Sec. 7.2](sec7_session.md#sessionreauthn). Reauthentication of the subscriber **SHALL** be repeated following any period of inactivity lasting 15 minutes or longer. Reauthentication **SHALL** use both authentication factors. The session **SHALL** be terminated (i.e., logged out) when either of these time limits is reached. The verifier **MAY** prompt the user to cause activity just before the inactivity timeout.

### Security Controls

The CSP **SHALL** employ appropriately tailored security controls from the baseline security controls defined in [[SP800-53]](references.md#ref-SP800-53) or equivalent federal (e.g., [[FEDRAMP]](references.md#ref-FEDRAMP)) or industry standard that the organization has determined for the information systems, applications, and online services that these guidelines are used to protect. The CSP **SHALL** ensure that the minimum assurance-related controls for the appropriate systems, or equivalent, are satisfied.

### Records Retention Policy {#aal3records}

The CSP **SHALL** comply with its respective records retention policies in accordance with applicable laws, regulations, and policies, including any NARA records retention schedules that may apply. If the CSP opts to retain records in the absence of any mandatory requirements, the CSP **SHALL** conduct a risk management process, including assessments of privacy and security risks, to determine how long records should be retained and **SHALL** inform the subscriber of that retention policy.

## Privacy Requirements {#aal_privacy}

The CSP **SHALL** employ appropriately tailored privacy controls defined in [[SP800-53]](references.md#ref-SP800-53) or equivalent industry standard.

If CSPs process attributes for purposes other than identity proofing, authentication, or attribute assertions (collectively "identity service"), related fraud mitigation, or to comply with law or legal process, CSPs **SHALL** implement measures to maintain predictability and manageability commensurate with the privacy risk arising from the additional processing. Measures **MAY** include providing clear notice, obtaining subscriber consent, or enabling selective use or disclosure of attributes. When CSPs use consent measures, CSPs **SHALL NOT** make consent for the additional processing a condition of the identity service.

Regardless of whether the CSP is an agency or private sector provider, the following requirements apply to a federal agency offering or using the authentication service:

1. The agency **SHALL** consult with their Senior Agency Official for Privacy (SAOP) and conduct an analysis to determine whether the collection of PII to issue or maintain authenticators triggers the requirements of the *Privacy Act of 1974* [[PrivacyAct]](references.md#ref-PrivacyAct) (see [Sec. 9.4](sec9_privacy.md#agency-privacy)).
2. The agency **SHALL** publish a System of Records Notice (SORN) to cover such collections, as applicable.
3. The agency **SHALL** consult with their SAOP and conduct an analysis to determine whether the collection of PII to issue or maintain authenticators triggers the requirements of the *E-Government Act of 2002* [[E-Gov]](references.md#ref-E-Gov).
4. The agency **SHALL** publish a Privacy Impact Assessment (PIA) to cover such collection, as applicable.

## Summary of Requirements

[Table 1](sec4_aal.md#table-1) provides a non-normative summary of the requirements for each of the AALs.

[Table 1 AAL Summary of Requirements](sec4_aal.md#table-1){:name="table-1"}
{:latex-ignore="true"}

Requirement | AAL1 | AAL2 | AAL3
------------|-------|-------|-------
**Permitted authenticator types** | Memorized Secret; Look-up Secret; Out-of-Band; SF OTP Device; MF OTP Device; SF Crypto Software; SF Crypto Device; MF Crypto Software; MF Crypto Device  | MF Out-of-Band; MF OTP Device; MF Crypto Software; MF Crypto Device; or Memorized Secret plus: Look-up Secret, Out-of-Band, SF OTP Device, SF Crypto Software, SF Crypto Device  | MF Crypto Device; SF Crypto Device plus Memorized Secret; SF OTP Device plus MF Crypto Device or Software; SF OTP Device plus SF Crypto Software plus Memorized Secret
**FIPS 140 validation** | Level 1 (Government agency verifiers) | Level 1 (Government agency authenticators and verifiers) | Level 2 overall (MF authenticators) Level 1 overall (verifiers and SF Crypto Devices) Level 3 physical security (all authenticators)
**Reauthentication** | 30 days | 12 hours or 30 minutes inactivity; one authentication factor | 12 hours or 15 minutes inactivity; both authentication factors
**Security controls**|[[SP800-53]](references.md#ref-SP800-53) Low Baseline (or equivalent)|[[SP800-53]](references.md#ref-SP800-53) Moderate Baseline (or equivalent)|[[SP800-53]](references.md#ref-SP800-53) High Baseline (or equivalent)
**AitM resistance** | Required | Required | Required |
**Phishing resistance** | Not required | Recommended | Required |
**Verifier-compromise resistance** | Not required | Not required | Required |
**Replay resistance** | Not required | Required | Required |
**Authentication intent** | Not required | Recommended | Required |
{:latex-table="1" latex-caption="AAL Summary of Requirements" latex-columns="p@0.20\textwidth,p@0.22\textwidth,p@0.22\textwidth,p@0.25\textwidth"}
