---
layout: default
title: Glossary
navOrder: 7
navTitle: Glossary
permalink: /sp800-63/glossary/
anchor: def
section: B
---

# Glossary {#def}

*This section is informative.*

A wide variety of terms are used in the realm of digital identity. While many definitions are consistent with earlier versions of SP 800-63, some have changed in this revision. Many of these terms lack a single, consistent definition, warranting careful attention to how the terms are defined here.

account linking
: The association of multiple _federated identifiers_ with a single _RP subscriber account_, or the management of those associations.

account recovery
: The ability to regain ownership of a _subscriber account_ and its associated information and privileges.

account resolution
: The association of an _RP subscriber account_ with information already held by the _RP_ prior to the _federation transaction_ and outside of a _trust agreement_.

activation
: The process of inputting an _activation factor_ into a _multi-factor authenticator_ to enable its use for _authentication_.

activation factor
: An additional _authentication factor_ that is used to enable successful _authentication_ with a _multi-factor authenticator_.

activation secret
: A _password_ that is used locally as an _activation factor_ for a _multi-factor authenticator_.

allowlist
: A documented list of specific elements that are allowed, per policy decision. In _federation_ contexts, this is most commonly used to refer to the list of _RPs_ allowed to connect to an _IdP_ without subscriber intervention. This concept has historically been known as a _whitelist_.

applicant
: A _subject_ undergoing the processes of _identity proofing_ and _enrollment_.

~~~
\clearpage
~~~
{:latex-literal="true"}

applicant reference
: A representative of the _applicant_ who can vouch for the identity of the applicant, specific _attributes_ related to the applicant, or conditions relative to the context of the individual (e.g., emergency status, homelessness).

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

attestation
: Information conveyed to the _CSP_, generally at the time that an _authenticator_ is bound, describing the characteristics of a connected authenticator or the _endpoint_ involved in an authentication operation.

attribute
: A quality or characteristic ascribed to someone or something. An identity attribute is an attribute about the identity of a subscriber.

attribute bundle
: A package  of _attribute values_ and _derived attribute values_ from a _CSP_. The package has necessary cryptographic protection to allow _validation_ of the bundle independent from interaction with the CSP or _IdP_. Attribute bundles are often used with subscriber-controlled wallets.

attribute provider
: The provider of an _identity API_ that provides access to a subscriber's attributes without necessarily asserting that the subscriber is present to the _RP_.

attribute validation
: The process or act of confirming that a set of attributes are accurate and associated with a real-life identity. See *validation*.

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
: A category that describes the strength of the authentication process.

authentication factor
: The three types of authentication factors are *something you know*, *something you have*, and *something you are*. Every _authenticator_ has one or more authentication factors.

authentication intent
: The process of confirming the _claimant's_ intent to _authenticate_ or reauthenticate by requiring user intervention in the authentication flow. Some _authenticators_ (e.g., OTPs) establish authentication intent as part of their operation. Others require a specific step, such as pressing a button, to establish intent. Authentication intent is a countermeasure against use by malware at the _endpoint_ as a proxy for authenticating an attacker without the subscriber's knowledge.

authentication protocol
: A defined sequence of messages between a _claimant_ and a _verifier_ that demonstrates that the claimant has possession and control of one or more valid _authenticators_ to establish their identity, and, optionally, demonstrates that the claimant is communicating with the intended verifier.

authentication secret
: A generic term for any secret value that an attacker could use to impersonate the subscriber in an _authentication protocol_.

    These are further divided into *short-term authentication secrets*, which are only useful to an attacker for a limited period of time, and *long-term authentication secrets*, which allow an attacker to impersonate the subscriber until they are manually reset. The _authenticator_ secret is the canonical example of a long-term authentication secret, while the _authenticator output_ &mdash; if it is different from the _authenticator secret_ &mdash; is usually a short-term authentication secret.

authenticator
: Something that the subscriber possesses and controls (e.g., a _cryptographic module_ or _password_) and that is used to _authenticate_ a _claimant's_ identity. See _authenticator type_ and _multi-factor authenticator_.

authenticator binding
: The establishment of an association between a specific _authenticator_ and a _subscriber account_ that allows the _authenticator_ to be used to _authenticate_ for that subscriber account, possibly in conjunction with other authenticators.

