---
layout: default
title: Examples
navOrder: 11
navTitle: Examples
permalink: /sp800-63c/examples/
anchor: examples
section: 10
---

# Examples {#examples}

*This section is informative.*

This appendix contains several example scenarios of federation used in conjunction with the requirements in these guidelines.

The scenarios in this section are for illustrative purposes and do not convey additional requirements beyond those imposed by these guidelines.

## Mapping FALs to Common Federation Protocols

Of protocols commonly in use today, OpenID Connect [[OIDC]](references.md#ref-OIDC) and SAML [[SAML]](references.md#ref-SAML) both provide a variety of capabilities that can be leveraged to reach the requirements at different FALs. [Table 5](10_examples.md#table-5) provides examples of specific options in these protocols that could be deployed to reach a given FAL. It's important to note that these guidelines do not represent a normative mapping to the given FALs and the entirety of the federation process has to be considered when establishing an FAL. Additionally, each FAL could be reached by processes, deployments, and procedures that are not listed in this table.

[Table 5. FAL Protocol Examples](10_examples.md#table-5){:name="table-5"}
{:latex-ignore="true"}

||OIDC|SAML|
|---|---|---|
|FAL1| All core flows in [[OIDC]](references.md#ref-OIDC) (Authorization Code, Implicit, and Hybrid) can all be configured to require signing of the assertion (the ID Token) using JSON Web Signatures. Assertions are presented in a variety of front and back channel methods. Each of these flows can be built using both static and dynamic client registration. Profiles such as [[OIDC-Basic]](references.md#ref-OIDC-basic) and [[OIDC-Implicit]](references.md#ref-OIDC-implicit) can provide additional guidance for interoperable deployments.|The [[SAML-WebSSO]](references.md#ref-SAML-WebSSO) profile allows for the signing of assertions using XML D-Sig and presentation of the assertion using the front channel. SAML deployments are generally set up with a static registration, sometimes managed through a federation authority, which can meet the requirements at this FAL and above.|
|FAL2|Flows that present the ID Token in the back channel (such as Authorization Code and Hybrid) can provide a level of injection protection.|The Artifact Binding of SAML defined in [[SAML-Bindings]](references.md#ref-SAML-bindings) allows for a back-channel presentation of SAML assertions that can provide a level of injection protection.|
|FAL3|The ID Token can include the claims necessary for Holder-of-Key and Bound Authenticator assertion presentations, though to date there are not industry standard profiles for doing so.|The SAML Holder-of-Key profile can fit the assertion requirements at this level, if combined with other deployment choices.|
{:latex-table="5" latex-caption="FAL Protocol Examples" latex-columns="p@0.10\textwidth,p@0.42\textwidth,p@0.42\textwidth"}

For OpenID Connect in particular, it is common practice to give access to both an identity API (the UserInfo Endpoint) as well as additional APIs. While the security of API access is outside the scope of these guidelines (which are concerned with the identity assertion primarily), it is sensible for an OpenID Connect implementation to want to increase the security of all API calls in tandem with the FAL. For example, in addition to requiring a Holder-of-Key assertion at FAL3, which requires verification of a subscriber-held key, an OpenID Connect system might also require sender-constrained access tokens for API access, which require the verification of a key held by the RP for each API call.

## Direct Connection to an Agency's IdP

Agency A, which issues and manages subscriber accounts, sets up and operates an OpenID Connect IdP in order to make these subscriber accounts available online through a federation process.

The RP enters into a pairwise trust agreement with the IdP to accept assertions for subscribers from Agency A. The RP declares the set of attributes that it needs from the IdP as part of this agreement. The trust agreement stipulates that the subscriber is the authorized party for determining the release of attributes in the federation transaction.

The IdP generates a federated identifier for the subscriber account by taking the unique internal identifier for the subscriber account (such as an employee record number) and passing it through a one-way cryptographic function to create a unique identifier for the subscriber account. Such an identifier does not allow an RP to calculate the internal identifier but will be stable across attribute changes.

Per the terms of the trust agreement, the subscriber is prompted by the IdP the first time they log on to the RP. The IdP asks for the subscriber's consent at runtime to share their attributes with the RP, displaying to the subscriber the RP's requested uses for these attributes on the consent screen. The IdP also prompts the subscriber to allow the IdP to remember this consent decision. This stored decision causes the IdP to act on the stored consent in a future request and not prompt the subscriber if the same RP requests the same attributes.

The assertion, formatted as an OpenID Connect ID Token, contains the minimum set of attributes to facilitate the federated log in. Apart from the federated identifier, the assertion contains no identifying information about the subscriber. In addition to the assertion, the RP is given an OAuth 2.0 access token that allows the RP to access the identity API hosted by the IdP, the OpenID Connect UserInfo Endpoint. The RP can choose to call this API to get additional attributes as needed, such as the first time the subscriber uses the RP. Since this RP follows a just-in-time provisioning model, when the RP sees the subscriber's federated identifier for the first time, the RP creates an RP subscriber account for that federated identifier and calls the identity API to populate the RP subscriber account with the subscriber's attributes. For future authentications with this subscriber, the RP can decide if its cache of attributes is reasonably recent enough or if it should be refreshed by calling the identity API.

## Multilateral Federation Network

Agencies A, B, and C each have an IdP running OpenID Connect for their subscriber accounts. All three agencies join a multilateral federation run by an independent agency set up to provide inter-agency connections. The federation authority independently verifies that each IdP represents the agency in question. The federation authority publishes the discovery records of the IdPs for all agencies that are part of the multilateral federation. This publication allows RPs within the federation to discover which IdP is to be used to access accounts for a given agency under the rules of the federation agreement.

RPs X and Y wish to allow logins from agencies A, B, and C, and the RPs declare their intent and a list of required attributes to the federation authority. The federation authority assesses both RP requests and adds them to the multilateral federation's trust agreement. This allows both RPs to register at each of the three separate IdPs as needed for each agency.

Both RPs interface directly with each of the three IdPs and not through a federation proxy. When a new IdP or RP is added to the multilateral federation agreement, the existing IdPs and RPs are notified of the new component and its parameters.

The IdPs and RPs establish a shared signaling channel under the auspices of the federation authority. This allows any IdP and any RP to report suspicious or malicious behavior that involves a specific account to the rest of the members under the federation authority.

## Issuance of a Credential to a Digital Wallet

Agency B makes its subscriber accounts available for federation through the use of digital wallet technology. The agency's agreement for issuing credentials into wallets is facilitated by a federation authority that is set up to manage digital wallets across the federal government. The federation authority establishes the identity of the CSP for each agency under the multilateral agreement, and it ensures that only the CSP for Agency B can onboard subscriber-controlled wallets for Agency B within the multilateral trust agreement.

A subscriber has a digital wallet running on their device that they want to use with their subscriber account from Agency B. Within these guidelines, the digital subscriber-controlled wallet needs to be onboarded by the CSP before it can act as an IdP. To begin this process, the subscriber directs their digital wallet software to Agency B's CSP. The subscriber uses a biometric factor to activate their digital wallet, and the digital wallet makes an onboarding request to the CSP for the subscriber account. This onboarding request includes proof of a key held by the digital wallet. The CSP verifies the wallet's proof and processes any additional attestations from the wallet device.

The subscriber authenticates to the CSP during the onboarding process. The CSP prompts the subscriber with the terms of the trust agreement from the federation authority, and asks the subscriber to confirm that they wish to issue an identity to the digital wallet in question. The subscriber is informed of the sets of attributes that are made available to the wallet.

The CSP creates an attribute bundle that includes the subscriber's attributes as well as a reference to the digital wallet's key. The CSP signs this attribute bundle with its own key and returns the bundle to the digital wallet.

When the subscriber needs to authenticate to an RP, the RP sends a query to the subscriber's wallet for a credential that fits the RP's needs. The RP has a trust agreement with the same federation authority, agreeing to trust identities issued under the multilateral trust agreement's rules. The digital wallet, acting as an IdP, identifies that the RP's request can be fulfilled by the attribute bundle issued from Agency B's CSP. The digital wallet prompts the subscriber to activate the IdP function of the digital wallet software using a local biometric factor. The digital wallet prompts the subscriber to confirm that they want to present the requested attributes to the RP in question. When the subscriber accepts, the IdP function of the digital wallet creates an assertion for the RP that is signed with the digital wallet's keys. The assertion includes the attribute bundle from the CSP, which itself is covered by the signature from the IdP function. The IdP delivers the assertion to the RP.

The RP receives the signed assertion and validates the signature of the attribute bundle from the CSP, using the CSP's keys identified by the federation authority. The RP then validates the signature of the assertion using the key identified in the assertion. When these checks pass successfully, the RP creates an RP subscriber account to represent the subscriber at the RP, based on the information in the assertion.

## Enterprise Application Single-Sign-On {#enterprise-sso}

For enterprise applications, it is a common pattern for the organization to make the application available to all potential subscribers within the agency, through the use of an allowlist and pre-provisioned accounts.

In this scenario, Agency E establishes a pairwise agreement with an RP to provide an enterprise-class service to all employees of Agency E through the agency's OpenID Connect IdP. As part of this trust agreement, the IdP allows access to a SCIM-based provisioning API for the RP. The IdP creates a federated identifier for each subscriber account and uses the provisioning API to push the federated identifiers and their associated attributes to the RP. In this way, the RP can pre-provision an RP subscriber account for every subscriber in the IdP's system, allowing the RP to offer functions like access rights, data sharing, and messaging to all accounts on the system, whether or not a specific account has logged in to the RP yet.

Under the terms of the trust agreement, the RP is placed on an allowlist with the IdP. The allowlist entry states that:

- The subscriber has an active subscriber account at Agency E
- The subscriber has authenticated with the IdP at AAL2 or greater
- The RP is allowed to request only the federated identifier and basic authentication event information, since all other necessary attributes will be available through the provisioning API
- The federation transaction is at FAL2

Consequently, subscribers are not prompted for consent at runtime because the agency consented to use the service on behalf of all accounts at the time the RP was onboarded. This gives subscribers a seamless single sign-on experience, even though a federation protocol is being used across security domain boundaries. Since the IdP does not use any runtime decisions, any deviation from the allowlist parameters causes the federation transaction to fail.

The RP subscriber accounts are synchronized using the provisioning API. When a new subscriber account is created, modified, or deleted at the IdP, the IdP updates the status of the RP subscriber account using the provisioning API. This allows the RP to always have an up-to-date status for each subscriber account. For example, when the subscriber account is terminated at the IdP, the provisioning API signals to the RP that the corresponding RP subscriber account is to be terminated immediately. The RP removes all locally cached attributes for the account in question, except for the identifiers and references in audit and access logs.

## FAL3 With a Smart Card {#fal3-smart-card}

A subscriber has a cryptographic authenticator on a smart card. The certificate on this smart card can be verified independently by both the IdP and RP thanks to the use of a shared PKI system stipulated by the trust agreement. This type of authenticator can be used in a holder-of-key assertion at FAL3.

The subscriber starts the federation process and authenticates to the IdP using their authenticator. The IdP creates an assertion that includes a flag indicating that the assertion is intended for use at FAL3. The assertion also contains the certificate common name (CN) and thumbprint of the certificate to be used as a bound authenticator.

When the RP receives the assertion, the RP processes the assertion as usual and sees the FAL3 flag and the certificate attributes. The subscriber authenticates to the RP using their authenticator, and the RP verifies that the certificate presented by the subscriber matches the certificate in the assertion from the IdP. When these match, the RP creates a secure session with the subscriber at FAL3.

## FAL3 With a non-PKI Authenticator {#fal3-nonpki}

A subscriber has a hardware cryptographic authenticator that speaks the WebAuthn protocol. This authenticator is not tied to any PKI system, and in fact the authenticator device presents completely different and unlinked keys to both the IdP and RP during its normal authentication process. This kind of authenticator can still be used at FAL3 if the RP manages the bound authenticator.

In this example, when the subscriber uses this authentication device at the IdP, it presents proof of Key1. When the subscriber uses the same device at the RP, it presents proof of Key2. These are logically two separate authenticators, but from the perspective of the subscriber, they are using the same device in multiple places.

To start a federation transaction, the subscriber authenticates to the IdP using Key1. The IdP then creates an assertion that is flagged as FAL3. Since the IdP has no visibility into the existence and use of Key2, the assertion says that the subscriber is using a bound authenticator to reach FAL3. When the RP processes this assertion, the RP checks the RP subscriber account associated with the federated identifier in the assertion to find an RP bound authenticator for that account using Key2. The RP prompts the subscriber to authenticate using Key2. When that key is verified, the RP creates a secure session with the subscriber at FAL3.

## FAL3 With Referred Token Binding

A subscriber authenticates to their IdP using a certificate that is trusted by the IdP but not known to the RP, since the IdP and RP are not in a shared PKI environment. However, the IdP and RP support the referred token binding extension of TLS. When the subscriber presents their certificate to the IdP, the IdP creates an assertion with the CN and thumbprint of the subscriber's certificate. Along with the assertion or assertion reference, the IdP returns token binding headers. When these headers are presented to the RP, the RP can use them to associate the contents of the assertion with the subscriber's bound authenticator. The RP still has to verify the certificate, but the token binding allows the RP to do so without having to separately trust the certificate chain of the authenticator's certificate.

## Ephemeral Federated Attribute Exchange

An RP needs to access a specific attribute for a subscriber, such as proof of age or affiliation with a known entity like a specific agency, without needing to know the identity of the subscriber. The RP requests only the derived attribute values that it needs in order to process its transaction, in this case a simple boolean of whether the subscriber is of age or is affiliated with the entity. The federation process creates an authenticated session between the RP and the subscriber. However, the RP uses an ephemeral provisioning mechanism, retaining only a record of the transaction and no further identifying attributes of the subscriber. The IdP provides a pairwise pseudonymous identifier to the RP. Since the IdP knows of the ephemeral nature of the RP subscriber account, the IdP can provide a distinct PPI to the RP on each request without affecting the subscriber's usage of the RP. The IdP prompts the subscriber at runtime to release the derived attributes, preventing the RP from silently polling subscriber accounts against changes in information over time.

## Multiple Different Authorized Parties and Trust Agreements {#authorized-party-example}

As a subscriber uses services at multiple RPs, different trust agreements can come into play, and those agreements can have different requirements and experiences. In this scenario, the subscriber has an account through a single IdP which they use at three different RPs, each with a different kind of trust agreement and different requirements for consent and notification.

Organizational Authorized Party:
: An apriori trust agreement is established for an agency connecting to an enterprise service (the RP) to be made available to all subscribers at the agency. The authorized party for this trust agreement is the agency, and the IdP is configured with an allowlist entry for the RP with the set of common attributes requested by the RP for its use. When a subscriber logs in to the enterprise service, they are not prompted with any runtime decisions regarding the service, since the trust agreement establishes this connection as trusted. The details of this trust agreement are available to the subscriber from the IdP, including the list of attributes that are released to the RP and for what purpose.

Individual Authorized Party:
: A separate a priori trust agreement is established by the agency for another service (a different RP), and this service is made available to all subscribers at the same agency. This trust agreement stipulates that the subscriber is the authorized party for release of attribute information to the RP. When logging in to the service, each subscriber is prompted for their consent to release their attributes to the RP. The prompt includes the context for the subscriber to make an appropriate security decision, including a link to the details of the trust agreement and a list of attributes being released and their purpose of use. The IdP allows the subscriber to save this consent decision so that when this subscriber logs in to this same RP in the future, the subscriber is not prompted again for their consent so long as the trust agreement and the request from the RP have not changed.

Subscriber-driven Service Access:
: A subscriber-driven trust agreement is established when the subscriber goes to access an RP that is otherwise unknown by their IdP. The RP informs the subscriber about the uses of all attributes being requested from the IdP, and the IdP prompts the subscriber for consent to release their attributes to the RP. The IdP also warns the subscriber that the RP is unknown to the agency, and provides the subscriber with information received by the RP to help the subscriber make a secure decision.

All of these scenarios are involve the same subscriber account.

## Shared Pairwise Pseudonymous Identifiers for Multiple RPs {#shared-ppi}

A group of three applications is deployed in support of a specific mission, giving collaboration, document storage, and calendar capabilities. Due to the nature of the separate applications, they are deployed as separate RPs, but all are bound to the same IdP using a common trust agreement. The trust agreement stipulates that the three RPs are to be issued a shared PPI, so that the applications can coordinate individual subscriber accounts with each other but not with any other applications in the deployed environment. The IdP uses an algorithm to generate a shared PPI that incorporates a randomized identifier for the set of applications as well as a unique identifier for each subscriber accounts. As a result, all three RPs get the same PPI for each subscriber, but no other RP is issued that same identifier.

## RP Authentication to an IdP {#rp-auth}

A federation transaction typically takes place over multiple network calls. Throughout this process, it is important for the IdP and RP to know that they are talking to the same party that they were in a previous step, and ultimately to the party that they expect to be in the transaction with in the first place.

Different techniques exist that provide different degrees of assurance, depending on the federation protocol in use and the needs of the system. For example, the Authorization Code Flow of [[OIDC]](references.md#ref-OIDC) allows the RP to register a shared secret or private key with the IdP prior to the transaction, allowing the IdP to strongly authenticate the RP's request in the back channel to retrieve the assertion. In addition, the Proof Key for Code Exchange protocol in [[RFC7636]](references.md#ref-RFC7636) allows the RP to dynamically create an unguessable secret that is transmitted in hashed form in the front channel and then transmitted in full in the back channel along with the assertion reference. These techniques can of course be combined for even greater assurance.

Federation authorities can also facilitate the authentication process. If the RP registers its public key and identifier with the federation authority, the IdP needs only to retrieve the appropriate keys from the federation authority instead of requiring the RP to register itself ahead of time.

Technical profiles of specific federation protocols are out of scope of these guidelines, but high security profiles such as [[FAPI]](references.md#ref-FAPI) provide extensive guidelines for implementers to deploy secure federation protocols.
