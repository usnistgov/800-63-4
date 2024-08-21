---
layout: default
title: Glossary
navOrder: 13
navTitle: Glossary
permalink: /sp800-63a/glossary/
anchor: def-and-acr
section: C
---

# Glossary {#def-and-acr}

*This section is informative.*

A wide variety of terms are used in the realm of digital identity. While many definitions are consistent with earlier versions of SP 800-63, some have changed in this revision. Many of these terms lack a single, consistent definition, warranting careful attention to how the terms are defined here.

applicant
: A _subject_ undergoing the processes of _identity proofing_ and _enrollment_.

applicant reference
: A representative of the _applicant_ who can vouch for the identity of the applicant, specific _attributes_ related to the applicant, or conditions relative to the context of the individual (e.g., emergency status, homelessness).

approved cryptography
: An encryption algorithm, _hash function_, random bit generator, or similar technique that is _Federal Information Processing Standard_ (FIPS)-approved or NIST-recommended. Approved algorithms and techniques are either specified or adopted in a FIPS or NIST recommendation.

assertion
: A statement from an _IdP_ to an _RP_ that contains information about an authentication event for a subscriber. Assertions can also contain identity _attributes_ for the subscriber.

attribute
: A quality or characteristic ascribed to someone or something. An identity attribute is an attribute about the identity of a subscriber.

attribute validation
: The process or act of confirming that a set of attributes are accurate and associated with a real-life identity. See *validation*.

authenticate
: See _authentication_.

authentication
: The process by which a _claimant_ proves possession and control of one or more _authenticators_ bound to a _subscriber account_ to demonstrate that they are the subscriber associated with that account.

Authentication Assurance Level (AAL)
: A category that describes the strength of the authentication process.

authenticator
: Something that the subscriber possesses and controls (e.g., a _cryptographic module_ or _password_) and that is used to _authenticate_ a _claimant's_ identity. See _authenticator type_ and _multi-factor authenticator_.

authenticity
: The property that data originated from its purported source.

authoritative source
: An entity that has access to or verified copies of accurate information from an _issuing source_ such that a _CSP_ has high confidence that the source can confirm the validity of the identity attributes or evidence supplied by an _applicant_ during _identity proofing_. An issuing source may also be an authoritative source. Often, authoritative sources are determined by a policy decision of the agency or CSP before they can be used in the identity proofing _validation_ phase.

authorize
: A decision to grant access, typically automated by evaluating a _subject_'s _attributes_.

biometric reference
: One or more stored _biometric samples_, templates, or models attributed to an individual and used as the object of biometric comparison in a database, such as a facial image stored digitally on a passport, fingerprint minutiae template on a National ID card or Gaussian Mixture Model for speaker recognition.

biometric sample
: An analog or digital representation of biometric characteristics prior to biometric feature extraction, such as a record that contains a fingerprint image.

biometrics
: Automated recognition of individuals based on their biological or behavioral characteristics. Biological characteristics include but are not limited to fingerprints, palm prints, facial features, iris and retina patterns, voiceprints, and vein patterns. Behavioral characteristics include but are not limited to keystrokes, angle of holding a smart phone, screen pressure, typing speed, mouse or mobile phone movements, and gyroscope position.

claimant
: A _subject_ whose identity is to be verified using one or more _authentication protocols_.

claimed address
: The physical location asserted by a _subject_ where they can be reached. It includes the individual's residential street address and may also include their mailing address.

claimed identity
: An _applicant's_ declaration of unvalidated and unverified personal _attributes_.

core attributes
: The set of identity _attributes_ that the _CSP_ has determined and documented to be required for _identity proofing_.

credential service provider (CSP)
: A trusted entity whose functions include _identity proofing_ _applicants_ to the identity service and registering _authenticators_ to _subscriber accounts_. A CSP may be an independent third party.

credible source
: An entity that can provide or validate the accuracy of _identity evidence_ and _attribute_ information. A credible source has access to attribute information that was validated through an _identity proofing_ process or that can be traced to an _authoritative source_, or it maintains identity attribute information obtained from multiple sources that is checked for data correlation for accuracy, consistency, and currency.

digital identity
: An _attribute_ or set of attributes that uniquely describes a _subject_ within a given context.

