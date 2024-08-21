---
layout: default
title: Common Federation Requirements
navOrder: 4
navTitle: Federation
permalink: /sp800-63c/Federation/
anchor: common
section: 3
---

# Common Federation Requirements {#common}

*This section is normative.*

A federation transaction serves to allow the subscriber to establish an authenticated session with the RP based on a subscriber account known to the IdP. The federation transaction can also provide the RP with a set of identity attributes within the authenticated session. The authenticated session can then be used by the RP for:

- logging in the subscriber to access functionality at the RP,
- identifying the subscriber based on presented attributes, and
- processing the subscriber attributes presented in the federation transaction.

A federation transaction requires relatively complex multiparty protocols that have subtle security and privacy requirements. When evaluating a particular federation protocol, profile, or deployment structure, it is often instructive to break it down into its component relationships and evaluate the needs for each of these:

- the subscriber to the CSP,
- the CSP to the IdP,
- the subscriber to the IdP,
- the IdP to the RP, and
- the subscriber to the RP.

In addition, the subscriber often interacts with the CSP, IdP, and RP through a user agent like a web browser. The user agent is therefore often involved in the federation process, but it is not necessary for all types of applications and interactions. As such, the actions of the subscriber described throughout these guidelines can optionally be performed through a user agent. Where necessary, requirements on the user agent are called out directly.

Each party in a federation protocol bears specific responsibilities and expectations that must be fulfilled in order for the federated system to function as intended.

The subscriber account is augmented by the IdP with federation-specific items, including but not limited to the following:

- One or more external subject identifiers, for use with a federation protocol
- A set of access rights, detailing which RPs can access which attributes of the subscriber account (such as allowlists and saved runtime decisions by the subscriber)
- Federated account usage information
- Additional attributes collected by or assigned by the IdP to the account