authenticator output
: The output value generated by an _authenticator_. The ability to generate valid authenticator outputs on demand proves that the _claimant_ possesses and controls the authenticator. Protocol messages sent to the _verifier_ depend on the authenticator output, but they may or may not explicitly contain it.

authenticator secret
: The secret value contained within an _authenticator_.

authenticator type
: A category of _authenticators_ with common characteristics, such as the types of _authentication factors_ they provide and the mechanisms by which they operate.

authenticity
: The property that data originated from its purported source.

authoritative source
: An entity that has access to or verified copies of accurate information from an _issuing source_ such that a _CSP_ has high confidence that the source can confirm the validity of the identity attributes or evidence supplied by an _applicant_ during _identity proofing_. An issuing source may also be an authoritative source. Often, authoritative sources are determined by a policy decision of the agency or CSP before they can be used in the identity proofing _validation_ phase.

authorize
: A decision to grant access, typically automated by evaluating a _subject_'s _attributes_.

authorized party
: In _federation_, the organization, person, or entity that is responsible for making decisions regarding the release of information within the _federation transaction_, most notably subscriber _attributes_. This is often the subscriber (when runtime decisions are used) or the party operating the _IdP_ (when _allowlists_ are used).

back-channel communication
: Communication between two systems that relies on a direct connection without using redirects through an intermediary such as a browser.

bearer assertion
: An _assertion_ that can be presented on its own as proof of the identity of the presenter.

~~~
\clearpage
~~~
{:latex-literal="true"}

biometric reference
: One or more stored _biometric samples_, templates, or models attributed to an individual and used as the object of biometric comparison in a database, such as a facial image stored digitally on a passport, fingerprint minutiae template on a National ID card or Gaussian Mixture Model for speaker recognition.

biometric sample
: An analog or digital representation of biometric characteristics prior to biometric feature extraction, such as a record that contains a fingerprint image.

biometrics
: Automated recognition of individuals based on their biological or behavioral characteristics. Biological characteristics include but are not limited to fingerprints, palm prints, facial features, iris and retina patterns, voiceprints, and vein patterns. Behavioral characteristics include but are not limited to keystrokes, angle of holding a smart phone, screen pressure, typing speed, mouse or mobile phone movements, and gyroscope position.

blocklist
: A documented list of specific elements that are blocked, per policy decision. This concept has historically been known as a _blacklist_.

challenge-response protocol
: An _authentication protocol_ in which the _verifier_ sends the _claimant_ a challenge (e.g., a random value or _nonce_) that the claimant combines with a secret (e.g., by hashing the challenge and a _shared secret_ together or by applying a _private-key_ operation to the challenge) to generate a response that is sent to the verifier. The verifier can independently verify the response generated by the claimant (e.g., by re-computing the hash of the challenge and the shared secret and comparing to the response or performing a public-key operation on the response) and establish that the claimant possesses and controls the secret.

claimant
: A _subject_ whose identity is to be verified using one or more _authentication protocols_.

claimed address
: The physical location asserted by a _subject_ where they can be reached. It includes the individual's residential street address and may also include their mailing address.

claimed identity
: An _applicant's_ declaration of unvalidated and unverified personal _attributes_.

compensating controls
: Alternative _controls_ to the normative controls for the assessed and selected xALs of an organization based on that organization's mission, risk tolerance, business processes, and _risk assessments_ and considerations for the privacy, _usability_, and _equity_ of the populations served by the _online service_.

controls  
: Policies, procedures, guidelines, practices, or organizational structures that manage security, privacy, and other risks.
See *supplemental controls* and *compensating controls*

core attributes
: The set of identity _attributes_ that the _CSP_ has determined and documented to be required for _identity proofing_.

credential
: An object or data structure that authoritatively binds an identity &mdash; via an _identifier_ &mdash; and (optionally) additional _attributes_, to at least one _authenticator_ possessed and controlled by a subscriber.

    A credential is issued, stored, and maintained by the _CSP_. Copies of information from the credential can be possessed by the subscriber, typically in the form of one or more digital certificates that are often contained in an authenticator along with their associated _private keys_.

