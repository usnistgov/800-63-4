---
layout: default
title: General-Purpose IdP
navOrder: 5
navTitle: General-Purpose IdP
permalink: /sp800-63c/GenIdP/
anchor: GenIdP
section: 4
---

# General-Purpose IdPs {#GenIdP}

*This section is normative.*

When the IdP is hosted on a service and not on the subscriber's device, or when the IdP represents multiple subscribers, the IdP is known as a _general-purpose IdP_ and the following requirements apply.

Digital wallets that are deployed to networked systems and not to subscriber devices are considered general-purpose IdPs for the purposes of these guidelines.

## IdP Account Provisioning {#idp-account-provisioning}

In order to make subscriber accounts available through an IdP, the subscriber accounts need to be provisioned at the IdP. The means by which the subscriber account is provisioned to the IdP **SHALL** be disclosed in the trust agreement.

Due to the requirement for the IdP to be able to authenticate the subscriber, the IdP is often a service of the CSP, where the IdP has some level of access to the attributes and authenticators in the subscriber account. Such IdPs are generally in the same security domain as the IdAM that houses the subscriber account. In other cases, one or more authenticators in the subscriber account can be verified outside of the security domain, such as authenticators tied to a common PKI.

The IdP augments the subscriber account with federation-specific attributes, such as a subject identifier. The IdP can collect additional attributes, subject to the privacy and storage requirements enumerated by the trust agreement.

Once the subscriber account is provisioned to the IdP, the CSP is no longer an active participant in the federation process.
Consequently, even if the RP fetches attributes through an identity API hosted by the CSP, the identity API is considered a function of the IdP and not the CSP for the purposes of these guidelines.

~~~
\clearpage
~~~
{:latex-literal="true"}

## Federation Transaction

