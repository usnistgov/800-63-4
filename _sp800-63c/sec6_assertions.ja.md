---
layout: default.ja
title: Assertions
navOrder: 6
navTitle: Assertions
permalink: /sp800-63c/assertions/
anchor: assertions
section: 6
---

# Assertions {#assertions}

*This section is normative.*

An assertion used for authentication is a packaged set of attribute values or derived attribute values about or associated with an authenticated subscriber that is passed from the IdP to the RP in a federated identity system. Assertions contain a variety of information, including: assertion metadata, attribute values and derived attribute values about the subscriber, information about the subscriber's authentication at the IdP, and other information that the RP can leverage (e.g., restrictions and validity time window). While the assertion's primary function is to authenticate the user to an RP, the information conveyed in the assertion can be used by the RP for a number of use cases &mdash; for example, authorization or personalization of a website. These guidelines do not restrict RP use cases nor the type of protocol or data payload used to federate an identity, provided the chosen solution meets all mandatory requirements contained herein.

Assertions **SHALL** represent a discrete authentication event of the subscriber at the IdP and **SHALL** be processed as a discrete authentication event at the RP.

All assertions **SHALL** include the following attributes:

1. Subject identifier: An identifier for the party to which the assertion applies (i.e., the subscriber).
2. Issuer identifier: An identifier for the issuer of the assertion (i.e., the IdP).
3. Audience identifier: An identifier for the party intended to consume the assertion (i.e., the RP).
4. Issuance time: A timestamp indicating when the IdP issued the assertion.
5. Validity time window: A period of time outside of which the assertion **SHALL NOT** be accepted as valid by the RP for the purposes of authenticating the subscriber and starting an authenticated session at the RP. This is usually communicated by means of an expiration timestamp for the assertion in addition to the issuance timestamp.
6. Assertion identifier: A value uniquely identifying this assertion, used to prevent attackers from replaying prior assertions.
7. Signature: Digital signature or message authentication code (MAC), including key identifier or public key associated with the IdP, covering the entire assertion.
8. Authentication time: A timestamp indicating when the IdP last verified the presence of the subscriber at the IdP through a primary authentication event (if available).
9. IAL: Indicator of the IAL of the subscriber account being represented in the assertion, or an indication that no IAL is asserted.
10. AAL: Indicator of the AAL used when the subscriber authenticated to the IdP, or an indication that no AAL is asserted.
11. FAL: An indicator of the IdP's intended FAL of the federation process represented by the assertion.

