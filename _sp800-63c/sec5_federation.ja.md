---
layout: default.ja
title: Federation
navOrder: 5
navTitle: Federation
permalink: /sp800-63c/federation/
anchor: federation
section: 5
---

# Federation {#federation}

*This section is normative.*

In a federation protocol, a three-party relationship is formed between the subscriber, the IdP, and the RP, as shown in [Figure 1](sec5_federation.md#fig-1).

[Figure 1. Federation Overview](sec5_federation.md#fig-1){:name="fig-1"}
{:latex-ignore="true"}

![Overview diagram of federated authentication systems showing parties involved and major steps in the process.]({{site.baseurl}}/{{page.collection}}/media/federation.png 'Federation Overview'){:style="width:628px;height:600px;;min-width: 628px;min-height: 600px;" latex-src="federation.png" latex-fig="1" latex-place="h"}

A federation relationship between an IdP and RP is established in a multi-stage process:

1. First, the IdP and RP agree to enter into a trust agreement. This agreement can be bilateral between the parties, multilateral at the behest of an authority, or proxied through a trusted party. This step represents initial permission for the two systems in question to connect. Parameters of what can be requested and released are established in this step, though the details of which attributes are released to a given RP for a given subscriber can be deferred until a later stage.

2. Next, the IdP and RP perform registration to establish their trust at a protocol level, allowing for information to be securely exchanged between the parties. While the first step entails a policy decision representing a permission to connect, this step entails establishment of credentials and identifiers representing the IdP and RP to allow communication through the federation protocol. This stage can occur before any subscriber tries to log in to the RP or as a response to a subscriber's attempt to use an IdP at an RP.

3. Next, the IdP and RP determine that they want to engage in a federated authentication transaction to authenticate the subscriber. As part of this, they determine which attributes about the subscriber are to be passed from the IdP to the RP during this transaction. The decision made in this step builds on the trust agreement established in the first step and the identities of the RP and IdP established in the second step.

4. Finally, the subscriber authenticates to the IdP and the result of that authentication event is asserted to the RP across the network. The RP processes this assertion from the IdP and establishes an authenticated session with the subscriber.

In this transaction, the IdP acts as the verifier of the subscriber's authenticators, as described in [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}. The authentication event information is carried from the IdP to the RP through the use of an assertion, described in [Sec. 6](sec6_assertions.md#assertions). The IdP can also make statements about identity attributes of the subscriber as part of this assertion or through a secondary identity protocol protected by an authorized credential.

## Trust Agreements {#trust-agreement}

IdPs that provide authentication services and RPs that consume those services are known as members of a federation. From an IdP's perspective, the federation consists of the RPs that it serves. From an RP's perspective, the federation consists of the IdPs that it uses. This section provides an overview of and requirements for common identity federation models currently in use. In each model, relationships are established between members of the federation. These relationships are  established in either a bilateral or multilateral fashion, as described in the following sections.

Trust agreements **SHALL** establish the following parameters:

- The set of attributes the IdP can make available to the RP
- The population of subscriber accounts the IdP can create assertions for
- The set of attributes the RP will request (a subset of the attributes made available)
- The purpose for each attribute requested by the RP
- The authorized party responsible for decisions regarding the release of subscriber attributes
- The means of informing subscribers about attribute release to the RP
- The xALs available from the IdP
- The xALs required by the RP

Trust agreements are able to be established either statically or dynamically. In a static establishment, there is often a legal or contractual agreement binding the parties to a set of expected behaviors, rights, and requirements. The parameters of static trust agreements **SHALL** be available to all parties in the agreement, including the operator of the IdP, the operator of the RP, and affected subscribers.

In dynamic trust establishment, in contrast, the trust agreement is implicitly defined when the RP and IdP first contact each other for the purposes of a subscriber's login. The expression of the parameters of a dynamic trust agreement is driven by the federation protocol in place, and are not usually tied to a contractual agreement between the federating parties. The parameters of a dynamic trust agreement **SHALL** be disclosed to the subscriber by the RP and the IdP during the federation transaction.

The _authorized party_ in a trust agreement is the organization, person, or entity that is responsible for the specific release decisions covered by the trust agreement, including the release of subscriber attributes. For a static trust agreement, the authorized party **MAY** be the organization responsible for the IdP. In this case, consent to release attributes is decided for all subscribers and established by an allowlist as described in [Sec. 5.3.1](sec5_federation.md#idp-allowlist), allowing for the disclosure of attribute information without direct decisions and involvement by the subscriber. A static trust agreement **MAY** stipulate that an individual, such as the subscriber, is to be prompted at runtime for consent to disclose attributes as discussed in [Sec. 5.3.3](sec5_federation.md#idp-runtime-decision). Since dynamic trust agreements are established by subscriber actions, the authorized party in a dynamic trust agreement is always the subscriber. Disclosure of attributes in dynamic trust agreements **SHALL** be subject to a runtime decision from the subscriber and **SHALL NOT** be subject to an allowlist at the IdP.

For example, a static trust agreement is established for an organization (the IdP) connecting to an enterprise service (the RP) to be made available to all subscribers at the organization on an allowlist. The authorized party for this trust agreement is the organization. When a subscriber logs in to the enterprise service, they are not prompted with any runtime decisions regarding the service since the static trust agreement establishes this a priori. In a different scenario, another service is made available to all subscribers at the same organization, but the static trust agreement stipulates that the subscriber is the authorized party. When logging in to the service for the first time, each subscriber is prompted for their consent to release their attributes to the RP. In another scenario, a dynamic trust agreement is established implicitly when a subscriber goes to access an RP that is otherwise unknown by their IdP. The RP informs the subscriber about the uses of all attributes being requested from the IdP, and the IdP prompts the subscriber for consent to release their attributes to the RP.

Establishment of a trust agreement is required for all federation transactions, even those in which the IdP and RP have a shared security domain or shared legal ownership. In such cases, the establishment of the trust agreement is an internal process that can be completed quickly.

During the course of a single federation transaction, it is important for the policies and expectations of the IdP and RP to be unambiguous for all parties involved. Therefore, there **SHOULD** be only one set of trust agreements in effect for a given transaction. This will usually be determined by the unique pair consisting of a single IdP and a single RP. However, these agreements could vary in other ways, such as an IdP and RP having different agreements for different populations of subscribers.

The existence of a trust agreement between two parties does not preclude the existence of other agreements for each party in the agreement to have with other parties. That is to say, an IdP can have (and generally does have) independent agreements with multiple RPs simultaneously, and an RP can likewise have independent agreements with multiple IdPs simultaneously.

### Bilateral Trust Agreements {#bilateral}

In a bilateral trust agreement, each potential pairing of an IdP and RP form a trust relationship with each other. In this model, the IdP and RP each act as their own authority and establish the other party as capable of performing its role within the federation.

The IdP **SHALL** disclose its supported IAL, AAL, and FAL levels to the RP. The IdP **MAY** disclose a subset of its capabilities to a given RP depending on the needs of the application, for example only disclosing to a low-risk RP that accounts are proofed at IAL1 or better.

The RP **SHALL** disclose its list of required attributes to the IdP, including its purpose for use of each requested attribute. The RP **SHALL** communicate its required IAL, AAL, and FAL to the IdP, including whether no claim is required for IAL or AAL.

The IdP **SHALL** transmit only those attributes that were explicitly requested by the RP. RPs **SHALL** include their requested attributes in their privacy risk assessment.

### Multilateral Trust Agreements {#authorities}

In a multilateral trust agreement, the federated parties defer to a *federation authority* to assist in making federation trust decisions and to establish the working relationship between parties. In this model, the federation authority manages the membership of IdPs and RPs in the federation agreement. The federation authority conducts some level of vetting on each party in the federation to verify compliance with predetermined standards that define the trust agreement. The level of vetting is unique to the use cases and models employed within the federation. This vetting is depicted in the left side of [Figure 2](sec5_federation.md#fig-2).

Federation authorities approve IdPs to operate at certain IALs, AALs, and FALs. This information is used by relying parties, as shown in the right side of [Figure 2](sec5_federation.md#fig-2), to determine which identity providers meet their requirements.

Federation authorities **SHALL** establish parameters regarding expected and acceptable IALs, AALs, and FALs in connection with the federated relationships they enable. Federation authorities **SHALL** individually vet each participant in the federation to determine whether they adhere to their expected standards.

[Figure 2. Federation Authority](sec5_federation.md#fig-2){:name="fig-2"}
{:latex-ignore="true"}

![Diagram of a federation authority providing trust decisions for a federation network of IdPs and RPs.]({{site.baseurl}}/{{page.collection}}/media/authority.png 'Federation Authority'){:style="width:789px;height:490px;;min-width:789px;min-height:490px;" latex-src="authority.png" latex-fig="2" latex-place="h"}

Vetting of IdPs and RPs **SHALL** establish, as a minimum, that:

* Assertions generated by IdPs adhere to the requirements in [Sec. 6](sec6_assertions.md#assertions).
* RPs adhere to requirements for handling subscriber attribute data, such as retention, aggregation, and disclosure to third parties.
* RP and IdP systems use approved profiles of federation protocols.

Federation authorities **MAY** assist the technical connection and configuration process between members, such as by publishing configuration data for IdPs or by issuing software statements for RPs.

Most federations managed through authorities have a simple membership model: parties are either in the federation or they are not. More sophisticated federations **MAY** have multiple membership tiers that federated parties can use to tell whether other parties in the federation have been more thoroughly vetted. IdPs **MAY** decide that certain subscriber attributes are only releasable to RPs in higher tiers and RPs **MAY** decide to accept certain information only from IdPs in higher tiers.

### Proxied Federation {#proxied}

In a proxied federation, all communication between the IdP and the RP is passed through an intermediary party in a way that prevents direct communication between the two parties. There are multiple methods to achieve this effect. Common configurations include:

* A third party that acts as a federation proxy (or *broker*)
* A network of nodes that distributes the communications and functions as a proxy between the endpoints

Where proxies are used, they function as an IdP on one side and an RP on the other. Therefore, all normative requirements that apply to IdPs and RPs **SHALL** apply to proxies in their respective roles.

[Figure 3. Federation Proxy](sec5_federation.md#fig-3){:name="fig-3"}
{:latex-ignore="true"}

![Diagram of a federation proxy accepting assertions from an upstream IdP and providing assertions to a downstream RP.]({{site.baseurl}}/{{page.collection}}/media/broker.png 'Federation Proxy'){:style="width:600px;height:150px;;min-width:600px;min-height:150px;" latex-src="broker.png" latex-fig="3" latex-place="h"}

A proxied federation model can provide several benefits. Federation proxies can simplify technical integration between the RP and IdP by providing a common interface for integration. Additionally, to the extent a proxy effectively blinds the RP and IdP from each other, it can provide some business confidentiality for organizations that want to guard their subscriber lists from each other. Proxies can also mitigate some of the privacy risks described in [Sec. 5.5](sec5_federation.md#privacy-reqs) below.

See [Sec. 9.5](sec9_privacy.md#blinding) for further information on blinding techniques, their uses, and limitations.

Federations presented through a proxy **SHALL** be represented by the lowest FAL used during the proxied transaction. For example, if a proxy takes in an assertion from the IdP at FAL2 but presents a downstream assertion to the RP at FAL1, the entire transaction is considered FAL1. Likewise if a federation takes in an assertion at FAL1 but presents a downstream assertion to the RP at FAL3, the entire transaction is still considered FAL1. The proxy **SHALL** communicate this aspect to the RP either at runtime or through pre-configuration as part of the trust agreement.

## Registration

Within federation protocols, protocol-specific information such as cryptographic keys, system identifiers, service endpoint URLs, and required access rights need to be established between the IdPs and RPs, allowing them to communicate securely with each other. Furthermore, subscriber-facing information such as system display names and home pages can be established to facilitate trust in and usability of the system. All of this information is used to digitally and programmatically establish trust between the IdP and RP within the scope of the federation protocol.

These exchanges of information happen in a pairwise fashion for each IdP and RP communicating within a federation transaction, regardless of the trust agreement underlying that transaction. The two phases of this process are commonly known as _discovery_ of the IdP by the RP and _registration_ of the RP at the IdP. These processes can happen in a manual, static fashion, where system administrators or developers enter the information into the target systems, or in an automated, dynamic fashion, where the systems themselves exchange information without direct human involvement.

~~~
\clearpage
~~~
{:latex-literal="true"}

### Manual Registration {#manual-registration}

In the manual registration model, the operators of the IdP and RP manually provision configuration information about parties with which they expect to interoperate, prior to involvement of the subscriber.

[Figure 4. Manual Registration](sec5_federation.md#fig-4){:name="fig-4"}
{:latex-ignore="true"}

![Diagram of the steps involved in a manual registration process between an RP and IdP.]({{site.baseurl}}/{{page.collection}}/media/manual.png 'Manual Registration'){:style="width:630px;height:400px;;min-width: 630px;min-height:400px;" latex-src="manual.png" latex-fig="4" latex-place="h"}

As shown in [Figure 4](sec5_federation.md#fig-4), manual registration involves three steps:

1. The RP's system administrator shares the RP's attributes with the IdP's system administrator, who associates those attributes with the RP.

2. The IdP's system administrator shares the IdP's attributes with the RP's system administrator, who associates those attributes with the IdP.

3. The IdP and RP then communicate using a standard federation protocol.

IdPs and RPs **MAY** act as their own authorities on who to federate with as in [Sec. 5.1.1](sec5_federation.md#bilateral) or **MAY** externalize those authority decisions to an external party as in [Sec. 5.1.2](sec5_federation.md#authorities).

Protocols requiring the transfer of keying information **SHALL** use a secure method during the registration process to exchange keying information needed to operate the federated relationship, including any shared secrets or public keys. Any symmetric keys used in this relationship **SHALL** be unique to a pair of federation participants.

Federation relationships **SHALL** establish parameters regarding expected and acceptable IALs and AALs in connection with the federated relationship.

### Dynamic Registration {#dynamic-registration}

In the dynamic registration model of federation, it is possible for relationships between members of the federation to be negotiated at the time of a transaction. This process allows IdPs and RPs to be connected together without manually establishing a connection between them using manual registration (See [Sec. 5.2.1](sec5_federation.md#manual-registration)). IdPs that support dynamic registration **SHALL** make their configuration information (such as dynamic registration endpoints) available in such a way as to minimize system administrator involvement.

[Figure 5. Dynamic Registration](sec5_federation.md#fig-5){:name="fig-5"}
{:latex-ignore="true"}

![Diagram of the steps in a dynamic registration process between an IdP and an RP.]({{site.baseurl}}/{{page.collection}}/media/dynamic.png 'Dynamic Registration'){:style="width:630px;height:338px;;min-width: 630px;min-height:338px;" latex-src="dynamic.png" latex-fig="5" latex-place="h"}

As shown in [Figure 5](sec5_federation.md#fig-5), dynamic registration involves four steps:

1. Discover. The RP goes to a well-known location at the IdP to find the IdP's metadata.

2. Validate. The RP and IdP determine each other's validity. This can be accomplished through keying information, metadata, software statements, or other means.

3. Register RP attributes. The RP sends its attributes to the IdP, and the IdP associates those attributes with the RP.

4. Federation Protocol. The IdP and RP then communicate using a standard federation protocol.

Protocols requiring the transfer of keying information **SHALL** use a secure method during the registration process to establish such keying information needed to operate the federated relationship, including any shared secrets or public keys. Any symmetric keys used in this relationship **SHALL** be unique to a pair of federation participants.

IdPs **SHOULD** issue pairwise pseudonymous subject identifiers to dynamically registered RPs, as discussed in [Sec. 6.2.5](sec6_assertions.md#ppi).

Where possible, dynamic registration **SHOULD** be augmented by *software statements* anchored in their trust agreement. Software statements are lists of attributes describing the RP software, cryptographically signed by an authority (either the IdP itself, a federation authority as in [Sec. 5.1.2](sec5_federation.md#authorities), or another trusted party). Software statements allow federated parties to cryptographically verify some attributes of an RP being dynamically registered without necessarily having all of the identifying information for that RP ahead of time. This cryptographically verifiable statement allows the connection to be established or elevated between the federating parties without relying solely on self-asserted attributes. (See [[RFC7591]](references.md#ref-RFC7591) Sec. 2.3 for more information on one protocol's implementation of software statements.)

## Authentication and Attribute Disclosure

Once the IdP and RP have entered into a trust agreement and have completed registration, the federation protocol can be used to pass subscriber attributes from the IdP to the RP. The decision of whether an authentication can occur or attributes may be passed **SHALL** be determined by the authorized party stipulated by the trust agreement, through use of an allowlist, a blocklist, or a runtime decision.

A subscriber's attributes **SHALL** be transmitted between IdP and RP only for identity federation transactions or support functions such as identification of compromised subscriber accounts as discussed in [Sec. 5.5](sec5_federation.md#privacy-reqs). A subscriber's attributes are not to be transmitted for any other purposes, even when parties are allowlisted.

A subscriber's attributes **SHALL NOT** be used by the RP for purposes other than those stipulated in the trust agreement.

The subscriber **SHALL** be informed of the transmission of attributes to an RP. In the case where the authorized party is the organization, the organization **SHALL** make available to the subscriber the list of approved RPs and the associated sets of attributes sent to those RPs. In the case where the authorized party is the subscriber, the subscriber **SHALL** be prompted prior to release of attributes using a runtime decision at the IdP as described in [Sec. 5.3.3](sec5_federation.md#idp-runtime-decision).

The IdP **SHALL** provide effective mechanisms for redress of subscriber complaints or problems (e.g., subscriber identifies an inaccurate attribute value). See [Sec. 10](sec10_usability.md#usability) on usability considerations for redress.

### IdP Allowlists of RPs {#idp-allowlist}

In a static trust agreement, IdPs **MAY** establish allowlists of RPs authorized to receive authentication and attributes from the IdP without a runtime decision from the subscriber. When placing an RP on its allowlist, the IdP **SHALL** ensure that the RP abides by all applicable provisions and requirements in the SP 800-63 guidelines. The IdP **SHALL** determine which identity attributes are passed to the allowlisted RP upon authentication. IdPs **SHALL** make allowlists available to subscribers as described in [Sec. 9.2](sec9_privacy.md#notice).

IdP allowlists **SHALL** uniquely identify RPs through the means of domain names, cryptographic keys, or other identifiers applicable to the federation protocol in use. Any entities that share an identifier **SHALL** be considered equivalent for the purposes of the allowlist. For example, a wildcard domain identifier of "*.example.com" would match the domains "www.example.com", "service.example.com", and "unknown.example.com" equally. All three of these sites would be treated as the same RP for disclosure decisions using the allowlist. Allowlists **SHOULD** be as specific as possible to avoid unintentional impersonation of an RP.

### IdP Blocklists of RPs

IdPs **MAY** establish blocklists of RPs not authorized to receive authentication assertions or attributes from the IdP, even if requested to do so by the subscriber. If an RP is on an IdP's blocklist, the IdP **SHALL NOT** produce an assertion targeting the RP in question under any circumstances.

IdP blocklists **SHALL** uniquely identify RPs through the means of domain names, cryptographic keys, or other identifiers applicable to the federation protocol in use. Any entities that share an identifier **SHALL** be considered equivalent for the purposes of the blocklist. For example, a wildcard domain identifier of "*.example.com" would match the domains "www.example.com", "service.example.com", and "unknown.example.com" equally. All three of these sites would be treated as the same RP for decisions using the blocklist.

### IdP Runtime Decisions {#idp-runtime-decision}

Every RP that is in a trust agreement with an IdP but not on an allowlist or a blocklist with that IdP **SHALL** be governed by a default policy in which runtime authorization decisions will be made by an authorized party identified by the trust agreement. In most circumstances, and for practical purposes, the authorized party is the subscriber; however, it is possible for an administrator or other party to be prompted on behalf of the subscriber. Note that in a dynamic trust agreement, only a runtime decision can be used to authorize the release of attributes.

In this mode of operation, the authorized party is prompted by the IdP during the federation transaction for their consent to provide an authentication assertion and release specific attributes to the RP on behalf of the subscriber. The IdP **SHALL** provide the authorized party with explicit notice and prompt them for positive confirmation before any attributes about the subscriber are transmitted to the RP. At a minimum, the notice **SHOULD** be provided by the party in the position to provide the most effective notice and obtain confirmation, consistent with [Sec. 9.2](sec9_privacy.md#notice). The IdP **SHALL** disclose which attributes will be released to the RP if the transaction is approved. If the federation protocol in use allows for optional attribute disclosure at runtime, the authorized party **SHALL** be given the option to decide whether to transmit specific attributes to the RP without terminating the federation transaction entirely.

To mitigate the risk of unauthorized exposure of sensitive information (e.g., shoulder surfing), the IdP **SHALL**, by default, mask sensitive information displayed to the authorized party. If the authorized party is the subscriber, the IdP **SHALL** provide mechanisms for the subscriber to temporarily unmask such information in order for the subscriber to view full values before transmission. For more details on masking, see [Sec. 10](sec10_usability.md#usability) on usability considerations.

An IdP **MAY** employ mechanisms to remember and re-transmit the exact attribute bundle to the same RP, remembering the authorized party's decision. This mechanism is associated with the subscriber account as managed by the IdP. If such a mechanism is provided, the IdP **SHALL** allow the authorized party to revoke such remembered access at a future time.

### RP Allowlists of IdPs

RPs **MAY** establish allowlists of IdPs from which the RP will accept authentication and attributes without a runtime decision from the subscriber. When placing an IdP in its allowlist, the RP **SHALL** ensure that the IdP abides by the provisions and requirements in these guidelines.

RP allowlists **SHALL** uniquely identify IdPs through the means of domain names, cryptographic keys, or other identifiers applicable to the federation protocol in use.

### RP Blocklists of IdPs

RPs **MAY** also establish blocklists of IdPs that the RP will not accept authentication or attributes from, even when requested by the subscriber. A blocklisted IdP can be otherwise in a valid trust agreement with the RP, for example if both are under the same federation authority.

RP blocklists **SHALL** uniquely identify IdPs through the means of domain names, cryptographic keys, or other identifiers applicable to the federation protocol in use.

### RP Runtime Decisions {#rp-runtime-decision}

Every IdP that is in a trust agreement with an RP but not on an allowlist or a blocklist with that RP **SHALL** be governed by a default policy in which runtime authorization decisions will be made by the authorized party indicated in the trust agreement. In this mode, the authorized party is prompted by the RP to select or enter which IdP to contact for authentication on behalf of the subscriber. This process can be facilitated through use of a discovery mechanism allowing the subscriber to enter a human-facing identifier such as an email address. This process allows the RP to programmatically select the appropriate IdP for that identifier.

The RP **MAY** employ mechanisms to remember the authorized party's decision to use a given IdP. Since this mechanism is employed prior to authentication at the RP, the manner in which the RP provides this mechanism (e.g., a browser cookie outside the authenticated session) is separate from the RP subscriber account described in [Sec. 5.4](sec5_federation.md#rp-account). If such a mechanism is provided, the RP **SHALL** allow the authorized party to revoke such remembered options at a future time.

## RP Subscriber Accounts {#rp-account}

It is common for an RP to keep a record representing a subscriber local to the RP itself, known as the *RP subscriber account*. The RP subscriber account can contain things like access rights at the RP as well as a cache of identity attributes for the subscriber. An active RP subscriber account is bound to one or more federated identifiers from the RP's trusted IdPs. Successful authentication of one of these federated identifiers through a federation protocol allows the subscriber to access the information and functionality protected by the RP subscriber account.

An RP subscriber account is _provisioned_ when the RP has associated a set of attributes about the subscriber with a data record representing the subscriber account at the RP. The RP subscriber account **SHALL** be bound to at least one federated identifier, and a given federated identifier is bound to only one RP subscriber account at a given RP. The provisioning can happen prior to authentication or as a result of the federated authentication process, depending on the deployment patterns as discussed in [Sec. 5.4.1](sec5_federation.md#provisioning). Prior to being provisioned, the RP subscriber account does not exist and has no associated data record at the RP.

An RP subscriber account is _terminated_ when the RP removes all access to the account at the RP. Termination **SHALL** include unbinding any federated identifiers and bound authenticators as well as removing attributes and information associated with the account except what is required for auditing and security purposes. An RP **MAY** terminate an RP subscriber account independently from the IdP for a variety of reasons, regardless of the current validity of the subscriber account from which it is derived.

An authenticated session **SHALL** be created by the RP only when the RP has processed and verified a valid assertion from the IdP that is the issuer of the federated identifier associated with the RP subscriber account. If the assertion also requires presentation of a bound authenticator at FAL3, the bound authenticator **SHALL** also be presented and processed before the RP subscriber account is associated with an authenticated session, as discussed in [Sec. 6.1.2](sec6_assertions.md#boundauth). Before the federated assertion is processed and after termination of the authenticated session, the RP subscriber account is unauthenticated though it could still be provisioned.

### Provisioning Models {#provisioning}

The lifecycle of the provisioning process for an RP subscriber account varies depending on factors including the trust agreement discussed in [Sec. 5.1](sec5_federation.md#trust-agreement) and the deployment pattern of the IdP and RP. However, in all cases, the RP subscriber account **SHALL** be provisioned at the RP prior to the establishment of an authenticated session at the RP in one of the following ways:

Just-In-Time Provisioning
: An RP subscriber account is created automatically the first time the RP receives an assertion with an unknown federated identifier from an IdP. Any identity attributes learned during the federation process, either within the assertion or through an identity API as discussed in [Sec. 6.3](sec6_assertions.md#s-identity-api), **MAY** be associated with the RP subscriber account. Accounts provisioned in this way are bound to the federated identifier in the assertion used to provision them.
This is the most common form of provisioning in federation systems, as it requires the least coordination between the RP and IdP. However, in such systems, the RP **SHALL** be responsible for managing any cached attributes it might have.

[Figure 6. Just-In-Time Provisioning](sec5_federation.md#fig-6){:name="fig-6"}
{:latex-ignore="true"}

![Diagram of the stages of a just-in-time provisioning of an RP subscriber account based on a subscriber account.]({{site.baseurl}}/{{page.collection}}/media/JIT-provisioning.png 'Just-In-Time Provisioning'){:latex-src="JIT-provisioning.pdf" latex-fig="6" latex-place="h"}

~~~
\clearpage
~~~
{:latex-literal="true"}

Pre-provisioning
: An RP subscriber account is created by the IdP pushing the attributes to the RP or the RP pulling attributes from the IdP. Pre-provisioning of accounts generally occurs in bulk through a provisioning API as discussed in [Sec. 5.4.3](sec5_federation.md#provisioning-api), as the provisioning occurs prior to the represented subscribers authenticating through a federated transaction. Pre-provisioned accounts **SHALL** be bound to a federated identifier at the time of provisioning. Any time a particular federated identifier is seen by the RP, the associated account can be logged in as a result.
This form of provisioning requires infrastructure and planning on the part of the IdP and RP, but these processes can be facilitated by automated protocols. The RP also collects attributes about users who have not interacted with the RP system yet, which can cause privacy issues. Additionally, the IdP and RP must keep the set of provisioned accounts synchronized over time as discussed in [Sec. 5.4.2](sec5_federation.md#attribute-sync).

[Figure 7. Pre-Provisioning](sec5_federation.md#fig-7){:name="fig-7"}
{:latex-ignore="true"}

![Diagram of the stages of a pre-provisioned RP subscriber account based on a subscriber account.]({{site.baseurl}}/{{page.collection}}/media/Pre-provisioning.png 'Pre-Provisioning'){:latex-src="Pre-provisioning.pdf" latex-fig="7" latex-place="h"}

~~~
\clearpage
~~~
{:latex-literal="true"}

Ephemeral
: An RP subscriber account is created when processing the assertion, but then the RP subscriber account is terminated when the authenticated session ends. This process is similar to a just-in-time provisioning, but the RP keeps no long-term record of the account when the session is complete, except what is required for audit and security purposes (such as access logs).
This form of provisioning is useful for RPs that fully externalize access rights to the IdP, allowing the RP to be more simplified with less internal state. However, this pattern is not common because even the simplest RPs tend to have a need to track state within the application or at least keep a record of actions associated with the federated identifier.

[Figure 8. Ephemeral Provisioning](sec5_federation.md#fig-8){:name="fig-8"}
{:latex-ignore="true"}

![Diagram of the stages of an ephemeral RP subscriber account based on a subscriber account.]({{site.baseurl}}/{{page.collection}}/media/Ephemeral-provisioning.png 'Ephemeral Provisioning'){:latex-src="Ephemeral-provisioning.pdf" latex-fig="8" latex-place="h"}

Other
: Other RP subscriber account provisioning models are possible but the details of such models are outside the scope of these guidelines. The details of any alternative provisioning model **SHALL** be included in the privacy risk assessments of the IdP and RP.

All organizations **SHALL** document their provisioning model as part of their trust agreement.

### Attribute Synchronization {#attribute-sync}

In a federated process, the IdP and RP each have their own stores of identity attributes associated with the subscriber account. The IdP has a direct view of the subscriber account, but the RP subscriber account is derived from a subset of attributes from the subscriber account that are presented during the federation transaction. Therefore, it is possible for the IdP's and RP's attribute stores to diverge from with each other over time.

From the RP's perspective, the IdP is the authoritative source for any attributes that the IdP asserts as being associated with the subscriber account at the IdP. However, the RP **MAY** additionally collect, and optionally verify, other attributes to associate with the RP subscriber account. Sometimes, these attributes can even override what's asserted by the IdP. For example, if an IdP asserts a full display name for the subscriber, the RP can allow the subscriber to provide an alternative preferred name for use at the RP.

The IdP **SHOULD** signal downstream RPs when the attributes of a subscriber account available to the RP have been updated. This can be accomplished using shared signaling as described in [Sec. 5.7](sec5_federation.md#shared-signals), through a provisioning API as described in [Sec. 5.4.3](sec5_federation.md#provisioning-api), or by providing a signal in the assertion (e.g., a timestamp indicating when relevant attributes were last updated, allowing the RP to determine that its cache is out of date).

The IdP **SHOULD** signal downstream RPs when a subscriber account is terminated, or when the subscriber account's access to an RP is revoked. This can be accomplished using shared signaling as described in [Sec. 5.7](sec5_federation.md#shared-signals) or through a provisioning API as described in [Sec. 5.4.3](sec5_federation.md#provisioning-api). Upon receiving such a signal, the RP **SHALL** terminate the RP subscriber account and remove all personal information associated with the RP subscriber account, except what is required for audit and security purposes.

### Provisioning APIs {#provisioning-api}

As part of some proactive forms of provisioning, the RP can be given access to subscriber attributes through a general-purpose attribute API known as a _provisioning API_. This type of API allows an IdP to push attributes for a range of subscriber accounts, and sometimes allows an RP to query the attributes of these subscriber accounts directly. Since access to the API is granted outside the context of a federated transaction, access to the provisioning API for a given subscriber does not indicate to the RP that a given subscriber has been authenticated. See [Sec. 6, Assertions](sec6_assertions.md#assertions) for more information on how the federated authentication process is accomplished using assertions.

The attributes in the provisioning API available to a given RP **SHALL** be limited to only those necessary for the RP to perform its functions. As part of establishing the trust agreement, the IdP **SHALL** document when an RP is given access to a provisioning API including at least the following:

- the purpose for the access using the provisioning model;
- the set of attributes made available to the RP;
- whether the API functions as a push to the RP, a pull from the RP, or both; and
- the population of subscribers whose attributes are made available to the RP.

The IdP **SHALL** require authentication from the RP for any pull-based access to a provisioning API. The RP **SHALL** require authentication from the IdP for any push-based access to a provisioning API.

A provisioning API **SHALL NOT** be made available under a dynamic or implicit trust agreement. The IdP **SHALL NOT** make a provisioning API available to any RP outside of an established trust agreement. The IdP **SHALL** provide access to a provisioning API only as part of a federated identity relationship with an RP to facilitate federated transactions with that RP and related functions such as signaling revocation of the subscriber account. The IdP **SHALL** revoke an RP's access to the provisioning API once access is no longer required by the RP for its functioning purposes or when the trust agreement is terminated.

Any provisioning API provided to the RP **SHALL** be under the control and jurisdiction of the IdP. External attribute providers **MAY** be used as information sources by the IdP to provide attributes through this provisioning API, but the IdP is responsible for the content and accuracy of the information provided by the referenced attribute providers.

When a provisioning API is in use, the IdP **SHALL** signal to the RP when a subscriber account has been terminated. When receiving such a signal, the RP **SHALL** terminate the associated RP subscriber account.

### Attribute Collection {#rp-attribute-collection}

The RP **MAY** collect and maintain additional attributes from the subscriber beyond those provided by the IdP. These attributes are governed separately from any federation agreement since they are collected directly by the RP. All attributes associated with an RP subscriber account, regardless of their source, **SHALL** be removed when the RP subscriber account is terminated.

The RP **SHALL** disclose to the subscriber the purpose for collection of any additional attributes. These attributes **SHALL** be used solely for the stated purposes of the RP's functionality and **SHALL NOT** have any secondary use, including communication of said attributes to other parties.

An RP **SHALL** disclose any additional attributes collected, and their use, as part of its System of Records Notice (SORN). The RP **SHALL** provide an effective means of redress for the subscriber to update and remove these additionally-collected attributes from the RP subscriber account. See [Sec. 10](sec10_usability.md#usability) on usability considerations for redress.

### Time-based Removal of RP Subscriber Accounts {#stale-account}

Over time, an RP could accumulate RP subscriber accounts that are no longer accessible from the IdP. This poses a risk to the RP for holding personal information in the RP subscriber accounts, especially when a just-in-time provisioning model is in use and no shared signaling is available from the IdP to signal subscriber account termination as discussed in [Sec. 5.7](sec5_federation.md#shared-signals). In such circumstances, the RP **SHOULD** employ a time-based mechanism to identify RP subscriber accounts for termination that have not been accessed after a period of time, for example, 120 days since last access.

When processing such an inactive account, the RP **SHALL** provide sufficient notice to the subscriber, if possible, about the pending termination of the account and provide the subscriber with an option to re-activate the account prior to its scheduled termination. Upon termination, the RP **SHALL** remove all personal information associated with the RP subscriber account, except what is required for audit and security purposes.

## Privacy Requirements {#privacy-reqs}

The ultimate goal of a subscriber is to interact with and use the RP. Federation involves the transfer of personal attributes from a third party that is not otherwise involved in a transaction &mdash; the IdP. Federation also potentially gives the IdP broad visibility into subscriber activities and status. Accordingly, there are specific privacy requirements associated with federation.

Communication between the RP and the IdP could reveal to the IdP where the subscriber is conducting a transaction. Communication with multiple RPs allows the IdP to build a profile of subscriber transactions that would not have existed without federation. This aggregation could enable new opportunities for subscriber tracking and use of profile information that do not always align with subscribers' privacy interests.

If an IdP discloses information on subscriber activities at an RP to any party, or processes the subscriber's attributes for any purpose other than identity proofing, authentication, or attribute assertions (collectively "identity service"), related fraud mitigation, to comply with law or legal process, or, in the case of a specific user request, to transmit the information, the IdP **SHALL** implement measures to maintain predictability and manageability commensurate with the privacy risk arising from the additional processing. Measures **MAY** include providing clear notice, obtaining subscriber consent, or enabling selective use or disclosure of attributes. When an IdP uses consent measures, the IdP **SHALL NOT** make consent for the additional processing a condition of the identity service.

If the same subscriber account is asserted to multiple RPs, and those RPs communicate with each other, the colluding RPs could track a subscriber's activity across multiple applications and security domains. The IdP **SHOULD** employ technical measures, such as the use of pairwise pseudonymous identifiers described in [Sec. 6.2.5](sec6_assertions.md#ppi) or privacy-enhancing cryptographic protocols, to provide disassociability and discourage subscriber activity tracking and profiling between RPs.

An IdP **MAY** disclose information on subscriber activities to RPs for security purposes, such as communication of suspicious activity or a compromised subscriber account as described in [Sec. 5.7](sec5_federation.md#shared-signals), if stated within the trust agreement. An RP **MAY** disclose information on subscriber activities to IdPs for security purposes, such as communication of suspicious activity or a compromised RP subscriber account, if stated within the trust agreement.

An IdP **SHOULD** signal subscriber account termination to RPs that have been provisioned with federated identifiers bound to that subscriber account using shared signaling as discussed in [Sec. 5.7](sec5_federation.md#shared-signals). RPs that receive such a signal from the IdP **SHALL** terminate the RP subscriber account and remove all personal information associated with the RP subscriber account, except what is required for audit and security purposes.

The following requirements apply specifically to federal agencies:

1. The agency **SHALL** consult with their Senior Agency Official for Privacy (SAOP) to conduct an analysis determining whether the requirements of the Privacy Act are triggered by the agency that is acting as an IdP, by the agency that is acting as an RP, or both (see [Sec. 9.4](sec9_privacy.md#agency-privacy)).

2. The agency **SHALL** publish or identify coverage by a System of Records Notice (SORN) as applicable.

3. The agency **SHALL** consult with their SAOP to conduct an analysis determining whether the requirements of the E-Government Act are triggered by the agency that is acting as an IdP, the agency that is acting as an RP, or both.

4. The agency **SHALL** publish or identify coverage by a Privacy Impact Assessment (PIA) as applicable.

If the RP subscriber account lifecycle process gives the RP access to attributes through a provisioning API as discussed in [Sec. 5.4.3](sec5_federation.md#provisioning-api), additional privacy measures **SHALL** be implemented given the wide nature of information access. Specifically, it is possible for the attributes of a subscriber to be provided to an RP without the subscriber ever interacting with the RP in question. As a consequence, when a provisioning API is used, the IdP **SHALL** minimize the attributes made available to the RP. To prevent the transmission of attributes for users that will never use an RP, the IdP **SHALL** limit the population of subscriber accounts available via the provisioning API to the population of subscribers authorized to use the RP by the trust agreement.

##  Reauthentication and Session Requirements in Federated Environments {#federation-session}

In a federated environment, the RP manages its sessions separately from any sessions at the IdP. The assertion is related to both sessions but its validity period is ultimately independent of them. In order for the IdP to create an assertion for the subscriber, the subscriber needs to establish an authenticated session with the IdP. To create an authenticated session at the RP, the RP needs to process a valid assertion from the IdP.

Due to the distributed nature of a federated system, the subscriber's sessions with the IdP and with the RP terminate independently of each other. The RP **SHALL NOT** assume that the subscriber has an active session at the IdP past the issuance time of the assertion. The IdP **SHALL NOT** assume that termination of the subscriber's session at the IdP will propagate to any sessions that subscriber would have at downstream RPs. The RP and IdP **MAY** communicate session termination requests to other parties in the federation network, if supported by the federation protocol.

At the time of a federated login request, the subscriber **MAY** have a pre-existing session at the IdP which **MAY** be used to generate an assertion to the RP. The IdP **SHALL** communicate any information it has regarding the time of the subscriber's latest authentication event at the IdP, and the RP **MAY** use this information in making authorization and access decisions. Depending on the capabilities of the federation protocol in use, the IdP **SHOULD** allow the RP to request that the subscriber repeat authentication at the IdP as part of a federation request.

An RP requiring authentication through a federation protocol **SHALL** specify the maximum acceptable authentication age to the IdP, either through the federation protocol (if possible) or through the parameters of the trust agreement. The authentication age represents the time since the last authentication event in the subscriber's session at the IdP, and the IdP **SHALL** reauthenticate the subscriber if they have not been authenticated within that time period. The IdP **SHALL** communicate the authentication event time to the RP to allow the RP to decide if the assertion is sufficient for authentication at the RP and to determine the time for the next reauthentication event.

If an RP is granted access to an identity API along with the assertion, the lifetime of the access to the identity API is independent from the lifetime of the assertion itself. Since access to the identity API is often combined with access to additional APIs, it is common for this access to be valid long after the assertion has expired and possibly after the session with the RP has ended, allowing the RP to access APIs on the subscriber's behalf while the subscriber is no longer present. As a consequence, the RP's ability to successfully fetch additional attributes through an identity API **SHALL NOT** be used to establish a session at the RP. Likewise, inability to access an identity API **SHOULD NOT** be used to end the session at the RP.

See [[SP800-63B]](../_sp800-63b/sec7_session.md#sec7){:latex-href="#ref-SP800-63B"}, Sec. 7 for more information about session management requirements for both IdPs and RPs.

## Shared Signaling {#shared-signals}

In some environments, it is useful for the IdP and RP to send information to each other outside of the federation transaction. These signals can communicate important changes in state between parties that would not be otherwise known. The use of any shared signaling **SHALL** be documented in the trust agreement between the IdP and RP. Signaling from the IdP to the RP **SHALL** require a static trust agreement. Signaling from the RP to the IdP **MAY** be used in a static or dynamic trust agreement.

Any use of shared signaling **SHALL** be documented and made available to the authorized party stipulated by the trust agreement. This documentation **SHALL** include the events under which a signal is sent, the information included in such a signal (including any attribute information), and any additional parameters sent with the signal. The use of shared signaling **SHALL** be subject to privacy review under the trust agreement.

The IdP **MAY** send a signal regarding the following changes to the subscriber account:

- The account has been terminated.
- The account is suspected of being compromised.
- Attributes of the account, including identifiers other than the federated identifier (such as email address or certificate CN), have changed.
- The possible range of IAL, AAL, or FAL for the account has changed.

The RP **MAY** send a signal regarding the following changes to the RP subscriber account:

- The account has been terminated.
- The account is suspected of being compromised.
- An RP-managed bound authenticator is added.
- An RP-managed bound authenticator is removed.

Additional signals from both the IdP and RP **MAY** be allowed subject to privacy and security review as part of the trust agreement.
