---
layout: default.ja
title: Identity Assurance Level Requirements
navOrder: 5
navTitle: IAL
permalink: /sp800-63a/ial/
anchor: ial-section
section: 5
---

# Identity Assurance Level Requirements {#ial-section}

_This section is normative._

This section provides requirements for CSPs that operate identity proofing and enrollment services, including requirements for identity proofing at each of the IALs. This section also includes additional requirements for Federal Agencies regardless of whether they operate their own identity service or use an external CSP.

## General Requirements {#genProofReqs}

The requirements in this section apply to all CSPs performing identity proofing at any IAL.

### Identity Service Documentation and Records {#DocRecReqs}

The CSP **SHALL** conduct its operations according to a practice statement that details all identity proofing processes as they are implemented to achieve the defined IAL. The practice statement **SHALL** include, at a minimum:

1. A complete service description including the particular steps the CSP follows to identity proof applicants at each offered assurance level;
2. Types of identity evidence the CSP accepts to meet the evidence strength requirements;
3. If applicable, alternative ways for an individual applicant who does not possess the required identity evidence to complete the identity proofing process[^alternatives];
4. The attributes the CSP considers to be core attributes. Core attributes include the minimum set of attributes the CSP needs to perform identity resolution as well as any additional attributes the CSP collects and validates for the purposes of identity proofing, fraud mitigation, complying with laws or legal process, or conveying to relying parties (RPs) through attribute assertions;
5. The CSP's policy and process for dealing with identity proofing errors;
6. The CSP's policy and process for identifying and communicating suspected or confirmed fraudulent accounts to RPs and affected individuals;
7. The CSP's policy for managing and communicating service changes (e.g., change in data sources, integrated vendors, or biometric algorithms) to RPs;
8. The CSP's policy for conducting privacy risk assessments, including the timing of its periodic reviews and specific conditions that will trigger an updated privacy risk assessment (see [Section 5.1.2](sec5_ial.md#PrivacyReqs));
9. The CSP's policy for conducting assessments to determine potential equity impacts, including the timing of its periodic reviews and any specific conditions that will trigger an out-of-cycle review (see [Section 5.1.3](sec5_ial.md#EquityReqs)); and


#### Ceasing Operations


1. The CSP **SHALL** document its policy and plan for when it ceases its operations.
2. This plan **SHALL** include whether the CSP's identity service is subject to retention requirements and how it will protect any sensitive data (including identity attributes, and information contained in subscriber accounts and audit logs) during the period of retention.
3. At the end of any required retention period, the CSP **SHALL** be responsible for fully disposing of or destroying all sensitive data.

#### Fraud Mitigation Measures

