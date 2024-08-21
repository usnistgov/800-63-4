---
layout: default
title: Glossary
navOrder: 14
navTitle: Glossary
permalink: /sp800-63c/glossary/
anchor: def-and-acr
section: B
---

# Glossary {#def-and-acr}

A wide variety of terms are used in the realm of digital identity. While many definitions are consistent with earlier versions of SP 800-63, some have changed in this revision. Many of these terms lack a single, consistent definition, warranting careful attention to how the terms are defined here.

account linking
: The association of multiple _federated identifiers_ with a single _RP subscriber account_, or the management of those associations.

account resolution
: The association of an _RP subscriber account_ with information already held by the _RP_ prior to the _federation transaction_ and outside of a _trust agreement_.

activation factor
: An additional _authentication factor_ that is used to enable successful _authentication_ with a _multi-factor authenticator_.

allowlist
: A documented list of specific elements that are allowed, per policy decision. In _federation_ contexts, this is most commonly used to refer to the list of _RPs_ allowed to connect to an _IdP_ without subscriber intervention. This concept has historically been known as a _whitelist_.

approved cryptography
: An encryption algorithm, _hash function_, random bit generator, or similar technique that is _Federal Information Processing Standard_ (FIPS)-approved or NIST-recommended. Approved algorithms and techniques are either specified or adopted in a FIPS or NIST recommendation.

assertion
: A statement from an _IdP_ to an _RP_ that contains information about an authentication event for a subscriber. Assertions can also contain identity _attributes_ for the subscriber.

assertion reference
: A data object, created in conjunction with an _assertion_, that is used by the _RP_ to retrieve an assertion over an _authenticated_ protected channel.

assertion presentation
: The method by which an _assertion_ is transmitted to the _RP_.

asymmetric keys
: Two related keys, comprised of a _public key_ and a _private key_, that are used to perform complementary operations such as encryption and decryption or signature _verification_ and generation.

attribute
: A quality or characteristic ascribed to someone or something. An identity attribute is an attribute about the identity of a subscriber.

attribute bundle
: A package  of _attribute values_ and _derived attribute values_ from a _CSP_. The package has necessary cryptographic protection to allow _validation_ of the bundle independent from interaction with the CSP or _IdP_. Attribute bundles are often used with subscriber-controlled wallets.

attribute provider
: The provider of an _identity API_ that provides access to a subscriber's attributes without necessarily asserting that the subscriber is present to the _RP_.

attribute value
: A complete statement that asserts an identity attribute of a subscriber, independent of format. For example, for the _attribute_ "birthday," a value could be "12/1/1980" or "December 1, 1980."

audience restriction
: The restriction of a message to a specific target audience to prevent a receiver from unknowingly _processing_ a message intended for another recipient. In _federation protocols_, _assertions_ are audience _restricted_ to specific _RPs_ to prevent an RP from accepting an assertion generated for a different RP.

authenticate
: See _authentication_.

