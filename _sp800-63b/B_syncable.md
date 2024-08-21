---
layout: default
title: Syncable Authenticators
navOrder: 13
navTitle: Syncable
permalink: /sp800-63b/syncable/
anchor: appB
section: B
---

# Syncable Authenticators {#appB}

*This appendix is normative.*

## Introduction

The ability to "sync" authenticators &mdash; specifically to copy (i.e., clone) their authentication secrets to the cloud and thence to additional authenticators &mdash; is a relatively new development in authentication. This appendix provides additional guidelines on the use of syncable authenticators.

## Cloning of Authentication Keys {#cloning}

In some cases, the secret keys associated with multi-factor cryptographic authenticators (e.g., those based on the WebAuthn standard [[WebAuthn]](references.md#ref-WebAuthn)) may be stored in a sync fabric. This allows the keys to be backed up and transferred to other devices. The following requirements apply to keys managed in this manner:

* All keys **SHALL** be generated using approved cryptography.
* Private keys that are cloned or exported from a device **SHALL** only be stored in an encrypted form.
* All authentication transactions **SHALL** perform private-key operations on the local device using cryptographic keys that are generated on-device or recovered from the sync fabric (e.g., in cloud storage).
* Private keys stored in cloud-based accounts **SHALL** be protected by access control mechanisms such that only the authenticated user can access their private keys in the sync fabric.
* User access to private keys in the sync fabric **SHALL** be protected by AAL2-equivalent MFA to preserve the integrity of the authentication protocols using the synced keys.
* These general requirements and any other agency-specific requirements for using syncable authenticators **SHALL** be documented and communicated, including on public-facing websites and digital service policies, where applicable.

Additional requirements for federal enterprise[^fed] use of syncable authenticators:

[^fed]: With respect to these requirements, federal enterprise systems and keys include what would be considered in scope for PIV guidance, such as government contractors, government employees, and mission partners. It does not include government-to-consumer or public-facing use cases.

* Federal enterprise private keys (i.e., federal keys) **SHALL** be stored in sync fabrics that have achieved FISMA Moderate protections or equivalent.
* Devices (e.g., mobile phones, laptops, tablets) that generate, store, and sync authenticators containing federal enterprise private keys **SHALL** be protected by mobile device management software or other device configuration controls that prevent the syncing or sharing of keys to unauthorized devices or sync fabrics.
* Access to the sync fabric **SHALL** be controlled by agency-managed accounts (e.g., a central identity and access management solution or platform-based managed account) to maintain enterprise control over the private key's life cycle.
* Authenticators that generate private keys **SHOULD** support attestation features that can be used to verify the capabilities and sources of the authenticator (e.g., enterprise attestation).

These controls specifically support syncing and should be considered additive to the existing multi-factor cryptographic authenticator requirements and AAL2 requirements, including [[FIPS140]](reference.md#ref-FIPS140) validation.

> Syncing authentication keys inherently means that the key can be exported. Authentication at AAL2 may be supported subject to the above requirements. However, syncing violates the non-exportability requirements of AAL3. Similar protocols using keys not stored in an exportable manner that meet the other requirements of AAL3 may be used.

## Implementation Requirements

Many syncable authenticators are built upon W3C's [[WebAuthn]](references.md#ref-WebAuthn) specification, which provides a common data structure, a challenge-response cryptographic protocol, and an API for leveraging public-key credentials. The specification is flexible and adaptive, meaning that not all deployments of WebAuthn credentials will meet the requirements of federal agencies for implementation.

The specification has a series of flags that the RP application can request from the authenticator to provide additional context for the authentication event and determine whether it meets the RP's access policies. This section describes certain flags in the WebAuthn specification that federal agencies acting as RPs should understand and interrogate when building their syncable authenticator implementations to align with NIST AAL2 guidelines.

The following requirements apply to WebAuthn Level 3 flags:

User Present (UP)
: The User Present flag indicates that a "presence" test was used to confirm that the user has interacted with the authenticator (e.g., tapping a hardware token inserted into a USB port). This supports authentication intent, as described in [Sec. 3.2.8](3_authenticators.md#intent). Verifiers **SHOULD** confirm that the User Present flag has been set.

User Verified (UV)
: The User Verified flag indicates that the authenticator has locally authenticated the user using one of the available "user verification" methods. Verifiers **SHALL** indicate that UV is preferred and **SHALL** inspect responses to confirm the value of the UV flag. This indicates whether the authenticator can be treated as a multi-factor cryptographic authenticator. If the user is not verified, agencies **SHALL** treat the authenticator as a single-factor cryptographic authenticator. A further extension to the WebAuthn Level 3 specification (see Sec. 10.3 of [[WebAuthn]](references.md#ref-WebAuthn)) provides additional data on verification methods if agencies seek to gain context on the local authentication event.

Backup Eligible
: The Backup Eligible flag indicates whether the authenticator can be synced to a different device (i.e., whether the key can be stored elsewhere). It is important to note that just because an authenticator *can* be synced does not mean that it *has* been synced. Verifiers **MAY** use this flag to establish policies that restrict the use of syncable authenticators. This flag is necessary to distinguish authenticators that are device-bound from those that may be cloned to more than one device.

Backup State
: The Backup State flag indicates whether an authenticator *has* been synced to a different device. Verifiers **MAY** use this flag to establish restrictions on authenticators that are synced to other devices. Agencies **SHOULD NOT** condition acceptance based on this flag for public-facing applications due to user experience concerns. This flag **MAY** be used for enterprise applications to support the restriction of syncable authenticators for specific applications.

In addition to the flags specified above, agencies may wish to gain additional information on the origins and capabilities of the syncable authenticators that they choose to implement and accept. Within the context of FIDO2 WebAuthn, some authenticators support attestation features that can be used to determine the capabilities and manufacturers of specific authenticators. For enterprise use cases, agencies **SHOULD** implement attestation capabilities based on the functionality offered by their platform providers. This would take the form of an enterprise attestation in which the RP requests identifying information about the authenticator.

Attestations **SHOULD NOT** block the use of syncable authenticators for broad public-facing applications. Due to their limited availability in consumer products, requiring their use is likely to divert users to less secure authentication options that are vulnerable to phishing (e.g., PSTN-based out-of-band authentication). While authentication transaction metadata, such as the User Verified flag indicating the use of a local activation factor, is available in WebAuthn responses, attestation can provide stronger assurance of the characteristics of the authenticator used in a transaction.  RPs **MAY** use attestation to determine the level of confidence they have in a syncable authenticator.

Even if the RP requests flag and attestation data, the authenticator may not return all of the requested information, or it may return information that is inconsistent with the expected response mandated for access to a resource. Agencies **SHALL** evaluate the use cases for syncable authenticators and determine the appropriate access policy decisions that they intend to make based on the returned information.

## Sharing

Cybersecurity guidelines have historically cautioned against sharing authenticators between users, expecting different users to maintain their own unique authenticators. Despite this guidance, authenticator and password sharing occurs within some user groups and applications to allow individuals to share access to a digital account.

As indicated in [Table 5](B_syncable.md#table-5), some syncable authenticator implementations have embraced this user behavior and established methods for sharing authentication keys between different users. Further, some implementations actively encourage sharing syncable authenticators as a convenient and more secure alternative to sharing passwords for common services.

For enterprise use cases, concerns over sharing keys can be effectively mitigated using device management techniques that limit the ability for keys to be moved off of approved devices or sync fabrics. However, similar mitigations are not currently available for public-facing use cases, leaving RPs dependent on the sharing models adopted by syncable authenticator providers. Owners of public-facing applications should be aware of the risks associated with shared authenticators. When interacting with the public, agencies have limited visibility into which specific authenticators are being employed by their users and should assume that all syncable authenticators may be subject to sharing. While many sharing models have substantial controls that minimize risks (e.g., requiring close proximity between devices to allow sharing), other implementations are less restrictive.

The risk of sharing posed by this new class of authenticators is not unique. It applies to all authenticator types, some of which are weaker than syncable authenticators. Any authenticator can be shared by a user who is determined to share it. Users can actively share passwords, OTPs, out-of-band authenticators, and even push authentication events that allow a designee (whether formal or not) to authenticate on behalf of an end user.

Agencies determine which authenticators they will accept for their applications based on the specific risks, threats, and usability considerations they face. Syncable authenticators may be offered as a new option for applications that seek to implement up to AAL2. The trade-offs of this technology should be well-balanced based on their expected outcomes for security, privacy, equity, and usability.

## Example

A common use of syncable authenticators is in an AAL2 authentication transaction. The following items summarize how WebAuthn syncable authenticators satisfy various aspects of AAL2 requirements:

Phishing resistance (recommended; required for federal enterprise)
: **Achieved**: Properly configured syncable authenticators create a unique public or private key pair whose use is constrained to the domain in which it was created (i.e., the key can only be used with a specific website or RP). This prevents a falsified web page from being able to capture and reuse an authenticator output.

Replay resistance (required)
: **Achieved**: Syncable authenticators prevent replay resistance (i.e., prevention of reuse in future transactions) through a random nonce that is incorporated into each authentication transaction.

Authentication intent (required)
: **Achieved**: Syncable authenticators require users to input an activation secret to initiate the cryptographic authentication protocol. This serves as authentication intent, as the event cannot proceed without the user's active participation.

Multi-factor (required)
: **Achieved**: The user verified (UV) flag value indicates whether a local authentication mechanism (i.e., an activation factor) was used to complete the transaction. Without user verification, the verifier prompts for an additional authentication factor as part of the transaction.

## Security Considerations

Syncable authenticators present distinct threats and challenges that agencies should evaluate before implementation or deployment, as shown in [Table 4](B_syncable#table-4).

~~~
\clearpage
~~~
{:latex-literal="true"}

[Table 4. Syncable authenticator threats, challenges, and mitigations](B_syncable.md#table-4){:name="table-4"}
{:latex-ignore="true"}

| Threat or Challenge | Description | Mitigations |
|---------------------|-------------|-------------|
| **Unauthorized key use or loss of control** | Some syncable authenticator deployments support sharing private keys to devices that belong to other users who can then misuse the key | Enforce enterprise device management features or managed profiles that prevent synced keys from being shared. |
| | | Notify users of key-sharing events through all available notification channels. |
| | | Provide mechanisms for users to view keys, key statuses, and whether/where keys have been shared. |
| | | Educate users about the risks of unauthorized key use through existing awareness and training mechanisms. |
| **Sync fabric compromise** | To support key syncing, most implementations clone keys to a sync fabric (i.e., a cloud-based service connected to multiple devices associated with an account). | Store only encrypted key material. |
| | | Implement syncing fabric access controls that prevent anyone other than the authenticated user from accessing the private key. |
| | | Evaluate cloud services for baseline security features (e.g., FISMA Moderate protections or comparable). |
| | | Leverage hardware security modules to protect encrypted keys. |
| **Unauthorized access to sync fabric and recovery** | Synced keys are accessible via cloud-based account recovery processes, which represent a potential weakness to the authenticators. | Implement authentication recovery processes that are consistent with SP 800-63B. |
| | | Restrict recovery capabilities for federal enterprise keys through device management or managed account capabilities. |
| | | Bind multiple authenticators at AAL2 and above to support recovery. |
| | | Require AAL2 authentication to add any new authenticators for user access to the sync fabric. |
| | | Use only as a derived authenticator in federal enterprise scenarios [[SP800-157]](references.md#ref-sp800-157). |
| | | Notify the user of any recovery activities. |
| | | Leverage a user-controlled secret (i.e., something not known to the sync fabric provider) to encrypt and recover keys. |
| **Revocation** | Since syncable authenticators use RP-specific keys, the ability to centrally revoke access based on those keys is challenging. For example, with traditional PKI, CRLs can be used centrally to revoke access. A similar process is not available for syncable authenticators (or any FIDO WebAuthn-based credentials). | Implement a central identity management (IDM) account for users to manage authenticators and remove them from the "home agency" account if they are compromised or expired. |
| | | Leverage SSO and federation to limit the number of RP-specific keys that will need to be revoked in an incident. |
| | | Establish policies and tools to request that users periodically review keys for validity and currency. |
{:latex-table="4" latex-caption="Syncable Authenticator Threats, Challenges, and Mitigations" latex-longtable="true"  latex-columns="p@0.20\textwidth,p@0.35\textwidth,p@0.35\textwidth"}
