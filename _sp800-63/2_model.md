---
layout: default
title: Digital Identity Model
navOrder: 3
navTitle: Model
permalink: /sp800-63/model/
anchor: sec4
section: 2
---

# Digital Identity Model {#sec4}

*This section is informative.*

## Overview {#s-4-1}

The SP 800-63 guidelines use digital identity models that reflect technologies and architectures that already currently available in the market. These models have a variety of entities and functions and vary in complexity. Simple models group functions, such as creating subscriber accounts and providing attributes, under a single entity. More complex models separate these functions among a larger number of entities. The entities, and their associated functions, found in digital identity models include:

**Subject**: In these guidelines, a subject is a person and is represented by one of three roles, depending on where they are in the digital identity process.

- Applicant &mdash; The subject to be identity-proofed and enrolled.
- Subscriber &mdash; - The subject who has successfully completed the identity proofing and enrollment process or authentication (i.e., when the subject is in an active on-line session).
- Claimant &mdash; The subject "making a claim" to be eligible for authentication.

**Service provider**: Service providers can perform any combination of functions involved in granting access to and delivering online services, such as a credential service provider, relyin party, verifier, and Identity provider.

**Credential service provider (CSP)**: CSP functions include identity proofing applicants to the identity service and registering authenticators to subscriber accounts. A _subscriber account_ is the CSP's established record of the subscriber, the subscriber's attributes, and associated authenticators. CSP functions may be performed by an independent third party.

**Relying party (RP)**: RP functions rely on the information in the subscriber account from the CSP, typically to process a digital transaction or grant access to information or a system. When using federation, the RP accesses the information in the subscriber account through assertions from an identity provider.

**Verifier**: The function of a verifier is to verify the claimant's identity by verifying the claimant's possession and control of one or more authenticators using an authentication protocol. To do this, the verifier needs to confirm the binding of the authenticators with the subscriber account and check that the subscriber account is active.

**Identity provider (IdP)**: When using federation, the IdP manages the subscriber's primary authenticators and issues assertions derived from the subscriber account.

## Identity Proofing and Enrollment