authenticated protected channel
: An encrypted communication channel that uses _approved cryptography_ where the connection initiator (client) has authenticated the recipient (server). Authenticated protected channels are encrypted to provide confidentiality and protection against active intermediaries and are frequently used in the user _authentication_ process. _Transport Layer Security_ (TLS) and Datagram Transport Layer Security (DTLS) [[RFC9325]](references.md#ref-rfc9325) are examples of authenticated protected channels in which the certificate presented by the recipient is verified by the initiator. Unless otherwise specified, authenticated protected channels do not require the server to authenticate the client. Authentication of the server is often accomplished through a certificate chain that leads to a trusted root rather than individually with each server.

authenticated session
: See _protected session_.

authentication
: The process by which a _claimant_ proves possession and control of one or more _authenticators_ bound to a _subscriber account_ to demonstrate that they are the subscriber associated with that account.

Authentication Assurance Level (AAL)
: A category describing the strength of the authentication process.

authenticator
: Something that the subscriber possesses and controls (e.g., a _cryptographic module_ or _password_) and that is used to _authenticate_ a _claimant's_ identity. See _authenticator type_ and _multi-factor authenticator_.

authenticator binding
: The establishment of an association between a specific _authenticator_ and a _subscriber account_ that allows the _authenticator_ to be used to _authenticate_ for that subscriber account, possibly in conjunction with other authenticators.

authorize
: A decision to grant access, typically automated by evaluating a _subject_'s _attributes_.

authorized party
: In _federation_, the organization, person, or entity that is responsible for making decisions regarding the release of information within the _federation transaction_, most notably subscriber _attributes_. This is often the subscriber (when runtime decisions are used) or the party operating the _IdP_ (when _allowlists_ are used).

back-channel communication
: Communication between two systems that relies on a direct connection without using redirects through an intermediary such as a browser.

bearer assertion
: An _assertion_ that can be presented on its own as proof of the identity of the presenter.

blocklist
: A documented list of specific elements that are blocked, per policy decision. This concept has historically been known as a _blacklist_.

challenge-response protocol
: An _authentication protocol_ in which the _verifier_ sends the _claimant_ a challenge (e.g., a random value or _nonce_) that the claimant combines with a secret (e.g., by hashing the challenge and a _shared secret_ together or by applying a _private-key_ operation to the challenge) to generate a response that is sent to the verifier. The verifier can independently verify the response generated by the claimant (e.g., by re-computing the hash of the challenge and the shared secret and comparing to the response or performing a public-key operation on the response) and establish that the claimant possesses and controls the secret.

core attributes
: The set of identity _attributes_ that the _CSP_ has determined and documented to be required for _identity proofing_.

credential service provider (CSP)
: A trusted entity whose functions include _identity proofing_ _applicants_ to the identity service and registering _authenticators_ to _subscriber accounts_. A CSP may be an independent third party.

cross-site request forgery (CSRF)
: An attack in which a subscriber who is currently _authenticated_ to an _RP_ and connected through a secure session browses an attacker's website, causing the subscriber to unknowingly invoke unwanted actions at the RP.

    For example, if a bank website is vulnerable to a CSRF attack, it may be possible for a subscriber to unintentionally _authorize_ a large money transfer by clicking on a malicious link in an email while a connection to the bank is open in another browser window.

cross-site scripting (XSS)
: A vulnerability that allows attackers to inject malicious code into an otherwise benign website. These scripts acquire the permissions of scripts generated by the target website to compromise the confidentiality and integrity of data transfers between the website and clients. Websites are vulnerable if they display user-supplied data from requests or forms without sanitizing the data so that it is not executable.

derived attribute value
: A statement that asserts a limited identity _attribute_ of a subscriber without containing the attribute value from which it is derived, independent of format. For example, instead of requesting the attribute "birthday," a derived value could be "older than 18". Instead of requesting the attribute for "physical address," a derived value could be "currently residing in this district." Previous versions of these guidelines referred to this construct as an "attribute reference."

digital identity
: An _attribute_ or set of attributes that uniquely describes a _subject_ within a given context.

digital signature
: An _asymmetric key_ operation in which the _private key_ is used to digitally sign data and the _public key_ is used to verify the signature. Digital signatures provide _authenticity_ protection, integrity protection, and _non-repudiation_ support but not confidentiality or _replay attack_ protection.

disassociability
: Enabling the _processing_ of PII or events without association to individuals or devices beyond the operational requirements of the system. [[NISTIR8062]](references.md#ref-NISTIR8062)

entropy
: The amount of uncertainty that an attacker faces to determine the value of a secret. Entropy is usually stated in bits. A value with *n* bits of entropy has the same degree of uncertainty as a uniformly distributed *n*-bit random value.

equity
: The consistent and systematic fair, just, and impartial treatment of all individuals, including individuals who belong to underserved communities that have been denied such treatment, such as Black, Latino, and Indigenous and Native American persons, Asian Americans and Pacific Islanders, and other persons of color; members of religious minorities; lesbian, gay, bisexual, transgender, and queer (LGBTQ+) persons; persons with disabilities; persons who live in rural areas; and persons otherwise adversely affected by persistent poverty or inequality. [[EO13985]](references.md#ref-EO13985)

Federal Information Processing Standard (FIPS)
: Under the Information Technology Management Reform Act (Public Law 104-106), the Secretary of Commerce approves the standards and guidelines that the National Institute of Standards and Technology (NIST) develops for federal computer systems. NIST issues these standards and guidelines as Federal Information Processing Standards (FIPS) for government-wide use. NIST develops FIPS when there are compelling federal government requirements, such as for security and interoperability, and there are no acceptable industry standards or solutions. See background information for more details.

    FIPS documents are available online on the FIPS home page: <https://www.nist.gov/itl/fips.cfm>

federated identifier
: The combination of a _subject identifier_ within an _assertion_ and an _identifier_ for the _IdP_ that issued that assertion. When combined, these pieces of information uniquely identify the _subscriber_ in the context of a _federation transaction_.

federation
: A process that allows for the conveyance of identity and authentication information across a set of _networked_ systems.

Federation Assurance Level (FAL)
: A category that describes the process used in a _federation transaction_ to communicate authentication events and subscriber _attributes_ to an _RP_.

federation protocol
: A technical protocol that is used in a _federation transaction_ between _networked_ systems.

federation proxy
: A component that acts as a logical _RP_ to a set of _IdPs_ and a logical IdP to a set of RPs, bridging the two systems with a single component. These are sometimes referred to as "brokers."

federation transaction
: A specific instance of _processing_ an authentication using a _federation_ process for a specific _subscriber_ by conveying an _assertion_ from an _IdP_ to an _RP_.

front-channel communication
: Communication between two systems that relies on passing messages through an intermediary, such as using redirects through the subscriber's browser.

hash function
: A function that maps a bit string of arbitrary length to a fixed-length bit string. Approved hash functions satisfy the following properties:

    1. One-way &mdash; It is computationally infeasible to find any input that maps to any pre-specified output.

    2. Collision-resistant &mdash; It is computationally infeasible to find any two distinct inputs that map to the same output.

identifier
: A data object that is associated with a single, unique entity (e.g., individual, device, or _session_) within a given context and is never assigned to any other entity within that context.

identity
: See _digital identity_

identity API
: A protected API accessed by an _RP_ to access the _attributes_ of a specific subscriber.

Identity Assurance Level (IAL)
: A category that conveys the degree of confidence that the _subject_'s _claimed identity_ is their real identity.

identity provider (IdP)
: The party in a _federation transaction_ that creates an _assertion_ for the subscriber and transmits the assertion to the _RP_.

injection attack
: An attack in which an attacker supplies untrusted input to a program. In the context of federation, the attacker presents an untrusted _assertion_ or _assertion reference_ to the _RP_ in order to create an _authenticated_ _session_ with the RP.

login
: Establishment of an _authenticated_ _session_ between a person and a system. Also known as _"sign in"_, _"log on"_, and _"sign on."_

message authentication code (MAC)
: A cryptographic checksum on data that uses a _symmetric key_ to detect both accidental and intentional modifications of the data. MACs provide _authenticity_ and integrity protection, but not _non-repudiation_ protection.

network
: An open communications medium, typically the Internet, used to transport messages between the _claimant_ and other parties. Unless otherwise stated, no assumptions are made about the network's security; it is assumed to be open and subject to active (e.g., impersonation, _session_ hijacking) and passive (e.g., eavesdropping) attacks at any point between the parties (e.g., claimant, _verifier_, _CSP_, _RP_).

nonce
: A value used in security protocols that is never repeated with the same key. For example, nonces used as challenges in _challenge-response authentication protocols_ must not be repeated until authentication keys are changed. Otherwise, there is a possibility of a _replay attack_. Using a nonce as a challenge is a different requirement than a random challenge, because a nonce is not necessarily unpredictable.

pairwise pseudonymous identifier
: A _pseudonymous identifier_ generated by an IdP for use at a specific _RP_.

personal information
: See *personally identifiable information*.

personally identifiable information (PII)
: Information that can be used to distinguish or trace an individual's identity, either alone or when combined with other information that is linked or linkable to a specific individual. [[A-130]](references.md#ref-A-130)

predictability
: Enabling reliable assumptions by individuals, owners, and operators about PII and its _processing_ by an information system. [[NISTIR8062]](references.md#ref-NISTIR8062)

private key
: In _asymmetric key_ cryptography, the private key (i.e., a secret key) is a mathematical key used to create _digital signatures_ and, depending on the algorithm, decrypt messages or files that are encrypted with the corresponding _public key_. In _symmetric key_ cryptography, the same private key is used for both encryption and decryption.

processing
: Operation or set of operations performed upon PII that can include, but is not limited to, the collection, retention, logging, generation, transformation, use, disclosure, transfer, and disposal of PII. [[NISTIR8062]](references.md#ref-NISTIR8062)

protected session
: A _session_ in which messages between two participants are encrypted and integrity is protected using a set of _shared secrets_ called "session keys."

    A protected session is said to be _authenticated_ if &mdash; during the session &mdash; one participant proves possession of one or more _authenticators_ in addition to the session keys, and if the other party can verify the identity associated with the authenticators. If both participants are authenticated, the protected session is said to be *mutually authenticated*.

Provisioning API
: A protected API that allows an _RP_ to access identity _attributes_ for multiple subscribers for the purposes of provisioning and managing RP _subscriber accounts_.

pseudonymous identifier
: A meaningless but unique _identifier_ that does not allow the _RP_ to infer anything regarding the subscriber but that does permit the RP to associate multiple interactions with a single subscriber.

public key
: The public part of an _asymmetric key_ pair that is used to verify signatures or encrypt data.

public key certificate
: A digital document issued and digitally signed by the _private key_ of a certificate authority that binds an _identifier_ to a subscriber's _public key_. The certificate indicates that the subscriber identified in the certificate has sole control of and access to the private key. See also [[RFC5280]](references.md#ref-RFC5280).

public key infrastructure (PKI)
: A set of policies, processes, server platforms, software, and workstations used to administer certificates and public-_private key_ pairs, including the ability to issue, maintain, and revoke _public key certificates_.

reauthentication
: The process of confirming the subscriber's continued presence and intent to be _authenticated_ during an extended usage _session_.

relying party (RP)
: An entity that relies upon a _verifier_'s _assertion_ of a subscriber's identity, typically to process a transaction or grant access to information or a system.

replay attack
: An attack in which the attacker is able to replay previously captured messages (between a legitimate _claimant_ and a _verifier_) to masquerade as that claimant to the verifier or vice versa.

risk assessment
: The process of identifying, estimating, and prioritizing risks to organizational operations (i.e., mission, functions, image, or reputation), organizational assets, individuals, and other organizations that result from the operation of a system. A risk assessment is part of _risk management_, incorporates threat and vulnerability analyses, and considers mitigations provided by security _controls_ that are planned or in-place. It is synonymous with "risk analysis."

risk management
: The program and supporting processes that manage information security risk to organizational operations (including mission, functions, image, reputation), organizational assets, individuals, and other organizations and includes (i) establishing the context for risk-related activities, (ii) assessing risk, (iii) responding to risk once determined, and (iv) monitoring risk over time.

RP subscriber account
: An account established and managed by the _RP_ in a federated system based on the RP's view of the _subscriber account_ from the _IdP_. An RP subscriber account is associated with one or more _federated identifiers_ and allows the subscriber to access the account through a _federation transaction_ with the IdP.

security domain
: A set of systems under a common administrative and access control.

session
: A persistent interaction between a subscriber and an _endpoint_, either an _RP_ or a _CSP_. A session begins with an authentication event and ends with a session termination event. A session is bound by the use of a session secret that the subscriber's software (e.g., a browser, application, or OS) can present to the RP to prove association of the session with the authentication event.

session hijack attack
: An attack in which the attacker is able to insert themselves between a _claimant_ and a _verifier_ subsequent to a successful authentication exchange between the latter two parties. The attacker is able to pose as a subscriber to the verifier or vice versa to control _session_ data exchange. Sessions between the claimant and the _RP_ can be similarly compromised.

single sign-on (SSO)
: An authentication process by which one account and its _authenticators_ are used to access multiple applications in a seamless manner, generally implemented with a _federation protocol_.

subject
: A person, organization, device, hardware, _network_, software, or service. In these guidelines, a subject is a _natural person_.

subscriber
: An individual enrolled in the _CSP_ identity service.

subscriber account
: An account established by the _CSP_ containing information and _authenticators_ registered for each subscriber enrolled in the CSP identity service.

symmetric key
: A _cryptographic key_ used to perform both the cryptographic operation and its inverse. (e.g., to encrypt and decrypt or create a _message authentication code_ and to verify the code).

Transport Layer Security (TLS)
: An authentication and security protocol widely implemented in browsers and web servers. TLS is defined by [[RFC5246]](references.md#ref-RFC5246). TLS is similar to the older SSL protocol, and TLS 1.0 is effectively SSL version 3.1. SP 800-52, Guidelines for the Selection and Use of Transport Layer Security (TLS) Implementations [[SP800-52]](references.md#ref-SP800-52), specifies how TLS is to be used in government applications.

trust agreement
: A set of conditions under which a _CSP_, _IdP_, and _RP_ are allowed to participate in a _federation transaction_ for the purposes of establishing an authentication _session_ between the subscriber and the RP.

usability
: The extent to which a product can be used by specified users to achieve specified goals with effectiveness, efficiency, and satisfaction in a specified context of use. [[ISO/IEC9241-11]](references.md#ref-ISOIEC9241)

verifier
: An entity that verifies the _claimant's_ identity by verifying the claimant's possession and control of one or more _authenticators_ using an _authentication protocol_. To do this, the verifier needs to confirm the binding of the authenticators with the _subscriber account_ and check that the subscriber account is active.