If the assertion is used at FAL3 with a bound authenticator as described in [Sec. 6.1.2](sec6_assertions.md#boundauth), the assertion **SHALL** include the following:

1. Authenticator binding: The public key, key identifier, or other identifier of subscriber-held bound authenticator (for IdP-managed bound authenticators) or indicator that an RP-managed bound authenticator is required for verification of this assertion.

Assertions **MAY** also include additional items, including the following information:

1. Attribute values and derived attribute values: Information about the subscriber.
2. Attribute metadata: Additional information about one or more subscriber attributes, such as those described in NIST Internal Report 8112 [[NISTIR8112]](references.md#ref-nistir8112).

Assertions **SHOULD** specify the AAL when an authentication event is being asserted and IAL when identity proofed attributes (or values derived from those attributes) are being asserted.

All metadata within the assertion **SHALL** be validated by the RP upon receipt:

 - *Issuer verification*: ensuring the assertion was issued by the IdP the RP expects it to be from.
 - *Signature validation*: ensuring the signature of the assertion is valid and corresponds to a key belonging to the IdP sending the assertion.
 - *Time validation*: ensuring the expiration and issue times are within acceptable limits of the current timestamp.
 - *Audience restriction*: ensuring this RP is the intended recipient of the assertion.

An RP **SHALL** treat subject identifiers as not inherently globally unique. Instead, the value of the assertion's subject identifier is usually in a namespace under the assertion issuer's control. This allows an RP to talk to multiple IdPs without incorrectly conflating subjects from different IdPs.

Assertions **MAY** include additional attributes about the subscriber. [Section 6.2.3](sec6_assertions.md#encrypted-assertion) contains privacy requirements for presenting attributes in assertions. The RP **MAY** be given limited access to an identity API as discussed in [Sec. 6.3](#s-identity-api) along with the assertion, which the RP can use to fetch additional identity attributes for the subscriber.

Although details vary based on the exact federation protocol in use, an assertion represents a discrete login event to the RP. The validity time window of an assertion is related to but separate from any session management at the IdP or RP. Specifically, an assertion is created during an authenticated session at the IdP, and processing an assertion creates an authenticated session at the RP. After the IdP creates the assertion, the validity of the IdP's session is independent of the validity of the assertion. If a request comes to the IdP for a repeated authentication while the session is still valid at the IdP, this results in a new and separate assertion being created with its own validity time window. Similarly, after the RP consumes the assertion, the validity of the RP's session is independent of the validity of the assertion. Access granted to an identity API is likewise independent of the validity of the assertion or the lifetime of the authenticated session at the RP. See [Sec. 5.3](sec5_federation.md#federation-session) for more information on session management.

The assertion's validity time window is the time between its issuance and its expiration. This window needs to be large enough to allow the RP to process the assertion and create a local application session for the subscriber, but should not be longer than necessary for such establishment. Long-lived assertions have a greater risk of being stolen or replayed; a short assertion validity time window mitigates this risk. Assertion validity time windows **SHALL NOT** be used to limit the session at the RP. See [Sec. 5.3](sec5_federation.md#federation-session) for more information.

## Assertion Binding  {#assertion-binding}

Assertion binding can be classified based on whether presentation by a claimant of an assertion is sufficient for binding to the party currently in session with the RP as the subscriber, or if the RP requires additional proof through the successful presentation of an authenticator bound to the subscriber.

### Bearer Assertions  {#bearer}

A bearer assertion can be presented by any party as proof of the bearer's identity. Similarly, a bearer assertion reference can be presented by any party to the RP and used by the RP to fetch an assertion; the assertion in this instance is also considered a bearer assertion. If an attacker can capture or manufacture a valid assertion or assertion reference representing a subscriber and can successfully present that assertion or reference to the RP, then the attacker could be able to impersonate the subscriber at that RP.

Note that mere possession of a bearer assertion or reference is not always enough to impersonate a subscriber. For example, if an assertion is presented in the back-channel federation model (described in [Sec. 7.1](sec7_presentation.md#back-channel)), additional controls **MAY** be placed on the transaction (such as identification of the RP and assertion injection protections) that help further protect the RP from fraudulent activity.

### Bound Authenticators {#boundauth}

A bound authenticator is an authenticator presented to the RP by the subscriber alongside the assertion. In proving possession of the bound authenticator to the RP, the subscriber also proves with a certain degree of assurance that they are the rightful subject of the assertion. It is more difficult for an attacker to use a stolen assertion issued to a subscriber since the attacker would need to steal the bound authenticator as well as the assertion and be able to present them together. Furthermore, use of a bound authenticator protects the RP against malicious or compromised IdPs through the use of independent authentication.

A bound authenticator **SHALL** be unique per subscriber at the RP such that two subscribers cannot present the same authenticator for their separate RP subscriber accounts. All bound authenticators **SHALL** be phishing resistant. Consequently, subscriber-chosen values such as a memorized secret cannot be used as bound authenticators.
The RP **SHALL** accept authentication from a bound authenticator only in the context of processing an assertion. Consequently, the subscriber can not use a bound authenticator to log into the RP directly, bypassing the IdP in the process.

A bound authenticator can be managed by either the IdP or the RP under different circumstances, as detailed in the sections below. An FAL3 assertion contains an indication of whether the IdP expects the subscriber to present a specific IdP-managed bound authenticator or an RP-managed bound authenticator at the RP to reach FAL3.

#### IdP-Managed Bound Authenticators

When the bound authenticator is managed by the IdP as in [Fig. 9](sec6_assertions.md#fig-9), a unique identifier for the authenticator (such as its public key) **SHALL** be included in the assertion presented to the RP. The RP **SHALL** prompt the subscriber to prove possession of the identified bound authenticator.

[Figure 9. IdP-Managed Bound Authenticators](sec6_assertions.md#fig-9){:name="fig-9"}
{:latex-ignore="true"}

![Diagram illustrating the use of bound authenticators managed at the IdP.]({{site.baseurl}}/{{page.collection}}/media/IdP-Managed-Bound-Auth.png 'IdP-Managed Bound Authenticators'){:latex-src="IdP-Managed-Bound-Auth.pdf" latex-fig="9" latex-place="h"}

An IdP-managed bound authenticator **MAY** be distinct from the primary authenticator the subscriber uses to authenticate to the IdP. Bound authenticators managed at the IdP **SHALL** be phishing resistant and **SHALL** be independently dereferenceable by the RP based on a mutually-trusted security framework, such as a public-key infrastructure. When processing an IdP-managed bound authenticator for the first time, the RP **SHOULD** verify whether the authenticator being presented is appropriate to be associated with the subscriber account, such as through account resolution from the attributes in the authenticator's presented information.


For example, a subscriber could have a smart card loaded with a certificate, which is a multi-factor cryptographic device. Since the certificate can be presented to both the IdP and the RP, the IdP can include an identifier for the certificate in the FAL3 assertion to the RP. The RP would then prompt the subscriber to present the certificate from their smart card in order to reach FAL3.

"Holder of Key" (HoK) assertions are one example of IdP-managed bound authenticators, since the IdP knows the subscriber's key to be used at the RP and includes the key information in the assertion presented to the RP.

~~~
\clearpage
~~~
{:latex-literal="true"}

#### RP-Managed Bound Authenticators

When the bound authenticator is managed by the RP as in [Fig. 10](sec6_assertions.md#fig-10), the IdP **SHALL** include an indicator in the assertion that the assertion is to be used with a bound authenticator at FAL3. The unique identifier for the authenticator (such as its public key) **SHALL** be stored in the RP subscriber account.

[Figure 10. RP-Managed Bound Authenticators](sec6_assertions.md#fig-10){:name="fig-10"}
{:latex-ignore="true"}

![Diagram illustrating the use of bound authenticators managed at the RP.]({{site.baseurl}}/{{page.collection}}/media/RP-Managed-Bound-Auth.png 'RP-Managed Bound Authenticators'){:latex-src="RP-Managed-Bound-Auth.pdf" latex-fig="10" latex-place="h"}

Before an RP can successfully accept an FAL3 assertion, the RP subscriber account must include a bound authenticator. These authenticators can be provided by either the RP or the subscriber, with slightly different requirements applying to the initial binding of the authenticator to the RP subscriber account in each case.

For RP-provided authenticators, the administrator of the RP **SHALL** issue the authenticator to the subscriber directly for use with an FAL3 login. The administrator of the RP **SHALL** store a unique identifier for the bound authenticator in the RP subscriber account. The administrator of the RP **SHALL** determine through independent means that the party to which the authenticator is issued is the identified subject of the RP subscriber account.

For subscriber-provided authenticators, if no bound authenticators are associated with the RP subscriber account, the RP **SHALL** perform a binding ceremony to establish the connection between the authenticator, the subscriber, and the RP subscriber account as shown in [Fig. 11](sec6_assertions.md#fig-11). The RP **SHALL** first establish an authenticated session using federation with an assertion that meets all the other requirements of FAL3, including an indication that the assertion is intended for use at FAL3 with an RP-managed bound authenticator. The subscriber **SHALL** immediately be prompted to present and authenticate with the proposed authenticator. Upon successful presentation of the authenticator, the RP **SHALL** store a unique identifier for the authenticator (such as its public key) and associate this with the RP subscriber account associated with the federated identifier. If the subscriber fails to successfully present an appropriate authenticator, the binding ceremony fails. The binding ceremony session **SHALL** have a timeout of five minutes or less. The session used during the ceremony is not an authenticated session for the purposes of logging in. Upon successful completion of the binding ceremony, the RP **SHALL** immediately request a new assertion from the IdP at FAL3, including prompting the subscriber for the newly-bound authenticator.

[Figure 11. Binding Ceremony](sec6_assertions.md#fig-11){:name="fig-11"}
{:latex-ignore="true"}

![Sequence diagram of the steps involved in the binding ceremony used for bound authenticators managed at the RP and provided by the subscriber.]({{site.baseurl}}/{{page.collection}}/media/Binding-Ceremony.png 'Binding Ceremony'){:latex-src="Binding-Ceremony.pdf" latex-fig="11" latex-place="h"}

An RP **MAY** allow a subscriber to bind multiple subscriber-provided authenticators at FAL3. If this is the case, and the RP subscriber account has one or more existing bound authenticators, the binding ceremony makes use of the existing ability to reach FAL3. The subscriber **SHALL** first be prompted to present an existing bound authenticator to reach FAL3. Upon successful authentication, the RP **SHALL** immediately prompt the subscriber for the newly-bound authenticator.


An RP **MAY** allow a subscriber to unbind a bound subscriber-provided authenticator from their RP subscriber account, thereby removing the ability to use that authenticator for FAL3. When a bound authenticator is unbound, the RP **SHALL** terminate all current FAL3 sessions for the subscriber and **SHALL** require reauthentication of the subscriber from the IdP. Note that in many cases, a subscriber will need to unbind a bound authenticator to account for a lost or compromised authenticator, and the subscriber will therefore not have access to the authenticator during the unbinding process.

~~~
\clearpage
~~~
{:latex-literal="true"}

The RP **SHALL** notify the subscriber through an out-of-band mechanism, and **SHOULD** notify the IdP using a shared signaling system (see [Sec. 5.7](sec5_federation.md#shared-signals)), if any of the following events occur:

- A new authenticator is bound to the RP subscriber account.
- An existing bound authenticator is unbound from the RP subscriber account.

For example, a subscriber could have a single factor cryptographic device as an authenticator. This authenticator uses name-based phishing resistance so the IdP and RP would see different keys when used in each location. The RP can use a binding ceremony as described here to allow the subscriber to use this device as a bound authenticator at FAL3. The RP will prompt the subscriber for this authenticator whenever it sees an assertion for this subscriber at FAL3 from the IdP.

#### Processing Bound Authenticators

When the RP receives an assertion associated with a bound authenticator, the subscriber proves possession of the bound authenticator directly to the RP. The primary authentication at the IdP and the federated authentication at the RP are processed separately. While the subscriber could use the same authenticator during the primary authentication at the IdP and as the bound authenticator at the RP, there is no assumption that these will be the same.

The following requirements apply to all assertions associated with a bound authenticator:

1. The subscriber **SHALL** prove possession of the bound authenticator to the RP, in addition to presentation of the assertion itself.
2. If the authenticator is managed at the IdP, reference to a given authenticator found within an assertion **SHALL** be trusted at the same level as all other information within the assertion.
3. If the authenticator is managed at the IdP, the assertion **SHALL NOT** include an unencrypted private or symmetric key to be used as an authenticator with the presentation.
4. The RP **SHALL** process and validate the assertion in addition to the bound authenticator.
5. Failure to authenticate with the bound authenticator **SHALL** result in an error at the RP.

## Assertion Protection

Independent of the binding mechanism (discussed in [Sec. 6.1](sec6_assertions.md#assertion-binding)) or the federation model used to obtain them (described in [Sec. 5.1](sec5_federation.md#trust-agreement)), assertions **SHALL** include a set of protections to prevent attackers from manufacturing valid assertions or reusing captured assertions at disparate RPs. The protections required are dependent on the details of the use case being considered, and specific protections are listed here.

### Assertion Identifier {#assertion-id}

Assertions **SHALL** be sufficiently unique to permit unique identification by the target RP. Assertions **MAY** accomplish this by use of an embedded nonce, issuance timestamp, assertion identifier, or a combination of these or other techniques.

### Signed Assertion {#signed-assertion}

Assertions **SHALL** be cryptographically signed by the issuer (IdP). The RP **SHALL** validate the digital signature or MAC of each such assertion based on the issuer's key. This signature **SHALL** cover the entire assertion, including its identifier, issuer, audience, subject, and expiration.

The assertion signature **SHALL** either be a digital signature using asymmetric keys or a MAC using a symmetric key shared between the RP and issuer. Shared symmetric keys used for this purpose by the IdP **SHALL** be independent for each RP to which they send assertions, and are normally established during registration of the RP. Public keys for verifying digital signatures **SHALL** be transferred to the RP in a secure manner, and **MAY** be fetched by the RP in a secure fashion at runtime, such as through an HTTPS URL hosted by the IdP. Approved cryptography **SHALL** be used.

### Encrypted Assertion {#encrypted-assertion}

Encrypted assertions protect the contents of the assertion from being read by unintended parties, ensuring that only the targeted RP is able to read the assertion. Encrypting assertions provides two primary benefits: the assertion contents cannot be seen by any party other than the intended RP, and the assertion cannot be used by any RP other than the targeted one.

When encrypting assertions, the IdP **SHALL** encrypt the contents of the assertion using either the RP's public key or a shared symmetric key. Shared symmetric keys used for this purpose by the IdP **SHALL** be independent for each RP to which they send assertions, and are normally established during registration of the RP. Public keys for encryption **SHALL** be securely transferred to the IdP and **MAY** be fetched by the IdP in a secure fashion at runtime, such as through an HTTPS URL hosted by the RP.

All encryption of assertions **SHALL** use approved cryptography.

When personally-identifiable information is included in the assertion and the assertion is handled by intermediaries such as a browser, the federation protocol **SHALL** encrypt assertions to protect the sensitive information in the assertion from leaking to unintended parties. For example, a SAML assertion can be encrypted using XML-Encryption, or an OpenID Connect ID Token can be encrypted using JSON Web Encryption (JWE).

### Audience Restriction

Assertions **SHALL** use audience restriction techniques to allow an RP to recognize whether or not it is the intended target of an issued assertion. All RPs **SHALL** check that the audience of an assertion contains an identifier for their RP to prevent the injection and replay of an assertion generated for one RP at another RP.

### Pairwise Pseudonymous Identifiers {#ppi}

In some circumstances, it is desirable to prevent the subscriber account from being easily linked at multiple RPs through use of a common identifier. A pairwise pseudonymous identifier (PPI) allows an IdP to provide multiple distinct federated identifiers to different RPs for a single subscriber account. This prevents different RPs from colluding together to track the subscriber using the federated identifier.

#### General Requirements

When using pairwise pseudonymous identifiers within the assertions generated by the IdP for the RP, the IdP **SHALL** generate a different federated identifier for each RP as described in [Sec. 6.2.5.2](sec6_assertions.md#ppi-gen) below.

When PPIs are used with RPs alongside attributes, it may still be possible for multiple colluding RPs to re-identify a subscriber by correlation across systems using these identity attributes. For example, if two independent RPs each see the same subscriber identified with different pairwise pseudonymous identifiers, they could still determine that the subscriber is the same person by comparing the name, email address, physical address, or other identifying attributes carried alongside the pairwise pseudonymous identifier in the respective assertions. Privacy policies **SHOULD** prohibit such correlation, and pairwise pseudonymous identifiers can increase effectiveness of these policies by increasing the administrative effort in managing the attribute correlation.

Note that in a proxied federation model, the initial IdP may be unable to generate a pairwise pseudonymous identifier for the ultimate RP, since the proxy could blind the IdP from knowing which RP is being accessed by the subscriber. In such situations, the pairwise pseudonymous identifier is generally established between the IdP and the federation proxy itself. The proxy, acting as an IdP, can itself provide pairwise pseudonymous identifiers to downstream RPs. Depending on the protocol, the federation proxy may need to map the pairwise pseudonymous identifiers back to the associated identifiers from upstream IdPs in order to allow the identity protocol to function. In such cases, the proxy will be able to track and determine which pairwise pseudonymous identifiers represent the same subscriber at different RPs. The proxy **SHALL NOT** disclose the mapping between the pairwise pseudonymous identifier and any other identifiers to a third party or use the information for any purpose other than federated authentication, related fraud mitigation, to comply with law or legal process, or in the case of a specific user request for the information.

#### Pairwise Pseudonymous Identifier Generation {#ppi-gen}

Pairwise pseudonymous identifiers **SHALL** contain no identifying information about the subscriber. They **SHALL** also be unguessable by a party having access to some information identifying the subscriber. Pairwise pseudonymous identifiers **MAY** be generated randomly and assigned to subscribers by the IdP or **MAY** be derived from other subscriber information if the derivation is done in an irreversible, unguessable manner (e.g., using a keyed hash function with a secret key).

Normally, the identifiers **SHALL** only be known by and used by one pair of endpoints (e.g., IdP-RP). An IdP **MAY** generate the same identifier for a subscriber at multiple RPs at the request of those RPs, provided:

* The trust agreement stipulates a shared pseudonymous identifier for a specific family of RPs;
* The authorized party consents to and is notified of the use of a shared pseudonymous identifier;
* Those RPs have a demonstrable relationship that justifies an operational need for the correlation, such as a shared security domain or shared legal ownership; and
* All RPs sharing an identifier consent to being correlated in such a manner (i.e., one RP cannot request to have another RP's PPI without that other RP's knowledge and consent).

The RPs **SHALL** conduct a privacy risk assessment to consider the privacy risks associated with requesting a common identifier. See [Sec. 9.2](sec9_privacy.md#notice) for further privacy considerations.

The IdP **SHALL** ensure that only intended RPs are correlated; otherwise, a rogue RP could learn of the pseudonymous identifier for a set of correlated RPs by fraudulently posing as part of that set.

## Identity APIs {#s-identity-api}

Attributes about the subscriber, including profile information, **MAY** be provided to the RP through a protected _attribute API_ known as the _identity API_. The RP is granted limited access to the identity API during the federation transaction, in concert with the assertion. For example, in OpenID Connect, the UserInfo Endpoint provides a standardized identity API for fetching attributes about the subscriber. This API is protected by an OAuth 2.0 Access Token, which is issued to the RP along with OpenID Connect's assertion, the ID Token. The use of identity APIs along with federation assertions has several advantages for the overall security, privacy, and efficiency of the federation system.

By making attributes available at an identity API, the IdP no longer has to use the assertion to convey as much information to the RP. This not only means that sensitive attributes do not have to be carried in the assertion itself, it also makes the assertion smaller and easier to process by the RP. The contents of the assertion can then be limited to essential fields (e.g., unique subject identifiers) and information about the immediate authentication event being asserted.

The RP often caches attributes provided by the IdP in an RP subscriber account, discussed in [Sec. 5.4](../sec5_federation.md#rp-account). Attributes provided in the assertion are passed on every login, and since the RP does not know the identity of the subscriber before the attribute is requested, the IdP is incentivized to include as much information as possible in the assertion itself. However, most of a subscriber's attributes will not change in between subsequent logins, making this information redundant. As a consequence, most of these more-stable attributes can instead be made available through an identity API that is called by the RP only when necessary. The IdP can indicate in the assertion when the last time the subscriber's attributes have been updated in the subscriber account, allowing the RP to decide if it needs to fetch the attributes anew or if those in the RP subscriber account are sufficient.

Access to the identity API **SHALL** be time limited. The time limitation is separate from the validity time window of the assertion and the lifetime of the authenticated session at the RP. Access to an identity API by the RP without an associated valid assertion **SHALL NOT** be sufficient for the establishment of an authenticated session at the RP.

A given identity API deployment is expected to be capable of providing attributes for all subscribers for whom the IdP can create assertions. However, when access to the identity API is granted within the context of a federation transaction, the attributes provided by an identity API **SHALL** be associated with only the single subscriber identified in the associated assertion. If the identity API is hosted by the IdP, the returned attributes **SHALL** include the subject identifier for the subscriber. This allows the RP to positively correlate the assertion's subject to the returned attributes. Note that when access to an attribute API is provided as part of pre-provisioning of RP subscriber accounts as discussed in [Sec. 5.4.1](sec5_federation.md#provisioning), the RP is usually granted blanket access to the identity API outside the context of the federated transaction and these requirements do not apply.

### Attribute Providers {#s-attribute-providers}

While most attribute APIs used in federation are hosted as part of the IdP, it is also possible for the IdP to grant access to identity APIs hosted by external attribute providers. These services provide attributes about the subscriber in addition to those made available directly from the IdP.

When the IdP grants access to an attribute provider, the IdP is making an explicit statement that the information returned from the attribute provider is associated with the subscriber identified in the associated assertion. For the purposes of the trust agreement, the IdP is the responsible party for the accuracy and content of the attribute API.

The attributes returned by the attribute provider are assumed to be independent of those returned directly from the IdP, and as such **MAY** use different identifiers, formats, or schemas. The RP **SHALL** verify that the identified attribute provider is capable of providing the kinds of attributes that are present, under the auspices of the applicable trust agreement.

For example, an IdP could provide access to a subscriber's medical license information as part of the federation process. Instead of the IdP asserting the license status directly, the IdP provides the RP access to a record for the subscriber at a medical licensure agency. The RP can make a strong association between the current subscriber and the license record, even though the license record will not likely use the same subject identifier that the IdP does in this case.