Normative requirements can be found in [[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"}, *Identity Proofing and Enrollment*.

[[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"} provides general information and normative requirements for the identity proofing and enrollment processes as well as requirements that are specific to IALs.

[Figure 1](2_model.md#fig-1) shows a sample of interactions for identity proofing and enrollment.

To start, an *applicant* opts to enroll with a CSP by requesting access. The CSP or the entity fulfilling CSP functions requests identity evidence and attributes, which the applicant provides. If the applicant is successfully identity-proofed, they are enrolled in the identity service as a *subscriber* of that CSP. A unique subscriber account is then created and one or more authenticators are registered to the subscriber account.

Subscribers have a responsibility to maintain control of their authenticators (e.g., guard against theft) and comply with CSP policies to remain in good standing with the CSP.

[Fig. 1. Sample Identity Proofing and Enrollment Digital Identity Model](2_model.md#fig-1){:name="fig-1"}  
{:latex-ignore="true"}

![Sequence diagram of identity proofing and enrollment showing the parties involved and the major steps in the process.]({{site.baseurl}}/{{page.collection}}/images/ID_Proofing.png 'Sample Identity Proofing and Enrollment Digital Identity Model'){:latex-src="ID_Proofing.pdf" latex-fig="1" latex-place="h"}

### Subscriber Accounts

At the time of enrollment, the CSP establishes a subscriber account to uniquely identify each subscriber and record any authenticators registered (bound) to that subscriber account. The CSP may:

- Issue and register one or more authenticators to the subscriber at the time of enrollment,
- Register authenticators provided by the subscriber to the subscriber account,
- Register additional authenticators to the subscriber account at a later time as needed, or  
- Provision the subscriber account to one or more general-purpose or subscriber-controlled wallets, for use in a federated protocol system.

See [Sec. 5 of [SP800-63A]](../_sp800-63a/5_accounts.md#accounts){:latex-href="#ref-SP800-63A"}, *Subscriber-Accounts*, for more information and normative requirements.

## Authentication and Authenticator Management

Normative requirements can be found in [[SP800-63B]](../_sp800-63b/1_introduction.md#introduction){:latex-href="#ref-SP800-63B"}, *Authentication and Authenticator Management*.

### Authenticators

[[SP800-63B]](../_sp800-63b/1_introduction.md#introduction){:latex-href="#ref-SP800-63B"} provides normative descriptions of permitted authenticator types, their characteristics (e.g.,  phishing resistance), and authentication processes appropriate for each AAL.

This guidance defines three types of authentication factors used for authentication:

* Something you know (e.g., a password)
* Something you have (e.g., a device containing a cryptographic key)
* Something you are (e.g., a fingerprint or other biometric characteristic data)

Single-factor authentication requires only one of the above factors, most often "something you know". Multiple instances of the same factor still constitute single-factor authentication. For example, a user-generated PIN and a password do not constitute two factors as they are both "something you know." Multi-factor authentication (MFA) refers to the use of more than one distinct factor.

This guidance specifies that authenticators always contain or comprise a secret. The secrets contained in an authenticator are based on either key pairs (i.e., asymmetric cryptographic keys) or shared secrets (including symmetric cryptographic keys, seeds for generating one-time passwords (OTP), and passwords). Asymmetric key pairs are comprised of a public key and a related private key. The private key is stored on the authenticator and is only available for use by the claimant who possesses and controls the authenticators. A verifier that has the subscriber's public key (e.g., through a public key certificate) can use an authentication protocol to verify that the claimant is a subscriber who has possession and control of the associated private key contained in the authenticator. Symmetric keys are generally chosen at random, complex and long enough to thwart network-based guessing attacks, and stored in hardware or software that the subscriber controls. Passwords typically have fewer characters and less complexity than cryptographic keys resulting in increased vulnerabilities that require additional defenses to mitigate.

Passwords used as activation factors for multi-factor authenticators are referred to as _activation secrets_. An activation secret is used to decrypt a stored key used for authentication or is compared against a locally held and stored verifier to provide access to the authentication key. In either of these cases, the activation secret remains within the authenticator and its associated user endpoint. An example of an activation secret would be the PIN used to activate a PIV card.

Biometric characteristics are unique, personal attributes that can be used to verify the identity of a person who is physically present at the point of authentication. This includes, but is not limited to, facial features, fingerprints, and iris patterns. While biometric characteristics cannot be used for single-factor authentication, they can be used as an authentication factor for multi-factor authentication when used in combination with a physical authenticator (i.e., something you have).

Some authentication methods used for in-person interactions do not apply directly to digital authentication. For example, a physical driver's license is something you have and may be useful when authenticating to a human (e.g., a security guard), but it is not an authenticator for online services.

Some commonly used authentication methods do not contain or comprise secrets and are therefore not acceptable for use under these guidelines. For example:

-  Knowledge-based authentication, where the claimant is prompted to answer questions that are presumably known only by the claimant, does not constitute an acceptable secret for digital authentication.
-  A biometric characteristic does not constitute a secret and cannot be used as a single-factor authenticator.

### Authentication Process

The authentication process enables an RP to trust that a claimant is who they say they are.  Some approaches are described in [[SP800-63B]](../_sp800-63b/1_introduction.md#introduction){:latex-href="#ref-SP800-63B"}, *Authentication and Authenticator Management*. The sample authentication process in [Fig. 2](2_model.md#fig-2) shows interactions between the RP, a claimant, and a verifier/CSP. The verifier is a functional role and is frequently implemented in combination with the CSP, the RP, or both (as shown in [Fig. 4](2_model.md#fig-4)).

[Fig. 2. Sample Authentication Process](2_model.md#fig-2){:name="fig-2"}
{:latex-ignore="true"}

![Sequence diagram of a sample authentication process showing parties involved and major steps in the process.]({{site.baseurl}}/{{page.collection}}/images/Sample_Authn_Process.png 'Sample Authentication Process'){:latex-src="Sample_Authn_Process.pdf" latex-fig="2" latex-place="h"}

A successful authentication process demonstrates that the claimant has possession and control of one or more valid authenticators that are bound to the subscriber's identity. In general, this is done using an authentication protocol that involves an interaction between the verifier and the claimant. The exact nature of the interaction is extremely important in determining the overall security of the system. Well-designed protocols can protect the integrity and confidentiality of communication between the claimant and the verifier both during and after the authentication and can help limit the damage done by an attacker masquerading as a legitimate verifier.

Additionally, mechanisms located at the verifier can mitigate online guessing attacks against lower entropy secrets (e.g., passwords and PINs) by limiting the rate at which an attacker can make authentication attempts, or otherwise delaying incorrect attempts. Generally, this is done by keeping track of and limiting the number of unsuccessful attempts, since the premise of an online guessing attack is that most attempts will fail.

## Federation and Assertions {#Federation}

Normative requirements can be found in [[SP800-63C]](../_sp800-63c/1_introduction.md#introduction){:latex-href="#ref-SP800-63C"}, *Federation and Assertions*.

Section III of OMB [[M-19-17]](references.md#ref-M-19-17) *Enabling Mission Delivery through Improved Identity, Credential, and Access Management* directs agencies to support cross-government identity federation and interoperability. The term _federation_ can be applied to several different approaches that involve the sharing of information between different trust domains. These approaches differ based on the kind of information that is being shared between the domains. These guidelines address the federation processes that allow for the conveyance of identity and authentication information based on trust agreements across a set of networked systems through federation assertions.

There are many benefits to using federated architectures including, but not limited to:

* Enhanced user experience (e.g., a subject can be identity proofed once but their subscriber account used at multiple RPs).
* Cost reduction to both the subscriber (e.g., reduction in authenticators) and the organization (e.g., reduction in information technology infrastructure and a streamlined architecture).
* Minimizing data in RPs that do not need to collect, store, or dispose of personal information.
* Minimizing data exposed to RPs by using pseudonymous identifiers and derived attribute values instead of copying account values to each application.
* Mission enablement, since organizations will need to focus fewer resources on complex identity management processes.

While the federation process is generally the preferred approach to authentication when the RP and IdP are not administered together under a common security domain, federation can also be applied within a single security domain for a variety of benefits including centralized account management and technical integration.

The SP 800-63 guidelines are agnostic to the identity proofing, authentication, and federation architectures that an organization selects, and they allow organizations to deploy a digital identity scheme according to their own requirements. However, there are scenarios that an organization may encounter that make federation potentially more efficient and effective than establishing identity services that are local to the organization or individual applications. The following lists detailed potential scenarios in which the organization may consider federation to be a viable option:

- Potential users already have an authenticator at or above the required AAL.
-  Multiple types of authenticators are required to cover all possible user communities.
- An organization does not have the necessary infrastructure to support management of subscriber accounts (e.g., account recovery, authenticator issuance, help desk).
- There is a desire to allow primary authenticators to be added and upgraded over time without changing the RP's implementation.
- There are different environments to be supported, since federation protocols are network-based and allow for implementation on a wide variety of platforms and languages.
- Potential users come from multiple communities, each with its own existing identity infrastructure.
- The organization needs the ability to centrally manage account lifecycles, including account revocation and the binding of new authenticators.

An organization may want to consider accepting federated identity attributes if any of the following apply:

- Pseudonymity is required, necessary, feasible, or important to stakeholders accessing the service.
- Access to the service requires a defined list of attributes.
- Access to the service requires at least one derived attribute value.
- The organization is not the authoritative source or issuing source for required attributes.
- Attributes are only required temporarily during use (e.g., to make an access decision), and the organization does not need to retain the data.

## Examples of Digital Identity Models

The entities and interactions that comprise the non-federated digital identity model are illustrated in [Fig. 3](2_model.md#fig-3). The general-purpose federated digital identity model is illustrated in [Fig. 4](2_model.md#fig-4), and a federated digital identity model with a subscriber-controlled wallet is illustrated in [Fig. 5](2_model.md#fig-5).

[Fig. 3. Non-Federated Digital Identity Model Example](2_model.md#fig-3){:name="fig-3"}
{:latex-ignore="true"}

![High-level diagram of a non-federated digital identity model showing the entities and interactions between entities of the entire digital identity process, in which the verifier function is done by the RP.]({{site.baseurl}}/{{page.collection}}/images/Non-Federated.png 'Non-Federated Digital Identity Model Example'){:latex-src="Non-Federated.pdf" latex-fig="3" latex-place="h"}

[Figure 3](2_model.md#fig-3) shows an example of a common sequence of interactions in the non-federated model. Other sequences could also achieve the same functional requirements. One common sequence of interactions for identity proofing and enrollment activities is as follows:

- Step 1: An applicant applies to a CSP through an identity proofing and enrollment process. The CSP identity proofs that applicant.
- Step 2: Upon successful identity proofing, the applicant is enrolled in the identity service as a subscriber.  
    *	A subscriber account and corresponding authenticators are established between the CSP and the subscriber. The CSP maintains the subscriber account, its status, and the enrollment data. The subscriber maintains their authenticators.

 Steps 3 through 5 may immediately follow steps 1 and 2 or they may be done at a later time. The usual sequence of interactions involved in using one or more authenticators to perform digital authentication in the non-federated model is as follows:

- Step 3: The claimant initiates an online interaction with the RP and the RP requests that the claimant authenticate.
- Step 4: The claimant proves possession and control of the authenticators to the verifier through an authentication process:  
    -	The verifier interacts with the CSP to verify the binding of the claimant's identity to their authenticators in the subscriber account and to optionally obtain additional subscriber attributes.
    -  The CSP or verifier functions of the service provider give information about the subscriber. The RP requests the attributes it requires from the CSP. The RP optionally uses this information to make authorization decisions.
- Step 5: An authenticated session is established between the subscriber and the RP.

[Fig. 4. Federated Digital Identity Model Example](2_model.md#fig-4){:name="fig-4"}  
{:latex-ignore="true"}

![High-level diagram of a federated digital identity model showing the entities and interactions between entities of the entire digital identity process, in which the CSP and verifier functions are done by the IdP.]({{site.baseurl}}/{{page.collection}}/images/Federated.png 'Federated Digital Identity Model Example'){:latex-src="Federated.pdf" latex-fig="4" latex-place="h"}

[Figure 4](2_model.md#fig-4) shows an example of those same common interactions in a federated model.

- Step 1: An applicant applies to a CSP through an identity proofing and enrollment process. The CSP identity proofs that applicant.
- Step 2: Upon successful identity proofing, the applicant is enrolled in the identity service as a subscriber.
    -	A subscriber account and corresponding authenticators are established between the CSP and the subscriber.
    - Unlike in [Fig. 3](2_model.md#fig-3), the IdP is provisioned either directly by the CSP or indirectly through access to attributes of the subscriber account. The CSP maintains the subscriber account, its status, and the enrollment data collected in accordance with the record retention and disposal requirements described in [Sec. 3.1.1 of [SP800-63A]](../_sp800-63a/3_ialgen.md#DocRecReqs){:latex-href="#ref-SP800-63A"}. The subscriber maintains their authenticators. The IdP maintains its view of the subscriber account, any federated identifiers assigned to the subscriber account, and authorizations to RPs.

The usual sequence of interactions involved in using one or more authenticators in the federated model to perform digital authentication is as follows:

- Step 3: The RP requests that the claimant authenticate. This triggers a request for federated authentication to the IdP.
- Step 4: The claimant proves possession and control of the authenticators to the verifier function of the IdP through an authentication process.  
    -	Within the IdP, the verifier and CSP functions interact to verify the binding of the claimant's authenticators with those bound to the claimed subscriber account and optionally to obtain additional subscriber attributes.
- Step 5: The RP and the IdP communicate through a federation protocol. The IdP provides an assertion and optionally additional attributes to the RP through a federation protocol. The RP verifies the assertion to establish confidence in the identity and attributes of a subscriber for an online service at the RP. RPs may use a subscriber's federated identity (pseudonymous or non-pseudonymous), IAL, AAL, FAL, and other factors to make authorization decisions.
- Step 6: An authenticated session is established between the subscriber and the RP.

In the two cases described in [Fig. 3](2_model.md#fig-3) and [Fig. 4](2_model.md#fig-4), the verifier does not always need to communicate in real time with the CSP to complete the authentication activity (e.g., digital certificates can be used). Therefore, the line between the verifier and the CSP represents a logical link between the two entities. In some implementations, the verifier, RP, and CSP functions may be distributed and separated. However, if these functions reside on the same platform, the interactions between the functions are signals between applications or application modules that run on the same system rather than using network protocols.

[Fig. 5. Federated Digital Identity Model With Subscriber-Controlled Wallet Example](2_model.md#fig-5){:name="fig-5"}  
{:latex-ignore="true"}

![High-level diagram of a federated digital identity model with a subscriber-controlled wallet showing the entities and interactions between entities of the entire digital identity process in which the subscriber controls a device with software (commonly known as a digital wallet) that acts as the IdP.]({{site.baseurl}}/{{page.collection}}/images/Wallet.png 'Federated Digital Identity Model with Subscriber-Controlled Wallet Example'){:latex-src="Wallet.pdf" latex-fig="5" latex-place="h"}

[Figure 5](2_model.md#fig-5) shows an example of the interactions in a federated digital identity model in which the subscriber controls a device with software (i.e., a digital wallet) that acts as the IdP. In the terminology of the "three-party model", the CSP is the issuer, the IdP is the holder, and the RP is the verifier. In this model, it is common for the RP to establish a trust agreement with the CSP through the use of a federation authority as defined in [[SP800-63C]](../_sp800-63c/3_federation.md#trust-agreement){:latex-href="#ref-SP800-63C"}. This arrangement allows the RP to accept assertions from the subscriber-controlled wallet without needing a direct trust relationship with the wallet.

- Step 1: An applicant applies to a CSP identity proofing and enrollment process.
- Step 2: Upon successful identity proofing, the applicant goes through an onboarding process and is enrolled in the identity service as a subscriber.
- Step 3: The subscriber-controlled wallet is onboarded by the CSP.
    - The subscriber authenticates to the CSP's onboarding function.
    - The subscriber activates the subscriber-controlled wallet using an activation factor.
    - The wallet sends a request to the CSP, including proof of a key held by the wallet.
    - The CSP creates an attribute bundle that contains a reference for the key of the wallet and any additional attributes.

The usual sequence of interactions involved in providing an assertion to the RP from a subscriber-controlled wallet is as follows:

- Step 4: The RP requests that the claimant authenticate. This triggers a request for federated authentication to the wallet.
- Step 5: The claimant proves possession and control of the subscriber-controlled wallet.
    - The subscriber activates the wallet using an activation factor.
    - The wallet prepares an assertion including the attribute bundle provided by the CSP for the subscriber account.
- Step 6: The RP and the wallet communicate through a federation protocol. The wallet provides an assertion and optionally additional attributes to the RP through a federation protocol. The RP verifies the assertion to establish confidence in the identity and attributes of a subscriber for an online service at the RP. RPs may use a subscriber's federated identity (pseudonymous or non-pseudonymous), IAL, AAL, FAL, and other factors to make authorization decisions.
- Step 7: An authenticated session is established between the subscriber and the RP.

> Note: Other protocols and specifications often refer to attribute bundles as _credentials_. These guidelines use the term _credentials_ for a different concept. To avoid a conflict, the term _attribute bundle_ is used within these guidelines. Normative requirements for attribute bundles can be found including [Sec. 3.11.1 of [SP800-63C]](../_sp800-63c/3_federation.md#attribute-bundles){:latex-href="#ref-SP800-63C"}.