A subset of these attributes is made available to the RP through the federation process, either in the assertion or through an identity API (see [Sec 3.11.3](3_federation.md#s-identity-api)). These attributes are often used in determining access privileges for attribute-based access control (ABAC) or facilitating a transaction (e.g., providing a shipping address). The details of authorization and access control are outside the scope of these guidelines.

To keep and manage these attributes, the RP often maintains an *RP subscriber account* for the subscriber. The RP subscriber account also contains information local to the RP itself, as described in [Sec. 3.7](3_federation.md#rp-account).

Federation transactions take place across three dimensions:

Trust Agreements:
: The establishment of a policy decision that allows the CSP, IdP, and RP to connect for the purposes of federation. This policy is governed by a trust agreement, which establishes the permission to connect.

Associating Keys and Identifiers:
: The association of keys and identifiers for the CSP, IdP, and RP that take part in the federation transaction. This process enables the parties to identify each other securely for future exchanges.

Federation Protocol:
: The verification of the subscriber's identity by the IdP and subsequent issuance of an assertion to the RP. This results in the passing of subscriber attributes to the RP and establishing an authenticated session for the subscriber at the RP.

These dimensions all need to be fulfilled for a federation process to be complete. The exact order in which that happens, and which parties are involved in which steps, can vary depending on deployment models and other factors.

The requirements for IdPs in this section apply to both general-purpose IdPs as discussed in [Sec. 4](4_generalidp.md#GenIdP) and subscriber-controlled wallets as discussed in [Sec. 5](5_subscriberidp.md#wallet).

## Roles

### Credential Service Provider (CSP)

The CSP collects and verifies attributes from the subscriber and stores them in a subscriber account. The CSP also binds one or more authenticators to the subscriber account, allowing the subscriber to authenticate directly to systems capable of verifying an authenticator.

### Identity Provider (IdP)

The IdP provides a bridge between the subscriber account (as established by the CSP) and the RP that the subscriber is accessing. An IdP can be deployed as a service for multiple subscriber accounts or as a component controlled by a single subscriber.

The IdP establishes an authentication event with the subscriber, either through the verification of an authenticator (for general-purpose IdPs) or presentation of an activation factor (for subscriber-controlled wallets). The IdP creates assertions to represent the authentication event.

The IdP makes identity attributes of the subscriber available within the assertion or through an identity API (see [Sec. 3.11.3](3_federation.md#s-identity-api)).

_In some systems, this is also known as the offering party (OP)._

### Relying Party (RP)

The RP processes assertions from the IdP and provides the service that the subscriber is trying to access. Unlike in a direct authentication model, the RP does not provide the verifier function to authenticators tied to the subscriber account.

_In some systems, this is also known as the service provider (SP)._

## Functions

### Trust Agreement Management

The trust agreement (see [Sec. 3.4](3_federation.md#trust-agreement)) can be managed through a dedicated party, known as a _federation authority_. The federation authority facilitates the onboarding and management of parties fulfilling different roles and functions within a trust agreement. This management provides a transitive trust to other parties in the agreement.

For example, an RP can enter a trust agreement with a federation authority and decide that any IdP approved by that federation authority is suitable for its purposes. This trust can hold true whether or not the IdP was covered by the trust agreement at the time the RP joined. Federation authorities are used in multilateral trust agreements as discussed in [Sec. 3.4.2](3_federation.md#authorities).

### Authorized Party

The _authorized party_ in a trust agreement is the organization, person, or entity that is responsible for the specific release decisions covered by the trust agreement, including the release of subscriber attributes. The trust agreement stipulates who the expected authorized party is, as well as the parameters under which a request could be automatically granted, automatically denied, or require a runtime decision from an individual. For public-facing scenarios, the authorized party is expected to be the subscriber. For enterprise scenarios, the authorized party is expected to be the agency.

If the authorized party is the operator of the IdP, consent to release attributes is decided for all subscribers and established by an allowlist as described in [Sec. 4.6.1.1](4_generalidp.md#idp-allowlist), allowing for the disclosure of identity attribute without direct decisions and involvement by the subscriber. A trust agreement can alternatively stipulate that an individual, such as the subscriber, is to be prompted at runtime for consent to disclose certain attributes to the RP as discussed in [Sec. 4.6.1.3](4_generalidp.md#idp-runtime-decision). If specified by the trust agreement, it is also possible for an individual other than a subscriber to act as the authorized party. For example, an administrator of a system being prompted to release attribute information on behalf of a subscriber as part of a provisioning API.

Examples of different authorized parties are found in [Sec 10.10](10_examples.md#authorized-party-example).

### Proxied Federation {#proxied}

A federation _proxy_ acts as an intermediary between the IdP and RP for all communication in the federation protocol. The proxy functions as an RP on the upstream side and an IdP on the downstream side, as shown in [Fig. 1](3_federation.md#fig-1). When communicating through a proxy, the upstream IdP and downstream RP communicate with the proxy using a standard federation protocol, and the subscriber takes part in two separate federation transactions. As a consequence, all normative requirements that apply to IdPs and RPs **SHALL** apply to proxies in their respective roles on each side. Additionally, it is possible for a proxy to act as an upstream IdP to another proxy downstream, and so on in a chain.

[Fig. 1. Federation Proxy](3_federation.md#fig-3){:name="fig-1"}
{:latex-ignore="true"}

![Diagram of a federation proxy accepting assertions from an upstream IdP and providing assertions to a downstream RP.]({{site.baseurl}}/{{page.collection}}/images/proxy.png 'Federation Proxy'){:latex-src="proxy.pdf" latex-fig="1" latex-place="h"}

The role of the proxy is limited to the federation protocol; it is not involved in establishment or facilitation of a trust agreement between the upstream IdP and downstream RP. The same party can operate a federation authority as well as a proxy to facilitate federation transactions, but this function is separate from their role in managing the trust agreement. Just like other members of a federation system, the proxy can be involved in separate trust agreements with each of the upstream and downstream components, or a single trust agreement can apply to all parties such as in a multilateral agreement.

The federated identifier (see [Sec. 3.3](3_federation.md#federated-identifier)) of an assertion from a proxy **SHALL** indicate the proxy as the issuer of the assertion. The downstream RP receives and validates the assertion generated by the proxy, as it would an assertion from any other IdP. This assertion is based on the assertion the proxy receives from the upstream IdP. The contents of the assertion from the upstream IdP can be handled in several ways, depending on the method of proxying in use:

- The proxy can create an all-new assertion with no information from the assertion from the upstream IdP carried in it. This pattern is useful for blinding the downstream RP, so that the RP does not know which upstream IdP the subscriber originally came from.
- The proxy can copy attributes from the assertion from the upstream IdP into the assertion from the proxy. This pattern is useful for carrying identity attributes in the assertion to the downstream RP.
- The proxy can include the entire assertion from the upstream IdP in the assertion from the proxy. This pattern allows the RP to independently validate the assertion from the upstream IdP as well as the assertion from the proxy.

A proxied federation model can provide several benefits. Federation proxies can simplify technical integration between the RP and IdP by providing a common interface for integration. Additionally, to the extent a proxy effectively blinds the RP and IdP from each other, it can provide some business confidentiality for organizations that want to guard their subscriber lists from each other. Proxies can also mitigate some of the privacy risks described in [Sec. 3.9](3_federation.md#privacy-reqs), though other risks arise from their use since an additional party is now involved in handling subscriber information. For example, if an attacker is able to compromise the proxy, the attacker need not target the IdP or RP directly in order to gain access to subscriber attributes or activity since all of that information flows through the proxy. Additionally, the proxy can perform additional profiling of the subscriber beyond what the IdP and RP can do, since the proxy brokers the federation transactions between the parties and binds the subscriber account to either side of the connection.

See [Sec. 7.5](7_privacy.md#blinding) for further information on blinding techniques, their uses, and limitations.

The FAL of the connection between the proxy and the downstream RP is considered as the lowest FAL along the entire path, and the proxy **SHALL** accurately represent this to the downstream RP. For example, if the connection between the upstream IdP and the proxy is FAL1 and the connection between the proxy and the downstream RP otherwise meets the requirements of FAL2, the connection between the proxy and the downstream RP is still considered FAL1. Likewise, if the connection between the upstream IdP and the proxy is FAL2 and the connection between the proxy and the downstream RP is only FAL1, the overall connection through the proxy is considered FAL1.

### Fulfilling Roles and Functions of a Federation Model

The roles in a federation transaction can be connected in a variety of ways, but several common patterns are anticipated by these guidelines. The expected trust agreement structure and connection between components will vary based on which pattern is in use.

Different roles and functions can be fulfilled by separate parties who integrate with each other. For example, a CSP can provide attributes of the subscriber account to an IdP that is not operated by the same party or agency as the CSP.

It is also possible for a single party to fulfil multiple roles within a given federation agreement. For example, if the CSP provides the IdP as part of its identity services, the CSP can provision the subscriber accounts at the IdP as part of the subscriber account establishment process. Similarly, the RP can also be in the same security and administrative domain as the IdP, but still use federation technology to connect for technical, deployment, and account management benefits.

The same is true for other functions in the overall federation system, such as a federation authority and proxy. While the roles may seem similar, they are fundamentally distinct and do not need to be connected: a federation authority facilitates establishment of a trust agreement between parties, and a proxy facilitates connection of the federation protocol by acting as an RP to the upstream IdP and as an IdP to the downstream RP. The same entity can fulfill both the federation authority and proxy functions in the system, providing both a means of establishing trust agreements and a means of establishing technical connections between IdPs and RPs.

## Federated Identifiers {#federated-identifier}

The subscriber **SHALL** be identified in the federation transaction using a federated identifier unique to that subscriber. A federated identifier is the logical combination of a subject identifier, representing a subscriber account, and an issuer identifier, representing the IdP. The subject identifier is assigned by the IdP, and the issuer identifier is assigned to the IdP usually through configuration.

The multi-part federated identifier pattern is required because different IdPs manage their subject identifiers independently, and could therefore potentially collide in their choices of subject identifiers for different subjects. Therefore, it is imperative that an RP never process the subject identifier without taking into account which IdP issued that subject identifier. For most use cases, the federated identifier is stable for the subscriber across multiple sessions and is independent of the authenticator used, allowing the RP to reliably identify the subscriber across multiple authenticated sessions and account changes. However, it is also possible for the federated identifier and its associated use at the RP to be ephemeral, providing some privacy enhancement. Federated identifiers, and their constituent parts, are intended to be machine-readable and not managed by or exposed to the subscriber, unlike a username or other human-facing identifier.

Federated identifiers **SHALL** contain no plaintext personally-identifiable information (PII), such as usernames, email addresses, or employee numbers, etc.

### Pairwise Pseudonymous Identifiers (PPI) {#ppi}

In some circumstances, it is desirable to prevent the subscriber account from being easily linked at multiple RPs through use of a common subject identifier. The use of a pairwise pseudonymous identifier (PPI) allows an IdP to provide multiple distinct federated identifiers to different RPs for a single subscriber account. Use of a PPI prevents different RPs from colluding together to track the subscriber using the federated identifier.

#### General Requirements

When using pairwise pseudonymous identifiers within the assertions generated by the IdP for the RP, the IdP **SHALL** generate a different federated identifier for each RP as described in [Sec. 3.3.1.2](3_federation.md#ppi-gen) or set of RPs as described in [Sec. 3.3.1.3](3_federation.md#ppi-shared).

Some identity attributes such as names, physical address, phone numbers, email addresses, and others can be used to identify a subscriber outside of a federation transaction. When PPIs are used alongside these kinds of identifying attributes, it may still be possible for multiple colluding RPs to re-identify a subscriber by correlation across systems. For example, if two independent RPs each see the same subscriber identified with a different PPI, the RPs could still determine that the subscriber is the same person by comparing the name, email address, physical address, or other identifying attributes carried alongside the PPI in the respective assertions. Where PPIs are used alongside identifying attributes, privacy policies **SHALL** be established to prevent correlation of subscriber data consistent with applicable legal and regulatory requirements.

Note that in a proxied federation model (see [Sec. 3.2.3](3_federation.md#proxied)), the upstream IdP may be unable to generate a PPI for the downstream RP, since the proxy could blind the IdP from knowing which RP is being accessed by the subscriber. In such situations, the PPI is generally established between the IdP and the federation proxy. The proxy, acting as an IdP, can provide a PPI to the downstream RP. Depending on the protocol, the federation proxy may need to map the PPI back to the associated identifiers from upstream IdPs in order to allow the identity protocol to function. In such cases, the proxy will be able to track and determine which PPIs represent the same subscriber at different RPs. The proxy **SHALL NOT** disclose the mapping between the PPI and any other identifiers to a third party or use the information for any purpose other than those allowed for transmission of subscriber information defined in [Sec. 3.9.1](3_federation.md#transmit-subscriber-info).

#### Pairwise Pseudonymous Identifier Generation {#ppi-gen}

The PPI **SHALL** contain no identifying information about the subscriber (e.g., username, email address, employee number, etc.). The PPI **SHALL** be difficult to guess by a party having access to information about the subscriber, having at least 112 bits of entropy as stated in [[SP800-131A]](references.md#ref-SP800-131A). PPIs can be generated randomly and assigned to subscribers by the IdP or could be derived from other subscriber information if the derivation is done in an irreversible, unguessable manner (e.g., using a keyed hash function with a secret key as discussed in [[SP800-131A]](references.md#ref-SP800-131A)).

Unless the PPI is designated as shared by the trust agreement, the PPI **SHALL** be disclosed to only a single RP.

#### Shared Pairwise Pseudonymous Identifiers {#ppi-shared}

The same shared PPI **SHALL** be used for a specific set of RPs if all the following criteria are met:

* The trust agreement stipulates a shared PPI for a specific set of RPs;
* The authorized party consents to and is notified of the use of a shared PPI;
* Those RPs have a demonstrable relationship that justifies an operational need for the correlation, such as a shared security domain or shared legal ownership; and
* All RPs in the set of a shared PPI consent to being correlated in such a manner (i.e., one RP cannot request to have another RP's PPI without that other RP's knowledge and consent).

The RPs **SHALL** conduct a privacy risk assessment to consider the privacy risks associated with requesting a shared PPI. See [Sec. 7.2](7_privacy.md#notice) for further privacy considerations.

The IdP **SHALL** ensure that only intended RPs are included in the set; otherwise, a rogue RP could learn of the shared PPI for a set of RPs by fraudulently posing as part of that set.

The sector identifier feature of [[OIDC]](references.md#ref-OIDC) provides a mechanism to calculate a shared PPI for a group of RPs. In this protocol, the identifiers of the RPs are all listed at a URL that can be fetched by the IdP over an authorized protected channel. The shared PPI is calculated by taking into account the sector identifier URL along with other inputs to the algorithm, such that all RPs listed in the sector identifier URL's contents receive the same shared PPI.

## Trust Agreements {#trust-agreement}

All federation transactions **SHALL** be defined by one or more trust agreements between the applicable parties.

The trust agreement **SHALL** establish a trust relationship between the RP and:

- The CSP responsible for provisioning and managing the subscriber account,
- The IdP responsible for providing assertions and attributes, or
- Both the CSP and IdP.

Trust agreements establish the terms for federation transactions between the parties they affect, including things like the allowed xALs and the intended purposes of identity attributes exchanged in the federation transaction. The trust agreement **SHALL** establish usability and equity requirements for the federation transaction. The trust agreement **SHALL** disclose details of the proofing process used at the CSP, including any compensating controls and exception handling processes.

All trust agreements **SHALL** define a specific population of subscriber accounts that the agreement is applicable to. The exact means of defining this population are out of scope of this document. In many cases, the population is defined as the full set of subscriber accounts that the CSP manages and makes available through an IdP. In other cases, the population is a demarcated subset of accounts available through an IdP. It is also possible for an RP to have a distinct trust agreement established with an IdP for a single subscriber account, such as in a subscriber-driven trust agreement.

During the course of a single federation transaction, it is important for the policies and expectations of all parties be unambiguous for all parties involved. Therefore, there **SHOULD** be only one set of trust agreements in effect for a given transaction. This will usually be determined by the unique combination of CSP, IdP, and RP participating in the transaction. However, these agreements could vary in other ways, such as different populations of subscribers being governed by different trust agreements.

The existence of a trust agreement between parties does not preclude the existence of other agreements for each party in the agreement to have with other parties. For example, an IdP can have independent agreements with multiple RPs simultaneously, and an RP can likewise have independent agreements with multiple IdPs simultaneously. The IdP and RP need not disclose the existence or terms of trust agreements to parties outside of or not covered by the agreement in question.

Trust agreements **SHALL** establish terms regarding expected and acceptable IALs and AALs in connection with the federated relationship.

Trust agreements **SHALL** define necessary mechanisms and materials to coordinate redress and issues between the different participants in the federation, as discussed in [Sec. 3.4.3](3_federation.md#redress).

Establishment of a trust agreement is required for all federation transactions, even those in which the roles and applications exist within a single security domain or shared legal ownership. In such cases, the establishment of the trust agreement can be an internal process and does not need to involve a formal agreement. Even in such cases, it is still required for the IdP to document and disclose the trust agreement to the subscriber upon request.

Even though subscribers are not generally a party directly involved in the trust agreement's terms, subscribers are affected by the terms of the trust agreement and the resulting federation transactions. As such, the terms of the trust agreement need to be made available to subscribers in clear and understandable language. The means by which the subscriber can access these terms, and the party responsible for informing the subscriber, varies based on the means of establishment of the trust agreement and the terms of the trust agreement itself. Additionally, the subscriber's user agent is not usually party to the trust agreement, unless it is acting in one of the roles of the federation transaction.

### Bilateral Trust Agreements {#bilateral}

In a bilateral trust agreement, the establishment of the trust agreement occurs directly between the federated parties, and the trust agreement is not managed or facilitated by a separate party. Bilateral trust agreements allow for a point-to-point connection to be established between organizations wishing to provide federated identity access to services. Bilateral connections can take many forms, including large enterprise applications with static contracts and subscriber-driven dynamic connections to previously unknown RPs. In all cases, the CSP, IdP, and RP manage their policies regarding the federated connection directly.

Bilateral trust agreements impose no additional requirements beyond those needed to establish the trust agreement itself.

~~~
\clearpage
~~~
{:latex-literal="true"}

### Multilateral Trust Agreements {#authorities}

In a multilateral trust agreement, the federated parties look to a *federation authority* to assist in establishing the trust agreement between parties. In this model, the federation authority facilitates the inclusion of CSPs, IdPs, and RPs under the trust agreement.

When onboarding a party in any role, the federation authority conducts vetting on that party to verify its compliance with the tenets of the trust agreement. The level of vetting is unique to the use cases and models employed within the federation, and details are outside the scope of this document. This vetting is depicted in [Fig. 2](3_federation.md#fig-2).

[Fig. 2. Federation Authority](3_federation.md#fig-2){:name="fig-2"}
{:latex-ignore="true"}

![Diagram of a federation authority facilitating trust agreement terms for a variety of parties under the federation authority.]({{site.baseurl}}/{{page.collection}}/images/authority.png 'Federation Authority'){:latex-src="authority.pdf" latex-fig="2" latex-place="h"}

The trust agreement **SHALL** enumerate the required practices for vetting all parties, and **SHALL** indicate the party or parties responsible for performing the vetting process.

Vetting of CSPs, IdPs, and RPs **SHALL** establish, as a minimum, that:

* CSPs are performing identity proofing of subscriber accounts in accordance with [[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"}
* CSPs onboard subscriber accounts to IdPs in a secure fashion in adherence to the requirements in [Sec. 4.1](4_generalidp.md#idp-account-provisioning) or [Sec. 5.4](5_subscriberidp.md#scidp-provisioning) as applicable
* Authenticators used for authenticating the subscriber at the IdP or onboarding a subscriber-controlled wallet are used in accordance with [[SP800-63B]](../_sp800-63b/1_introduction.md#introduction){:latex-href="#ref-SP800-63B"}
* Assertions generated by IdPs adhere to the requirements in [Sec. 4.9](4_generalidp.md#assertions) or [Sec. 5.8](5_subscriberidp.md#assertion-contents).
* RPs adhere to requirements for handling subscriber attribute data, such as retention, aggregation, and disclosure to third parties.
* RP and IdP systems use approved profiles of federation protocols.

The federation authority **MAY** provide a programmatic means for parties under the trust agreement to verify membership of other parties under the trust agreement. For example, a federation authority could provide a discovery API that provides the vetted capabilities of an IdP for providing identities to RPs within the system, or it could provide a signed attestation for RPs to present to IdPs during a registration step.

Federation authorities **SHALL** periodically re-evaluate members for compliance, in terms disclosed in the trust agreement.

When information needs to be shared between CSPs, such as during suspicion of fraud on a subscriber account, the federation authority can define the policies that apply for the transfer of this information. While sharing information in this way can be used to mitigate fraud, there are also substantial privacy concerns. The federation authority **SHALL** include all information sharing between parties other than for identity purposes in its privacy risk assessment.

A federation authority **MAY** incorporate other multilateral trust agreements managed by other federation authorities in its trust agreement, creating an interfederation agreement. For example, IdP1 has been vetted under a multilateral agreement with FA1, and RP2 has been vetted under a multilateral agreement with FA2. In order to facilitate connection between IdP1 and RP2, a new federation authority FA3 can provide a multilateral agreement that accepts IdPs from FA1 and RPs from FA2. If IdP1 and RP2 accept the authority of FA3, the federation connection can continue under the auspices of this interfederation agreement.

### Redress Requirements {#redress}

Federation transactions occur between multiple parties that are often controlled by multiple entities, and different stages of the federation transaction can lead to different situations in which a subscriber would need to seek redress from the different parties.

As the recipient of a subscriber's identity attributes, the RP is the subscriber's primary view into the federated system, and in some instances the subscriber may be unaware that an IdP is involved with their use of the RP. Therefore it falls to the RP to provide the subscriber with a clear and accessible method of contacting the RP to request redress. For matters that involve the RP subscriber account (including any attributes stored in the account), RP functionality, bound authenticators, RP allowlists, and other items under the RP's control, the RP **SHALL** provide clear and accessible means of redress to the subscriber. For matters that involve the IdP or CSP, the RP **SHALL** provide the subscriber with a means of initiating the redress process with the IdP or CSP, as appropriate.

For matters involving the use of the subscriber account in federation transactions, including attribute values and derived attribute values made available over federation transactions, IdP functionality, holder-of-key authenticators, IdP allowlists, and other items in the IdP's control, the IdP **SHALL** provide clear and accessible means of redress to the subscriber. For matters that also involve a particular RP, the IdP **SHALL** provide the subscriber with a means of initiating the redress process with the RP. For matters involving the subscriber account that has been made available to the IdP, the IdP **SHALL** provide the subscriber with a means of initiating the redress process with the CSP.

For matters involving the subscriber account, including identity attributes and authenticators in the subscriber account, the CSP **SHALL** provide the subscriber with a clear and accessible means of redress.

See [Sec. 3.6 of [SP800-63]](../_sp800-63/3_DIRM.md#redress){:latex-href="#ref-SP800-63"} for more requirements on providing redress.

## Identifiers and Cryptographic Key Management for CSPs, IdPs, and RPs {#identifiers-keys}

While a trust agreement establishes permission to federate, it does not facilitate the secure connection of parties in the federation.
In order to communicate over a federation protocol, the CSP, IdP, and RP need to be able to identify each other in a secure fashion, with the ability to associate identifiers with cryptographic keys and related security artifacts.
In this way, an RP can ensure that an assertion is coming from the intended IdP, or that an attribute bundle is coming from the intended CSP. Likewise, an IdP can ensure that it is sending an assertion to the intended RP.

The process of an RP establishing cryptographic keys and identifiers for an IdP or CSP is known as _discovery_. The process of the IdP establishing cryptographic keys and identifiers for the RP is known as _registration_. Both the discovery and registration processes can happen prior to any federation transaction happening, or inline as part of the transaction itself. Both the discovery and registration processes can happen directly between parties or be facilitated through use of a third party service. Different federation protocols and processes have different processes for establishing these cryptographic keys and identifiers, but the end result is that each party can properly identify others as necessary within the protocol.

The discovery and registration processes **SHALL** be established in a secure fashion as defined by the trust agreement governing the transaction. Protocols requiring the transfer of cryptographic key information **SHALL** use an authenticated protected channel to exchange cryptographic key information needed to operate the federated relationship, including any shared secrets or public keys. Any symmetric keys used in this relationship **SHALL** be unique to a pair of federation participants.

CSPs, IdPs (including subscriber-controlled wallets), and RPs **MAY** have multiple cryptographic keys and identifiers to serve different purposes within a trust agreement, or to serve different trust agreements. For example, an IdP could use one set of assertion signing keys for all FAL1 and FAL2 transactions, but use a separately managed set of cryptographic keys for FAL3 transactions, stored in a higher security container.

When domain names, URIs, or other structured identifiers are used to identify parties, wildcards **SHALL NOT** be used. For example, if an RP is deployed at "www.example.com", "service.example.com", and "gateway.example.com", then each of these identifiers would have to be registered for the RP. A wildcard of "*.example.com" cannot be used, as it would unintentionally allow access to "user.example.com" and "unknown.example.com" under the same RP identifier.

### Cryptographic Key Rotation

Over time, it can be desirable or necessary to update the cryptographic key associated with a CSP, IdP, or RP. The allowable update process for any cryptographic keys and identifiers **SHALL** be defined by the trust agreement and **SHALL** be executed using an authenticated protected channel, as in the initial cryptographic key establishment.

For example, if the IdP is identified by a URL, the IdP could publish its current public key set at a location underneath that URL. RPs can then fetch the public key from the known location as needed, getting updated public keys as they are made available.

### Cryptographic Key Storage {#key-storage}

CSPs, IdPs (including subscriber-controlled wallets), and RPs **SHALL** store all private and shared keys used for signing, encryption, and any other cryptographic operations in a secure fashion. Key storage is subject to applicable [[FIPS140]](references.md#ref-FIPS140) requirements of the FAL at which the key is being used, including applicable tamper resistance requirements.

Some circumstances, such as reaching FAL3 with a subscriber-controlled wallet, require the cryptographic keys to be stored in a non-exportable manner. To be considered non-exportable, key storage **SHALL** either be a separate piece of hardware or an embedded processor or execution environment, e.g., secure element, trusted execution environment (TEE), or trusted platform module (TPM). These hardware modules or embedded processors are separate from a host processor such as the CPU on a laptop or mobile device. Non-exportable key storage **SHALL** be designed to prohibit the export of the secret keys to the host processor and **SHALL NOT** be capable of being reprogrammed by the host processor to allow the secret keys to be extracted.

### Software Attestations {#attestations}

Software and device attestation can be used to augment the establishment of cryptographic keys and identifiers, especially in dynamic and distributed systems. Attestations in this usage are cryptographically-bound statements that a particular piece of software, device, or runtime system meets a set of agreed-upon parameters. The attestation is presented by the software in the context of establishing its identity, and allows the receiver to verify the request with a higher degree of certainty than they would otherwise.

For example, a specific distribution of subscriber-controlled wallet software can be signed by its distributor, allowing RPs to recognize individual instances of that software. Alternatively, an RP could be issued an attestation from a federation authority, allowing IdPs to recognize the RP as part of the federation.

When attestations are required by the trust agreement or requested as part of the federation protocol, received attestations **SHALL** be validated by the receiver.

See [[RFC7591]](references.md#ref-RFC7591) Sec. 2.3 for more information about _software statements_, which are a means for OAuth and OpenID Connect RPs to communicate a signed set of software attributes during dynamic client registration.

## Authentication and Attribute Disclosure

Once the IdP and RP have entered into a trust agreement and have completed registration, the federation protocol can be used to pass subscriber attributes from the IdP to the RP.

A subscriber's attributes **SHALL** be transmitted between IdP and RP only for federation transactions or support functions such as identification of compromised subscriber accounts as discussed in [Sec. 3.9](3_federation.md#privacy-reqs). A subscriber's attributes **SHALL NOT** be transmitted for any other purposes, even when parties are allowlisted.

A subscriber's attributes **SHALL NOT** be used by the RP for purposes other than those stipulated in the trust agreement. A subscribers attributes **SHALL** be stored and managed in accordance with [Sec. 3.10.3](3_federation.md#store-subscriber-info).

The subscriber **SHALL** be informed of the transmission of attributes to an RP. In the case where the authorized party is the organization, the organization **SHALL** make available to the subscriber the list of approved RPs and the associated sets of attributes sent to those RPs. In the case where the authorized party is the subscriber, the subscriber **SHALL** be prompted prior to release of attributes using a runtime decision at the IdP as described in [Sec. 4.6.1.3](4_generalidp.md#idp-runtime-decision).

## RP Subscriber Accounts {#rp-account}

It is common for an RP to keep a record representing a subscriber local to the RP itself, known as the *RP subscriber account*. The RP subscriber account can contain things like access rights at the RP as well as a cache of identity attributes for the subscriber. An active RP subscriber account is bound to one or more federated identifiers from the RP's trusted IdPs. Successful authentication of one of these federated identifiers through a federation protocol allows the subscriber to access the information and functionality protected by the RP subscriber account.

An RP subscriber account is _provisioned_ when the RP has associated a set of attributes about the subscriber with a data record representing the subscriber account at the RP. The RP subscriber account **SHALL** be bound to at least one federated identifier, and a given federated identifier is bound to only one RP subscriber account at a given RP. The provisioning can happen prior to authentication or as a result of the federated authentication process, depending on the deployment patterns as discussed in [Sec. 4.6.3](4_generalidp.md#provisioning). Prior to being provisioned, the RP subscriber account does not exist and has no associated data record at the RP.

An RP subscriber account is _terminated_ when the RP removes all access to the account at the RP. Termination **SHALL** include removal of all federated identifiers and bound authenticators from the RP subscriber account (to prevent future federation transactions) as well as removal of attributes and information associated with the account in accordance with [Sec. 3.10.3](3_federation.md#store-subscriber-info). An RP **MAY** terminate an RP subscriber account independently from the IdP for a variety of reasons, regardless of the current validity of the subscriber account from which it is derived.

The RP subscriber account can be provisioned at the RP without an authenticated session, but an authenticated session can only be created on a provisioned account. See [Sec. 3.8](3_federation.md#rp-session) for more information.

### Account Linking

A single RP subscriber account **MAY** be associated with more than one federated identifier. This practice is sometimes known as _account linking_. If the RP allows a subscriber to manage multiple accounts in this way, the RP **SHALL** require an authenticated session with the subscriber account for all management and linking functions. This authenticated session **SHOULD** require one existing federated identifier before linking the new federated identifier to the RP subscriber account. An RP **MAY** offer a means of recovery of an RP subscriber account with no current means of access.

When a federated identifier is removed from an RP subscriber account, the RP **SHALL** disallow access to the RP subscriber account from the removed federated identifier.

The RP **SHALL** document its practices and policies that it enacts when an RP subscriber account reaches a state of having zero associated federated identifiers, no means of access, and no means of recovery. In such cases, the RP subscriber account **SHOULD** be terminated and information associated with the account in accordance with [Sec. 3.10.3](3_federation.md#store-subscriber-info).

The RP **SHALL** provide notice to the subscriber when:

- A new federated identifier is added to an existing RP subscriber account
- A federated identifier is removed from an RP subscriber account, but the account is not terminated

For additional considerations on providing notice to a subscriber about account management events, see [Sec. 4.6 of [SP800-63B]](../_sp800-63b/4_events.md#notification){:latex-href="#ref-SP800-63B"}.

The RP **MAY** associate different access rights to the same account depending on which federated account is used to access the RP. The means by which an RP determines authorization and access is out of scope of these guidelines.

### Account Resolution {#account-resolution}

If the RP has access to existing information about a set of subscribers, and this information is not associated with a federated identifier, the RP performs a process known as _account resolution_ to determine which set of subscriber information to associate with a new RP subscriber account.

An RP performing account resolution **SHALL** ensure that the attributes requested from the IdP are sufficient to uniquely resolve the subscriber within the RP's system before linking the federated identifier with the RP subscriber account and granting access. The intended use of each attribute by the RP is detailed in the trust agreement, including whether the attribute is used for account resolution in this manner.

An RP performing account resolution **SHALL** perform a risk assessment to ensure that the resolution process does not associate an RP subscriber account's information with a federated identifier not belonging to the subscriber.

A similar account resolution process is also used when the RP verifies an authenticator used in a holder-of-key assertion for the first time. In this case, the RP **SHALL** ensure that the attributes carried with the authenticator uniquely resolve to the subscriber.

### Alternative Authentication Processes

The RP **MAY** allow a subscriber to access their RP subscriber account using direct authentication processes by allowing the subscriber to add and remove authenticators in the RP subscriber account. The RP **SHALL** follow the requirements in [[SP800-63B]](../_sp800-63b/1_introduction.md#introduction){:latex-href="#ref-SP800-63B"} in managing all alternative authenticators.

Since the RP is using the direct authentication model discussed in [[SP800-63]](../_sp800-63/1_introduction.md#introduction){:latex-href="#ref-SP800-63"}, there is no federation transaction and therefore no FAL assigned.

~~~
\clearpage
~~~
{:latex-literal="true"}

If the RP allows this kind of access, the RP **SHALL** disclose in the trust agreement:

- The process for adding and removing alternative authenticators in the RP subscriber account
- Any restrictions on authenticators the subscriber can use to access the RP
- The AAL required for access to the subscriber account without a federation transaction
- The circumstances under which the RP will require the subscriber to authenticate with their IdP, such as a period of time since last federation transaction

For additional considerations on providing notice to a subscriber about authenticator management events, see [Sec. 4.6 of [SP800-63B]](../_sp800-63b/4_events.md#notification){:latex-href="#ref-SP800-63B"}.

While it is possible for a bound authenticator to be used as an alternative authenticator for direct access to the RP, these uses are distinct from each other and an RP needs to determine that the use of a given authenticator can be used in one or both scenarios.

## Authenticated Sessions at the RP {#rp-session}

The end goal of a federation transaction is creating an authenticated session between the subscriber and the RP, backed by a verified assertion from the IdP. This authenticated session can be used to allow the subscriber access to functions at the RP (i.e., logging in), identifying the subscriber to the RP, or processing attributes about the subscriber carried in the federation transaction.
An authenticated session **SHALL** be created by the RP only when the following conditions are true:

- The RP has processed and verified a valid assertion
- The assertion is from the expected IdP for a transaction
- The IdP that issued the assertion is the IdP identified in the federated identifier of the assertion
- The assertion is associated with an RP subscriber account (which may be ephemeral)
- The RP subscriber account has been provisioned at the RP through the method specified in the trust agreement

If the assertion is a holder-of-key assertion at FAL3, the authenticator indicated in the assertion **SHALL** be verified before the RP subscriber account is associated with an authenticated session, as discussed in [Sec. 3.14](3_federation.md#idp-managed-bound-authn).
If the assertion also requires authentication with a bound authenticator at FAL3, a bound authenticator **SHALL** be verified before the RP subscriber account is associated with an authenticated session, as discussed in [Sec. 3.15](3_federation.md#bound-authn).

The authenticated session **MAY** be ended by the RP at any time.

See [[SP800-63B] Sec. 5](../_sp800-63b/5_session.md#sec7){:latex-href="#ref-SP800-63B"} for more information about session management requirements for both IdPs and RPs. For additional session requirements with general purpose IdPs, see [Sec. 4.7](4_generalidp.md#federation-session).


## Privacy Requirements {#privacy-reqs}

The ultimate goal of a subscriber is to interact with and use the RP. Federation involves the transfer of personal attributes from a third party that is not otherwise involved in a transaction &mdash; the IdP. Federation also potentially gives the IdP broad visibility into subscriber activities and status. Accordingly, there are specific privacy requirements associated with federation which do not exist in direct authentication.

When the RP requests a federation transaction from the IdP, this request and the subsequent processing of the federation transaction reveals to the IdP where the subscriber is logging in. Over time, the IdP could build a profile of subscriber transactions based on this knowledge of which RPs a given subscriber is using. This aggregation could enable new opportunities for subscriber tracking and use of profile information that do not align with subscribers' privacy interests.

If the same subscriber account is asserted to multiple RPs, and those RPs communicate with each other, the colluding RPs could track a subscriber's activity across multiple applications and security domains. The IdP **SHOULD** employ technical measures, such as the use of pairwise pseudonymous identifiers described in [Sec. 3.3.1](3_federation.md#ppi) or privacy-enhancing cryptographic protocols, to provide disassociability and discourage subscriber activity tracking and profiling between RPs.

The following requirements apply specifically to federal agencies acting as an IdP, an RP, or both:

1. The agency **SHALL** consult with their Senior Agency Official for Privacy (SAOP) to conduct an analysis determining whether the requirements of the Privacy Act are triggered by the agency that is acting as an IdP, by the agency that is acting as an RP, or both (see [Sec. 7.4](7_privacy.md#agency-privacy)).

2. The agency **SHALL** publish or identify coverage by a System of Records Notice (SORN) as applicable.

3. The agency **SHALL** consult with their SAOP to conduct an analysis determining whether the requirements of the E-Government Act are triggered by the agency that is acting as an IdP, the agency that is acting as an RP, or both.

4. The agency **SHALL** publish or identify coverage by a Privacy Impact Assessment (PIA) as applicable.

5. The agency **SHALL** conduct a privacy risk assessment regarding the sharing of subscriber identity information between the IdP and RP.

If the RP subscriber account lifecycle process gives the RP access to attributes through a provisioning API as discussed in [Sec. 4.6.3](4_generalidp.md#provisioning), additional privacy measures **SHALL** be implemented to account for the difference in RP subscriber account lifecycle. The IdP **SHALL** minimize the attributes made available to the RP through the provisioning API. The IdP **SHALL** limit the population of subscriber accounts available via the provisioning API to the population of subscribers authorized to use the RP by the trust agreement. To prevent RP retention of identity attributes for accounts that have been terminated at the IdP, the IdP **SHALL** use the provisioning API to de-provision RP subscriber accounts for terminated subscriber accounts.

Trust agreements **SHOULD** require identity attributes be shared only when the subscriber opts in, using a runtime decision as discussed in [Sec. 4.6.1.3](4_generalidp.md#idp-runtime-decision).

### Transmitting Subscriber Information {#transmit-subscriber-info}

The IdP **SHALL** limit transmission of subscriber information to only that which is necessary for functioning of the system.
These functions include the following:

- identity proofing, authentication, or attribute assertions (collectively "identity service"); or
- in the case of a specific subscriber request to transmit the information

The IdP **MAY** additionally transmit the subscriber's information in the following cases, if stipulated and disclosed by the trust agreement:

- fraud mitigation related to the identity service,
- to respond to a security incident related to the identity service, or
- to comply with law or legal process.

If an IdP discloses information on subscriber activities at an RP to any party, or processes the subscriber's attributes for any purpose other than these cases, the IdP **SHALL** implement measures to maintain predictability and manageability commensurate with the privacy risk arising from the additional processing. Measures **MAY** include providing clear notice, obtaining subscriber consent, or enabling selective use or disclosure of attributes. When an IdP uses consent measures for this purpose, the IdP **SHALL NOT** make consent for the additional processing a condition of the identity service.

An RP **MAY** disclose information on subscriber activities to the associated IdP in the following cases, if stipulated and disclosed by the trust agreement:

- fraud mitigation related to the identity service,
- to respond to a security incident related to the identity service, or
- to comply with law or legal process.

See [[NISTIR8062](references.md#ref-NISTIR8062)] for additional information on privacy engineering and risk management.

## Security Controls {#security-controls}

The IdP and RP **SHALL** employ appropriately tailored security controls from the moderate baseline security controls defined in 
[[SP800-53]](references.md#ref-SP800-53) or equivalent federal (e.g., [[FEDRAMP]](references.md#ref-FEDRAMP))
or industry standard that the organization has determined for the information systems, applications, and
online services that these guidelines are used to protect. The IdP and RP **SHALL** ensure that the minimum
assurance-related controls for the appropriate systems, or equivalent, are satisfied.

### Protection from Injection Attacks {#injection-protection}

An _injection attack_ in the context of a federated protocol consists of an attacker attempting to force an RP to accept or process an assertion or assertion reference in order to gain access to the RP or deny a legitimate subscriber access to the RP. The attacker does this by taking an assertion or assertion reference and injecting it into a vulnerable RP. If the attacker is able to do this successfully, the attacker can trick an RP into binding the attacker's session to the federated identifier in the assertion. The attackers assertion could be either stolen from a legitimate subscriber or manufactured to perpetrate the attack.

Protection from injection attacks is recommended at all FALs, and this protection is required at FAL2 and above. In all cases, the RP needs to take reasonable steps to prevent an attacker from presenting an injected assertion or assertion reference based on the nature of the RP software, the capabilities of the federation protocol in use, and the needs of the overall system. Both [[OIDC]](references.md#ref-OIDC) and [[SAML]](references.md#ref-SAML) provide mechanisms for injection protection including nonces sent from the RP during the request, RP authentication for back-channel communications, and methods for the RP to start the federation transaction and track its state throughout the process. Different mechanisms provide different degrees of protection and are applicable in different circumstances.
While the details of specific protections will vary based on the federation protocol and technology in use, common best practices such as the following can be used to limit the attack surface:

- The use of back channel assertion presentation as discussed in [Sec. 4.11.1](4_generalidp.md#back-channel), which prevents an attacker from presenting the assertion directly to the RP.
- The use of an unguessable value to tie the unauthenticated session at the RP with the request to the back channel, which prevents an attacker from injecting an assertion reference from one session to another.
- Requiring the RP to authenticate to the IdP during an assertion request, preventing the attacker from faking a request from the RP to begin a federation process.
- Prohibition of IdP-initiated federation processes, which prevent the RP from accepting unsolicited assertions and assertion references from the IdP. This prohibition does not include processes in which an external party (such as the IdP or a federation authority) signals the RP to start a federation process with the IdP, allowing the RP to begin the federation transaction and securely await a response within that transaction.
- The use of a signed front channel response from the IdP with an RP-provided nonce covered by the signature, which prevents the attacker from injecting an assertion reference from one session to another.
- The use of platform APIs for front-channel communication, as opposed to HTTP redirects.

Injection attacks are particularly dangerous when combined with phishing attacks. When combined, the attacker can either trick the subscriber into generating a valid assertion for the attacker to inject into the attacker's session, or the attacker can trick the subscriber into injecting the attacker's assertion into the subscriber's session at the RP.


### Protecting Subscriber Information {#protecting-information}

Communications between the IdP and the RP **SHALL** be protected in transit using an authenticated protected channel. Communications between the subscriber and either the IdP or the RP (usually through a user agent) **SHALL** be made using an authenticated protected channel.

Note that the IdP may have access to information that may be useful to the RP in enforcing security policies, such as device identity, location, system health checks, and configuration management. If so, it may be a good idea to pass this information along to the RP within the bounds of the subscriber's privacy preferences described in [Sec. 7.2](7_privacy.md#notice).

Additional attributes about the user **MAY** be included outside of the assertion itself by use of authorized access to an identity API as discussed in [Sec. 3.11.3](3_federation.md#s-identity-api). Splitting user information in this manner can aid in protecting user privacy and can allow for limited disclosure of identifying attributes on top of the essential information in the authentication assertion itself.

When derived attribute values are available and fulfill the RP's needs, the RP **SHOULD** request derived attribute values rather than full attribute values as described in [Sec. 7.3](7_privacy.md#minimization). The IdP **SHOULD** support derived attribute values to the extent the underlying federation protocol allows.

### Storing Subscriber Information {#store-subscriber-info}

The IdP and RP **SHALL** delete personal identity information in the subscriber account and RP subscriber account (respectively) upon account termination, unless required otherwise by legal action or policy.
Whenever personal identity information is stored in a subscriber account or RP subscriber account, whether the account is active or not, the IdP and RP **SHALL** determine and use appropriate controls to ensure secure storage of the personal identity information.

For example, the RP could record the federated identifier in access and audit logs, which logs are retained even after the account has been terminated. However, all identity attributes and personal information are removed from the RP's own storage.

When the RP uses an ephemeral provisioning mechanism as described in [Sec. 4.6.3](4_generalidp.md#provisioning), the RP **SHALL** remove all subscriber attributes at the termination of the session, unless required by legal action or policy.

## Identity Attributes

Identity attributes representing the subscriber are sent to the RP during a federation transaction. These attributes take on multiple aspects, which can be combined in different ways.

Bundling:
: Attributes **SHALL** be either _unbundled_ (presented directly by the IdP) or _bundled_ into a package that is cryptographically signed by the CSP, as described in [Sec. 3.11.1](3_federation.md#attribute-bundles).

Derivation:
: Attributes **SHALL** be either _attribute values_ (e.g., a date of birth) or _derived attribute values_ (e.g., an indication of age of majority).

Presentation:
: Attributes **SHALL** be either presented in the assertion (and therefore covered by the assertion's signature) or made available as part of a protected identity API.


Trust agreements **SHALL** record the validation practices for all attributes made available under the trust agreement (e.g., whether the attribute is from an authoritative or credible source, self-asserted by the subscriber, assigned by the IdP, etc.).

### Attribute Bundles {#attribute-bundles}

> Note: Attribute bundles are often referred to elsewhere as _credentials_ by other protocols and specifications, but usage of this term would be in conflict with its use within these guidelines for a different concept. Consequently, the term attribute bundle is used within these guidelines instead.

As an alternative to sending attributes directly from the IdP, attributes can be collected into bundles that are signed by the CSP. These attribute bundles can be independently verified by the RP. This pattern is commonly used by a subscriber-controlled wallet. Some examples of technologies used to bundle attributes are Selective Disclosure JSON Web Tokens [[SD-JWT]](references.md#ref-SD-JWT) and the mDoc security object defined in [[ISOIEC18013-5]](references.md#ref-ISOIEC18013).

The presentation of an attribute bundle **SHALL** be protected by the IdP in the same manner as non-bundled attributes. That is to say, attribute bundles presented in an assertion are covered by the signature of the assertion, and attribute bundles made available by an identity API are protected by the limited access controls to that API.

Attribute bundles include one or more attribute values and derived attribute values. Attribute bundles are carried in the assertion from the IdP, the subscriber attributes within the bundle need not be fully disclosed to all RPs on every transaction and instead **MAY** be selectively disclosed to the RP. An attribute bundle using selective disclosure technology can effectively limit which attributes an RP can read from the attribute bundle. The RP can still verify the signature of the attribute bundle as a whole, confirming its source as the CSP, without the IdP having to disclose all of the contents of the attribute bundle to the RP.

The RP **SHALL** validate the signature covering the attribute bundle itself as well as the signature of the assertion as a whole. The RP **SHALL** ensure that the attribute bundle is able to be presented by the IdP that created the assertion containing the attribute bundle, such as by verifying that the public key used to sign the assertion is included in the signature of the attribute bundle.

### Derived Attribute Values

For some use cases, knowing the actual value of an identity attribute is not strictly necessary for the RP to function, but a value derived from the identity attribute is sufficient instead. For example, if the RP needs to know if the subscriber is above the age of majority, the RP could request the subscriber's birth date and calculate the majority age question from this value. However, doing so reveals more specific information to the RP than it truly needed. Instead, if the IdP can calculate whether the subscriber's age meets the definitions for majority at the time of the RP's request and return a simple boolean for this derivation instead of the birth date value itself. The RP can then continue its processing without needing to see the underlying value.

Derived attribute values increase the privacy of a system since they allow a more focused release of information to the RP. While some federation systems allow the RP to dynamically query for an arbitrary derived attribute value at request time, many common use cases can be accommodated by the IdP pre-calculating common derived attribute values and offering them as alternatives to the full attribute value.

### Identity APIs {#s-identity-api}

Attributes about the subscriber, including profile information, **MAY** be provided to the RP through a protected API known as the _identity API_. The RP is granted limited access to the identity API during the federation transaction, in concert with the assertion. For example, in OpenID Connect, the UserInfo Endpoint provides a standardized identity API for fetching attributes about the subscriber. This API is protected by an OAuth 2.0 Access Token, which is issued to the RP along with OpenID Connect's assertion, the ID Token.

By making attributes available at an identity API, the IdP no longer has to use the assertion to convey as much information to the RP. This not only means that sensitive attributes do not have to be carried in the assertion itself, it also makes the assertion smaller and easier to process by the RP. The contents of the assertion can then be limited to essential fields (e.g., unique subject identifiers) and information about the immediate authentication event being asserted.

Identity APIs also make it possible for the RP to help manage when subscriber attributes are transmitted from the IdP. The RP often caches attributes provided by the IdP in an RP subscriber account, discussed in [Sec. 3.10.1](3_federation.md#rp-account), and the RP can record when these attributes were last received from the IdP. The RP can request subscriber attributes only when needed to update the RP subscriber account, instead of receiving them on every federation transaction in the assertion. The IdP can aid this decision by indicating in the assertion the time at which any of the subscriber attributes available to the RP were updated at the IdP. This approach is particularly helpful when a subscriber's attributes are stable over time, allowing the RP to function without fetching them on every request.

All possible use of identity APIs, including which provisioning models are available through the API, **SHALL** be recorded and disclosed as part of the trust agreement. Access to the identity API **SHALL** be time limited by the trust agreement. Access to the identity API **SHOULD** be limited to the duration of the federation transaction plus time necessary for synchronization of attributes, as discussed in [Sec. 4.6.4](4_generalidp.md#attribute-sync). Since the time limitation is separate from the validity time window of the assertion and the lifetime of the authenticated session at the RP, access to an identity API by the RP without an associated valid assertion **SHALL NOT** be sufficient for the establishment of an authenticated session at the RP.

A given identity API deployment is expected to be capable of providing attributes for all subscribers for whom the IdP can create assertions. However, when access to the identity API is granted within the context of a federation transaction, the attributes provided by an identity API **SHALL** be associated with only the single subscriber identified in the associated assertion. If the identity API is hosted by the IdP, the returned attributes **SHALL** include the subject identifier for the subscriber. This allows the RP to positively correlate the assertion's subject to the returned attributes. Note that when access to an identity API is provided as part of pre-provisioning of RP subscriber accounts as discussed in [Sec. 4.6.3](4_generalidp.md#provisioning), the RP is usually granted blanket access to the identity API outside the context of the federation transaction and these requirements do not apply. For pre-provisioning use cases, the privacy considerations **SHALL** be evaluated and recorded as part of the trust agreement. If the identity API is hosted externally, the requirements in [Sec. 3.11.3.1](3_federation#external-identity-api) apply.

#### External Identity APIs {#external-identity-api}

While most identity APIs used in federation protocols are hosted as part of the IdP, it is also possible for the IdP to grant access to identity APIs hosted directly by attribute providers. These services provide attributes about the subscriber in addition to those made available directly from the IdP.

When the IdP grants access to an external attribute provider, the IdP is making an explicit statement that the information returned from the attribute provider is associated with the subscriber identified in the associated assertion. For the purposes of the trust agreement, the IdP is the responsible party for the accuracy and content of the identity API and its association with the represented subscriber account.

The attributes returned by the attribute provider are assumed to be independent of those returned directly from the IdP, and as such **MAY** use different identifiers, formats, or schemas.

For example, an IdP could provide access to a subscriber's medical license information as part of the federation process. Instead of the IdP asserting the license status directly, the IdP provides the RP access to a record for the subscriber at a medical licensure agency by providing a link to an API containing the record representing the subscriber as well as a credential allowing limited access to this API. The RP can then make a strong association between the current subscriber and the license record, even though the license record will likely use a different subject identifier and would otherwise be not correlatable by the RP. The trust agreement would list the medical licensure agency as an additional attribute provider to the IdP. The IdP remains responsible for providing this linked data.

Before accepting attributes from an external identity provider and associating them with the RP subscriber account, the RP **SHALL** verify that the attributes in question are allowed to be provided by the external attribute provider under the auspices of the trust agreement.

## Assertion Protection

Assertions **SHALL** include a set of protections to prevent attackers from manufacturing valid assertions or reusing captured assertions at disparate RPs. The protections required are dependent on the details of the use case being considered, and specific protections are listed here.

### Assertion Identifier {#assertion-id}

Assertions **SHALL** be sufficiently unique to permit unique identification by the target RP. Assertions **MAY** accomplish this by use of an embedded nonce, issuance timestamp, assertion identifier, or a combination of these or other techniques.

### Signed Assertion {#signed-assertion}

Assertions **SHALL** be cryptographically signed by the issuer (IdP). The RP **SHALL** validate the digital signature or MAC of each such assertion based on the issuer's key. This signature **SHALL** cover the entire assertion, including its identifier, issuer, audience, subject, and expiration.

The assertion signature **SHALL** either be a digital signature using asymmetric keys or a MAC using a symmetric key shared between the RP and issuer. Shared symmetric keys used for this purpose by the IdP **SHALL** be independent for each RP to which they send assertions, and are normally established during registration of the RP. Public keys for verifying digital signatures **SHALL** be transferred to the RP in a secure manner, and **MAY** be fetched by the RP in a secure fashion at runtime, such as through an HTTPS URL hosted by the IdP. Approved cryptography **SHALL** be used.

### Encrypted Assertion {#encrypted-assertion}

The contents of the assertion can be encrypted to protect their exposure to untrusted third parties, such as a user agent. This protection is especially relevant when the assertion contains PII of the subscriber&mdash;excluding opaque identifiers such as the subject identifier. Subject identifiers are meaningless outside of their target systems, unlike other possible identifiers such as SSN, email address, or driver's license number. Therefore, subject identifiers are excluded as a qualifier for encrypting the assertion.
A trust agreement **MAY** require encryption of assertion contents in other situations.

When the entire assertion is encrypted, the encryption protects the contents of the assertion from being read by unintended parties, ensuring that only the targeted RP is able to process the assertion.
While most assertion formats support encryption of the entire assertion, some assertion formats allow for only the PII portions of the assertion to be encrypted, providing selective disclosure of sensitive information to the RP without encrypting the entire assertion.

When encrypting assertions, the IdP **SHALL** encrypt the contents of the assertion using either the RP's public key or a shared symmetric key. Shared symmetric keys used for this purpose by the IdP **SHALL** be independent for each RP to which they send assertions, and are normally established during registration of the RP. Public keys for encryption **SHALL** be transferred over an authenticated protected channel and **MAY** be fetched by the IdP at runtime, such as through an HTTPS URL hosted by the RP.

All encryption of assertions **SHALL** use approved cryptography applied to the federation technology in use.
For example, a SAML assertion can be encrypted using XML-Encryption, or an OpenID Connect ID Token can be encrypted using JSON Web Encryption (JWE).
When used with back-channel presentation, an assertion can also be encrypted with a mutually-authenticated TLS connection, so long as there are no intermediaries between the IdP and RP that interrupt the TLS channel.

### Audience Restriction

Assertions **SHALL** use audience restriction techniques to allow an RP to recognize whether or not it is the intended target of an issued assertion. All RPs **SHALL** check that the audience of an assertion contains an identifier for their RP to prevent the injection and replay of an assertion generated for one RP at another RP.

In order to limit the places that an assertion could successfully be replayed by an attacker, IdPs **SHOULD** issue assertions designated for only a single audience. Restriction to a single audience is required at FAL2 and above.

## Bearer Assertions  {#bearer}

A bearer assertion can be presented on its own as proof of the identity of the party presenting it. No other proof beyond validation of the assertion is required. Similarly, a bearer assertion reference can be presented own its own to the RP and used by the RP to fetch an assertion. If an attacker can capture or manufacture a valid assertion or assertion reference representing a subscriber and can successfully present that assertion or reference to the RP, then the attacker could be able to impersonate the subscriber at that RP.

Note that mere possession of a bearer assertion or reference is not always enough to impersonate a subscriber. For example, if an assertion is presented in the back-channel federation model (described in [Sec. 4.11.1](4_generalidp.md#back-channel)), additional controls can be placed on the transaction (such as identification of the RP and assertion injection protections) that help further protect the RP from fraudulent activity.

~~~
\clearpage
~~~
{:latex-literal="true"}

## Holder-of-Key Assertions {#idp-managed-bound-authn}

A holder-of-key assertion as in [Fig. 3](3_federation.md#fig-3) **SHALL** include a unique identifier for an authenticator that can be verified independently by the RP, such as the public key of a certificate controlled by the subscriber. The RP **SHALL** verify that the subscriber possesses the authenticator identified by the assertion.

[Fig. 3. Holder-of-Key Assertions](3_federation.md#fig-9){:name="fig-3"}
{:latex-ignore="true"}

![Diagram illustrating the use of holder-of-key assertions.]({{site.baseurl}}/{{page.collection}}/images/IdP-Managed-Bound-Auth.png 'Holder-of-Key Assertions'){:latex-src="IdP-Managed-Bound-Auth.pdf" latex-fig="3" latex-place="h"}

The authenticator identified in a holder-of-key assertion **MAY** be distinct from the primary authenticator the subscriber uses to authenticate to the IdP. The authenticator identified in a holder-of-key assertion **SHALL** be phishing resistant. When the RP encounters an authenticator in a holder-of-key assertion for the first time, the RP **SHALL** ensure that the authenticator can be uniquely resolved to the RP subscriber account, as discussed in [Sec. 3.7.2](3_federation.md#account-resolution).

A holder-of-key assertion **SHALL NOT** include an unencrypted private or symmetric key to be used as an authenticator.

When the RP uses an ephemeral provisioning mechanism as described in [Sec. 4.6.3](4_generalidp.md#provisioning), the IdP **SHOULD** use a unique pairwise identifier for each authorization request to the RP to prevent the RP from storing or correlating information.

A more complete example is found in [Sec 10.6](10_examples.md#fal3-smart-card), which shows the use of a mutual TLS connection to provide the proof of possession of a certificate on a smart card that is listed by the assertion.

Since the authenticators used in holder-of-key assertions are presented to multiple parties, and these authenticators often contain identity attributes, there are additional privacy considerations to address as discussed in [Sec. 7](7_privacy.md#privacy).

## Bound Authenticators {#bound-authn}

A bound authenticator as shown in [Fig. 4](3_federation.md#fig-4) is an authenticator bound to the RP subscriber account and managed by the RP. The IdP **SHALL** include an indicator in the assertion when the assertion is to be used with a bound authenticator at FAL3. The unique identifier for the authenticator (such as its public key) **SHALL** be stored in the RP subscriber account. The RP needs to have a reliable basis for evaluating the characteristics of the bound authenticator; one such basis is the inclusion of a signed attestation, as discussed in [Sec. 3.2.4 of [SP800-63B]](../_sp800-63b/3_authenticators.md#attestation){:latex-href="#ref-SP800-63B"}.

[Fig. 4. Bound Authenticators](3_federation.md#fig-10){:name="fig-4"}
{:latex-ignore="true"}

![Diagram illustrating the use of bound authenticators managed at the RP.]({{site.baseurl}}/{{page.collection}}/images/RP-Managed-Bound-Auth.png 'Bound Authenticators'){:latex-src="RP-Managed-Bound-Auth.pdf" latex-fig="4" latex-place="h"}

A bound authenticator **SHALL** be unique per subscriber at the RP such that two subscribers cannot present the same authenticator for their separate RP subscriber accounts. All bound authenticators **SHALL** be phishing resistant. Consequently, subscriber-chosen values such as a password cannot be used as bound authenticators.
The RP **SHALL** accept authentication from a bound authenticator only in the context of processing an FAL3 assertion for a federation transaction. While it's possible for the same authenticator to also be used for direct authentication to the RP, such use is not considered a bound authenticator and the RP **SHALL** document these as distinct use cases.

Before an RP can successfully accept an FAL3 assertion, the RP subscriber account **SHALL** include a reference to a bound authenticator that is to be verified during the FAL3 transaction. These authenticators can be provided by either the RP or the subscriber, with slightly different requirements applying to the initial binding of the authenticator to the RP subscriber account in each case.

The RP **SHALL** send a notification to the subscriber via a mechanism that is independent of the transaction binding the new authenticator (e.g., an email to an address previously associated with the subscriber), and **SHOULD** notify the IdP using a shared signaling system (see [Sec. 4.8](4_generalidp.md#shared-signals)), if any of the following events occur:

- A new bound authenticator is added to the RP subscriber account.
- An existing bound authenticator is removed from the RP subscriber account.

For additional considerations on providing notice to a subscriber about authenticator management events, see [Sec. 4.6 of [SP800-63B]](../_sp800-63b/4_events.md#notification){:latex-href="#ref-SP800-63B"}.

### RP-Provided Bound Authenticator Issuance {#rp-managed-rp-provided-bound-authn}

For RP-provided authenticators, the administrator of the RP **SHALL** issue the authenticator to the subscriber directly for use with an FAL3 federation transaction. The administrator of the RP **SHALL** store a unique identifier for the bound authenticator in the RP subscriber account, such as the public key of the authenticator.

The administrator of the RP **SHALL** determine through independent means that the identified subject of the RP subscriber account is the party to which the authenticator is issued.

For example, consider an RP that has a collection of cryptographic authenticators that it has purchased for use with FAL3 authentication. These authenticators are each provisioned to a specific RP subscriber account, but are held in a controlled environment by the administrator of the RP. To issue the authenticator, the RP could use an in-person process in which the administrator of the RP has the subscriber authenticate to an RP-controlled kiosk using an FAL3 federation transaction from the IdP. The administrator then hands the subscriber the bound authenticator indicated by the RP subscriber account and has them authenticate to the kiosk using that. The subscriber is now in possession of a bound authenticator supplied by the RP, which can be used to reach FAL3 for future transactions. Alternatively, the administrator of the RP could send the authenticator to a verified address for the subscriber and have the subscriber verify receipt through an activation process. Since the use of the bound authenticator still requires a valid assertion from the IdP, interception of the authenticator alone is not sufficient for accessing the RP subscriber account.

### Subscriber-Provided Bound Authenticator Binding Ceremony {#rp-managed-subscriber-provided-bound-authn}

The RP **MAY** provide a process for associating subscriber-provided authenticators to the RP subscriber account on a trust-on-first-use basis. This process is known as a _binding ceremony_ and has additional requirements beyond a typical FAL3 federation process. This is similar to the subscriber-provided authenticator binding process discussed in [Sec. 4.1.3 of [SP800-63B]](../_sp800-63b/4_events.md#bind-subscriber-authenticator){:latex-href="#ref-SP800-63B"}.

If no bound authenticators are associated with the RP subscriber account, the RP **SHALL** perform a binding ceremony to establish the connection between the authenticator, the subscriber, and the RP subscriber account as shown in [Fig. 5](3_federation.md#fig-5). The RP **SHALL** first establish an authenticated session using federation with an assertion that meets all the other requirements of FAL3, including an indication that the assertion is intended for use at FAL3 with a bound authenticator. The subscriber **SHALL** immediately be prompted to present and authenticate with the proposed authenticator. Upon successful presentation of the authenticator, the RP **SHALL** store a unique identifier for the authenticator (such as its public key) and associate this with the RP subscriber account associated with the federated identifier. If the subscriber fails to successfully authenticate to the RP using an appropriate authenticator, the binding ceremony fails. The binding ceremony session **SHALL** have a timeout of five minutes or less and **SHALL NOT** be used as an authenticated session for any other purpose as described in [Sec. 3.8](3_federation.md#rp-session). Upon successful completion of the binding ceremony, the RP **SHALL** immediately request a new assertion from the IdP at FAL3, including prompting the subscriber for the newly-bound authenticator.

[Fig. 5. Subscriber-Provided Bound Authenticator Binding Ceremony](3_federation.md#fig-11){:name="fig-5"}
{:latex-ignore="true"}

![Sequence diagram of the steps involved in the binding ceremony used for bound authenticators managed at the RP and provided by the subscriber.]({{site.baseurl}}/{{page.collection}}/images/Binding-Ceremony.png 'Subscriber-Provided Bound Authenticator Binding Ceremony'){:latex-src="Binding-Ceremony.pdf" latex-fig="5" latex-place="p"}

An RP **MAY** allow a subscriber to bind multiple subscriber-provided authenticators at FAL3. If this is the case, and the RP subscriber account has one or more existing bound authenticators, the binding ceremony makes use of the existing ability to reach FAL3. The subscriber **SHALL** first be prompted to authenticate to the RP with an existing bound authenticator to reach FAL3. Upon successful authentication, the RP **SHALL** immediately prompt the subscriber to authenticate to the RP using the newly-bound authenticator.

In addition to an RP determining a bound authenticator is no longer viable, a subscriber could choose to stop using a bound authenticator for a variety of reasons, such as the authenticator being lost, compromised, or no longer usable due to technology and platform changes.
In such cases, an RP **MAY** allow a subscriber to remove a subscriber-provided bound authenticator from their RP subscriber account, thereby removing the ability to use that authenticator for FAL3 sessions. When a bound authenticator is removed, the RP **SHALL** terminate all current FAL3 sessions for the subscriber and **SHALL** require reauthentication at FAL3 of the subscriber from the IdP. The RP **SHALL NOT** prompt the subscriber to authenticate with the authenticator being removed, since the subscriber will often not have access to the authenticator in question during the unbinding process, particularly in cases where the authenticator is lost or compromised.

This option is particularly helpful in situations where the subscriber already has access to an appropriate authenticator that the RP wants to allow them to use for FAL3 transactions.
For example, a subscriber could have a single-factor cryptographic authenticator which uses name-based phishing resistance as described in [Sec. 3.2.5.2 of [SP800-63B]](../_sp800-63b/3_authenticators.md#verifier-name-binding){:latex-href="#ref-SP800-63B"}. With such a device, the IdP and RP would see different keys when the authenticator is used in each location, meaning the bound authenticator cannot be easily verified by the IdP. Furthermore, since the RP did not issue the authenticator, the RP does not know the authenticator's key ahead of time, nor does it know which subscriber account to associate to the key. Instead, the RP can use a binding ceremony as described here to allow the subscriber to use this device as a bound authenticator at FAL3.
A more complete example is found in [Sec 10.7](10_examples.md#fal3-nonpki).

## RP Requirements for Processing Holder-of-Key Assertions and Bound Authenticators

When the RP receives an assertion associated with a bound authenticator, the subscriber proves possession of the bound authenticator directly to the RP. The primary authentication at the IdP and the federated authentication at the RP are processed separately. While the subscriber could use the same authenticator during the primary authentication at the IdP and as the bound authenticator at the RP, there is no assumption that these will be the same.

The following requirements apply to all assertions associated with a bound authenticator:

1. The subscriber **SHALL** prove possession of the bound authenticator to the RP, in addition to presentation of the assertion itself.
2. For a holder-of-key assertion, a reference to a given authenticator found within an assertion **SHALL** be trusted at the same level as all other information within the assertion, as stipulated in the trust agreement.
4. The RP **SHALL** process and validate the assertion in addition to the bound authenticator.
5. Failure to authenticate with the bound authenticator **SHALL** result in an error at the RP.