1. The CSP **SHOULD** obtain additional confidence in identity proofing using fraud mitigation measures (e.g., examining the device characteristics of the applicant, evaluating behavioral characteristics, and checking vital statistic repositories such as the Death Master File ([[DMF]](sec11_references.md#ref-dmf)).
2. In the event the CSP uses fraud mitigation measures, the CSP **SHALL** conduct a privacy risk assessment for these mitigation measures.
3. Such assessments **SHALL** include any privacy risk mitigations (e.g., risk acceptance or transfer, limited retention, use limitations, notice) or other technological mitigations (e.g., cryptography), and be documented per these guidelines.


[^alternatives]: Options include using a Trusted Referee, with or without an Applicant Representative; see [Sec. 5.1.9](../ial/#TRs-ARs) for supplemental identity evidence types.

### General Privacy Requirements {#PrivacyReqs}

The following privacy requirements apply to all CSPs providing identity services at any IAL.

#### Privacy Risk Assessment

1. The CSP **SHALL** conduct and document a privacy risk assessment for the processes used for identity proofing and enrollment.[^privacyframework]  At a minimum, the privacy risk assessment **SHALL** assess the risks associated with:

	1. Any processing of PII for the purpose of identity proofing and enrollment, including identity attributes, biometrics, images, video, scans, or copies of identity evidence;
	2. Any additional steps the CSP takes to verify the identity of an applicant beyond the mandatory requirements specified herein;
	3. Any processing of PII for purposes outside the scope of identity proofing and enrollment except to comply with law or legal process;
	4. The retention schedule for identity records and PII; and,
	5. Any PII that is processed by a third party service on behalf of the CSP.
	{:.letter-list}
2. Based on the results of its privacy risk assessment, the CSP **SHALL** document the measures it takes to maintain the disassociability, predictability, manageability, confidentiality, integrity, and availability of the PII it processes. In determining such measures, the CSP **SHALL** consult the *NIST Privacy Framework* [[NIST-Privacy]](sec11_references.md#ref-NIST-Privacy) and NIST Special Publication [[SP800-53]](sec11_references.md#ref-SP800-53).
3. The CSP **SHALL** re-assess privacy risks and update its privacy risk assessment any time it makes changes to its identity service that affect the processing of PII.
4. The CSP **SHALL** review its privacy risk assessment periodically, as documented in its practice statement, to ensure it accurately reflects the current risks associated with the processing of PII.
5. The CSP **SHALL** make a summary of its privacy risk assessment available to any organizations that use its services. The summary **SHALL** be in sufficient detail to enable such organizations to do due dilligence.

#### Additional Privacy Protective Measures

1. Processing of PII **SHALL** be limited to the minimum necessary to validate the existence of the claimed identity, associate the claimed identity with the applicant, and provide RPs with attributes they may use to make authorization decisions.
2. The CSP **MAY** collect the Social Security Number (SSN) as an attribute when necessary for identity resolution, in accordance with the privacy requirements in [Sec. 5.1.2](sec5_ial.md#PrivacyReqs). Additionally, CSPs **SHALL** implement privacy protective techniques (e.g., transmitting and accepting derived attribute values rather than full attribute values themselves) to limit the proliferation and retention of SSN data. Knowledge of the SSN **SHALL NOT** be considered identity evidence.
3. At the time of collection, the CSP **SHALL** provide explicit notice to the applicant regarding the purpose for collecting attributes necessary for identity proofing, including whether such attributes are voluntary or mandatory to complete the identity proofing process, the specific attributes and other sensitive data that the CSP intends to store in the applicant's subsequent subscriber account, the consequences for not providing the attributes, and the details of any records retention requirement if one is in place.
4. The CSP **SHALL** provide mechanisms for redress of applicant complaints and for problems arising from the identity proofing. These mechanisms **SHALL** be easy for applicants to find and use. The CSP **SHALL** assess the mechanisms for their efficacy in achieving resolution of complaints or problems.

[^privacyframework]: For more information about privacy risk assessments, refer to the NIST Privacy Framework: A Tool for Improving Privacy through Enterprise Risk Management at <https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.01162020.pdf>.

[^notice]: [[NISTIR8062]](sec11_references.md#ref-NISTIR8062) provides an overview of predictability and manageability including examples of how these objectives can be met.

### General Equity Requirements {#EquityReqs}

In support of the goal of improved equity, and as part of its overall risk assessment process, the CSP **SHALL** assess the elements of its identity service to identify processes or technologies that can possibly result in inequitable access, treatment, or outcomes for members of one group as compared to others.  See [Sec. 10](sec10_equity.md#EquityConsiderations) for a non-exhaustive list of identity proofing processes and technologies that may be subject to inequitable access or outcomes.


Note that executive order 13985 [[EO13985]](sec11_references.md#ref-EO13985), _Advancing Racial Equity and Support for Underserved Communities Through the Federal Government_, requires each federal agency to assess whether, and to what extent, its programs and policies perpetuate systemic barriers to opportunities and benefits for people of color and other underserved groups.

When assessing the risk of inequitable access, treatment, or outcomes, the following requirements apply:

1.  Based on the results of its risk assessment, the CSP **SHALL** document the measures it takes to mitigate the possibility of inequitable access, treatment, or outcomes.
2.  The CSP **SHALL** re-assess the risks to equitable access, treatment, or outcomes any time it makes changes to its identity service that affect the processes or technologies.
3.  The CSP **SHALL** re-assess the risks to equitable access, treatment, or outcomes periodically to ensure it accurately reflects the current risks associated with its service.
4.  The CSP **SHALL NOT** make applicant participation in these risk assessments mandatory.
5.  The CSP **SHALL** make the results of its assessment of risks associated with inequitable access, treatment, or outcomes, and any associated mitigations, available to any organizations or individuals that use its service.
6.  The CSP **SHALL** also make the results of its assessment publicly available.


### General Security Requirements {#SecurityReqs}

1. Each online transaction within the identity proofing process, including transactions that involve third parties, **SHALL** occur over an authenticated protected channel.
2. All PII, in the form of identity attributes, collected as part of the identity proofing process **SHALL** be protected to ensure the confidentiality and integrity of the information.
3. The CSP **SHALL** assess the risks associated with operating its identity service, according to the NIST risk management framework [[NIST-RMF]](sec11_references.md#ref-NIST-RMF), and apply an appropriate baseline security controls.


### Additional Requirements for Federal Agencies {#Feds}

The following requirements apply to federal agencies, regardless of whether they operate their own identity service or use an external CSP as part of their identity service:

1. The agency **SHALL** consult with their Senior Agency Official for Privacy (SAOP) to conduct an analysis determining whether the collection of PII, including biometrics, to conduct identity proofing triggers Privacy Act requirements.
2. The agency **SHALL** consult with their SAOP to conduct an analysis determining whether the collection of PII, including biometrics, to conduct identity proofing triggers E-Government Act of 2002 [[E-Gov]](sec11_references.md#ref-E-Gov) requirements.
3. The agency **SHALL** publish a System of Records Notice (SORN) to cover such collection, as applicable.
4. The agency **SHALL** publish a Privacy Impact Assessment (PIA) to cover such collection, as applicable.
5. The agency **SHALL** consult with the senior official, office, or governance body responsible for diversity, equity, inclusion, and accessibility (DEIA) for their agency to determine how the identity proofing service should be designed, resourced, and administered to meet the needs of all served populations.
6. The agency **SHOULD** consult with public affairs and communications professionals within their organization to determine if a communications or public awareness strategy should be developed to accompany the roll-out of any new process, or an update to an existing process, including requirements associated with identity proofing. This may include materials detailing information about how to use the technology associated with the service, a Frequently Asked Questions (FAQs) page, prerequisites to participate in the identity proofing process (such as required evidence), webinars or other live or pre-recorded information sessions, or other media to support adoption and provide applicants with a mechanism to communicate questions, issues, and feedback.
5. If the agency uses a third-party CSP, the agency SHALL be responsible for conducting its own privacy risk assessments or doing due diligence before relying on the CSP’s privacy risk assessment as part of its PIA process.
6. If the agency uses a third-party CSP, the agency **SHALL** incorporate the CSP’s assessment of equity risks into its own assessment of equity risks.


###  Requirements for Enrollment Codes {#EnrollCodes}

Enrollment codes are used to confirm an applicant has access to a validated address. If identity proofing and enrollment are not completed in a single session, an enrollment code can also be used to re-establish an applicant’s binding to their enrollment record for the purposes of completing the enrollment process.

The following requirements apply to all CSPs that employ enrollment codes at any IAL:

1. Enrollment codes **SHALL** be sent to a validated address (e.g., postal address, telephone number, or email address).
2. The applicant **SHALL** present a valid enrollment code to complete the identity proofing process.
3. Enrollment codes **SHALL** be comprised of one of the following:
    1. A random six digit number generated by an approved random number generator with at least 20 bits of entropy;
    2. A secure link delivered to a uniquely identified address containing an appropriately constructed session ID (at least 64 bits of entropy); or
    3. A machine readable optical label (such as a QR code) that contains a random secret with at least 20 bits of entropy.
    {:.letter-list}
4. Enrollment codes **SHALL** be valid for at most:
    1. 21 days, when sent to a validated postal address within the contiguous United States;
    2. 30 days, when sent to a validated postal address outside the contiguous United States;
    3. 10 minutes, when sent to a validated telephone number (SMS or voice); or
    4. 24 hours, when sent to a validated email address.
    {:.letter-list}
5. The enrollment code **SHALL NOT** be used as an authentication factor.

###  Requirements for Notifications of Identity Proofing {#ProofingNotifs}

Notifications of proofing are sent to the applicant's validated address notifying them that they have been successfully identity proofed.  These notices provide added assurance that the person who underwent identity proofing is the owner of the claimed identity.

The following requirements apply to all CSPs that send notifications of proofing as part of their identity proofing processes at any IAL.

Notifications of proofing:

1.  **SHALL** be sent to a validated address (e.g., postal address, telephone number, or email address) of record. Whenever possible, CSPs **SHOULD** send notifications of proofing and enrollment codes to different validated addresses.
2.  **SHALL** include details about the identity proofing event, such as the name of the identity service and the date the identity proofing was completed.
3.  **SHALL** provide clear instructions, including contact information, on actions to take in the case the recipient repudiates the identity proofing event.
4.  **SHOULD** provide additional information, such as how the organization or CSP protects the security and privacy of the information it collects and any responsibilities the recipient has as a subscriber of the identity service.

###  Requirements for Use of Biometrics {#ProofBios}

Biometrics is the automated recognition of individuals based on their biological and behavioral characteristics such as, but not limited to, fingerprints, iris structures, or facial features that can be used to recognize an individual. As used in these guidelines, biometric data refers to any analog or digital representation of biological and behavioral characteristics at any stage of their capture, storage, or processing. This includes live biometric samples from applicants (e.g., facial images, fingerprint), as well as biometric references obtained from evidence (e.g., facial image on a driver’s license, fingerprint minutiae template on identification cards). As applied to the identity proofing process, CSPs may use biometrics to uniquely resolve an individual identity within a given population or context, verify that an individual is the rightful subject of identity evidence, and/or bind that individual to a new piece of identity evidence or credential.

The following requirements apply to CSPs that employ biometric mechanisms as part of their identity proofing process:

1. CSPs **SHALL** provide clear, publicly available information about all uses of biometrics, what biometric data is collected, how it is stored, and information on how to remove biometric information consistent with applicable laws and regulations.
2. CSPs **SHALL** collect an explicit biometric consent from all applicants before collecting biometric information.
3. CSPs **SHALL** store the biometric consent with the subscriber's account.
4. CSPs **SHALL** have a documented, and publicly available, deletion process and default retention period for all biometric information.
5. CSPs **SHALL** allow individuals to request deletion of their biometric information at any time, except where otherwise restricted by regulation, law, or statute.
6. CSPs **SHALL** have all biometric algorithms tested by an independent entity (e.g., accredited laboratory or research institution) for performance, including performance across demographic groups.
7. Testing of all algorithms **SHALL** be consistent with published ISO/IEC standards for the given modality.
9. CSPs **SHALL** meet the minimum performance thresholds for biometric usage:
	- False match rate: 1:10,000 or better; and
	- False non-match rate: 1:100 or better
10. CSPs **SHALL** employ biometric technologies that provide similar performance characteristics for applicants of different demographic groups (racial background, gender, ethnicity, etc.). If performance differences across demographic groups are discovered, CSPs **SHALL** act expeditiously to provide redress options to affected individuals and to close performance gaps.
11. CSPs **SHALL** make all performance and operational test results publicly available.
11. CSPs **SHALL** assess the performance and demographic impacts of employed biometric technologies in conditions substantially similar to the operational environment and user base of the system. When such assessments include real-world users, participation by users **SHALL** be voluntary.
12. CSPs **SHALL** make all performance and operational test results publicly available.


The following requirements apply to CSPs who collect biometric characteristics from applicants:

1. CSP **SHALL** collect biometrics in such a way that ensures that the biometric is collected from the applicant, and not another subject.
2. When collecting and comparing biometrics remotely, the CSP **SHALL** implement liveness detection capabilities to confirm the genuine presence of a live human being and to mitigate spoofing and impersonation attempts.
3. When collecting biometrics in person, the CSP **SHALL** have the operator view the biometric source (e.g., fingers, face) for presence of non-natural materials and perform such inspections as part of the proofing process.

###  Trusted Referees and Applicant References {#TRs-ARs}

To increase accessibility and promote equal access to online government services, CSPs provide _trusted referees_. Trusted referees are used to facilitate the identity proofing and enrollment of individuals who are otherwise unable to meet the requirements for identity proofing to a specific IAL. Examples of such individuals and demographic groups include: individuals who do not possess and cannot obtain the required identity evidence; persons with disabilities; older individuals; persons experiencing homelessness; individuals with little or no access to online services or computing devices; persons without a bank account or with limited credit history; victims of identity theft; individuals displaced or affected by natural disasters; and children under 18.

Trusted referees are agents of the CSP or its partners who are trained and authorized to make risk-based decisions to facilitate the identity proofing and enrollment of individuals who are unable to complete the identity proofing process on their own or meet the specified requirements for a given IAL.

Additionally, there may be circumstances that encumber or preclude the active participation of an applicant in the identity proofing process. Such circumstances may be due to physical or mental limitations, disabilities, hospitalization, or other temporary or permanent conditions that make active participation in the identity proofing difficult. An _applicant reference_ may vouch for an applicant's particular circumstances and may also actively assist the applicant in the identity proofing process.

Applicant references are individuals who participate in the identity proofing of an applicant in order to assist the applicant in meeting the identity proofing requirements. Such assistance may include vouching for the applicant’s circumstances and actively assisting the applicant in completing the identity proofing process. Applicant references are not agents of the CSP but they would typically work in conjunction with a trusted referee to facilitate the identity proofing and enrollment of an applicant. Since information provided by the applicant reference may be used and relied upon in the identity proofing of the applicant, the applicant reference is identity proofed to the same or higher IAL as the applicant. The role of applicant reference is limited to facilitating the identity proofing process and applicant references are not authorized to represent subscribers in transactions with RPs. Persons who simply provide physical, technical, language translation or other similar assistance to an applicant who is otherwise able to meet the requirements for identity proofing to the specified IAL are not considered to be applicant references and do not require identity proofing.


####  Requirements for Trusted Referees {#TrustedRefs}

CSPs **SHALL** provide the option for the use of trusted referees for remote identity proofing at IALs 1 and 2.

Where trusted referees are offered, the following requirements apply to their use:

1. The CSP **SHALL** establish written policies and procedures for the use of trusted referees as part of its practice statement, as specified in [Sec. 5.1.1](sec5_ial.md#DocRecReqs).
2. The CSP **SHALL** train its trusted referees to make risk-based decisions that allow applicants to be successfully identity proofed based on their unique circumstances.
3. The CSP **SHALL** provide notification to the public of the availability of trusted referee services and how such services are obtained.

####  Requirements for Applicant References {#ApplicantRefs}

CSPs **SHOULD** allow the use of applicant references.

The following requirements apply to the use of applicant references at any IAL:

1. The CSP **SHALL** establish written policies and procedures for the use of applicant references as part of its practice statement, as specified in [Sec. 5.1.1](sec5_ial.md#DocRecReqs).
2. The CSP **SHALL** identity proof an applicant reference to the same or higher IAL intended for the applicant.
3. If the CSP allows for the use of applicant references, it **SHALL** provide notification to the public of the allowability of applicant references and any requirements for the relationship between the reference and the applicant.

### Requirements for Interacting with Minors {#Minors}

The following requirements apply to all CSPs providing identity proofing services to minors at any IAL.

1.  The CSP **SHALL** establish written policy and procedures as part of its practice statement for identity proofing minors who may not be able to meet the evidence requirements for a given IAL.
2.  When interacting with persons under the age of 13, the CSP **SHALL** ensure compliance with the Children’s Online Privacy Protection Act of 1998 [[COPPA]](sec11_references.md#ref-COPPA).
3.  CSPs **SHALL** support the use of applicant references when interacting with individuals under the age or 18.


##  Identity Proofing Process {#id-proof-process}

This document provides requirements that apply to several different identity proofing methods. These possible methods include:

* A fully automated, remote process;
* A CSP operator-assisted remote process;
* A combination of automated and operator-assisted remote process;
* An in-person, physical interaction with the applicant process; and
* An IAL3 Supervised Remote Identity Proofing process.

Identity proofing at IAL1 and IAL2 allow for any of the these processes to be used, while IAL3 requires in-person, physical interaction with the applicant or IAL3 Supervised Remote Identity Proofing.

The following sections provide requirements for identity proofing at each IAL.

## Identity Assurance Level 1 {#IAL1}

IAL1 permits both remote and in-person identity proofing. Identity proofing processes at IAL1 allow for a range of acceptable techniques in order to detect the presentation of fraudulent identities by a malicious actor while facilitating user adoption and minimizing false negatives and application departures (legitimate applicants who do not successfully complete identity proofing). Notably, the use of biometric matching, such as the automated comparison of a facial portrait to supplied evidence, at IAL1 is optional, providing pathways to proofing and enrollment where such collection may not be viable or where privacy and equity risks outweigh security considerations.


The following requirements apply to all CSPs providing identity proofing and enrollment services at IAL1.

###  Automated Attack Prevention

The CSP **SHALL** implement a means to prevent automated attacks on the identity proofing process. Acceptable means include, but are not limited to: bot detection, mitigation, and management solutions; behavioral analytics; web application firewall settings; and traffic analysis.



### Evidence and Core Attributes Collection Requirements

#### Evidence Collection

For remote or in-person identity proofing, the CSP **SHALL** collect _one_ of the following from the applicant:

1. One piece of SUPERIOR evidence, or
2. One piece of STRONG evidence and one piece of FAIR evidence


#### Collection of Additional Attributes

Validated evidence is the preferred source of identity attributes. If the presented identity evidence does not provide all the attributes the CSP considers core attributes, it **MAY** collect attributes that are self-asserted by the applicant.

### Evidence and Core Attributes Validation Requirements

The CSP **SHALL** validate the genuineness of each piece of SUPERIOR and STRONG evidence by _one_ of the following:

1. Visual inspection by trained personnel
2. The use of technologies that can confirm the integrity of physical security features or detect if the evidence is fraudulent or has been inappropriately modified
3. If present, confirming the integrity of digital security features

The CSP **SHALL** validate the genuineness of each piece of FAIR evidence by visual inspection by trained personnel.

The CSP **SHALL** validate all core attributes by _both_:

1. Validating the accuracy of attributes (such as account or reference number, name, and date of birth) obtained from pieces of evidence by comparison with authoritative or credible sources, and
2. Validating the accuracy of self-asserted attributes by comparison with authoritative or credible sources.

For added assurance, the CSP **SHALL** evaluate the core attributes, as validated by various sources, for overall consistency.


### Identity Verification Requirements

The CSP **SHALL** verify the binding of the applicant to the claimed identity by _one_ of the following:

1.	Physical comparison of the applicant’s face or biometric comparison of the facial image of the applicant to the facial portrait included on a piece of SUPERIOR or STRONG evidence, or
2.	Demonstrated association with a digital account through an AAL1 authentication or an AAL1 and FAL1 federation protocol, or
3.	Verification of the applicant's return of a valid enrollment code [Sec. 5.1.6](sec5_ial.md#EnrollCodes)

### Notification of Proofing Requirement

Upon the successful completion of identity proofing at IAL1, the CSP **SHOULD** send a notification of proofing to a validated address for the applicant, as specified in [Sec. 5.1.7](sec5_ial.md#ProofingNotifs).


## Identity Assurance Level 2 {#IAL2}

Like IAL1, IAL2 identity proofing allows for both remote and in-person identity proofing processes in order to maximize accessibility while still mitigating against impersonation attacks and other identity proofing errors.  Remote IAL2 identity proofing can be accomplished by the CSP via a fully automated process, a CSP operator attended process, or a combination of the two.

###  Automated Attack Prevention

The CSP **SHALL** implement a means to prevent automated attacks on the identity proofing process. Acceptable means include, but are not limited to: bot detection, mitigation, and management solutions; behavioral analytics; web application firewall settings; and traffic analysis.


### Evidence and Core Attribute Collection Requirements

#### Evidence Collection

For remote or in-person identity proofing, the CSP **SHALL** collect _one_ of the following from the applicant:

1. One piece of SUPERIOR evidence
2. One piece of STRONG evidence and one piece of FAIR evidence



#### Collection of Attributes

Validated evidence is the preferred source of identity attributes. If the presented identity evidence does not provide all the attributes the CSP considers core attributes, it **MAY** collect attributes that are self-asserted by the applicant.

### Evidence and Core Attributes Validation Requirements

The CSP **SHALL** validate the genuineness of each piece of SUPERIOR and STRONG evidence by one of the following:

1. Visual inspection by trained personnel
2. The use of technologies that can confirm the integrity of physical security features or detect if the evidence is fraudulent or has been inappropriately modified
3. If present, confirming the integrity of digital security features

The CSP **SHALL** validate all core attributes by:

1. Validating the accuracy of attributes (such as account or reference number, name, and date of birth) obtained from pieces of evidence by comparison with authoritative or credible sources, and

2. validating the accuracy of self-asserted attributes by comparison with authoritative or credible sources


For added assurance, the CSP **SHALL** evaluate the core attributes, as validated by various sources, for overall consistency.


### Identity Verification Requirements

#### Remote Identity Proofing

The CSP **SHALL** verify the binding of the applicant to the claimed identity by _one_ of the following:

1.	Comparison of a collected biometric characteristic, such as a facial image, to the associated reference biometric contained on a piece of presented SUPERIOR or STRONG evidence
2.	Demonstrated association with a digital account through an AAL2 authentication or an AAL2 and FAL2 federation protocol


#### In-person Identity Proofing

The CSP **SHALL** verify the binding of the applicant to the claimed identity by physical or biometric comparison of the facial image of the applicant to the facial portrait contained on a piece of presented SUPERIOR or STRONG evidence.

### Notification of Proofing Requirement

Upon the successful completion of identity proofing at IAL2, the CSP **SHALL** send a notification of proofing to a validated address for the applicant, as specified in [Sec. 5.1.7](sec5_ial.md#ProofingNotices).

## Identity Assurance Level 3 {#IAL3}

IAL3 adds additional rigor to the steps required at IAL2 and is subject to additional and specific processes (including the use of biometric information comparison, collection, and retention) to further protect the identity and RP from impersonation, fraud, or other significantly harmful damages. In addition, identity proofing at IAL3 is performed in person (to include supervised remote identity proofing defined in [Sec. 5.5.8](sec4_proofing.md#IAL3supervised)).

###  Automated Attack Prevention

The CSP **SHALL** implement a means to prevent automated attacks on the identity proofing process. Acceptable means include, but are not limited to: bot detection, mitigation, and management solutions; behavioral analytics; web application firewall settings; and traffic analysis.


### Evidence and Core Attributes Collection Requirements

#### Evidence Collection

The CSP **SHALL** collect evidence from the applicant according to _one_ of the following options:

1. Two pieces of SUPERIOR evidence, or
2. One piece of SUPERIOR evidence and one piece of STRONG evidence, or
3. Two pieces of STRONG evidence and one piece of FAIR evidence

#### Collection of Attributes

Validated evidence is the preferred source of identity attributes. If the presented identity evidence does not provide all the attributes the CSP considers core attributes, it **MAY** collect attributes that are self-asserted by the applicant.

### Validation Requirements {#s-4-5-3}

#### Evidence Validation Requirements

The CSP **SHALL** validate the genuineness of each piece of SUPERIOR evidence by confirming the integrity of its cryptographic security features and validating any digital signatures.

The CSP **SHALL** validate the genuineness of each piece of STRONG evidence by _one_ of the following:

1. Visual inspection by trained personnel
2. The use of technologies that can confirm the integrity of physical security features and detect if the evidence is fraudulent or has been inappropriately modified
3. If present, confirming the integrity of digital security features, including the validity of the issuer's digital signature

#### Core Attribute Validation Requirements

The CSP **SHALL** validate all core attributes by _both_:

1. Validating the accuracy of attributes obtained from pieces of evidence or applicant self-assertion by comparison with authoritative or credible sources
2. Validating the cryptographic features of any presented digital evidence, as described above


For added assurance, the CSP **SHALL** evaluate the core attributes, as validated by various sources, for overall consistency.

### Identity Verification Requirements

The CSP **SHALL** verify the binding of the applicant to the claimed identity by _one_ of the following:

1.	Comparison of a collected biometric characteristic, such as a facial image, to the associated reference biometric characteristic contained on a piece of presented SUPERIOR or STRONG evidence
2.	Demonstrated association with a digital account through, at a minimum, an AAL2 authentication or an AAL2 and FAL2 federation protocol


### Notification of Proofing Requirement

Upon the successful completion of identity proofing at IAL3, the CSP **SHALL** send a notification of proofing to a validated address for the applicant, as specified in [Sec. 5.1.7](sec5_ial.md#ProofingNotices).

### Biometric Collection

The CSP **SHALL** collect and record a biometric sample at the time of proofing (e.g., facial image, fingerprints) for the purposes of non-repudiation and re-proofing.

### In-person Proofing Requirements {#vip}

In-person proofing at IAL3 **SHALL** be conducted in _one_ of two ways:

- An in-person interaction between the applicant and a CSP operator, or
- A remote interaction with the applicant, supervised by an operator, based on the requirements in [Sec. 5.5.8](sec5_ial.md#IAL3supervised), _IAL3 Supervised Remote Identity Proofing_.


Regardless of which of the two methods the CSP employs, the following requirements apply to identity proofing at IAL3:

1. The CSP **SHALL** have the operator view the biometric source (e.g., fingers, face) for the presence of any non-natural materials.
2. The CSP **SHALL** collect biometrics in such a way that ensures that the biometric is collected from the applicant, and not another subject.

### Requirements for IAL3 Supervised Remote Identity Proofing {#IAL3supervised}

IAL3 Supervised Remote Identity Proofing is intended to achieve comparable levels of confidence and security to an in-person interaction with the applicant.

The following requirements apply to all IAL3 Supervised Remote Identity Proofing sessions:

1. The CSP **SHALL** monitor the entire identity proofing session, and **SHALL** ensure the applicant is continuously present during the entire identity proofing session — for example, by a continuous high-resolution video transmission of the applicant.
2. The CSP **SHALL** have a live operator participate remotely with the applicant for the entirety of the identity proofing session.
3. The CSP **SHALL** require all actions taken by the applicant during the identity proofing session to be clearly visible to the remote operator.
4. The CSP **SHALL** require that all digital verification of evidence (e.g., via chip or wireless technologies) be performed by integrated scanners and sensors (e.g., embedded fingerprint reader).
5. The CSP **SHALL** require operators to have undergone a training program to detect potential fraud and to properly perform a supervised remote proofing session.
6. The CSP **SHALL** employ physical tamper detection and resistance features appropriate for the environment in which it is located. For example, a kiosk located in a restricted area or one where it is monitored by a trusted individual requires less tamper detection than one that is located in a semi-public area such as a shopping mall concourse.
7. The CSP **SHALL** ensure that all communications occur over a mutually authenticated protected channel.

## Summary of Requirements

[Table 1](sec5_ial.md#table-1) summarizes the requirements for each of the identity assurance levels:

[Table 1 IAL Requirements Summary](sec5_ial.md#table-1){:name="table-1"}
{:latex-ignore="true"}

Requirement | IAL1 | IAL2 | IAL3
------------|-------|-------|-------
Presence|Remote or In-person|Remote or In-person|In-person or Supervised Remote Identity Proofing
Resolution|Minimum attributes to accomplish resolution|Same as IAL1| Same as IAL1
Evidence|1 piece of SUPERIOR or 1 piece of STRONG plus 1 piece of FAIR|1 piece of SUPERIOR or 1 piece of STRONG plus 1 piece of FAIR|2 pieces of SUPERIOR or 1 piece of SUPERIOR plus 1 piece of STRONG or 2 pieces of STRONG plus 1 piece of FAIR
Validation|Evidence is validated for genuineness, accuracy, and currency. All core attributes are validated by authoritative or credible sources|Same as IAL1|Same as IAL1
Verification|Return of an enrollment code or Demonstrated access to a digital account at AAL1 or FAL1|Biometric comparison or Demonstrated access to a digital account at AAL2 or FAL2|Biometric comparison or Demonstrated access to a digital account at AAL2 or FAL2
Biometric Collection|Optional|Optional|Mandatory
{:latex-table="1" latex-caption="IAL Requirements Summary" latex-columns="p@0.15\textwidth,p@0.22\textwidth,p@0.22\textwidth,p@0.22\textwidth"}