A federation transaction involving a general-purpose IdP establishes the subscriber account at the IdP and culminates in an authenticated session for the subscriber at the RP. This process is shown in [Fig. 6](4_generalidp.md#fig-6).

[Fig. 6. Federation Overview](3_federation.md#fig-6){:name="fig-6"}
{:latex-ignore="true"}

![Overview diagram of federated authentication systems showing parties involved and major steps in the process.]({{site.baseurl}}/{{page.collection}}/images/federation.png 'Federation Overview'){:latex-src="federation.pdf" latex-fig="6" latex-place="h"}

A federation transaction is a multi-stage process:

1. Before federation can occur, the subscriber account is established by the CSP. This account binds the identity attributes collected by the CSP to a set of authenticators used by the subscriber.

1. The subscriber account is provisioned at the IdP. The IdP augments the subscriber account with federation-specific attributes, such as a subject identifier.

1. The IdP and RP perform discovery and registration to establish the cryptographic keys and identifiers needed for information to be securely exchanged between the parties in the federation protocol. While there may have been an existing policy decision representing a permission to connect (through an apriori trust agreement), this step entails a connection and integration at the technical level. This stage can occur before any subscriber tries to access the RP or as a response to a subscriber's attempt to use an IdP at an RP.

1. The IdP and RP begin a federated authentication transaction to authenticate a subscriber to the RP. As part of this, the set of attributes that is to be passed to the RP is selected from a subset of what the RP has requested, what is allowed by the trust agreement, and what is permitted by the authorized party. If necessary, the authorized party is prompted at runtime to approve the release of attributes.

1. The subscriber authenticates to the IdP using an authenticator bound to the subscriber account.

1. The IdP creates an assertion to represent the results of the authentication event. The assertion is based on terms established by the trust agreement, the request from the RP, the capabilities of the IdP, the subscriber account known to the IdP, and the attributes permitted by the authorized party.

1. The assertion is passed to the RP across the network.

1. The RP processes this assertion from the IdP and establishes an authenticated session with the subscriber. Optionally, the RP receives identity attributes from the IdP representing the subscriber account, either in the assertion or through an identity API.

In all transactions, the parties involved enter into a trust agreement, described in [Sec. 3.4](3_federation.md#trust-agreement). This agreement establishes which parties are fulfilling which roles, and its execution represents initial permission for the systems in question to connect. The list of available subscriber identity attributes is established in this step, though the decision of which attributes are released to a given RP for a given transaction is finalized during the federation transaction itself.

In a federated identity transaction, the IdP is the source of identity and authentication attributes for the RP. The normal flow of information for a federation transaction is from the IdP to the RP. Due to the directional nature of this information flow, the IdP is considered to be _upstream_ of the RP and the RP is considered to be _downstream_ of the IdP. It is also possible for additional information to flow back up from the RP, particularly through use of shared signals as discussed in [Sec. 4.8](4_generalidp.md#shared-signals).

~~~
\clearpage
~~~
{:latex-literal="true"}

## Trust Agreements

Trust agreements **SHALL** be established either:

- as the result of an agreement by the federated parties, prior to the federation transaction, or
- as the result of decision or action by the subscriber, during the federation transaction.

### Apriori Trust Agreement Establishment

When the trust agreement is established by the federated parties prior to the federation transaction, the trust agreement **SHALL** establish the following terms, which **MAY** vary per IdP and RP relationship:

- The set of subscriber attributes the CSP makes available to the IdP as part of the subscriber account
- The set of subscriber attributes the IdP can make available to the RP
- The attribute storage policy of the IdP for the subscriber account, including any available means for the subscriber to request deletion
- Any additional attribute sources that the IdP receives applicable subscriber attributes from
- What if any identity APIs are made available by the IdP, either directly or through an external provider, and which subscriber attributes are available at these APIs
- The population of subscriber accounts that the IdP can create assertions for
- Any additional uses of subscriber information, beyond providing the identity service
- The set of subscriber attributes that the RP will request (a subset of the attributes made available)
- The purpose for each attribute requested by the RP
- The attribute storage policy of the RP for the RP subscriber account, including any available means for the subscriber to request deletion
- The use of any shared signaling between the IdP and RP
- The authorized party responsible for decisions regarding the release of subscriber attributes to the RP (e.g., the IdP organization, the subscriber, etc.)
- The means of informing subscribers about attribute release to the RP
- The xALs available from the IdP
- The xALs required by the RP

The terms of the trust agreement **SHALL** be available to the operators of the RP and the IdP upon its establishment. The terms of the trust agreement **SHALL** be made available to subscribers upon request to the IdP or RP.

The IdP and RP **SHALL** each assess their respective redress mechanisms for their efficacy in achieving a resolution of complaints or problems and disclose the results of this assessment as part of the trust agreement. See [Sec. 3.4.3](3_federation.md#redress) for additional requirements and considerations for redress mechanisms.

If FAL3 is allowed within the trust agreement, the trust agreement **SHALL** stipulate the following terms regarding holder-of-key assertions and bound authenticators (see [Sec. 3.14](3_federation.md#idp-managed-bound-authn) and [Sec. 3.15](3_federation.md#bound-authn)):

- The means by which holder-of-key assertions can be verified by the RP (such as a common trusted PKI system)
- The means by which the RP can associate holder-of-key assertions with specific RP subscriber accounts (such as attribute-based account resolution or pre-provisioning)
- Whether bound authenticators are supplied by the RP or by the subscriber
- Documentation of the binding ceremony used for any subscriber-provided bound authenticators

Runtime decisions at the IdP, as described in [Sec. 4.6.1.3](4_generalidp.md#idp-runtime-decision), **MAY** be used to further limit which subscriber attributes are sent between parties in the federated authentication process (e.g., a runtime decision could opt to not disclose an email address even though this attribute was included in the terms of the trust agreement).

The IdP and RP **SHALL** exchange only the minimum data necessary to achieve the function of the system.

The trust agreement **SHALL** be reviewed periodically to ensure it is still fit for purpose, and to avoid unnecessary data exchange and over-collection of subscriber data.

### Subscriber-driven Trust Agreement Establishment

When the trust agreement is established as the result of a subscriber's decision, such as a subscriber starting a federation transaction between an RP and their IdP who have no established agreement, the trust agreement is anchored by the subscriber. Consequently, the following terms **SHALL** be disclosed to the subscriber upon request to the IdP and to the RP during the runtime decision at the IdP as described in [Sec. 4.6.1.3](4_generalidp.md#idp-runtime-decision):

- The set of subscriber attributes the CSP makes available to the IdP
- Any additional attribute sources that the IdP receives applicable subscriber attributes from
- What if any identity APIs are made available by the IdP, either directly or through an external provider, and which subscriber attributes are available at these APIs
- The set of subscriber attributes the IdP can make available to the RP
- The attribute storage policy of the IdP for the subscriber account, including any available means for the subscriber to request deletion
- The use of any shared signaling between the IdP and RP
- The population of subscriber accounts that the IdP can create assertions for
- Any additional uses of subscriber information, beyond providing the identity service
- The xALs available from the IdP

The IdP **SHALL** assess its redress mechanisms for their efficacy in achieving a resolution of complaints or problems and disclose the results of this assessment to the subscriber. See [Sec. 3.4.3](3_federation.md#redress) for additional requirements and considerations for redress mechanisms.

The release of subscriber attributes **SHALL** be managed using a runtime decision at the IdP, as described in [Sec. 4.6.1.3](4_generalidp.md#idp-runtime-decision). The authorized party **SHALL** be the subscriber.

The following terms of the trust agreement **SHALL** be disclosed to the subscriber during the runtime decision:

- The set of subscriber attributes that the RP will request (a subset of the attributes made available by the IdP)
- The purpose for each attribute requested by the RP
- The attribute storage policy of the RP for the RP subscriber account, including any available means for the subscriber to request deletion
- The xALs required by the RP

Note that all information disclosed to the subscriber needs to be conveyed in a manner that is understandable and actionable, as discussed in [Sec. 8](8_usability.md#usability).

## Discovery and Registration

To perform a federation transaction with a general-purpose IdP, the RP **SHALL** associate the assertion signing keys and other relevant configuration information with the IdP's identifier, as stipulated by the trust agreement. If these are retrieved over a network connection, request and retrieval **SHALL** be made over a secure protected channel from a location associated with the IdP's identifier by the trust agreement. In many federation protocols, this is accomplished by the RP fetching the public keys and configuration data from a URL known to be controlled by the IdP or offered on the IdP's behalf. It is also possible for the RP to be configured directly with this information in a static fashion, whereby the RP's administrator enters the IdP information directly into the RP software.

Additionally, the RP **SHALL** register its information either with the IdP or with an authority the IdP trusts, as stipulated by the trust agreement. In many federation protocols, the RP is assigned an identifier during this stage, which the RP will use in subsequent communication with the IdP.

In all of these requirements, the IdP **MAY** use a trusted third party to facilitate its discovery and registration processes, so long as that trusted third party is identified in the trust agreement. For example, a consortium could make use of a hosted service that collects the configuration records of IdPs and RPs directly from participants. Instead of going to the IdP directly for its discovery record, an RP would instead go to this service. The IdP would in turn go to this service to find the identifiers and configuration information for RPs that are needed to connect.

### Manual Registration {#manual-registration}

At all FALs, the cryptographic keys and identifiers of the RP and IdP can be exchanged in a manual process, whereby the administrator of the RP submits the RP's configuration to the IdP (either directly or through a trusted third party) and receives the identifier to use with that IdP. The RP administrator then configures the RP with this identifier and any additional information needed for the federation transaction to continue.

As this is a manual process, the registration happens prior to the federation transaction beginning.

This process **MAY** be facilitated by some level of automated tooling, whereby the manual configuration points the systems in question to a trusted source of information that can be updated over time. If such automation is used, the trust agreement **SHALL** enumerate the allowable terms of the cryptographic key distribution and assignment, including allowable cache lifetimes.

### Dynamic Registration {#dynamic-registration}

At FAL1 and FAL2, the cryptographic keys and identifiers of the RP can be exchanged in a dynamic process, whereby the RP software presents its configuration to the IdP (either directly or through a trusted third party) and receives the identifier to use with that IdP. This process is specific to the federation protocol in use but requires machine-readable configuration data to be made available over the network. All transmission of configuration information **SHALL** be made over a secure protected channel to endpoints associated with the IdP's identifier by the trust agreement.

IdPs **SHOULD** consider the risks of information leakage to multiple RP instances and take appropriate countermeasures, such as issuing PPIs to dynamically registered RPs as discussed in [Sec. 3.3.1](3_federation.md#ppi).

Dynamic registration **SHOULD** be augmented by attestations about the RP software and device, as discussed in [Sec. 3.5.3](3_federation.md#attestations).

[[OIDC-Registration]](references.md#ref-OIDC-registration) defines a protocol for dynamic registration of RPs at an OpenID Connect IdP.

## Subscriber Authentication at the IdP

In a federation context, the IdP acts as the verifier for the authenticator bound to the subscriber account, as described in [[SP800-63B]](../_sp800-63b/1_introduction.md#introduction){:latex-href="#ref-SP800-63B"}.
Verification of the authenticator creates an authentication event which begins the authenticated session at the IdP. This authenticated session serves as the basis of the IdP's claim that the subscriber is present.

The IdP **SHALL** require the subscriber to have an authenticated session before any of the following events:

- Approval of attribute release
- Creation and issuance of an assertion
- Establishment of a subscriber-driven trust agreement.

Additional requirements for session management and reauthentication are discussed in [Sec. 4.7](4_generalidp.md#federation-session).

## Authentication and Attribute Disclosure

The decision of whether a federation transaction proceeds **SHALL** be determined by the authorized party stipulated by the trust agreement. The decision can be calculated in a variety of ways, including:

- an allowlist, which determines the circumstances under which the system can allow the federation transaction to proceed in an automated fashion;
- a blocklist, which determines the circumstances under which the system will not allow the federation transaction to proceed; and
- a runtime decision, which allows the authorized party to decide if the transaction can proceed and under what precise terms. Note that a runtime decision can be stored and applied to future transactions.

The applicability of an allowlist, blocklist, or runtime decision can be influenced by aspects of the federation transaction, including the identity of the IdP and RP, the subscriber attributes requested, the xAL required, and other factors. These decisions can be facilitated by risk management systems, federation authorities, and local system policies.

For a non-normative example of an RP that has been allowlisted at an IdP for a set of subscribers to facilitate single-sign-on for an enterprise application, see [Sec. 10.5](10_examples.md#enterprise-sso).

The IdP **SHALL** provide effective mechanisms for redress of subscriber complaints or problems (e.g., subscriber identifies an inaccurate attribute value). See [Sec. 3.4.3](3_federation.md#redress) for additional requirements and considerations for redress mechanisms.

### IdP-Controlled Decisions

#### IdP Allowlists of RPs {#idp-allowlist}

In an a priori trust agreement, IdPs **MAY** establish allowlists of RPs authorized to receive authentication and attributes from the IdP without a runtime decision from the subscriber. When placing an RP on its allowlist, the IdP **SHALL** confirm that the RP abides the terms of the trust agreement. The IdP **SHALL** determine which identity attributes are passed to the allowlisted RP upon authentication. IdPs **SHALL** make allowlists available to subscribers as described in [Sec. 7.2](7_privacy.md#notice).

IdP allowlists **SHALL** uniquely identify RPs through the means of domain names, cryptographic keys, or other identifiers applicable to the federation protocol in use. Any entities that share an identifier **SHALL** be considered equivalent for the purposes of the allowlist. Allowlists **SHOULD** be as specific as possible to avoid unintentional impersonation of an RP.

IdP allowlist entries for an RP **SHALL** indicate which attributes are included as part of an allowlisted decision. If additional attributes are requested by the RP, the request **SHALL** be either:

- subject to a runtime decision of the authorized party to approve the additional attributes requested,
- redacted to only the attributes in the allowlist entry, or
- denied outright by the IdP.

IdP allowlists **MAY** include other information, such as the xALs under which the allowlist entry is applied. For example, an IdP could use an allowlist entry to bypass a consent screen for an FAL1 transaction but require confirmation of consent from the subscriber during an FAL3 transaction.

#### IdP Blocklists of RPs

IdPs **MAY** establish blocklists of RPs not authorized to receive authentication assertions or attributes from the IdP, even if requested to do so by the subscriber. If an RP is on an IdP's blocklist, the IdP **SHALL NOT** produce an assertion targeting the RP in question under any circumstances.

IdP blocklists **SHALL** uniquely identify RPs through the means of domain names, cryptographic keys, or other identifiers applicable to the federation protocol in use. Any entities that share an identifier **SHALL** be considered equivalent for the purposes of the blocklist. For example, a wildcard domain identifier of "*.example.com" would match the domains "www.example.com", "service.example.com", and "unknown.example.com" equally. All three of these sites would blocked by the same blocklist entry.

#### IdP Runtime Decisions {#idp-runtime-decision}

Every RP that is in a trust agreement with an IdP but not on an allowlist with that IdP **SHALL** be governed by a default policy in which runtime authorization decisions will be made by an authorized party identified by the trust agreement. Since the runtime decision occurs during the federation transaction, the authorized party is generally a person and, in most circumstances, is the subscriber; however, it is possible for another party such as an administrator to be prompted on behalf of the subscriber. Note that in a subscriber-driven trust agreement, a runtime decision with the subscriber is the only allowable means to authorize the release of subscriber attributes.

When processing a runtime decision, the IdP prompts the authorized party interactively during the federation transaction. The authorized party provides consent to release an authentication assertion and specific attributes to the RP. The IdP **SHALL** provide the authorized party with explicit notice and prompt them for positive confirmation before any attributes about the subscriber are transmitted to the RP. At a minimum, the notice **SHOULD** be provided by the party in the position to provide the most effective notice and obtain confirmation, consistent with [Sec. 7.2](7_privacy.md#notice). The IdP **SHALL** disclose which attributes will be released to the RP if the transaction is approved. If the federation protocol in use allows for optional or selective attribute disclosure at runtime, the authorized party **SHALL** be given the option to decide whether to transmit specific attributes to the RP without terminating the federation transaction entirely.

If the authorized party is the subscriber, the IdP **SHALL** provide mechanisms for the subscriber to view the attribute values and derived attribute values to be sent to the RP. To mitigate the risk of unauthorized exposure of sensitive information (e.g., shoulder surfing), the IdP **SHALL**, by default, mask sensitive information displayed to the subscriber. For more details on masking, see [Sec. 8](8_usability.md#usability) on usability considerations.

An IdP **MAY** employ mechanisms to remember and re-transmit the same set of attributes to the same RP, remembering the authorized party's decision. This mechanism is associated with the subscriber account as managed by the IdP. If such a mechanism is provided, the IdP **SHALL** allow the authorized party to revoke such remembered access at a future time.

### RP-Controlled Decisions

#### RP Allowlists of IdPs

RPs **MAY** establish allowlists of IdPs from which the RP will accept authentication and attributes without a runtime decision from the subscriber to use the IdP. In practice, many RPs interface with only a single IdP, and this IdP is allowlisted as the only possible entry for that RP. When placing an IdP in its allowlist, the RP **SHALL** confirm that the IdP abides by the terms of the trust agreement. Note that this confirmation can be facilitated by a federation authority or be undertaken directly by the RP.

RP allowlists **SHALL** uniquely identify IdPs through the means of domain names, cryptographic keys, or other identifiers applicable to the federation protocol in use.

RP allowlist entries **MAY** be applied based on aspects of the subscriber account (such as the xALs required for the transaction). For example, an RP could use a runtime decision for FAL1 transactions but require an allowlisted IdP for FAL3 transactions.

#### RP Blocklists of IdPs

RPs **MAY** also establish blocklists of IdPs that the RP will not accept authentication or attributes from, even when requested by the subscriber. A blocklisted IdP can be otherwise in a valid trust agreement with the RP, for example if both are under the same federation authority.

RP blocklists **SHALL** uniquely identify IdPs through the means of domain names, cryptographic keys, or other identifiers applicable to the federation protocol in use.

#### RP Runtime Decisions {#rp-runtime-decision}

Every IdP that is in a trust agreement with an RP but not on an allowlist with that RP **SHALL** be governed by a default policy in which runtime authorization decisions will be made by the authorized party indicated in the trust agreement. In this mode, the authorized party is prompted by the RP to select or enter which IdP to contact for authentication on behalf of the subscriber. This process can be facilitated through the use of a discovery mechanism allowing the subscriber to enter a human-facing identifier such as an email address. This process allows the RP to programmatically select the appropriate IdP for that identifier. Since the runtime decision occurs during the federation transaction, the authorized party is generally a person and, in most circumstances, is the subscriber.

The RP **MAY** employ mechanisms to remember the authorized party's decision to use a given IdP. Since this mechanism is employed prior to authentication at the RP, the manner in which the RP provides this mechanism (e.g., a browser cookie outside the authenticated session) is separate from the RP subscriber account described in [Sec. 3.10.1](3_federation.md#rp-account). If such a mechanism is provided, the RP **SHALL** allow the authorized party to revoke such remembered options at a future time.

### Provisioning Models for RP subscriber accounts {#provisioning}

The lifecycle of the provisioning process for an RP subscriber account varies depending on factors including the trust agreement discussed in [Sec. 3.4](3_federation.md#trust-agreement) and the deployment pattern of the IdP and RP. However, in all cases, the RP subscriber account **SHALL** be provisioned at the RP prior to the establishment of an authenticated session at the RP in one of the following ways:

Just-In-Time Provisioning
: An RP subscriber account is created automatically the first time the RP receives an assertion with an unknown federated identifier from an IdP. Any identity attributes learned during the federation process, either within the assertion or through an identity API as discussed in [Sec. 3.11.3](3_federation.md#s-identity-api), **MAY** be associated with the RP subscriber account. Accounts provisioned in this way are bound to the federated identifier in the assertion used to provision them.
This is the most common form of provisioning in federation systems, as it requires the least coordination between the RP and IdP. However, in such systems, the RP **SHALL** be responsible for managing any cached attributes it might have. See [Fig. 7](4_generalidp.md#fig-7).

[Fig. 7. Just-In-Time Provisioning](3_federation.md#fig-7){:name="fig-7"}
{:latex-ignore="true"}

![Diagram of the stages of a just-in-time provisioning of an RP subscriber account based on a subscriber account.]({{site.baseurl}}/{{page.collection}}/images/JIT-provisioning.png 'Just-In-Time Provisioning'){:latex-src="JIT-provisioning.pdf" latex-fig="7" latex-place="p"}

Pre-provisioning
: An RP subscriber account is created by the IdP pushing the attributes to the RP or the RP pulling attributes from the IdP. Pre-provisioning of accounts generally occurs in bulk through a provisioning API as discussed in [Sec. 4.6.5](4_generalidp.md#provisioning-api), as the provisioning occurs prior to the represented subscribers authenticating through a federation transaction. Pre-provisioned accounts **SHALL** be bound to a federated identifier at the time of provisioning. Any time a particular federated identifier is seen by the RP, the associated account can be logged in as a result. 
This form of provisioning requires infrastructure and planning on the part of the IdP and RP, but these processes can be facilitated by automated protocols. Additionally, the IdP and RP must keep the set of provisioned accounts synchronized over time as discussed in [Sec. 4.6.4](4_generalidp.md#attribute-sync). See [Fig. 8](4_generalidp.md#fig-8).

  In this model, the RP also receives attributes about subscribers who have not yet interacted with the RP (and who may never do so). This is in contrast to other models, where the RP receives information only about the subset of subscribers that use the RP, and then only after the subscriber uses the RP for the first time. The privacy considerations of the RP having access to this information prior to a federation transaction **SHALL** be accounted for in the trust agreement.

[Fig. 8. Pre-Provisioning](3_federation.md#fig-8){:name="fig-8"}
{:latex-ignore="true"}

![Diagram of the stages of a pre-provisioned RP subscriber account based on a subscriber account.]({{site.baseurl}}/{{page.collection}}/images/Pre-provisioning.png 'Pre-Provisioning'){:latex-src="Pre-provisioning.pdf" latex-fig="8" latex-place="p"}

Ephemeral
: An RP subscriber account is created when processing the assertion, but then the RP subscriber account is terminated when the authenticated session ends. This process is similar to a just-in-time provisioning, but the RP keeps no long-term record of the account when the session is complete, in accordance with [Sec. 3.10.3](3_federation.md#store-subscriber-info).
This form of provisioning is useful for RPs that fully externalize access rights to the IdP, allowing the RP to be more simplified with less internal state. However, this pattern is not common because even the simplest RPs tend to have a need to track state within the application or at least keep a record of actions associated with the federated identifier. See [Fig. 9](4_generalidp.md#fig-9).

[Fig. 9. Ephemeral Provisioning](3_federation.md#fig-9){:name="fig-9"}
{:latex-ignore="true"}

![Diagram of the stages of an ephemeral RP subscriber account based on a subscriber account.]({{site.baseurl}}/{{page.collection}}/images/Ephemeral-provisioning.png 'Ephemeral Provisioning'){:latex-src="Ephemeral-provisioning.pdf" latex-fig="9" latex-place="p"}

~~~
\clearpage
~~~
{:latex-literal="true"}

Other
: Other RP subscriber account provisioning models are possible but the details of such models are outside the scope of these guidelines. The details of any alternative provisioning model **SHALL** be included in the privacy risk assessments of the IdP and RP.

All organizations **SHALL** document their provisioning models as part of their trust agreement.

### Attribute Synchronization {#attribute-sync}

In a federated process, the IdP and RP each have their own stores of identity attributes associated with the subscriber account. The IdP has a direct view of the subscriber account's attributes, but the RP subscriber account is derived from a subset of those attributes that are presented during the federation transaction. Therefore, it is possible for the IdP's and RP's attribute stores to diverge from each other over time.

From the RP's perspective, the IdP is the trusted source for any attributes that the IdP asserts as being associated with the subscriber account at the IdP. The provenance of the IdP's attributes, and their validation process, is stipulated in the trust agreement.

However, the RP **MAY** additionally collect, and optionally verify, other attributes to associate with the RP subscriber account, as discussed in [Sec. 4.6.6](4_generalidp.md#rp-attribute-collection). Sometimes, these attributes can even override what is asserted by the IdP. For example, if an IdP asserts a full display name for the subscriber, the RP can allow the subscriber to provide an alternative preferred name for use at the RP.

The IdP **SHOULD** signal downstream RPs when the attributes of a subscriber account available to the RP have been updated, and the RP **MAY** respond to this signal by updating the attributes in the RP subscriber account. This synchronization can be accomplished using shared signaling as described in [Sec. 4.8](4_generalidp.md#shared-signals), through a provisioning API as described in [Sec. 4.6.5](4_generalidp.md#provisioning-api), or by providing a signal in the assertion (e.g., a timestamp indicating when relevant attributes were last updated) allowing the RP to determine that its cache is out of date. If the RP is granted access to an identity API as in [Sec. 3.11.3](3_federation.md#s-identity-api), the IdP **SHOULD** allow the RP access to the API for sufficient time to perform synchronization operations after the federation transaction has concluded. For example, if the assertion is valid for five minutes, access to the identity API could be valid for 30 minutes to allow the RP to fetch and update attributes out of band.

The IdP **SHOULD** signal downstream RPs when a subscriber account is terminated, or when the subscriber account's access to an RP is revoked. This can be accomplished using shared signaling as described in [Sec. 4.8](4_generalidp.md#shared-signals) or through a provisioning API as described in [Sec. 4.6.5](4_generalidp.md#provisioning-api). Upon receiving such a signal, the RP **SHALL** process the RP subscriber account as stipulated in the trust agreement. If the RP subscriber account is terminated, the RP **SHALL** remove all personal information associated with the RP subscriber account, in accordance with [Sec. 3.10.3](3_federation.md#store-subscriber-info). If the reason for termination is suspicious or fraudulent activity, the IdP **SHALL** include this reason in its signal to the RP to allow the RP to review the account's activity at the RP for suspicious activity, if specified in the trust agreement with that RP.

### Provisioning APIs {#provisioning-api}

As part of some proactive forms of provisioning, the RP can be given access to subscriber attributes through a general-purpose identity API known as a _provisioning API_. This type of API allows an IdP to push attributes for a range of subscriber accounts, and sometimes allows an RP to query the attributes of these subscriber accounts directly. Since access to the API is granted outside the context of a federation transaction, access to the provisioning API for a given subscriber does not indicate to the RP that a given subscriber has been authenticated.

The attributes in the provisioning API available to a given RP **SHALL** be limited to only those necessary for the RP to perform its functions, including any audit and security purposes as discussed in [Sec. 3.9.1](3_federation.md#transmit-subscriber-info). As part of establishing the trust agreement, the IdP **SHALL** document when an RP is given access to a provisioning API including at least the following:

- the purpose for the access using the provisioning model;
- the set of attributes made available to the RP;
- whether the API functions as a push to the RP, a pull from the RP, or both; and
- the population of subscribers whose attributes are made available to the RP.

Access to the provisioning API **SHALL** occur over a mutually authenticated protected channel. The exact means of authentication varies depending on the specifics of the API and whether it is a push model (where the IdP connects to the RP) or a pull model (where the RP connects to the IdP).

A provisioning API **SHALL NOT** be made available under a subscriber-driven trust agreement. The IdP **SHALL NOT** make a provisioning API available to any RP outside of an established trust agreement. The IdP **SHALL** provide access to a provisioning API only as part of a federated identity relationship with an RP to facilitate federation transactions with that RP and related functions such as signaling revocation of the subscriber account. The IdP **SHALL** revoke an RP's access to the provisioning API once access is no longer required by the RP for its functioning purposes or when the trust agreement is terminated.

Any provisioning API provided to the RP **SHALL** be under the control and jurisdiction of the IdP. External attribute providers **MAY** be used as information sources by the IdP to provide attributes through this provisioning API, but the IdP is responsible for the content and accuracy of the information provided by the referenced attribute providers.

When a provisioning API is in use, the IdP **SHALL** signal to the RP when a subscriber account has been terminated. When receiving such a signal, the RP **SHALL** remove the binding of the federated identifier from the account and **SHALL** terminate the account if necessary (e.g., there are no other federated identifiers linked to this account or the trust agreement dictates such an action). The RP **SHALL** remove all personal information sourced from the provisioning API in accordance with [Sec. 3.10.3](3_federation.md#store-subscriber-info).

### Collection of Additional Attributes by the RP {#rp-attribute-collection}

The RP **MAY** collect and maintain additional attributes from the subscriber beyond those provided by the IdP. For example, the RP could collect a preferred display name directly from the subscriber that is not provided by the IdP. The RP could also have a separate agreement with an attribute provider that gives the RP access to an identity API not associated with the IdP. For example, the RP could receive a state license number from the IdP, but use a separate attribute verification API to check if a particular license number is currently valid. The assertion from the IdP binds the license to the subscriber, but the attribute verification API provides additional information beyond what the IdP can share or be authoritative for.

These attributes are governed separately from the trust agreement since they are collected by the RP outside of a federation transaction. All attributes associated with an RP subscriber account, regardless of their source, **SHALL** be removed when the RP subscriber account is terminated, in accordance with [Sec. 3.10.3](3_federation.md#store-subscriber-info).

The RP **SHALL** disclose to the subscriber the purpose for collection of any additional attributes. These attributes **SHALL** be used solely for the stated purposes of the RP's functionality and **SHALL NOT** have any secondary use, including communication of said attributes to other parties.

The RP **SHALL** provide an effective means of redress for the subscriber to update and remove these additionally-collected attributes from the RP subscriber account. See [Sec. 3.4.3](3_federation.md#redress) for additional requirements and considerations for redress mechanisms.

The following requirement applies to federal agencies, regardless of whether they operate their own identity service or use an external CSP as part of their identity service:

- An RP **SHALL** disclose any additional attributes collected, and their use, as part of its System of Records Notice (SORN)

### Time-based Removal of RP Subscriber Accounts {#stale-account}

If an RP is using a just-in-time provisioning mechanism, the RP only learns of the existence of a subscriber account when that account is first used at the RP. If the IdP does not inform the RP of terminated subscriber accounts using shared signaling as described in [Sec 4.8](4_generalidp.md#shared-signals), an RP could accumulate RP subscriber accounts that are no longer accessible from the IdP. This poses a risk to the RP for holding personal information in the RP subscriber accounts. In such circumstances, the RP **MAY** employ a time-based mechanism to identify RP subscriber accounts for termination that have not been accessed after a period of time tailored to the usage patterns of the application. For example, an RP that is usually accessed on a weekly basis could set a timeout of 120 days since last access at the RP to mark the RP subscriber account for termination. An RP that expects longer gaps between access, such as a service used annually, should have a much longer time frame, such as five years.

When processing such an inactive account, the RP **SHALL** provide sufficient notice to the subscriber, about the pending termination of the account and provide the subscriber with an option to re-activate the account prior to its scheduled termination. Upon termination, the RP **SHALL** remove all personal information associated with the RP subscriber account, in accordance with [Sec. 3.10.3](3_federation.md#store-subscriber-info).


##  Reauthentication and Session Requirements in Federated Environments {#federation-session}

In a federated environment, the RP manages its sessions separately from any sessions at the IdP. The assertion is related to both sessions but its validity period is ultimately independent of them.

As shown in [Fig. 10](4_generalidp.md#fig-10), an assertion is created during an authenticated session at the IdP, and processing an assertion creates an authenticated session at the RP. The validity time window of an assertion is used to manage the RP's processing of the assertion but does not indicate the lifetime of the authenticated session at the IdP or the RP. If a request comes to the IdP for a new federation transaction while the subscriber's session is still valid at the IdP, a new and separate assertion would be created with its own validity time window. Similarly, after the RP consumes the assertion, the validity of the RP's session is independent of the validity of the assertion, and in most cases the authenticated session at the RP will far outlive the validity of the assertion. Access granted to an identity API is likewise independent of the validity of the assertion or the lifetime of the authenticated session at the RP. 

[Fig. 10. Session Lifetimes](4_generalidp.md#fig-session){:name="fig-10"}
{:latex-ignore="true"}

![Diagram of the relationship between session lifetimes at the IdP and RP and assertion validity window.]({{site.baseurl}}/{{page.collection}}/images/Session.png 'Session Lifetimes'){:latex-src="Session.pdf" latex-fig="10" latex-place="h"}

The IdP ending the subscriber's session at the IdP will not necessarily cause any sessions that subscriber might have at downstream RPs to end as well. The RP and IdP **MAY** communicate end-session events to each other, if supported by the federation protocol or through shared signaling (see [Sec. 4.8](4_generalidp.md#shared-signals)).

At the time of a federated transaction request, the subscriber could have a pre-existing authenticated session at the IdP which **MAY** be used to generate an assertion to the RP. The IdP **SHALL** communicate to the RP any information the IdP has regarding the time of the subscriber's latest authentication event at the IdP, and the RP **MAY** use this information in making authorization and access decisions. Depending on the capabilities of the federation protocol in use, the IdP **SHOULD** allow the RP to request that the subscriber provide a fresh authentication at the IdP instead of using the existing session at the IdP. For example, suppose the subscriber authenticates at the IdP for one transaction. Then, 30 min later, the subscriber starts a federation transaction at the RP. Depending on xAL requirements, the subscriber's existing session at the IdP can be used to avoid prompting the subscriber for their authenticators. The resulting assertion to the RP will indicate that the last time the subscriber had authenticated to the RP was 30 min in the past. The RP can then use this information to determine whether this is reasonable for the RP's needs, and, if possible within the federation protocol, request the IdP to prompt the subscriber for a fresh authentication event instead.

An RP requiring authentication through a federation protocol **SHALL** specify the maximum acceptable authentication age to the IdP, either through the federation protocol (if possible) or through the terms of the trust agreement. The authentication age represents the time since the last authentication event in the subscriber's session at the IdP, and the IdP **SHALL** reauthenticate the subscriber if they have not been authenticated within that time period. The IdP **SHALL** communicate the authentication event time to the RP to allow the RP to decide if the assertion is sufficient for authentication at the RP and to determine the time for the next reauthentication event.

If an RP is granted access to an identity API at the same time the RP receives an assertion, the lifetime of the access to the identity API is independent from the lifetime of the assertion. As a consequence, the RP's ability to successfully fetch additional attributes through an identity API **SHALL NOT** be used to establish a session at the RP. Likewise, inability to access an identity API **SHOULD NOT** be used to end the session at the RP.

When the RP is granted access to the identity API, the RP is often also granted access to other APIs at the same time, such as granting access to a subscriber's calendar and data storage while also logging in. It is common for this access to be valid long after the assertion has expired and possibly after the session with the RP has ended, allowing the RP to access these non-identity APIs on the subscriber's behalf while the subscriber is no longer present at the RP. Providing access to non-identity APIs is outside the scope of these guidelines.

The RP **MAY** terminate its authenticated session with the subscriber or restrict access to the RP's functions if the assertion, authentication event, or attributes do not meet the RP's requirements. For example, if an RP is configured to allow access to certain high-risk functionality only if the federation transaction was at FAL3, but the incoming assertion only meets the requirements for FAL2, the RP could decide to deny access to the high-risk functionality while allowing access to lower-risk functionality, or the RP could choose to terminate the session entirely.

See [[SP800-63B] Sec. 5](../_sp800-63b/5_session.md#sec7){:latex-href="#ref-SP800-63B"} for more information about session management requirements that apply to both IdPs and RPs.

## Shared Signaling {#shared-signals}

In some environments, it is useful for the IdP and RP to send information to each other outside of the federation transaction. These signals can communicate important changes in state between parties that would not be otherwise known. The use of any shared signaling **SHALL** be documented in the trust agreement between the IdP and RP. Signaling from the IdP to the RP **SHALL** require an apriori trust agreement. Signaling from the RP to the IdP **MAY** be used in both apriori and subscriber-driven trust agreements.

Any use of shared signaling **SHALL** be documented and made available to the authorized party stipulated by the trust agreement. This documentation **SHALL** include the events under which a signal is sent, the information included in such a signal (including any attribute information), and any additional parameters sent with the signal. The use of shared signaling **SHALL** be subject to privacy review under the trust agreement.

The IdP **SHOULD** send a signal regarding the following changes to the subscriber account:

- The account has been terminated.
- The account is suspected of being compromised.
- Attributes of the account, including identifiers other than the federated identifier (such as email address or certificate common name), have changed.
- The possible range of IAL, AAL, or FAL for the account has changed.

If the RP receives a signal that an RP subscriber account is suspected of compromise, the RP **SHOULD** review actions taken by that account at the RP for suspicious activity.

The RP **SHOULD** send a signal regarding the following changes to the RP subscriber account:

- The account has been terminated.
- The account is suspected of being compromised.
- A bound authenticator is added by the RP.
- A bound authenticator is removed by the RP.

If the IdP receives a signal that a subscriber account is suspected of compromise, the IdP **SHALL** review actions taken by that account at the IdP for suspicious activity. If suspicious activity is confirmed at the IdP, the IdP **SHALL** signal any additional RPs the subscriber account was used for during the suspected time frame.

Additional signals from both the IdP and RP **MAY** be allowed subject to privacy and security review as part of the trust agreement.

## Assertion Contents {#assertions}

An assertion is a packaged set of attribute values or derived attribute values about or associated with an authenticated subscriber that is passed from the IdP to the RP in a federated identity system. Assertions contain a variety of information, including: assertion metadata, attribute values and derived attribute values about the subscriber, information about the subscriber's authentication at the IdP, and other information that the RP can leverage (e.g., restrictions and validity time window). While the assertion's primary function is to authenticate the user to an RP, the information conveyed in the assertion can be used by the RP for a number of use cases &mdash; for example, authorization or personalization of a website. These guidelines do not restrict RP use cases nor the type of protocol or data payload used to federate an identity, provided that the chosen solution meets all mandatory requirements contained herein.

Assertions **SHALL** represent a discrete authentication event of the subscriber at the IdP and **SHALL** be processed as a discrete authentication event at the RP.

All assertions **SHALL** include the following attributes:

1. Subject identifier: An identifier for the party to which the assertion applies (i.e., the subscriber).
2. Issuer identifier: An identifier for the issuer of the assertion (i.e., the IdP).
3. Audience identifier: An identifier for the party intended to consume the assertion (i.e., the RP). An assertion can contain more than one audience identifier at FAL1.
4. Issuance time: A timestamp indicating when the IdP issued the assertion.
5. Validity time window: A period of time outside of which the assertion **SHALL NOT** be accepted as valid by the RP for the purposes of authenticating the subscriber and starting an authenticated session at the RP. This is usually communicated by means of an expiration timestamp for the assertion in addition to the issuance timestamp.
6. Assertion identifier: A value uniquely identifying this assertion, used to prevent attackers from replaying prior assertions.
7. Authentication time: A timestamp indicating when the IdP last verified the presence of the subscriber at the IdP through a primary authentication event.
11. Nonce: A cryptographic nonce, if one is provided by the RP.
12. Signature: Digital signature or message authentication code (MAC), including key identifier, covering the entire assertion.

All assertions **SHALL** contain sufficient information to determine the following aspects of the federation transaction:

8. The IAL of the subscriber account being represented in the assertion, or an indication that no IAL is asserted.
9. The AAL used when the subscriber authenticated to the IdP, or an indication that no AAL is asserted.
10. The IdP's intended FAL of the federation process represented by the assertion.

At FAL3, the assertion **SHALL** include one of the following:

- The public key, key identifier, or other identifier for a holder-of-key assertion, or
- An indicator that verification of a bound authenticator is required to process this assertion. 

Assertions **MAY** also include additional items, including the following information:

1. Attribute values and derived attribute values: Information about the subscriber.
1. Attribute bundles: Collections of attributes in a signed bundle from the CSP.
2. Attribute metadata: Additional information about one or more subscriber attributes, such as those described in [[NISTIR8112]](references.md#ref-nistir8112).
3. Authentication event: Additional details about the authentication event, such as the class of authenticator used.

The RP **SHALL** validate the assertion by checking that all the following are true:

 - *Signature validation*: ensuring that the signature of the assertion is valid and corresponds to a key belonging to the IdP sending the assertion.
 - *Issuer verification*: ensuring that the assertion was issued by the IdP the RP expects it to be from.
 - *Time validation*: ensuring that the expiration and issue times are within acceptable limits of the current timestamp.
 - *Audience restriction*: ensuring that this RP is the intended recipient of the assertion.
 - *Nonce*: ensuring that the cryptographic nonce included in the RP's request (if applicable) is included in the presentation.
 - *Transaction terms*: ensuring that the IAL, AAL, and FAL represented by the assertion are allowable under the applicable trust agreement.

An RP **SHALL** treat subject identifiers as not inherently globally unique. Instead, the value of the assertion's subject identifier is usually in a namespace under the assertion issuer's control, as discussed in [Sec. 3.3](3_federation.md#federated-identifier). This allows an RP to talk to multiple IdPs without incorrectly conflating subjects from different IdPs.

Assertions **MAY** include additional attributes about the subscriber. [Section 3.9](3_federation.md#privacy-reqs) contains privacy requirements for presenting attributes in assertions. The RP **MAY** be given limited access to an identity API as discussed in [Sec. 3.11.3](3_federation.md#s-identity-api), either in the same response as the assertion is received or through some other mechanism. The RP can use this API to fetch additional identity attributes for the subscriber that are not included in the assertion itself.

The assertion's validity time window is the time between its issuance and its expiration. This window needs to be large enough to allow the RP to process the assertion and create a local application session for the subscriber, but should not be longer than necessary for such establishment. Long-lived assertions have a greater risk of being stolen or replayed; a short assertion validity time window mitigates this risk. Assertion validity time windows **SHALL NOT** be used to limit the session at the RP. See [Sec. 4.7](4_generalidp.md#federation-session) for more information.


## Assertion Requests

When the federation transaction is initiated by the RP, the RP's request for an assertion **SHALL** contain:

1. An identifier for the RP
2. A cryptographic nonce, to be returned in the assertion

The RP's request **SHOULD** additionally contain:

1. The set of identity attributes requested by the RP and their purpose of use at the RP; this is a subset of what is allowed by the trust agreement
2. The requirements for the authentication event at the IdP

Note that federation transactions are always initiated by the RP at FAL2 or higher.

## Assertion Presentation {#presentation}

 Depending on the specifics of the protocol, the RP and the IdP communicate with each other in two ways, which lends to two different ways in which an assertion can be passed from the IdP to the RP:

 - The *back channel*, through a direct connection between the RP and IdP, not involving the subscriber directly; or
 - The *front channel*, through a third party using redirects involving the subscriber and the subscriber's browser.

There are tradeoffs with each model, but each requires the proper validation of the assertion. Assertions **MAY** also be proxied to facilitate federation between IdPs and RPs using different presentation methods, as discussed in detail in [Sec. 3.2.3](3_federation.md#proxied).

### Back-Channel Presentation {#back-channel}

In the *back-channel* presentation model shown in [Fig. 11](4_generalidp.md#fig-11), the subscriber is given an assertion reference to present to the RP, generally through the front channel. The assertion reference itself contains no information about the subscriber and **SHALL** be resistant to tampering and fabrication by an attacker. The RP presents the assertion reference to the IdP to fetch the assertion. How this is achieved varies form one protocol to the next. In the authorization code flow and some forms of the hybrid flow of [[OIDC]](references.md#ref-OIDC) the assertion (the ID Token) is presented in the back channel in exchange for the assertion reference (the authorization code). In the artifact binding profile of [[SAML-Bindings]](references.md#ref-SAML-bindings), the SAML assertion is presented in the back channel.

~~~
\clearpage
~~~
{:latex-literal="true"}

[Fig. 11. Back-channel Presentation](4_generalidp.md#fig-63cSec7-Figure1){:name="fig-11"}
{:latex-ignore="true"}

![Diagram of the back-channel presentation model for communicating assertions to the RP.]({{site.baseurl}}/{{page.collection}}/images/back-channel.png 'Back-channel Presentation'){:latex-src="back-channel.pdf" latex-fig="11" latex-place="h"}

As shown in [Fig. 11](4_generalidp.md#fig-11), the back-channel presentation model consists of three steps:

1. The IdP sends an assertion reference to the subscriber through the front channel.
2. The subscriber sends the assertion reference to the RP through the front channel.
3. The RP presents the assertion reference and its RP credentials to the IdP through the back channel. The IdP validates the credentials and returns the assertion.

The assertion reference:

 1. **SHALL** be limited to use by a single RP.
 2. **SHALL** be single-use.
 3. **SHALL** be time limited, and **SHOULD** have a validity time window of no more than five minutes.
 4. **SHALL** be presented along with authentication of the RP to the IdP.
 5. **SHALL NOT** be predictable or guessable by an attacker.

In this model, the RP directly requests the assertion from the IdP, minimizing chances of interception and manipulation by a third party (including the subscriber themselves).
More network transactions are required in the back-channel method, but the information is limited to only those parties that need it. Since an RP is expecting to get an assertion only from the IdP directly as a result of its request, the attack surface is reduced. Consequently, it is more difficult to inject assertions directly into the RP and this presentation method is recommended for FAL2 and above.
Since the IdP and RP are already directly connected, the back-channel presentation method facilitates the use of identity APIs, as described in [Sec. 3.11.3](3_federation.md#s-identity-api).

Note that while it is technically possible for an assertion reference (which is single-audience) to result in a multi-audience assertion, this situation is unlikely. For this reason, back-channel presentation is practically limited to use with single-audience assertions.

Conveyance of the assertion reference from the IdP to the subscriber, as well as from the subscriber to the RP, **SHALL** be made over an authenticated protected channel. Conveyance of the assertion reference from the RP to the IdP, as well as the assertion from the IdP to the RP, **SHALL** be made over an authenticated protected channel.

The RP **SHALL** protect itself against injection of manufactured or captured assertion references by the use of cross-site scripting protection, rejecting assertion references outside of the correct stage of a federation transaction, or other accepted techniques discussed in [Sec. 3.10.1](3_federation.md#injection-protection).
When assertion references are presented to the IdP, the IdP **SHALL** verify that the RP presenting the assertion reference is the same RP that made the assertion request resulting in the assertion reference. Examples for this are discussed in [Sec 10.12](10_examples.md#rp-auth) such as the authorization code flow of [[OIDC]](references.md#ref-OIDC) with additional security profiles such as [[FAPI]](references.md#ref-FAPI).

Note that in a federation proxy described in [Sec. 3.2.3](3_federation.md#proxied), the upstream IdP audience restricts the assertion reference and assertion to the proxy, and the proxy restricts any newly-created assertion references or assertions to the downstream RP.

### Front-Channel Presentation {#front-channel}

In the *front-channel* presentation model shown in [Fig. 12](4_generalidp.md#fig-12), the IdP creates an assertion and sends it to the RP by means of a third party, such as the subscriber's user agent. In the implicit flow and some forms of the hybrid flow of [[OIDC]](references.md#ref-OIDC), the assertion (the ID Token) is presented in the front channel.  In the SAML Web SSO profile defined in [[SAML-WebSSO]](references.md#ref-SAML-WebSSO), the SAML assertion is presented in the front channel.

[Fig. 12. Front-channel Presentation](4_generalidp.md#fig-13){:name="fig-12"}
{:latex-ignore="true"}

![Diagram of the front-channel presentation model for communicating assertions to the RP.]({{site.baseurl}}/{{page.collection}}/images/front-channel.png 'Front-channel Presentation'){:latex-src="front-channel.pdf" latex-fig="12" latex-place="h"}

Front-channel presentation methods expose the assertion to parties other than the IdP and RP, which increases the risk for leakage of PII and other information included in the assertion. Additionally, there is an increased attack surface for the assertion to be captured and replayed by an attacker. As a consequence, it is recommended to not use front-channel presentation when other mechanisms are available.

The RP **SHALL** use the assertion identifier ensure that a given assertion is presented at most once during the assertion's validity time window.

The RP **SHALL** protect itself against injection of manufactured or captured assertion by the use of cross-site scripting protection, rejecting assertions outside of the correct stage of a federation transaction, or other accepted techniques discussed in [Sec. 3.10.1](3_federation.md#injection-protection).

Conveyance of the assertion from the IdP to the subscriber, as well as from the subscriber to the RP, **SHALL** be made over an authenticated protected channel.

With general-purpose IdPs, it is common for front-channel communications to be accomplished using HTTP redirects, where the contents of the assertion are made available as part of an HTTP request URL. Due to the nature of the HTTP ecosystem, these request URLs are sometimes available in unexpected places, such as access logs and browser history. These logs and other artifacts tend to live on long past the federation transaction and are available in other contexts, which increases the attack surface for reading the assertion. As a consequence, an IdP that uses HTTP redirects for front channel presentation of assertions that contain PII **SHALL** encrypt the assertion as discussed in [Sec 3.12.3](3_federation.md#encrypted-assertion).
