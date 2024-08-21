---
layout: default
title: Subscriber-Controlled Wallets
navOrder: 6
navTitle: Wallets
permalink: /sp800-63c/Wallets/
anchor: wallet
section: 5
---

# Subscriber-Controlled Wallets {#wallet}

*This section is normative.*

When the IdP runs on a device controlled by the subscriber, whether as a digital wallet or as a self-issued identity provider, the IdP is known as a _subscriber-controlled wallet_ and the following requirements apply.

Subscriber-controlled wallets **SHALL** require the presentation of an activation factor in order to perform any actions requiring the use of the wallet's signing key, including onboarding of the wallet and release of attributes to an RP.

## Wallet Activation

The subscriber-controlled wallet **SHALL** require presentation of an activation factor from the subscriber for the following actions:

- Providing proof of the signing key to the CSP during the provisioning process
- Signing the assertion for presentation to the RP

The subscriber-controlled wallet **SHOULD** require presentation of an activation factor before any other operations that involve use of the wallet's signing keys. The wallet **MAY** request reissuance of previously-issued attribute bundles without requiring subscriber involvement.

Submission of the activation factor **SHALL** be a separate operation from the unlocking of the host device (e.g., smartphone), although the same activation factor used to unlock the host device **MAY** be used in the activation operation. Agencies **MAY** relax this requirement for subscriber-controlled wallets managed by or on behalf of the CSP (e.g., via mobile device management) that are constrained to have short (agency-determined) inactivity timeouts and device activation factors meeting the above requirements. Additional discussion of activation factors for authenticators is found in [Sec. 3.2.10 of [SP800-63B]](../_sp800-63b/3_authenticators.md#s-5-2-10){:latex-href="#ref-SP800-63B"}.

## Federation Transaction

A federation transaction with a subscriber-controlled wallet establishes the subscriber's device as an IdP for the subscriber account and creates an authenticated session for the subscriber at the RP. The process is shown in [Fig. 13](5_subscriberidp.md#fig-13).

[Fig. 13. Federation with a Subscriber-Controlled Wallet](5_subscriberidp.md#fig-1){:name="fig-13"}
{:latex-ignore="true"}

![Overview diagram of federated authentication process using a subscriber-controlled wallet.]({{site.baseurl}}/{{page.collection}}/images/subscriberidp.png 'Subscriber-Controlled Wallet'){:latex-src="subscriberidp.pdf" latex-fig="13" latex-place="p"}


A federation transaction with a subscriber-controlled wallet takes place over several steps:

1. The CSP identity proofs the subscriber and creates a subscriber account.
1. The CSP provisions the wallet to the subscriber account, which includes the subscriber verifying an authenticator in their subscriber account.
1. The wallet receives a signed attribute bundle from the CSP, allowing the wallet to act as an IdP.
2. The RP requests a federated authentication from the wallet, usually through subscriber action.
3. The subscriber activates the wallet through an authentication factor.
4. The wallet creates an assertion based on the attribute bundles available to the wallet.
5. The wallet presents the assertion to the RP.
6. The RP validates the assertion.
7. The RP creates an authenticated session for the subscriber.

## Trust Agreements

The trust agreement for a transaction involving a subscriber-controlled wallet **SHALL** be established between the RP and the CSP. The trust agreement **MAY** be facilitated through use of a federation authority, as described in [Sec. 3.4.2](3_federation.md#authorities).

In most cases, the RP does not have a direct trust relationship with the wallet (acting as IdP), but instead trusts the wallet transitively through the wallet's established relationship with the CSP. This relationship can be verified by the means of attribute bundles, as described in [Sec. 3.11.1](3_federation.md#attribute-bundles). Even though the wallet is not usually involved in the process of establishing the trust agreement, the trust agreement between the RP and CSP can still be accomplished in either an a priori or subscriber-driven fashion.

The trust agreement **SHALL** include the following

- The set of subscriber attributes the CSP makes available to wallets in attribute bundles
- The set of subscriber attributes the wallet can make available to the RP
- The population of subscriber accounts that the CSP can represent
- The xALs available from the wallet

The release of subscriber attributes **SHALL** be managed using a runtime decision managed by the wallet, as described in [Sec. 4.6.1.3](4_generalidp.md#idp-runtime-decision). The authorized party **SHALL** be the subscriber.

The following terms **SHALL** be disclosed to the subscriber during the runtime decision:

- The set of subscriber attributes that the RP will request (a subset of the attributes made available)
- The purpose for each attribute requested by the RP
- The xALs required by the RP

Note that all information disclosed to the subscriber needs to be conveyed in a manner that is understandable and actionable, as discussed in [Sec. 8](8_usability.md#usability).

If FAL3 is allowed within the trust agreement and authenticators other than the wallet itself are allowed for use at FAL3, the trust agreement **SHALL** stipulate the following terms regarding holder-of-key assertions and bound authenticators (see [Sec. 3.14](3_federation.md#idp-managed-bound-authn) and [Sec. 3.15](3_federation.md#bound-authn)):

- Whether the wallet's presentation is considered sufficient for holder-of-key assertion requirements
- The means by which non-wallet holder-of-key assertions can be verified by the RP (such as a common trusted PKI system)
- The means by which the RP can associate non-wallet holder-of-key assertions with specific RP subscriber accounts (such as attribute-based account resolution or pre-provisioning)
- Whether bound authenticators are supplied by the RP or by the subscriber
- Documentation of the binding ceremony used for any subscriber-provided bound authenticators

## Provisioning the Subscriber-Controlled Wallet {#scidp-provisioning}

When the CSP provisions the subscriber-controlled wallet, the process **SHALL** include the following steps:

0. The subscriber authenticates to the CSP's provisioning system using one or more authenticators bound to the subscriber account.
0. The subscriber activates the wallet using an activation factor.
1. The wallet proves possession of its signing key to the CSP.
2. The CSP creates one or more attribute bundles that include subscriber attributes and the wallet's signing key (or a reference to that key).
3. The wallet stores the attribute bundle for later presentation to RPs.

The subscriber-controlled wallet **MAY** generate and use a different signing key for each provisioning request with the CSP.

The CSP **SHALL** create a unique attribute bundle for each requesting wallet.

### Deprovisioning the Subscriber-Controlled Wallet

The CSP **SHALL** provide a means of deprovisioning a subscriber-controlled wallet. The deprovisioning process is used when the subscriber account is terminated, thereby rendering downstream federation actions invalid, or when the wallet needs to be terminated due to the device being lost, stolen, or compromised.

To accomplish this, the CSP **SHALL** issue attribute bundles with a limited time validity window, **SHALL** issue attribute bundles specific to each wallet. The CSP **SHOULD** provide a means to independently verify the status of attribute bundles (i.e., whether a specific bundle has been revoked by the CSP). If such a service is offered, the service **SHALL** be deployed in a privacy-preserving way such that the CSP is not alerted to the use of a specific attribute bundle at a specific RP.

## Discovery and Registration

To perform a federation transaction with a subscriber-controlled wallet, the RP **SHALL** first determine the attribute bundle singing public key of the CSP through a secure process as stated by the trust agreement. In some systems, this is accomplished by retrieving the CSP's attribute bundle signing public keys from a URL known to be controlled by the CSP. In other systems, the RP is configured manually with the public key of the CSP before being deployed.

The RP learns the identifier and assertion signing public keys of the subscriber-controlled wallet as part of the attribute bundle signed by the CSP, presented in the federation transaction. The RP trusts the CSP's onboarding process of the wallet to provide assurance that the public key being presented can be trusted to present the attribute bundle in question.

The RP also needs to register with the subscriber-controlled wallet. In most cases, this is expected to be a dynamic process in which the RP introduces its properties during the federation transaction. The nature of a subscriber-controlled wallet makes it difficult for any specific RP to pre-register with an instance of the wallet, but this use case can be facilitated through the use of a trusted third party stipulated in the trust agreement. For example, an ecosystem has a centralized service for managing discovery and registration. When an RP joins the ecosystem, it registers itself with the trusted service, downloads the CSP's public keys, and receives an identifier to use with wallets. When the wallet is onboarded by the CSP, the wallet is informed where it can find the list of valid RP identifiers within the ecosystem. When the RP connects to the wallet, the wallet can verify the RP's identifier without the RP having to register itself directly with the wallet. Likewise, the RP can verify the wallet's signing keys by the fact they are presented in an attribute bundle signed by the CSP's public key, which had in turn been retrieved from the trusted third party.

## Authentication and Attribute Disclosure

The decision of whether a federated authentication can occur or attributes may be passed **SHALL** be determined by the subscriber, acting in the role of the authorized party.

The subscriber-controlled wallet **SHOULD** provide a means to selectively disclose a subset of the attributes in the attribute bundle from the CSP.

The CSP **SHALL** provide effective mechanisms for redress of subscriber complaints or problems (e.g., subscriber identifies an inaccurate attribute value, or the need to deprovision a subscriber-controlled wallet). See [Sec. 3.4.3](3_federation.md#redress) for additional requirements and considerations for redress mechanisms.

## Assertion Requests

When the federation transactions are initiated by the RP, the RP's request for an assertion **SHALL** contain:

1. An identifier for the RP
2. A cryptographic nonce
3. The set of identity attributes requested by the RP and their purpose of use at the RP

Note that federation transactions are always initiated by the RP at FAL2 or higher.

## Assertion Contents

Assertions from a subscriber-controlled wallet **SHALL** contain:

0. A signed attribute bundle from the CSP.
1. Subject identifier: An identifier for the party to which the assertion applies (i.e., the subscriber).
2. Issuer identifier: An identifier for the issuer of the assertion (i.e., the subscriber-controlled wallet).
3. Audience identifier: An identifier for the party intended to consume the assertion (i.e., the RP).
4. Issuance time: A timestamp indicating when the wallet issued the assertion.
5. Validity time window: A period of time outside of which the assertion **SHALL NOT** be accepted as valid by the RP for the purposes of authenticating the subscriber and starting an authenticated session at the RP. This is usually communicated by means of an expiration timestamp for the assertion in addition to the issuance timestamp.
6. Assertion identifier: A value uniquely identifying this assertion, used to prevent attackers from replaying prior assertions.
7. Authentication time: A timestamp indicating when the subscriber last used the wallet's activation factor.
11. Nonce: A cryptographic nonce, if one is provided by the RP.
11. Signature: Digital signature using asymmetric cryptography, covering the entire assertion.

All assertions **SHALL** contain sufficient information to determine the following aspects of the federation transaction:

8. The IAL of the subscriber account being represented in the assertion, or an indication that no IAL is asserted.
10. The wallet's intended FAL of the federation process represented by the assertion.

At FAL3, the assertion **SHALL** include one of the following:

- The public key, key identifier, or other identifier for a holder-of-key assertion. This **MAY** be the same key that the subscriber-controlled wallet uses to sign the assertion.
- An indicator that verification of a bound authenticator is required to process this assertion. 

The signed attribute bundle from the CSP **SHALL** contain:

0. A public key or key identifier for the key used by the subscriber-controlled wallet to sign the assertion
4. Issuance time: A timestamp indicating when the CSP issued the attribute bundle.
5. Validity time window: A period of time outside of which the attribute bundle **SHALL NOT** be accepted as valid by the RP for the purposes of authenticating the subscriber and starting an authenticated session at the RP. This is usually communicated by means of an expiration timestamp for the assertion in addition to the issuance timestamp.
8. IAL: Indicator of the IAL of the subscriber account being represented in the attribute bundle, or an indication that no IAL is asserted.
11. Signature: Digital signature using asymmetric cryptography, covering the entire attribute bundle.

Additional identity attributes and derived attribute values **MAY** be included in the attribute bundle. These attributes **SHOULD** be made available using a selective disclosure method, whereby the subscriber can, through their wallet software, determine which parts of the bundle to disclose to the RP.

Identity attributes in the assertion but outside of a signed attribute bundle **SHALL** be considered self-asserted. The RP **MAY** validate these additional attributes out of band.

Subscriber-controlled wallets **SHOULD** use non-exportable key storage as discussed in [Sec. 3.5.2](3_federation.md#key-storage).

## Assertion Presentation

Assertions **SHALL** be presented to the RP through an authenticated protected channel.

The presentation **SHALL** include the cryptographic nonce from the RP's request, if present. The RP **SHALL** verify the nonce in accordance with the federation protocol.

If the assertion contains PII, and the presentation mechanism passes the assertion through a component other than the wallet or RP, the assertion **SHOULD** be encrypted.

The RP **SHALL** protect itself against injection of manufactured or captured assertions by the use of cross-site scripting protection, rejecting assertions outside of the correct stage of a federation transaction, or other accepted techniques discussed in [Sec. 3.10.1](3_federation.md#injection-protection). When possible, the IdP **SHOULD** use platform APIs instead of HTTP redirects when delivering an assertion to the RP.

Since assertions from a subscriber-controlled wallet always contain a reference to the wallet's signing key inside the signed attribute bundle from the CSP, assertions from subscriber-controlled wallets **MAY** be used as holder-of-key assertions to reach FAL3, as long as all other requirements in these guidelines are met. For additional requirements for holder-of-key assertions, see [Sec. 3.14](3_federation.md#idp-managed-bound-authn).

## Assertion Validation

The RP **SHALL** validate the signature on all signed attribute bundles in the assertion, using the cryptographic key from the CSP issuing the signed attribute bundle. The RP **SHALL** validate the signature of the assertion using the identified cryptographic key in the signed attribute bundle.

The RP **SHALL** validate the assertion by checking that all the following are true:

 - *Issuer verification*: ensuring that the assertion was issued by the wallet the RP expects it to be from.
 - *Time validation*: ensuring that the expiration and issue times are within acceptable limits of the current timestamp.
 - *Audience restriction*: ensuring that this RP is the intended recipient of the assertion.
 - *Nonce*: ensuring that the cryptographic nonce included in the RP's request is included in the presentation.
 - *Transaction terms*: ensuring that the IAL, AAL, and FAL represented by the assertion are allowable under the applicable trust agreement.

Additionally, the issuer **MAY** make available an online mechanism to determine the validity of a given attribute bundle, such as a status list queryable by the RP.

## RP Subscriber Accounts

RP subscriber accounts **SHALL** be managed using a just-in-time or ephemeral provisioning model only (see [Sec. 4.6.3](4_generalidp.md#provisioning)). In each of these cases, the RP creates the RP subscriber account and associates it with the federated identifier only after successful validation of the assertion from the wallet.

The RP **SHALL** disclose its practices for management of subscriber information as part of the trust agreement. The RP **SHALL** provide effective means of redress to the subscriber for correcting and removing information from the RP subscriber account. See [Sec. 3.4.3](3_federation.md#redress) for additional requirements and considerations for redress mechanisms.