digital signature
: An _asymmetric key_ operation in which the _private key_ is used to digitally sign data and the _public key_ is used to verify the signature. Digital signatures provide _authenticity_ protection, integrity protection, and _non-repudiation_ support but not confidentiality or _replay attack_ protection.

disassociability
: Enabling the _processing_ of PII or events without association to individuals or devices beyond the operational requirements of the system. [[NISTIR8062]](references.md#ref-NISTIR8062)

electronic authentication (e-authentication)
: See _digital authentication_.

enrollment
: The process through which a _CSP_/_IdP_ provides a successfully identity-proofed _applicant_ with a _subscriber account_ and binds _authenticators_ to grant persistent access.

entropy
: The amount of uncertainty that an attacker faces to determine the value of a secret. Entropy is usually stated in bits. A value with *n* bits of entropy has the same degree of uncertainty as a uniformly distributed *n*-bit random value.

equity
: The consistent and systematic fair, just, and impartial treatment of all individuals, including individuals who belong to underserved communities that have been denied such treatment, such as Black, Latino, and Indigenous and Native American persons, Asian Americans and Pacific Islanders, and other persons of color; members of religious minorities; lesbian, gay, bisexual, transgender, and queer (LGBTQ+) persons; persons with disabilities; persons who live in rural areas; and persons otherwise adversely affected by persistent poverty or inequality. [[EO13985]](references.md#ref-EO13985)

Federal Information Processing Standard (FIPS)
: Under the Information Technology Management Reform Act (Public Law 104-106), the Secretary of Commerce approves the standards and guidelines that the National Institute of Standards and Technology (NIST) develops for federal computer systems. NIST issues these standards and guidelines as Federal Information Processing Standards (FIPS) for government-wide use. NIST develops FIPS when there are compelling federal government requirements, such as for security and interoperability, and there are no acceptable industry standards or solutions. See background information for more details.

    FIPS documents are available online on the FIPS home page: <https://www.nist.gov/itl/fips.cfm>

federation
: A process that allows for the conveyance of identity and authentication information across a set of _networked_ systems.

Federation Assurance Level (FAL)
: A category that describes the process used in a _federation transaction_ to communicate authentication events and subscriber _attributes_ to an _RP_.

hash function
: A function that maps a bit string of arbitrary length to a fixed-length bit string. Approved hash functions satisfy the following properties:

    1. One-way &mdash; It is computationally infeasible to find any input that maps to any pre-specified output.

    2. Collision-resistant &mdash; It is computationally infeasible to find any two distinct inputs that map to the same output.

identifier
: A data object that is associated with a single, unique entity (e.g., individual, device, or session) within a given context and is never assigned to any other entity within that context.

identity
: See _digital identity_

Identity Assurance Level (IAL)
: A category that conveys the degree of confidence that the _subject_'s _claimed identity_ is their real identity.

identity evidence
: Information or documentation that supports the real-world existence of the _claimed identity_. Identity evidence may be physical (e.g., a driver's license) or digital (e.g., a mobile driver's license or digital _assertion_). Evidence must support both _validation_ (i.e., confirming _authenticity_ and accuracy) and _verification_ (i.e., confirming that the _applicant_ is the true owner of the evidence).

identity proofing
: The processes used to collect, validate, and verify information about a _subject_ in order to establish assurance in the subject's _claimed identity_.

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

manageability
: Providing the capability for the granular administration of _personally identifiable information_, including alteration, deletion, and selective disclosure. [[NISTIR8062]](references.md#ref-NISTIR8062)

natural person
: A real-life human being, not synthetic or artificial.

network
: An open communications medium, typically the Internet, used to transport messages between the _claimant_ and other parties. Unless otherwise stated, no assumptions are made about the network's security; it is assumed to be open and subject to active (e.g., impersonation, _session_ hijacking) and passive (e.g., eavesdropping) attacks at any point between the parties (e.g., claimant, _verifier_, _CSP_, _RP_).

non-repudiation
: The capability to protect against an individual falsely denying having performed a particular transaction.

offline attack
: An attack in which the attacker obtains some data (typically by eavesdropping on an authentication transaction or by penetrating a system and stealing security files) that the attacker is able to analyze in a system of their own choosing.

one-to-one (1:1) comparison
: The process in which a _biometric sample_ from an individual is compared to a _biometric reference_ to produce a comparison score.

online attack
: An attack against an _authentication protocol_ in which the attacker either assumes the role of a _claimant_ with a genuine _verifier_ or actively alters the authentication channel.

online service
: A service that is accessed remotely via a _network_, typically the internet.

personal information
: See *personally identifiable information*.

personally identifiable information (PII)
: Information that can be used to distinguish or trace an individual's identity, either alone or when combined with other information that is linked or linkable to a specific individual. [[A-130]](references.md#ref-A-130)

personally identifiable information processing
: An operation or set of operations performed upon _personally identifiable information_ that can include the collection, retention, logging, generation, transformation, use, disclosure, transfer, or disposal of personally identifiable information.

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

registration
: See _enrollment_.

relying party (RP)
: An entity that relies upon a _verifier_'s _assertion_ of a subscriber's identity, typically to process a transaction or grant access to information or a system.

remote
: A process or transaction that is conducted through connected devices over a _network_, rather than in person.

resolution
: See *identity resolution*.

risk assessment
: The process of identifying, estimating, and prioritizing risks to organizational operations (i.e., mission, functions, image, or reputation), organizational assets, individuals, and other organizations that result from the operation of a system. A risk assessment is part of _risk management_, incorporates threat and vulnerability analyses, and considers mitigations provided by security _controls_ that are planned or in-place. It is synonymous with "risk analysis."

risk management
: The program and supporting processes that manage information security risk to organizational operations (including mission, functions, image, reputation), organizational assets, individuals, and other organizations and includes (i) establishing the context for risk-related activities, (ii) assessing risk, (iii) responding to risk once determined, and (iv) monitoring risk over time.

RP subscriber account
: An account established and managed by the _RP_ in a federated system based on the RP's view of the _subscriber account_ from the _IdP_. An RP subscriber account is associated with one or more _federated identifiers_ and allows the subscriber to access the account through a _federation transaction_ with the IdP.

Senior Agency Official for Privacy (SAOP)
: Person responsible for ensuring that an agency complies with privacy requirements and manages privacy risks. The SAOP is also responsible for ensuring that the agency considers the privacy impacts of all agency actions and policies that involve PII.

~~~
\clearpage
~~~
{:latex-literal="true"}

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

synthetic identity fraud
:  The use of a combination of _personally identifiable information_ (PII) to fabricate a person or entity in order to commit a dishonest act for personal or financial gain.

system of record (SOR)
: An SOR is a collection of records that contain information about individuals and are under the control of an agency. The records can be retrieved by the individual's name or by an identifying number, symbol, or other _identifier_.

System of Record Notice (SORN)
: A notice that federal agencies publish in the Federal Register to describe their systems of records.

transaction
: See _digital transaction_

trust agreement
: A set of conditions under which a _CSP_, _IdP_, and _RP_ are allowed to participate in a _federation transaction_ for the purposes of establishing an authentication _session_ between the subscriber and the RP.

trusted referee
:  An agent of the _CSP_ who is trained to make risk-based decisions regarding an _applicant's_ _identity proofing_ case when that applicant is unable to meet the expected requirements of a defined IAL proofing process.

usability
: The extent to which a product can be used by specified users to achieve specified goals with effectiveness, efficiency, and satisfaction in a specified context of use. [[ISO/IEC9241-11]](references.md#ref-ISOIEC9241)

validation
: The process or act of checking and confirming that the evidence and _attributes_ supplied by an _applicant_ are authentic, accurate and associated with a real-life identity. Specifically, evidence validation is the process or act of checking that the presented evidence is authentic, current, and issued from an acceptable source. See also _attribute validation_.

verification
: The process or act of confirming that the _applicant_ undergoing _identity proofing_ holds the claimed real-life identity represented by the validated identity _attributes_ and associated evidence. Synonymous with "identity verification."

verifier
: An entity that verifies the _claimant's_ identity by verifying the claimant's possession and control of one or more _authenticators_ using an _authentication protocol_. To do this, the verifier needs to confirm the binding of the authenticators with the _subscriber account_ and check that the subscriber account is