credential service provider (CSP)
: A trusted entity whose functions include _identity proofing_ _applicants_ to the identity service and registering _authenticators_ to _subscriber accounts_. A CSP may be an independent third party.

credible source
: An entity that can provide or validate the accuracy of _identity evidence_ and _attribute_ information. A credible source has access to attribute information that was validated through an _identity proofing_ process or that can be traced to an _authoritative source_, or it maintains identity attribute information obtained from multiple sources that is checked for data correlation for accuracy, consistency, and currency.

cross-site request forgery (CSRF)
: An attack in which a subscriber who is currently _authenticated_ to an _RP_ and connected through a secure session browses an attacker's website, causing the subscriber to unknowingly invoke unwanted actions at the RP.

    For example, if a bank website is vulnerable to a CSRF attack, it may be possible for a subscriber to unintentionally _authorize_ a large money transfer by clicking on a malicious link in an email while a connection to the bank is open in another browser window.

cross-site scripting (XSS)
: A vulnerability that allows attackers to inject malicious code into an otherwise benign website. These scripts acquire the permissions of scripts generated by the target website to compromise the confidentiality and integrity of data transfers between the website and clients. Websites are vulnerable if they display user-supplied data from requests or forms without sanitizing the data so that it is not executable.

cryptographic authenticator
: An _authenticator_ that proves possession of an _authentication secret_ through direct communication with a _verifier_ through a cryptographic _authentication protocol_.

