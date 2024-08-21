---
layout: default
title: Identity Proofing Requirements
navOrder: 4
navTitle: General IAL
permalink: /sp800-63a/ial-general/
anchor: ial-general
section: 3
---

# Identity Proofing Requirements {#ial-general}

_This section is normative._

This section provides requirements for CSPs that operate identity proofing and enrollment services, including requirements for identity proofing at each of the IALs. This section also includes additional requirements for federal agencies regardless of whether they operate their own identity service or use an external CSP.

Sections [4.1](4_ial.md#IAL1), [4.2](4_ial.md#IAL2), and [4.3](4_ial.md#IAL3) provide the requirements and guidelines for identity proofing at a specific IAL. [Section 4.4](4_ial.md#summary) includes a summarized list of these requirements by IAL in [Table 1](3_ialgen.md#table-1). 

## General Requirements {#genProofReqs}

The requirements in this section apply to all CSPs performing identity proofing at any IAL.

### Identity Service Documentation and Records {#DocRecReqs}

The CSP **SHALL** conduct its operations according to a practice statement that details all identity proofing processes as they are implemented to achieve the defined IAL. The practice statement **SHALL** include, at a minimum:  

1. A complete service description including the particular steps the CSP follows to identity proof applicants at each offered assurance level;
2. The CSP's policy for providing notice to applicants about the types of identity proofing processes available, the evidence and attribute collection requirements for the specified IAL, the purpose of PII collection (per [Sec. 3.1.3.2](3_ialgen.md#AddlPrivacy)), and for the collection, use, and retention of biometrics (see [Sec. 3.1.11](3_ialgen.md#ProofBios));  
2. The CSP's policy for ensuring the identity proofing process is concluded in a timely manner, once the applicant has met all of the requirements;  
3. Types of identity evidence the CSP accepts to meet the evidence strength requirements;
4. The CSP's policy and process for validating and verifying identity evidence, including training and qualification requirements for personnel who have validation and verification responsibilities, as well as specific technologies the CSP employs for evidence validation and verification; 
5. Alternative processes for the CSP to complete identity proofing for an individual applicant who does not possess the required identity evidence to complete the identity proofing process[^alternatives];  
6. The attributes that the CSP considers to be core attributes, and the authoritative and credible sources it uses for validating those attributes. Core attributes include the minimum set of attributes that the CSP needs to perform identity resolution as well as any additional attributes that the CSP collects and validates for the purposes of identity proofing, fraud mitigation, complying with laws or legal process, or conveying to relying parties (RPs) through attribute assertions;   
7. The CSP's policy and process for addressing identity proofing errors;
8. The CSP's policy and process for identifying and remediating suspected or confirmed fraudulent accounts, including communicating with RPs and affected individuals; 
9. The CSP's policy for managing and communicating service changes (e.g., changes in data sources, integrated vendors, or biometric algorithms) to RPs; 
10. The CSP's policy for any conditions that would require re-verification of the user (e.g., account recovery, account abandonment, regulatory "recertification" requirements); 
10. The CSP's policy for conducting privacy risk assessments, including the timing of its periodic reviews and specific conditions that will trigger an updated privacy risk assessment (see [Sec. 3.1.3.1](3_ialgen.md#PrivRiskAssess)); 
11. The CSP's policy for conducting assessments to determine potential equity impacts, including the timing of its periodic reviews and any specific conditions that will trigger an out-of-cycle review (see [Sec. 3.1.4](3_ialgen.md#EquityReqs)); and,
12. The CSP's policy for the collection, purpose, retention, protection, and deletion of all personal and sensitive data, including the treatment of all personal information if the CSP ceases operation or merges or transfers operations to another CSP.

> **Note:** 800-63C references the use of trust agreements to define requirements between an IdP, CSP, and RP in a federated relationship. CSP practice statements **MAY** be included directly in these agreements. 

### Fraud Management  {#FraudMgmt}

A critical aspect of the identity proofing process is to mitigate fraudulent attempts to gain access to benefits, services, data, or assets protected by identity management systems. Resolution, Validation, and Verification processes in many instances can mitigate many attacks. However, with the constantly changing threat environment, the layering of additional checks and controls can provide increased confidence in proofed identities and additional protections against attacks intended to defeat other controls. The ability to identify, detect, and resolve instances of potential fraud is a critical functionality for CSPs and RPs alike. 

#### CSP Fraud Management 

1. CSPs **SHALL** establish and maintain a fraud management program that provides fraud identification, detection, investigation, reporting, and resolution capabilities. The specific capabilities and details of this program **SHALL** be documented within their CSP practice statement.
2. CSPs **SHALL** conduct a Privacy Risk Assessment of all fraud checks and fraud mitigation technologies prior to implementation.
3. The CSP **SHALL** establish a self-reporting mechanism and investigation capability for subjects who believe they have been the victim of fraud or an attempt to compromise their involvement in the identity proofing processes.
4. The CSP **SHALL** take measures to prevent unsuccessful applicants from inferring the accuracy of any self-asserted information with that confirmed by authoritative or credible sources.
	NOTE: This is often called "data washing" and can be prevented through a number of methods, depending on the interfaces deployed by a CSP. As such, these guidelines do not dictate specific mechanisms to prevent this practice. 
5. CSPs **SHALL** implement the following fraud check for all identity proofing processes:
   - **Date of Death Check** – Confirm with a credible, authoritative, or issuing source that the applicant is not deceased. Such checks can aid in preventing synthetic identity fraud, the use of stolen identity information, and exploitation by a close associate or relative.
6. CSPs **SHOULD** implement - but are not limited to - the following fraud checks for their identity proofing processes based on their available identity proofing types, selected technologies, evidence, and user base:
   - **SIM Swap Detection** – Confirm that the phone number used in an identity proofing process has not been recently ported to a new user or device. Such checks can provide an indication that a phone or device was compromised by a targeted attack.
   - **Device or Account Tenure Check** – Evaluate the length of time a phone or other account has existed without substantial modifications or changes. Such checks can provide additional confidence in the reliability of a device or piece of evidence used in the identity proofing process.
   - **Transaction Analytics** – Evaluate anticipated transaction characteristics – such as IP Addresses, geolocations, and transaction velocities – to identify anomalous behaviors or activities that can indicate a higher risk or a potentially fraudulent event. Such checks can provide protections against scaled and automated attacks, as well as give indications of specific attack patterns being executed on identity systems.
   - **Fraud Indicator Check** – Evaluate records, such as reported, confirmed, or historical fraud events to determine if there is an elevated risk related to a specific applicant, applicant's data, or device. Such checks can give an indication of identity theft or compromise. Where such information is collected, aggregated, or exchanged across commercial platforms and made available for use to RPs and other CSPs, users **SHALL** be made aware of this practice. This also applies to all websites that report user activity to Federal RPs. 
7. CSPs **MAY** employ knowledge-based verification (KBV) as part of its fraud management program. 
8. CSPs **SHOULD** consider the recency of fraud-related data when factoring it into fraud prevention capabilities and decisions. 
9. For attended proofing processes, CSPs **SHALL** train proofing agents to detect indicators of fraud and **SHALL** provide proofing agents and trusted referees with tools to flag suspected fraudulent events for further treatment and investigation.
10. CSPs **SHALL** continuously monitor the performance of their fraud checks and fraud mitigation technologies to identify and remediate issues related to disparate performance across their platforms or between the demographic groups served by their identity service.
11. CSPs **SHALL** establish a technical or process-based mechanism to communicate suspected and confirmed fraudulent events to RPs.
12. CSPs **SHOULD** implement shared signaling, as described in NIST SP 800-63C-4, to communicate fraud events in real time to RPs.
13. CSPs **MAY** implement fraud mitigation measures as compensating controls. When this is done, these **SHALL** be documented as deviations from the normative guidance of these guidelines and **SHALL** be conveyed to all RPs through a Digital Identity Acceptance Statement prior to integration. 

#### RP Fraud Management

1. RPs **SHALL** establish a point of contact with whom CSPs interact and communicate fraud data.
2. Pursuant to a privacy risk assessment, the RP **MAY** also request additional attributes beyond what a CSP provides as its core attributes to combat fraud or to support other business processes.
3. Pursuant to applicable laws and regulations, RPs **SHOULD** establish a mechanism to communicate the outcomes of fraud reports and investigations, including both positive and negative results, to CSPs and other partners in order to allow them to improve their own fraud identification, mitigation, and reporting capabilities. 
4. RPs **SHOULD** establish a fraud management program consistent with their mission, regulatory environment, systems, applications, data, and resources.
5. RPs **SHALL** conduct a privacy risk assessment of any CSP fraud checks and mitigation technologies to identify potential privacy risks or unintended harms. Federal agency RPs **SHALL** implement this consistent with the requirements contained in [Sec. 3.1.7](3_ialgen.md#Feds).
6. RPs **SHALL** include any requirements for fraud checks and fraud mitigation technologies in trust agreements with their CSPs.
7. RPs **SHALL** conduct periodic reviews of their CSP's fraud management program, fraud checks, and fraud technologies to adjust thresholds, review investigations into fraud events, and make determinations about the effectiveness and efficacy of fraud controls.
8. RPs **SHALL** review all fraud mitigation measures that have been deployed as compensating or supplemental controls by CSPs for alignment to their internal risk tolerance and acceptance. The RP **SHALL** record the CSPs compensating controls in their own Digital Identity Acceptance Statement prior to integration. 

#### Treatment of Fraud Check Failures 
The effectiveness of fraud checks and mitigation technologies will vary based on numerous contributing factors including the data sources used, the technologies used, and – perhaps most importantly – the applicant population. It is therefore critical to have well-structured and documented processes for how to handle failures arising from the fraud management measures. The following requirements apply to handling these failures: 

1. CSPs **SHALL** establish and document thresholds and actions related to each of the fraud checks they implement and provide these thresholds to RPs.
2. CSPs **SHALL** establish procedures for redress to allow applicants to resolve issues associated with fraud checks and mitigation technologies. See (see [Sec. 3.6 of [SP800-63]](../_sp800-63/3_DIRM.md#redress){:latex-href="#ref-SP800-63"}) for a more information about redress.
3. The CSP **SHALL** offer trusted referee services to those who fail fraud checks in unattended remote processes. Trusted referees **SHALL** be provided with a summary of the results of the fraud failures to inform their risk-based decisioning processes. 

[^alternatives]: Options include using a trusted referee, with or without an applicant representative. 

~~~
\clearpage
~~~
{:latex-literal="true"}

### General Privacy Requirements {#PrivacyReqs}
 
The following privacy requirements apply to all CSPs providing identity services at any IAL. 

#### Privacy Risk Assessment {#PrivRiskAssess}

1. The CSP **SHALL** conduct and document a privacy risk assessment for the processes used for identity proofing and enrollment.[^privacyframework]  At a minimum, the privacy risk assessment **SHALL** assess the risks associated with:
	1. Any processing of PII - including identity attributes, biometrics, images, video, scans, or copies of identity evidence - for the purposes of identity proofing, enrollment, or fraud management;
	2. Any additional steps that the CSP takes to verify the identity of an applicant beyond the mandatory requirements specified herein;
	3. Any processing of PII for purposes outside the scope of identity proofing and enrollment, except to comply with law or legal processes;
	4. The retention schedule for identity records and PII; 
	5. Any non-PII that, when aggregated or processed by an algorithm ( e.g., artificial intelligence or machine learning tools), could be used to identify a person; and,
	6. Any PII that is processed by a third-party service on behalf of the CSP.
	{:.letter-list}
2. Based on the results of its privacy risk assessment, the CSP **SHALL** document the measures it takes to maintain the disassociability, predictability, manageability, confidentiality, integrity, and availability of the PII it processes. [^NISTIR8062] In determining such measures, the CSP **SHOULD** apply relevant guidance and standards, such as the *NIST Privacy Framework* [[NIST-Privacy]](references.md#ref-NIST-Privacy) and NIST Special Publication [[SP800-53]](references.md#ref-SP800-53).
3. The CSP **SHALL** re-assess privacy risks and update its privacy risk assessment any time it makes changes to its identity service that affect the processing of PII.
4. The CSP **SHALL** review its privacy risk assessment periodically, as documented in its practice statement, to ensure that it accurately reflects the current risks associated with the processing of PII.  
5. The CSP **SHALL** make a summary of its privacy risk assessment available to any organizations that use its services. The summary **SHALL** be in sufficient detail to enable such organizations to do a due diligence investigation.
6. The CSP **SHALL** perform a privacy risk assessment for the processing of any personal information maintained in the subscriber account [Sec. 5](5_accounts.md#accounts).

#### Additional Privacy Protective Measures {#AddlPrivacy}

1. The processing of PII **SHALL** be limited to the minimum necessary to validate the existence of the claimed identity, associate the claimed identity with the applicant, mitigate fraud, and provide RPs with attributes that they may use to make authorization decisions.
2. The CSP **SHALL** provide privacy training to all personnel and any third-party service providers who have access to sensitive information associated with the CSP's identity service.  
2. The CSP **MAY** collect the Social Security Number (SSN) as an attribute when necessary for identity resolution, in accordance with the privacy requirements in [Sec. 3.1.3](3_ialgen.md#PrivacyReqs). If SSNs are collected, CSPs **SHOULD** implement privacy protective techniques (e.g., transmitting and accepting derived attribute values rather than full attribute values) to limit the proliferation and retention of SSN data. Knowledge of an SSN is not sufficient to act as evidence of identity nor is it considered an acceptable method of verifying possession of the Social Security Card when used as evidence. If the SSN is collected on behalf of a federal, state, or local government agency, the CSP **SHALL** provide notice to the applicant for the collection in accordance with applicable laws.
3. At the time of collection, the CSP **SHALL** provide explicit notice to the applicant regarding the purpose for collecting the PII and attributes necessary for identity proofing, enrollment, and fraud mitigation, including whether such PII and attributes are voluntary or mandatory to complete the identity proofing process, the specific attributes and other sensitive data that the CSP intends to store in the applicant's subsequent subscriber account, the consequences for not providing the attributes, and the details of any records retention requirement if one is in place.

[^privacyframework]: For more information about privacy risk assessments, refer to the NIST Privacy Framework: A Tool for Improving Privacy through Enterprise Risk Management at <https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.01162020.pdf>.

[^NISTIR8062]: [[NISTIR8062]](references.md#ref-NISTIR8062) provides an overview of predictability and manageability including examples of how these objectives can be met.

### General Equity Requirements {#EquityReqs}
 
In support of the goal of improved equity, and as part of its overall risk assessment process, CSPs assess the elements of their identity services to identify processes and technologies that may result in inequitable access, treatment, or outcomes for members of one group as compared to others. Where risks to equity are identified, CSPs proactively employ mitigations that will reduce or eliminate these discrepancies between demographic groups. [Sec. 9](9_equity.md#equity) of this document provides a non-exhaustive list of identity proofing processes and technologies that may be subject to inequitable access or outcomes, as well as possible mitigations.   
 
Executive order [[EO13985]](references.md#ref-EO13985), _Advancing Racial Equity and Support for Underserved Communities Through the Federal Government_, requires each federal agency to assess whether, and to what extent, its programs and policies perpetuate systemic barriers to opportunities and benefits for people of color and other underserved groups. Additionally, executive order [[EO13988]](references.md#ref-EO13988), _Preventing and Combating Discrimination on the Basis of Gender Identity or Sexual Orientation_, sets policy that all persons are be treated with respect, regardless of gender identity or sexual orientation, and requires agencies to enforce this prohibition on sex discrimination.
 
CSPs **SHOULD** review the methods of assessment, data collection, and redress outlined in OMB Report, _A Vision for Equitable Data: Recommendations from the Equitable Data Working Group_ [[EO13985-vision]](references.md#ref-EO13985-vision) for the development of its equity assessment policy and practices.
 
The following requirements apply to all CSPs providing identity services at any IAL:
 
1.  The CSP **SHALL** assess the elements of its identity proofing process(es) to identify processes or technologies that can result in inequitable access, treatment, or outcomes for members of one group as compared to others.
2.  Based on the results of its assessment, the CSP **SHALL** document the measures it takes to mitigate the possibility of inequitable access, treatment, or outcomes. 
3.  The CSP **SHALL** re-assess the risks to equitable access, treatment, or outcomes periodically and any time the CSP makes changes to its identity service that affect the processes or technologies.
4.  The CSP **SHALL NOT** make applicant participation in these risk assessments mandatory.
5.  The CSP **SHALL** make the results of its equity assessment, including any associated mitigations, publicly available.      

### General Security Requirements {#SecurityReqs}

1. Each online transaction within the identity proofing process, including transactions that involve third parties, **SHALL** occur over an authenticated protected channel.
2. The CSP **SHALL** implement a means to prevent automated attacks on the identity proofing process. Acceptable means include, but are not limited to: bot detection, mitigation, and management solutions; behavioral analytics[^behavioral]; web application firewall settings; and network traffic analysis.
3. All PII collected as part of the identity proofing process **SHALL** be protected to maintain the confidentiality and integrity of the information, including the encryption of data at rest and the exchange of information using authenticated protected channels.
4. The CSP **SHALL** assess the risks associated with operating its identity service, according to the NIST _Risk Management Framework_ [[NIST-RMF]](references.md#ref-NIST-RMF) or equivalent risk management guidelines. At a minimum, the CSP **SHALL** apply appropriate controls consistent with [[SP800-53]](references.md#ref-SP800-53) moderate baseline, regardless of IAL.
5. The CSP **SHOULD** assess risks associated with its use of third-party services and apply appropriate controls, as provided in the [[SP800-161]](references.md#ref-SP800-161) _Cybersecurity Supply Chain Risk Management Practices for Systems and Organizations_.

[^behavioral]: Behavioral analytics in this context are used to determine if an interaction is indicative of an automated attack and not an effort to identify or authenticate a specific user based on a captured reference template for that user. 

### Redress Requirements {#redress}

1. The CSP **SHALL** provide mechanisms for the redress of applicant complaints and for problems arising from the identity proofing process, including but not limited to: proofing failures, delays, and difficulties. 
2. These mechanisms **SHALL** be easy for applicants to find and use. 
3. The CSP **SHALL** assess the mechanisms for their efficacy in achieving a resolution of complaints or problems. 

See [Sec. 3.6 of [SP800-63]](../_sp800-63/3_DIRM.md#redress){:latex-href="#ref-SP800-63"} for more information about redress.

### Additional Requirements for Federal Agencies {#Feds}

The following requirements apply to federal agencies, regardless of whether they operate their own identity service or use an external CSP as part of their identity service:

1. The agency **SHALL** consult with their Senior Agency Official for Privacy (SAOP) to conduct an analysis determining whether the collection of PII, including biometrics, to conduct identity proofing triggers Privacy Act requirements.
2. The agency **SHALL** consult with their SAOP to conduct an analysis determining whether the collection of PII, including biometrics, to conduct identity proofing triggers E-Government Act of 2002 [[E-Gov]](references.md#ref-E-Gov) requirements.
3. The agency **SHALL** publish a System of Records Notice (SORN) to cover such collection, as applicable.[^SORN]
4. The agency **SHALL** publish a Privacy Impact Assessment (PIA) to cover such collection, as applicable.
5. The agency **SHALL** consult with the senior official, office, or governance body responsible for diversity, equity, inclusion, and accessibility (DEIA) for their agency to determine how the identity proofing service can meet the needs of all served populations.
6. The agency **SHOULD** consult with public affairs and communications professionals within their organization to determine if a communications or public awareness strategy should be developed to accompany the roll-out of any new process, or an update to an existing process, including requirements associated with identity proofing. This may include materials detailing information about how to use the technology associated with the service, a Frequently Asked Questions (FAQs) page, prerequisites to participate in the identity proofing process (such as required evidence), webinars or other live or pre-recorded information sessions, or other media to support adoption of the identity service and provide applicants with a mechanism to communicate questions, issues, and feedback. 
5. If the agency uses a third-party CSP, the agency SHALL conduct its own privacy risk assessment as part of its PIA process, using the CSP's privacy risk assessment as input to the agency's assessment.
6. If the agency uses a third-party CSP, the agency **SHALL** incorporate the CSP's assessment of equity risks into its own assessment of equity risks.

[^SORN]: For more information about SORNs, see OPM's _System of Records Notice (SORN) Guide_ (https://www.opm.gov/information-management/privacy-policy/privacy-references/sornguide.pdf).

###  Requirements for Confirmation Codes {#ConfirmCodes}

This section includes requirements for CSPs that support the use of confirmation codes. 

Confirmation codes are used to confirm that an applicant has access to a postal address, email address, or phone number, for the purposes of future communications. They are also used as an identity verification option at IALs 1 and 2, as described in [Sec. 2.5.1](2_proofing.md#verification). 

Confirmation codes used for these purposes **SHALL** include at least 6 decimal digits (or equivalent) from an approved random bit generator (see [Sec. 3.2.12 of [SP800-63B]](../_sp800-63b/3_authenticators.md#randomness){:latex-href="#ref-SP800-63B"}). The confirmation code may be presented as numeric or alphanumeric (e.g., Base64) for manual entry; a secure (e.g., https) link containing a representation of the confirmation code; or a machine-readable optical label, such as a QR code, containing the confirmation code.

Confirmation codes **SHALL** be valid for at most:

- 21 days, when sent to a validated postal address within the contiguous United States;
- 30 days, when sent to a validated postal address outside the contiguous United States;
- 10 minutes, when sent to a validated telephone number (SMS or voice); or
- 24 hours, when sent to a validated email address.


Upon its use, the CSP **SHALL** invalidate the confirmation code.

###  Requirements for Continuation Codes {#ContinueCodes}

This section includes requirements for CSPs that support the use of continuation codes.

Continuation codes are used to re-establish an applicant's linkage to an incomplete identity proofing or enrollment process. CSPs **MAY** use continuation codes when an applicant is unable to complete all the steps necessary to be successfully identity proofed and enrolled into the CSP's identity service in a single session, or when switching between different identity proofing types (such as from remote unattended to remote attended). Continuation codes are intended to be maintained offline (e.g., printed or written down) and stored in a secure location by the applicant for use in re-establishing linkage to a previous, incomplete session. 

In order to facilitate the authentication of the applicant to a subsequent session, the CSP **SHALL** first bind an authenticator to a record or account established for the applicant prior to the cessation of the initial session. Continuation codes **SHALL** include at least 64 bits from an approved random bit generator (see [Sec. 3.2.12 of [SP800-63B]](../_sp800-63b/3_authenticators.md#randomness){:latex-href="#ref-SP800-63B"}). The continuation code **MAY** be presented as numeric or alphanumeric (e.g., Base64) for manual entry, or as a machine-readable optical label, such as a QR code containing the continuation code. 

Verification of continuation codes **SHALL** be subject to throttling requirements, as provided in [Sec. 3.2.2 of [SP800-63B]](../_sp800-63b/3_authenticators.md#throttle){:latex-href="#ref-SP800-63B"}. Continuation codes **SHALL** be stored in hashed form, using a FIPS-approved or NIST recommended one-way function. Upon its use, the CSP **SHALL** invalidate the continuation code.

###  Requirements for Notifications of Identity Proofing {#ProofingNotifs}

Notifications of proofing are sent to the applicant's validated address notifying them that they have been successfully identity proofed and provide information about the identity proofing event and subsequent enrollment, including how the recipient can repudiate they were the subject of the identity proofing.  

The following requirements apply to CSPs and RPs that send notifications of proofing at any IAL. 

Notifications of proofing:

1.  **SHALL** be sent to a validated postal address, email address, or phone number.   
2.  **SHALL** include details about the identity proofing event, including the name of the identity service and the date the identity proofing was completed.
3.  **SHALL** provide clear instructions, including contact information, on actions for the recipient to take in the case that they repudiate the identity proofing event. 
4.  **SHALL** provide additional information, such as how the organization or CSP protects the security and privacy of the information it collects and any responsibilities that the recipient has as a subscriber of the identity service. 
5.  **SHOULD** provide instructions on how to access their subscriber account or information about how the subscriber can update the information contained in that account.

In the event a subscriber repudiates having been identity proofed by the identity service, the CSP or RP **SHALL** respond in accordance to its fraud management program ([Sec. 3.1.2](3_ialgen.md#FraudMgmt)). 

###  Requirements for the Use of Biometrics {#ProofBios}

Biometrics is the automated recognition of individuals based on their biological and behavioral characteristics such as, but not limited to, fingerprints, voice patterns, or facial features (biological characteristics), and keystroke patterns, angle of holding a smart phone, screen pressure, typing speed, mouse movements, or gait (behavioral characteristics).  As used in these guidelines, biometric data refers to any analog or digital representation of biological and behavioral characteristics at any stage of their capture, storage, or processing. This includes live biometric samples from applicants (e.g., facial images, fingerprint), as well as biometric references obtained from evidence (e.g., facial image on a driver's license, fingerprint minutiae template on identification cards). As applied to the identity proofing process, CSPs can use biometrics to verify that an individual is the rightful subject of identity evidence, to bind an individual to a new piece of identity evidence or credential, or for the purposes of fraud detection.

The following requirements apply to CSPs that employ biometrics as part of their identity proofing process: 

1. CSPs **SHALL** provide clear, publicly available information about all uses of biometrics, what biometric data is collected, how it is stored, how it is protected, and information on how to remove biometric information consistent with applicable laws and regulations. 
2. CSPs **SHALL** collect an explicit biometric consent from all applicants before collecting biometric information. 
3. CSPs **SHALL** store a record of subscriber's consent for biometric use and associate it with subscriber's account. 
4. CSPs **SHALL** have a documented, and publicly available, deletion process and default retention period for all biometric information. 
5. CSPs **SHALL** support the deletion of all of a subscriber's biometric information upon the subscriber's request at any time, except where otherwise restricted by regulation, law, or statute. 
6. CSPs **SHALL** have their biometric algorithms periodically tested by independent entities (e.g., accredited laboratories or research institutions) for their performance characteristics, including performance across demographic groups. At a minimum, the CSP **SHALL** have an algorithm retested after it has been updated.
7. CSPs **SHALL** assess the performance and demographic impacts of employed biometric technologies in conditions that are substantially similar to the operational environment and user base of the system. The user base is defined by both the demographic characteristics of the expected users as well as the devices they are expected to use. When such assessments include real-world users, participation by users **SHALL** be voluntary.
8. CSPs **SHALL** meet the following minimum performance thresholds for biometric usage in verification scenarios:
	- False match rate: 1:10,000 or better; and
	- False non-match rate: 1:100 or better 
9. CSPs **MAY** use 1:N matching in support of resolution or fraud detection, pursuant to a privacy risk assessment. In 1:N scenarios, CSPs **SHALL** meet a minimum performance threshold for false positive identifications of 1:1,000. This applies to, and **SHALL** be tested for, each demographic group. Tests demonstrating this requirement **SHALL** employ a gallery no smaller than 90% of the current or intended operational size (N).
10. CSPs that make use of 1:N biometric matching for either resolution or fraud prevention purposes **SHALL NOT** decline a user's enrollment without a manual review by a trained proofing agent or trusted referee to confirm the automated matching results and confirm the results are not a false positive identification (for example, twins submitting for different accounts with the same CSP). 
11. CSPs **SHALL** employ biometric technologies that provide similar performance characteristics for applicants of different demographic groups (age, race, sex, etc.). If significant performance differences across demographic groups are discovered, CSPs **SHALL** act expeditiously to provide redress options to affected individuals and to close performance gaps. 
12. All biometric performance tests **SHALL** be conformant to ISO/IEC 19795-1:2021 and ISO/IEC 19795-10:2024, including demographics testing.
13. CSPs **SHALL** make performance and operational test results publicly available.

The following requirements apply to CSPs who collect biometric characteristics from applicants:  

1. CSP **SHALL** collect biometrics in such a way that provides reasonable assurance that the biometric is collected from the applicant, and not another subject. 
2. When collecting and comparing biometrics remotely, the CSP **SHALL** implement presentation attack detection (PAD) capabilities, which meet IAPAR performance metric <0.15, to confirm the genuine presence of a live human being and to mitigate spoofing and impersonation attempts. 
3. When collecting biometrics onsite, the CSP **SHALL** have the operator view the biometric source (e.g., fingers, face) for the presence of non-natural materials and perform such inspections as part of the proofing process. All biometric presentation attack detection tests **SHALL** be conformant to ISO/IEC 30107-3:2023

### Requirements for Evidence Validation Processes (Authenticity Checks)
Evidence validation can be conducted by remote optical capture and inspection (often called document authentication or doc auth) or conducted by visual inspection of a trained proofing agent or trusted referee. CSPs may employ either or both processes for evaluating the authenticity of identity evidence. 

The following requirements apply to CSPs that employ optical capture and inspection for the purposes of determining document authenticity: 

1. Automated evidence validation technology **SHALL** meet the following performance measures:
	- Document false acceptance rate (DFAR) of .10 or less. [^Note_DFAR]
	- Document false rejection rate (DFRR) of .10 or less. [^Note_DFRR]
3. If a Machine Readable Zone (MRZ) or barcode is present on the evidence, the optical capture and inspection **SHALL** compare the MRZ data to the printed data on the evidence for consistency.
4. CSPs **SHALL** implement live capture of documents during the validation process. CSPs **SHOULD** deploy technology controls to prevent the injection of document images, for example using document presence checks (also called document liveness) or inspecting device characteristics to determine the presence of a virtual camera or device emulator.
5. CSPs **SHALL** assess the performance of employed optical capture and inspection technologies in conditions that are substantially similar to the operational environment and user base of the system. These tests **SHALL** account for all available identity evidence types that the CSPs allow to be validated using optical capture and inspection technology. Where subscribers' documents, PII, or images are used as part of the testing, it **SHALL** be on a voluntary basis and with subscriber notification and consent.
6. CSPs **SHOULD** have their evidence validation technology periodically tested by independent entities (e.g., accredited laboratories or research institutions) for their performance characteristics.
7. CSPs **SHALL** make the results of their testing available publicly.

> **Note:** These requirements apply to technologies that capture and validate images of physical identity evidence. They do not apply to validation techniques that rely on PKI or other cryptographic technologies that are embedded in the evidence themselves. 

The following requirements apply to CSPs that employ visual inspection of evidence by trained proofing agents or trusted referees for the purposes of determining document authenticity: 

1. Proofing agents and trusted referees **SHALL** be trained and provided resources to visually inspect all forms of evidence supported by the CSP. This training **SHALL** include:
	- Authentic layouts and topography of evidence types 
	- Physical security features (e.g., raised letters, holographic features, microprinting)
	- Techniques for assessing features (e.g., tools to be used, where tactile inspection is needed, manipulation to view specific features)
	- Common indications of tampering (e.g., damage to the lamination, image modification)
3. When the setting allows for it (e.g., onsite attended proofing events), proofing agents and trusted referees **SHALL** be provided with specialized tools and equipment to support the visual inspection of evidence (e.g., magnifiers, ultraviolet lights, barcode readers).
4. Proofing agents and trusted referees who conduct visual inspection via remote means **SHALL** be provided with devices and internet connections that support sufficiently high-quality imagery to be able to effectively inspect presented evidence. In these instances, the visual validation **SHOULD** be supported by automated document validation technologies that provide additional confidence in the authenticity of the evidence (e.g., submitting and validating evidence in advance of an attended remote session)
5. Proofing agents and trusted referees **SHALL** be reviewed regarding their ability to visually inspect evidence on an ongoing basis, and be assessed and certified with at least annual evaluations.

> **Note:** Due to the potential number and permutations of identity evidence, these guidelines do not attempt to provide a comprehensive list of security features. CSPs need to provide evidence validation training specific to the types of identity evidence they accept.

[^Note_DFAR]: For the purposes of this document, the DFAR is the proportion of processed, fraudulent documents that the document validation system determined to be valid divided by the number of processed fraudulent documents. DFAR is defined as the number of fraudulent documents processed that were deemed valid by a document validation system divided by the number of processed fraudulent documents.

[^Note_DFRR]: For the purposes of this document, DFRR is the proportion of processed, genuine documents which the document validation system determined to be invalid. DFRR is defined as the number of genuine documents processed that were deemed invalid by a document validation system divided by the number of processed genuine documents.

### Exception and Error Handling {#TRs-ARs}

Throughout the identity proofing process there are many points where errors or failures may occur. Such exceptions to a standard identity proofing workflow include: process failures, such as when a user does not possess the required evidence; technical failures, such as when an integrated service is not available; and failures due to user error, such as when an applicant is unable to capture a clear image of their identity evidence when using remote validation tools. 

In order to increase the accessibility, usability, and equity of their identity proofing services, CSPs **SHALL** document their operational processes for dealing with errors and handling exceptions. These documented processes **SHALL** include providing trusted referees to support those applicants who are otherwise unable to meet the requirements of IALs 1 and 2. Additionally, CSPs **SHOULD** support the use of applicant references who can vouch for an applicant's attributes, conditions, or identity.

#### Trusted Referees Requirements {#TRs}

To increase accessibility and promote equal access to online government services, CSPs provide trusted referees. Trusted referees are used to facilitate the identity proofing and enrollment of individuals who are otherwise unable to meet the requirements for identity proofing to a specific IAL. A non-exhaustive list of examples of such individuals and demographic groups includes: individuals who do not possess and cannot obtain the required identity evidence; persons with disabilities; older individuals; persons experiencing homelessness; individuals with little or no access to online services or computing devices; persons without a bank account or with limited credit history; victims of identity theft; individuals displaced or affected by natural disasters; and children under 18. The following requirements apply to the use of trusted referees:

1. The CSP **SHALL** provide notification to the public of the availability of trusted referee services and how such services are obtained.
2. The CSP **SHALL** establish written policies and procedures for the use of trusted referees as part of its practice statement, as specified in [Sec. 3.1.1](3_ialgen.md#DocRecReqs).
3. The CSP **SHALL** train and certify its trusted referees to make risk-based decisions that allow applicants to be successfully identity proofed based on their unique circumstances. At a minimum such training **SHALL** include:
	1. Document identification and validation, such as common templates, security features, layouts, and topography.
	2. Indicators of fraudulent documents, such as damage, tampering, modification, and material types
	3. Facial and image comparisons to conduct verification of applicants against presented documents
	4. Indicators of social engineering - such as distress, confusion, or coercion - exhibited by an applicant
	5. Annual recertification of the trusted referee's capabilities   
5. The CSP **SHALL** establish a record of any identity proofing session that involves a trusted referee, to include: what evidence was presented; which processes were completed (e.g., validation or verification); and, the reason(s) why a trusted referee was used (e.g., automated process failure, applicant request, established exception policy).
6. The CSP **MAY** offer trusted referee services for either onsite-attended or remote-attended sessions. These sessions **SHALL** be consistent with the requirements of these proofing types based on the IAL of the proofing event.

#### Trusted Referee Uses 

Trusted referees offer a critical path for those who are unable to complete identity proofing by other means. However, given the number of possible failures that may occur within the proofing process, it is essential for CSPs to define the uses for which a trusted referee can be applied within their own service offerings. The following requirements apply to defining the integration of trusted referees into the identity proofing process: 

1. CSPs **SHALL** document which types of exceptions and failures are eligible for the use of a trusted referee. 
2. CSPs **SHALL** offer trusted referee services for failures of automated verification processes (e.g., biometric comparisons).
3. CSPs **SHOULD** offer trusted referee services for failures in completing automated validation processes, such as in cases of mismatched core attributes or the absence of the applicant in a record source. 
	1. CSPs **SHALL** provide a policy for additional evidence types that may be used to corroborate core attributes or changes in core attributes.
	2. Trusted referees **SHALL** review additional evidence types for authenticity to the greatest degree allowed by the evidence. 
	3. If no authoritative or credible records are available to support validation, the trusted referee **MAY** compare the attributes on additional pieces of evidence with the strongest piece of evidence available to corroborate the consistency of core attributes.
	4. If there is a partial mismatch of core attributes to authoritative records, the trusted referee **SHALL** review evidence that supports the legitimacy of the asserted attribute value (e.g., recent move or change of name).

#### Applicant Reference Requirements {#ARs}

Applicant references are individuals who participate in the identity proofing of an applicant in order to vouch for the applicant's identity, attributes, or circumstances related to the applicant's ability to complete identity proofing. Applicant representatives are not agents of the CSP, but instead are representatives of the applicant who have sufficient knowledge to aide in the completion of identity proofing when other forms of evidence, validation, and verification are not available. 

The following requirements apply to the use of applicant references at IAL1 or IAL2:
 
1. The CSP **SHALL** provide notification to the public of the allowability of applicant references and any requirements for the relationship between the reference and an applicant.
2. The CSP **SHALL** establish written policies and procedures for the use of applicant references as part of its practice statement, as specified in [Sec. 3.1.1](3_ialgen.md#DocRecReqs).
3. The CSP **SHALL** identity proof an applicant reference to the same or higher IAL intended for the applicant. The CSP **SHALL** include the information collected, recorded, and retained for identity proofing the applicant references in its privacy risk assessment for identity proofing applicants, as required in section [Sec. 3.1.3](3_ialgen.md#PrivacyReqs).
4. The CSP **SHALL** record the use of an applicant reference in the subscriber account as well as maintain a record of the applicant reference and their relationship to the applicant.
5. The RP **SHALL** conduct a risk assessment to determine the applicability, business requirements, and potential risks associated with excluding or including applicant references for proofing events.

#### Uses of Applicant References 

Applicant references may take several different actions to support an applicant in the identity proofing process. CSPs and RPs **SHALL** establish all acceptable uses for applicant references in their Trust Agreements. These **MAY** include the following:

1. The applicant reference **MAY** vouch for one or more claimed core attributes relative to the applicant as part of evidence and attribute validation process.
2. The applicant reference **MAY** vouch for a specific condition or status of an applicant relative to the identity proofing process (e.g., homelessness, disaster scenarios) 
> **Note:** This information is intended to support risk determinations relative to the identity proofing event. Use of applicant reference statements relative to eligibility for status or benefits is outside the scope of these guidelines.
3. The applicant reference **MAY** vouch for the identity of the applicant in the absence of sufficient identity evidence.

In all instances, the CSP **SHALL** establish a record of the role the applicant reference played in the process and document these actions sufficient to support any applicable legal and regulatory requirements. This **MAY** include:

1. Capturing and recording the statements and assertions made by the applicant reference; 
2. Capturing an electronic, digital signature, or physical signature of the applicant reference; or,
3. Capturing consent and acknowledgement relative to the legal and liability impacts of the applicant reference's statements.  

CSPs **SHALL** make available to the applicant reference clear and understandable information relative to the legal and liability impacts that may result from their participation as an applicant reference. 

#### Establishing Applicant Reference Relationships 

In many cases, there will be business, legal, or fraud prevention reasons to confirm the relationship between the applicant and an applicant reference. Where such steps are deemed necessary by a risk assessment, the following requirements **SHALL** apply: 

1. The CSP and RP **SHALL** establish requirements for applicant reference relationship confirmation processes and document this in any Trust Agreements.
2. The CSP **SHALL** make a list of acceptable evidence of relationship available to the applicant reference prior to initiating the relationship confirmation process
3. The CSP **SHALL** request evidence of the applicant's relationship (e.g., notarized power of attorney, a professional certification)
4. Upon successfully identity proofing an applicant, the CSP **SHALL** record the evidence used to confirm the applicant reference's relationship to the applicant in the subscriber account.  


#### Requirements for Interacting with Minors {#Minors}

The following requirements apply to all CSPs providing identity proofing services to minors at any IAL.

1.  The CSP **SHALL** establish written policy and procedures as part of its practice statement for identity proofing minors who may not be able to meet the evidence requirements for a given IAL.
2.  When interacting with persons under the age of 13, the CSP **SHALL** ensure compliance with the Children's Online Privacy Protection Act of 1998 [[COPPA]](references.md#ref-COPPA), or other laws and regulations dealing with the protection of minors, as applicable.
3.  CSPs **SHALL** support the use of applicant references when interacting with individuals under the age of 18. 

## Elevating Subscriber IALs {#upgradeIAL}

CSPs **SHOULD** allow subscribers to elevate identity assurance levels related to their subscriber accounts to support higher assurance transactions with RPs. For CSPs supporting these functions the following apply:

1. CSPs **SHALL** document their approved approaches for elevating assurance levels in their practice statements.
2. CSPs **SHALL** require subscribers to authenticate at the highest AAL available on their account prior to initiating the upgrade process.
3. CSPs **SHALL** collect, validate, and verify additional evidence, as mandated to achieve the higher IAL.
4. CSPs **SHOULD** avoid collecting, validating, and verifying previously processed evidence, though they **MAY** do so based on the age of the account, indicators of fraud, or if evidence has become invalidated since the original proofing event.