cryptographic key
: A value used to control cryptographic operations, such as decryption, encryption, signature generation, or signature _verification_. For the purposes of these guidelines, key requirements shall meet the minimum requirements stated in Table 2 of [[SP800-57Part1]](references.md#ref-SP800-57P1). See _asymmetric keys_ or _symmetric keys_.

cryptographic module
: A set of hardware, software, or firmware that implements approved security functions including cryptographic algorithms and key generation.

data integrity
: The property that data has not been altered by an unauthorized entity.

derived attribute value
: A statement that asserts a limited identity _attribute_ of a subscriber without containing the attribute value from which it is derived, independent of format. For example, instead of requesting the attribute "birthday," a derived value could be "older than 18". Instead of requesting the attribute for "physical address," a derived value could be "currently residing in this district." Previous versions of these guidelines referred to this construct as an "attribute reference."

digital authentication
: The process of establishing confidence in user identities that are digitally presented to a system. In previous editions of SP 800-63, this was referred to as electronic authentication.

digital identity
: An _attribute_ or set of attributes that uniquely describes a _subject_ within a given context.

Digital Identity Acceptance Statement (DIAS)
: Documents the results of the _digital identity_ _risk management_ process. This includes the impact assessment, initial assurance level selection, and _tailoring_ process.

digital signature
: An _asymmetric key_ operation in which the _private key_ is used to digitally sign data and the _public key_ is used to verify the signature. Digital signatures provide _authenticity_ protection, integrity protection, and _non-repudiation_ support but not confidentiality or _replay attack_ protection.

digital transaction
: A discrete digital event between a user and a system that supports a business or programmatic purpose.

disassociability
: Enabling the _processing_ of PII or events without association to individuals or devices beyond the operational requirements of the system. [[NISTIR8062]](references.md#ref-NISTIR8062)

electronic authentication (e-authentication)
: See _digital authentication_.

endpoint
: Any device that is used to access a _digital identity_ on a _network_, such as laptops, desktops, mobile phones, tablets, servers, Internet of Things devices, and virtual environments.

enrollment
: The process through which a _CSP_/_IdP_ provides a successfully identity-proofed _applicant_ with a _subscriber account_ and binds _authenticators_ to grant persistent access.

entropy
: The amount of uncertainty that an attacker faces to determine the value of a secret. Entropy is usually stated in bits. A value with *n* bits of entropy has the same degree of uncertainty as a uniformly distributed *n*-bit random value.

equity
: The consistent and systematic fair, just, and impartial treatment of all individuals, including individuals who belong to underserved communities that have been denied such treatment, such as Black, Latino, and Indigenous and Native American persons, Asian Americans and Pacific Islanders, and other persons of color; members of religious minorities; lesbian, gay, bisexual, transgender, and queer (LGBTQ+) persons; persons with disabilities; persons who live in rural areas; and persons otherwise adversely affected by persistent poverty or inequality. [[EO13985]](references.md#ref-EO13985)

factor
: See *authentication factor*

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

identity evidence
: Information or documentation that supports the real-world existence of the _claimed identity_. Identity evidence may be physical (e.g., a driver's license) or digital (e.g., a mobile driver's license or digital _assertion_). Evidence must support both _validation_ (i.e., confirming _authenticity_ and accuracy) and _verification_ (i.e., confirming that the _applicant_ is the true owner of the evidence).

identity proofing
: The processes used to collect, validate, and verify information about a _subject_ to establish assurance in the subject's _claimed identity_.

identity provider (IdP)
: The party in a _federation transaction_ that creates an _assertion_ for the subscriber and transmits the assertion to the _RP_.

identity resolution
: The process of collecting information about an _applicant_ to uniquely distinguish an individual within the context of the population that the _CSP_ serves.   

identity verification
: See *verification*

injection attack
: An attack in which an attacker supplies untrusted input to a program. In the context of federation, the attacker presents an untrusted _assertion_ or _assertion reference_ to the _RP_ in order to create an _authenticated_ _session_ with the RP.

issuing source
: An authority responsible for the generation of data, digital evidence (i.e., _assertions_), or physical documents that can be used as _identity evidence_.

knowledge-based verification (KBV)
: A process of validating knowledge of personal or private information associated with an individual for the purpose of verifying the _claimed identity_ of an _applicant_. KBV does not include collecting personal _attributes_ for the purposes of _identity resolution_.

legal person
: An individual, organization, or company with legal rights.

login
: Establishment of an _authenticated_ _session_ between a person and a system. Also known as _"sign in"_, _"log on"_, and _"sign on."_

manageability
: Providing the capability for the granular administration of _personally identifiable information_, including alteration, deletion, and selective disclosure. [[NISTIR8062]](references.md#ref-NISTIR8062)

memorized secret
: See _password_.

message authentication code (MAC)
: A cryptographic checksum on data that uses a _symmetric key_ to detect both accidental and intentional modifications of the data. MACs provide _authenticity_ and integrity protection, but not _non-repudiation_ protection.

mobile code
: Executable code that is normally transferred from its source to another computer system for execution. This transfer is often through the _network_ (e.g., JavaScript embedded in a web page) but may transfer through physical media as well.

multi-factor authentication (MFA)
: An authentication system that requires more than one distinct type of _authentication factor_ for successful authentication. MFA can be performed using a _multi-factor authenticator_ or by combining _single-factor_ authenticators that provide different types of factors.

multi-factor authenticator
: An _authenticator_ that provides more than one distinct _authentication factor_, such as a cryptographic authentication device with an integrated biometric sensor that is required to activate the device.

natural person
: A real-life human being, not synthetic or artificial.

network
: An open communications medium, typically the Internet, used to transport messages between the _claimant_ and other parties. Unless otherwise stated, no assumptions are made about the network's security; it is assumed to be open and subject to active (e.g., impersonation, _session_ hijacking) and passive (e.g., eavesdropping) attacks at any point between the parties (e.g., claimant, _verifier_, _CSP_, _RP_).

nonce
: A value used in security protocols that is never repeated with the same key. For example, nonces used as challenges in _challenge-response authentication protocols_ must not be repeated until authentication keys are changed. Otherwise, there is a possibility of a _replay attack_. Using a nonce as a challenge is a different requirement than a random challenge, because a nonce is not necessarily unpredictable.

non-repudiation
: The capability to protect against an individual falsely denying having performed a particular transaction.

offline attack
: An attack in which the attacker obtains some data (typically by eavesdropping on an authentication transaction or by penetrating a system and stealing security files) that the attacker is able to analyze in a system of their own choosing.

one-to-one (1:1) comparison
: The process in which a _biometric sample_ from an individual is compared to a _biometric reference_ to produce a comparison score.

online attack
: An attack against an _authentication protocol_ in which the attacker either assumes the role of a _claimant_ with a genuine _verifier_ or actively alters the authentication channel.

online guessing attack
: An attack in which an attacker performs repeated logon trials by guessing possible values of the _authenticator_ output.

online service
: A service that is accessed remotely via a _network_, typically the internet.

pairwise pseudonymous identifier
: A _pseudonymous identifier_ generated by an IdP for use at a specific _RP_.

passphrase
: A _password_ that consists of a sequence of words or other text that a _claimant_ uses to _authenticate_ their identity. A passphrase is similar to a password in usage but is generally longer for added security.

password
: A type of _authenticator_ consisting of a character string that is intended to be memorized or memorable by the subscriber to permit the _claimant_ to demonstrate *something they know* as part of an authentication process. Passwords are referred to as _memorized secrets_ in the initial release of SP 800-63B.

personal identification number (PIN)
: A _password_ that typically consists of only decimal digits.

personal information
: See *personally identifiable information*.

personally identifiable information (PII)
: Information that can be used to distinguish or trace an individual's identity, either alone or when combined with other information that is linked or linkable to a specific individual. [[A-130]](references.md#ref-A-130)

personally identifiable information processing
: An operation or set of operations performed upon _personally identifiable information_ that can include the collection, retention, logging, generation, transformation, use, disclosure, transfer, or disposal of personally identifiable information.

pharming
: An attack in which an attacker corrupts an infrastructure service such as DNS (e.g., Domain Name System [DNS]) and causes the subscriber to be misdirected to a forged _verifier_/_RP_, which could cause the subscriber to reveal sensitive information, download harmful software, or contribute to a fraudulent act.

phishing
: An attack in which the subscriber is lured (usually through an email) to interact with a counterfeit _verifier_/_RP_ and tricked into revealing information that can be used to masquerade as that subscriber to the real verifier/RP.

phishing resistance
: The ability of the _authentication protocol_ to prevent the disclosure of _authentication secrets_ and valid _authenticator_ outputs to an impostor _verifier_ without reliance on the vigilance of the _claimant_.

physical authenticator
: An _authenticator_ that the _claimant_ proves possession of as part of an authentication process.

possession and control of an authenticator
: The ability to activate and use the _authenticator_ in an _authentication protocol_.

practice statement
: A formal statement of the practices followed by the parties to an authentication process (e.g., _CSP_ or _verifier_). It usually describes the parties' policies and practices and can become legally binding.

predictability
: Enabling reliable assumptions by individuals, owners, and operators about PII and its _processing_ by an information system. [[NISTIR8062]](references.md#ref-NISTIR8062)

private key
: In _asymmetric key_ cryptography, the private key (i.e., a secret key) is a mathematical key used to create _digital signatures_ and, depending on the algorithm, decrypt messages or files that are encrypted with the corresponding _public key_. In _symmetric key_ cryptography, the same private key is used for both encryption and decryption.

processing
: Operation or set of operations performed upon PII that can include, but is not limited to, the collection, retention, logging, generation, transformation, use, disclosure, transfer, and disposal of PII. [[NISTIR8062]](references.md#ref-NISTIR8062)

presentation attack
: Presentation to the biometric data capture subsystem with the goal of interfering with the operation of the biometric system.

presentation attack detection (PAD)
: Automated determination of a _presentation attack_. A subset of presentation attack determination methods, referred to as *liveness detection*, involves the measurement and analysis of anatomical characteristics or voluntary or involuntary reactions, to determine if a _biometric sample_ is being captured from a living _subject_ that is present at the point of capture.

process assistant
: An individual who provides support for the proofing process but does not support decision-making or risk-based evaluation (e.g., translation, transcription, or accessibility support).

proofing agent
: An agent of the _CSP_ who is trained to attend _identity proofing_ _sessions_ and can make limited risk-based decisions – such as physically inspecting _identity evidence_ and making physical comparisons of the _applicant_ to identity evidence.

Privacy Impact Assessment (PIA)
: A method of analyzing how _personally identifiable information_ (PII) is collected, used, shared, and maintained. PIAs are used to identify and mitigate privacy risks throughout the development lifecycle of a program or system. They also help ensure that handling information conforms to legal, regulatory, and policy requirements regarding privacy.

protected session
: A _session_ in which messages between two participants are encrypted and integrity is protected using a set of _shared secrets_ called "session keys."

    A protected session is said to be _authenticated_ if &mdash; during the session &mdash; one participant proves possession of one or more _authenticators_ in addition to the session keys, and if the other party can verify the identity associated with the authenticators. If both participants are authenticated, the protected session is said to be *mutually authenticated*.

Provisioning API
: A protected API that allows an _RP_ to access identity _attributes_ for multiple subscribers for the purposes of provisioning and managing RP _subscriber accounts_.

pseudonym
: A name other than a legal name.

pseudonymity
: The use of a _pseudonym_ to identify a _subject_.

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

registration
: See _enrollment_.

relying party (RP)
: An entity that relies upon a _verifier_'s _assertion_ of a subscriber's identity, typically to process a transaction or grant access to information or a system.

remote
: A process or transaction that is conducted through connected devices over a _network_, rather than in person.

replay attack
: An attack in which the attacker is able to replay previously captured messages (between a legitimate _claimant_ and a _verifier_) to masquerade as that claimant to the verifier or vice versa.

replay resistance
: The property of an authentication process to resist _replay attacks_, typically by the use of an _authenticator_ output that is valid only for a specific authentication.

resolution
: See *identity resolution*.

restricted
: An _authenticator_ type, class, or instantiation that has additional risk of false acceptance associated with its use and is therefore subject to additional requirements.

risk assessment
: The process of identifying, estimating, and prioritizing risks to organizational operations (i.e., mission, functions, image, or reputation), organizational assets, individuals, and other organizations that result from the operation of a system. A risk assessment is part of _risk management_, incorporates threat and vulnerability analyses, and considers mitigations provided by security _controls_ that are planned or in-place. It is synonymous with "risk analysis."

risk management
: The program and supporting processes that manage information security risk to organizational operations (including mission, functions, image, reputation), organizational assets, individuals, and other organizations and includes (i) establishing the context for risk-related activities, (ii) assessing risk, (iii) responding to risk once determined, and (iv) monitoring risk over time.

RP subscriber account
: An account established and managed by the _RP_ in a federated system based on the RP's view of the _subscriber account_ from the _IdP_. An RP subscriber account is associated with one or more _federated identifiers_ and allows the subscriber to access the account through a _federation transaction_ with the IdP.

salt
: A non-secret value used in a cryptographic process, usually to ensure that the results of computations for one instance cannot be reused by an attacker.

Secure Sockets Layer (SSL)
: See *Transport Layer Security (TLS)*.

security domain
: A set of systems under a common administrative and access control.

Senior Agency Official for Privacy (SAOP)
: Person responsible for ensuring that an agency complies with privacy requirements and manages privacy risks. The SAOP is also responsible for ensuring that the agency considers the privacy impacts of all agency actions and policies that involve PII.

session
: A persistent interaction between a subscriber and an _endpoint_, either an _RP_ or a _CSP_. A session begins with an authentication event and ends with a session termination event. A session is bound by the use of a session secret that the subscriber's software (e.g., a browser, application, or OS) can present to the RP to prove association of the session with the authentication event.

session hijack attack
: An attack in which the attacker is able to insert themselves between a _claimant_ and a _verifier_ subsequent to a successful authentication exchange between the latter two parties. The attacker is able to pose as a subscriber to the verifier or vice versa to control _session_ data exchange. Sessions between the claimant and the _RP_ can be similarly compromised.

shared secret
: A secret used in authentication that is known to the subscriber and the verifier.

side-channel attack
: An attack enabled by the leakage of information from a physical cryptosystem. Characteristics that could be exploited in a side-channel attack include timing, power consumption, and electromagnetic and acoustic emissions.

single-factor
: A characteristic of an authentication system or an _authenticator_ that requires only one _authentication factor_ (i.e., something you know, something you have, or something you are) for successful authentication.

single sign-on (SSO)
: An authentication process by which one account and its _authenticators_ are used to access multiple applications in a seamless manner, generally implemented with a _federation protocol_.

social engineering
: The act of deceiving an individual into revealing sensitive information, obtaining unauthorized access, or committing fraud by associating with the individual to gain confidence and trust.

subject
: A person, organization, device, hardware, _network_, software, or service. In these guidelines, a subject is a _natural person_.

subscriber
: An individual enrolled in the _CSP_ identity service.

subscriber account
: An account established by the _CSP_ containing information and _authenticators_ registered for each subscriber enrolled in the CSP identity service.

supplemental controls
: _Controls_ that may be added, in addition to those specified in the organization's tailored assurance level, in order to address specific threats or attacks.

symmetric key
: A _cryptographic key_ used to perform both the cryptographic operation and its inverse. (e.g., to encrypt and decrypt or create a _message authentication code_ and to verify the code).

sync fabric
: Any on-premises, cloud-based, or hybrid service used to store, transmit, or manage authentication keys generated by syncable _authenticators_ that are not local to the user's device.

syncable authenticators
: Software or hardware cryptographic _authenticators_ that allow authentication keys to be cloned and exported to other storage to sync those keys to other authenticators (i.e., devices).

synthetic identity fraud
:  The use of a combination of _personally identifiable information_ (PII) to fabricate a person or entity in order to commit a dishonest act for personal or financial gain.

system of record (SOR)
: An SOR is a collection of records that contain information about individuals and are under the control of an agency. The records can be retrieved by the individual's name or by an identifying number, symbol, or other _identifier_.

System of Record Notice (SORN)
: A notice that federal agencies publish in the Federal Register to describe their systems of records.

tailoring
: The process by which xALs and specified _controls_ are modified by: considerations for the impacts on privacy, _usability_, and _equity_ on the user population, identifying and designating common controls, applying scoping considerations on the applicability and implementation of specified controls, selecting any _compensating controls_, assigning specific values to organization-defined security control parameters, supplementing xAL controls with additional controls or control enhancements, and providing additional specification information for control implementation.

token
: See _authenticator_.

transaction
: See _digital transaction_

Transport Layer Security (TLS)
: An authentication and security protocol widely implemented in browsers and web servers. TLS is defined by [[RFC5246]](references.md#ref-RFC5246). TLS is similar to the older SSL protocol, and TLS 1.0 is effectively SSL version 3.1. SP 800-52, Guidelines for the Selection and Use of Transport Layer Security (TLS) Implementations [[SP800-52]](references.md#ref-SP800-52), specifies how TLS is to be used in government applications.

trust agreement
: A set of conditions under which a _CSP_, _IdP_, and _RP_ are allowed to participate in a _federation transaction_ for the purposes of establishing an authentication _session_ between the subscriber and the RP.

trust anchor
: A public or _symmetric key_ that is trusted because it is built directly into hardware or software or securely provisioned via out-of-band means rather than because it is vouched for by another trusted entity (e.g., in a _public key_ certificate). A trust anchor may have name or policy constraints that limit its scope.

trusted referee
:  An agent of the _CSP_ who is trained to make risk-based decisions regarding an _applicant's_ _identity proofing_ case when that applicant is unable to meet the expected requirements of a defined IAL proofing process.

usability
: The extent to which a product can be used by specified users to achieve specified goals with effectiveness, efficiency, and satisfaction in a specified context of use. [[ISO/IEC9241-11]](references.md#ref-ISOIEC9241)

validation
: The process or act of checking and confirming that the evidence and _attributes_ supplied by an _applicant_ are authentic, accurate and associated with a real-life identity. Specifically, evidence validation is the process or act of checking that the presented evidence is authentic, current, and issued from an acceptable source. See also _attribute validation_.

verification
: The process or act of confirming that the _applicant_ undergoing _identity proofing_ holds the claimed real-life identity represented by the validated identity _attributes_ and associated evidence. Synonymous with "identity verification."

verifier
: An entity that verifies the _claimant's_ identity by verifying the claimant's possession and control of one or more _authenticators_ using an _authentication protocol_. To do this, the verifier needs to confirm the binding of the authenticators with the _subscriber account_ and check that the subscriber account is active.

verifier impersonation
: See _phishing_.

zeroize
: Overwrite a memory location with data that consists entirely of bits with the value zero so that the data is destroyed and unrecoverable. This is often contrasted with deletion methods that merely destroy references to data within a file system rather than the data itself.

zero-knowledge password protocol
: A password-based _authentication protocol_ that allows a _claimant_ to _authenticate_ to a _verifier_ without revealing the _password_ to the verifier. Examples of such protocols are EKE, SPEKE and SRP.
