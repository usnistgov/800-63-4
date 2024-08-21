---
layout: default
title: Identity Proofing Requirements
navOrder: 5
navTitle: IAL
permalink: /sp800-63a/ial/
anchor: ial-section
section: 4
---

# Identity Assurance Level Requirements {#ial-section}

_This section is normative._

## Identity Assurance Level 1 Requirements {#IAL1}

Identity proofing processes at IAL1 allow for a range of acceptable techniques in order to detect the fraudulent claims to identities by malicious actors, while facilitating user adoption, minimizing the rejection of legitimate users, and reducing application departures. The use of biometric matching, such as the automated comparison of a facial portrait to supplied evidence, at IAL1 is optional, providing pathways to proofing and enrollment where such collection may not be viable. 

### Proofing Types 

1. IAL1 Identity Proofing **MAY** be delivered through any proofing type, as described in [Sec. 2.1.3](2_proofing.md#ProofingTypes).
2. CSPs **SHALL** offer Unattended Remote identity proofing as an option.
3. CSPs **SHALL** offer at least one method of Attended (Remote or Onsite) identity proofing as an option.
4. CSPs MAY combine proofing types and their stated requirements to create hybrid processes. For example, a CSP might leverage remote unattended identity proofing validation processes in advance of a remote attended session where verification will take place. Where such steps are combined, CSPs SHALL document their processes in alignment of requirements of each proofing type that is applied. 

### Evidence Collection {#ial1-evidence-collection}

For each identity proofing type, the CSP **SHALL** collect the following: 
 
1. One piece of FAIR evidence or better (i.e., STRONG, SUPERIOR) evidence

For onsite attended identity proofing at IAL1, organizations **SHOULD** prioritize the use of evidence (FAIR or STRONG) that contains a facial portrait, which can be used for verification purposes. While forms of evidence that do not contain a facial portrait **MAY** be used for such sessions, the associated verification requirements (e.g., returning a confirmation code) may result in additional burden on applicants.

### Attribute Collection {#ial1-attribute-collection}

The CSP **SHALL** collect all Core Attributes. Validated evidence is the preferred source of identity attributes. If the presented identity evidence does not provide all the attributes that the CSP considers core attributes, it **MAY** collect attributes that are self-asserted by the applicant.

### Evidence Validation {#ial1-evidence-validation}

Each piece of evidence presented **SHALL** be validated using one of the following techniques: 

1. Confirming the authenticity of digital evidence through interrogation of digital security features (e.g., signatures on assertions or data).
2. Confirming the authenticity of physical evidence using automated scanning technology able to detect physical security features.
3. Confirming the integrity of physical security features of presented evidence through visual inspection by a proofing agent using real-time or asynchronous processes (e.g., offline manual review).
4. Confirming the integrity of physical security features through physical and tactile inspection of security features by a proofing agent at an onsite location. 

### Attribute Validation {#ial1-attribute-validation}

1. The CSP **SHALL** validate all core attributes and the government identifier against an authoritative or credible source to determine accuracy.
2. CSPs **SHOULD** correlate the data on evidence, self-asserted, and as presented by credible and authoritative sources for consistency.
3. CSPs **SHOULD** validate the reference numbers of presented identity evidence if available.

### Verification Requirements {#ial1-verification}

The CSP **SHALL** verify the applicant's ownership of one piece of evidence using one of the following processes:  

1. Confirming the applicant's ability to return a confirmation code delivered to a validated address associated with the evidence;
2. Confirming the applicant's ability to return a micro-transaction value delivered to a validated financial or similar account;
3. Confirming the applicant's ability to successfully complete an authentication and federation protocol equivalent to AAL2/FAL2, or higher, to access an account related to the identity evidence;
4. Comparing the applicant's facial image to a facial portrait on evidence via an automated comparison.
5. Visually comparing the applicant's facial image to a facial portrait on evidence, or in records associated with the evidence, during either an onsite attended session (in-person with a proofing agent), a remote attended session (live video with a proofing agent), or an asynchronous process (i.e., visual comparison made by a proofing agent at a different time).
6. Comparing a stored biometric on identity evidence, or in authoritative records related to the evidence, to a sample provided by the applicant. 

### Remote Attended Requirements 

1. All video sessions **SHALL** take place using a service that allows for the exchange of information over an authenticated protected channel.
2. During the video session, the applicant **SHALL** remain in view of the proofing agent during each step of the proofing process.
3. The video quality **SHALL** be sufficient to support the necessary steps in the validation and verification processes, such as inspecting evidence and making visual comparisons of the user to the evidence.
4. The proofing agent **SHALL** be trained to identify signs of manipulation, coercion, or social engineering occurring during the recorded session.
5. CSPs **MAY** record and maintain video sessions for fraud prevention and prosecution purposes pursuant to a privacy risk assessment, as defined in [Sec. 3.1.3.1](3_ialgen#PrivRiskAssess). If the CSP records session, the following further requirements apply: 
	1. The CSP **SHALL** notify the applicant of the recording prior to initiating a recorded session.
	2. The CSP **SHALL** gain consent from the applicant to prior to initiating a recorded session.
	3. The CSP **SHALL** publish their retention schedule and deletion processes for all video records. 
6. The CSP **SHOULD** introduce challenges and response features into their video sessions that are randomized or periodically changed to deter deep fakes and pre-recorded materials from being used to defeat the proofing process. These MAY be shifting questions, changes to the orders of sessions, or physical cues that would be hard for attackers to predict.
7. The CSP **SHALL** provide proofing agents with a method or mechanism to flag events for potential fraud. 

### Onsite Attended Requirements 

1. The CSP **SHALL** provide a physical setting in which onsite identity proofing sessions are conducted.
2. The CSP **SHALL** ensure all information systems and technology leveraged by proofing agents and trusted referees are protected consistent with FISMA Moderate or comparable levels of controls.
3. CSP proofing agents **SHALL** be trained to identify signs of manipulation, coercion, or social engineering occurring during the onsite session.
4. CSPs **MAY** record and maintain video sessions for fraud prevention and prosecution purposes pursuant to a privacy risk assessment, as defined in [Sec. 3.1.3.1](3_ialgen#PrivRiskAssess). If the CSP records session, the following further requirements apply: 
	1. The CSP **SHALL** notify the applicant of the recording prior to initiating a recorded session.  
	2. The CSP **SHALL** gain consent from the applicant prior to initiating a recorded session. 
	3. The CSP **SHALL** publish their retention schedule and deletion processes for all video records. 
5. The CSP **SHALL** provide proofing agents with a method or mechanism to safely flag events for potential fraud. 

### Onsite Unattended Requirements (Devices & Kiosks)  

1. All devices **SHALL** be safeguarded from tampering through either observation by CSP representatives or through physical and digital tamper prevention features.
2. All devices **SHALL** be protected by appropriate baseline security features comparable to FISMA Moderate controls – including Malware Protection, Admin Specific Access Controls, and Software Update processes.
3. All devices **SHALL** be inspected periodically by trained technicians to deter tampering, modification, or damage. 

### Initial Authenticator Binding

Upon the successful completion of the identity proofing process, a unique subscriber account is established and maintained for the applicant (now subscriber) in the CSP's identity system. One or more authenticators can be associated (bound) to the subscriber's account, either at the time of identity proofing or at a later time. See [Sec. 5](5_accounts.md#accounts) for more information about subscriber accounts.

1. The CSP **SHALL** provide the ability for the applicant to bind an authenticator using one of the following methods: 
	1. The remote enrollment of a subscriber-provided authenticator, consistent with the requirements for the authenticator type as defined in [Sec. 4.1.3 of [SP800-63B]](../_sp800-63b/4_events.md#bind-subscriber-authenticator){:latex-href="#ref-SP800-63B"}.
	3. Distribution of a physical authenticator to a validated address of record. 
	4. Distribution or onsite enrollment of an authenticator. 
2. Where authenticators are bound outside of a single protected session with the user, the CSP **SHALL** confirm the presence of the intended subscriber through one of the following methods: 
	1. Return of an confirmation code, or 
	2. Comparison against a biometric collected at the time of proofing. 
	
### Notification of Proofing

Upon the successful completion of identity proofing at IAL1, the CSP **SHALL** send a notification of proofing to a validated address for the applicant, as specified in [Sec. 3.1.10](3_ialgen.md#ProofingNotifs).

## Identity Assurance Level 2 Requirements {#IAL2}

IAL2 identity proofing includes additional evidence, validation, and verification requirements in order to provide increased mitigation against impersonation attacks and other identity proofing errors relative to IAL1. IAL2 can be achieved through a number of different types of proofing (e.g., remote unattended, remote attended, etc.) and identity verification at IAL2 can be accomplished with or without the use of biometrics. To provide clear options to achieving IAL2, this section presents three different pathways to achieving alignment with IAL2 outcomes and requirements: IAL2 Verification - Non-Biometric Pathway; IAL2 Verification - Biometric Pathway; and IAL2 Verification - Digital Evidence Pathway. These different options do not imply different security or assurance outcomes; instead they present requirements in a manner that allows for clear selection of non-biometric methods that can be used to achieve IAL2.

### Proofing Types 

1. Identity proofing at IAL2 **MAY** be delivered through any proofing type, as described in [Sec. 2.1.3](2_proofing.md#ProofingTypes).
2. CSPs **SHALL** offer Unattended Remote identity proofing as an option. 
3. CSPs **SHALL** offer at least one method of Attended (Remote or Onsite) identity proofing as an option.
4. CSPs **MAY** combine elements of different proofing types to create hybrid processes. For example, a CSP might leverage remote unattended identity proofing validation processes in advance of a remote attended session where verification will take place. If a CSP employs a hybrid process, it **SHALL** document how the process satisfies the requirements associated with the associated proofing types.

### Evidence Collection {#ial2-evidence-collection}

For all types of proofing the CSP **SHALL** collect:

1. One piece of FAIR Evidence and one piece of STRONG; or
2. One piece of SUPERIOR.

### Attribute Collection {#ial2-attribute-collection}

Same as IAL1 

### Evidence Validation  {#ial2-evidence-validation}

1. Each piece of FAIR or STRONG evidence presented **SHALL** be validated using one of the following techniques.
	1. Confirming the authenticity of digital evidence through interrogation of digital security features (e.g., signatures on assertions or data).
	2. Confirming the authenticity of physical evidence using automated scanning technology able to detect physical security features.
	3. Confirming the integrity of physical security features of presented evidence through visual inspection by a proofing agent using real-time or asynchronous processes (e.g., offline manual review).
	4. Confirming the integrity of physical security features through physical and tactile inspection of security features by a proofing agent at an onsite location.
2. Each Piece of SUPERIOR evidence **SHALL** be validated through cryptographic verification of the evidence contents and the issuing source, including digital signature verification and the validation of any trust chain back to a trust anchor. SUPERIOR evidence unable to be validated using cryptographic verification **SHALL** be considered STRONG evidence and validated consistent with the requirements above.

### Attribute Validation {#ial2-attribute-validation}

1. The CSP **SHALL** validate all core attributes by either: 
	1. Comparing the government identifier and core attributes against an authoritative or credible source to determine accuracy; or 
	2. Validating the accuracy of digitally signed attributes contained on SUPERIOR evidence through the public key of the issuing source. 
2. CSPs **SHOULD** correlate the attributes collected from evidence, self-assertion, and as presented by credible and authoritative sources for consistency.
3. CSPs **SHOULD** validate the reference numbers of presented identity evidence if available.

### Verification Requirements  {#ial2-verification}

Verification pathways **SHOULD** be implemented consistent with relevant policy and be responsive to the use cases, populations, and threat environment of the online service being protected. CSPs **SHOULD** deploy more than one pathway to IAL2 verification and **MAY** combine pathways in order to achieve desired outcomes. 

#### IAL2 Verification - Non-Biometric Pathway

The IAL2 Non-Biometric Pathway provides verification methods that do not use automated comparison of biometric samples provided by the applicant. Non-biometric processes will often still include biometric data being collected and verified - for example, through a visual comparison performed by a proofing agent and images contained on identity evidence - but comparisons are not done through automated means. Additional verification methods that may not require the use of automated biometric comparison are also included in the IAL2 Verification - Digital Evidence Pathway requirements specified in [Sec. 4.2.6.2](4_ial.md#dig-evidence-pathway).

1. The CSP **SHALL** verify the applicant's ownership of all presented identity evidence.
2. Approved non-biometric methods for verifying FAIR evidence at IAL2 include:  
	1. Confirming the applicant's ability to return a confirmation code delivered to a validated address associated with the evidence (e.g., postal address, email address, phone number)
	2. Visually comparing the applicant's facial image to a facial portrait on evidence, or in records associated with the evidence, during either an onsite attended session (in-person with a proofing agent), a remote attended session (live video with a proofing agent), or an asynchronous process (i.e., visual comparison made by a proofing agent at a different time)
2. Approved non-biometric methods for verifying STRONG and SUPERIOR evidence at IAL2 include: 
	1. Confirming the applicant's ability to return a confirmation code delivered to a physical address (i.e., postal address) that was obtained from the evidence and was validated with an authoritative source
	2. Visually comparing the applicant's facial image to a facial portrait on evidence, or in records associated with the evidence, during either an onsite attended session (in-person with a proofing agent), a remote attended session (live video with a proofing agent), or an asynchronous process (i.e., visual comparison made by a proofing agent at a different time)

~~~
\clearpage
~~~
{:latex-literal="true"}

#### IAL2 Verification - Digital Evidence Pathway {#dig-evidence-pathway}

The IAL2 Digital Evidence Pathway provides a means of allowing individuals to make use of digital forms of evidence, such as digital credentials (sometimes referred to as _digital identity documents_) or digital accounts as part of the verification process. This pathway achieves verification by confirming the individual's ability to access evidence through digital means.

1. The CSP **SHALL** verify the applicant's ownership of all pieces of presented identity evidence.
2. Approved digital evidence verification methods for FAIR evidence at IAL2 include: 
	1. Confirming the applicant's ability to return a micro-transaction value delivered to a validated account (e.g., a checking account)
	2. Confirming the applicant's ability to return a confirmation code delivered to a validated digital address associated with the digital evidence (e.g., MNO/Phone account)
	3. Confirming the applicant's ability to successfully complete an authentication and federation protocol equivalent to AAL2/FAL2 to access an account related to the identity evidence
2. Approved digital evidence verification methods for STRONG evidence at IAL2 include: 
	1. Confirming the applicant's ability to successfully complete an authentication and federation protocol equivalent to AAL2/FAL2, or higher, to access an account related to the identity evidence
3. Approved digital evidence verification methods for SUPERIOR evidence at IAL2 include: 
	1. Confirming the applicant's ability to successfully complete an authentication and federation protocol equivalent to AAL3/FAL2, or higher, to access an account related to the identity evidence
     
#### IAL2 Verification - Biometric Pathway

The IAL2 Biometric Pathway provides verification methods that support automated comparison of biometric samples provided by the applicant.

1. The CSP **SHALL** verify the applicant's ownership of all pieces of presented identity evidence.
2. Approved biometric methods for verifying FAIR evidence at IAL2 include:
	3. Comparing the applicant's facial image to a facial portrait on evidence via an automated comparison
1. Approved methods for verifying STRONG and SUPERIOR evidence for use in the IAL2 Biometric Pathway include:
	3. Comparing the applicant's facial image to a facial portrait on evidence via an automated comparison
	4. Comparing, via automated means, a non-facial portrait biometric stored on identity evidence, or in-records associated with the evidence, to a live sample provided by the applicant
    
### Remote Attended Requirements 

Same as IAL1.

### Onsite Attended Requirements 
Same as IAL1.

### Onsite Unattended Requirements (Devices & Kiosks)  

Same as IAL1. 

### Notification of Proofing

Same as IAL1.

### Initial Authenticator Binding 

Same as IAL 1.

## Identity Assurance Level 3 {#IAL3}

IAL3 adds additional rigor to the steps required at IAL2 and is subject to additional and specific processes (including the use of biometric information comparison, collection, and retention) to further protect the identity and RP from impersonation and other forms of identity fraud. In addition, identity proofing at IAL3 must be attended by a CSP proofing agent, as described in [Sec. 2.1.2](2_proofing.md#ProofingRoles).

### Proofing Types 

IAL 3 Identity Proofing **SHALL** only be delivered as Onsite Attended. The Proofing Agent **MAY** be collocated or attend the proofing session remotely via a CSP controlled kiosk or device. 
   
### Evidence Collection {#ial3-evidence-collection}

1. For all types of IAL 3 identity proofing the CSP **SHALL** collect either: 
	1. One piece of STRONG and one piece of FAIR (or better), or 
	2. One piece of SUPERIOR
    
### Attribute Requirements {#ial3-attribute-collection}

1. The CSP **SHALL** collect all core attributes. Validated evidence is the preferred source of identity attributes. If the presented identity evidence does not provide all the attributes that the CSP considers core attributes, it **MAY** collect attributes that are self-asserted by the applicant.
2. The CSP **SHALL** collect and retain a biometric sample from the applicant during the identity proofing process to support account recovery, non-repudiation, and establish a high level of confidence that the same participant is present in the proofing and issuance processes (if done separately). CSPs **MAY** choose to periodically re-enroll user biometrics based on the modalities they use and the likelihood that subscriber accounts will persist long enough to warrant such a refresh.

### Evidence Validation {#ial3-evidence-validation}

1. Each piece of FAIR or STRONG evidence presented **SHALL** be validated using one of the following techniques.
	1. Confirming the authenticity of digital evidence through interrogation of digital security features (e.g., signatures on assertions or data).
	2. Confirming the authenticity of physical evidence using automated scanning technology able to detect physical security features.
	3. Confirming the integrity of physical security features of presented evidence through physical inspection by a proofing agent using real-time or asynchronous processes (e.g., offline manual review).
	4. Confirming the integrity of physical security features through physical and tactile inspection of security features by a proofing agent at an onsite location. 
2. Each Piece of SUPERIOR evidence **SHALL** be validated through cryptographic verification of the evidence contents and the issuing source, including digital signature verification and the validation of any trust chain back to a trust anchor.
   
### Attribute Validation  {#ial3-attribute-validation}

1. The CSP **SHALL** validate all core attributes by either:
	1. Comparing the core attributes against an authoritative or credible source to determine accuracy; or
	2. Validating the accuracy of digitally signed attributes contained on SUPERIOR evidence through the public key of the issuing source.
2. CSPs **SHOULD** correlate the attributes collected from evidence, self-assertion, and as presented by credible and authoritative sources for consistency.
3. CSPs **SHOULD** validate the reference numbers of presented identity evidence if available.

   
### Verification Requirements  {#ial3-verification}

1. The CSP **SHALL** verify the applicants ownership of the strongest piece of evidence (STRONG or SUPERIOR) by one of the following methods:
	1. Confirming the applicant's ability to successfully authenticate to a physical device or application (for example a mobile driver's license) and comparing a digitally protected and transmitted facial portrait to the applicant.
	2. Comparing the applicant's facial image to the facial portrait on evidence via an automated comparison.
	3. Visually comparing the applicant's facial image to the facial portrait on evidence, either during an onsite attended session or a remote attended session (live video).
	4. Comparing a stored biometric on identity evidence, or in authoritative records associated with the evidence, to a sample provided by the applicant.

### Onsite Attended Requirements (Locally Attended)

1. The CSP **SHALL** provide a secure, physical setting in which onsite identity proofing sessions are conducted.
2. The CSP **SHALL** provide sensors and capture devices for the collection of biometrics from the applicant.
3. The CSP **SHALL** have the proofing agent view the source of the collected biometric for the presence of any non-natural materials.
4. The CSP **SHALL** have the proofing agent collect the biometric samples in such a way that ensures the sample was collected from the applicant and no other source.
5. The CSP **SHALL** ensure all information systems and technology leveraged by proofing agents and trusted referees are protected consistent with FISMA Moderate or comparable levels of controls to include physical controls for the proofing facility.
6. CSP proofing agents **SHALL** be trained to identify signs of manipulation, coercion, or social engineering occurring during the onsite session.
7. CSPs **MAY** record and maintain video sessions for fraud prevention and prosecution purposes pursuant to a privacy risk assessment, as defined in [Sec. 3.1.3.1](3_ialgen.md#PrivRiskAssess). If the CSP records session, the following further requirements apply:
	1. The CSP **SHALL** notify the applicant of the recording prior to initiating a recorded session.
	2. The CSP **SHALL** gain consent from the applicant to prior to initiating a recorded session.
	3. The CSP **SHALL** publish their retention schedule and deletion processes for all video records.
8. The CSP **SHALL** provide proofing agents with a method or mechanism to safely flag events for potential fraud.

### Onsite Attended Requirements (Remotely Attended - Formerly Supervised Remote Identity Proofing) 

1. The CSP **MAY** offer a remote means of interacting with a proofing agent whereby the agent and the applicant do not have to be at the same facility. In this scenario, the following requirements apply:   
	1. The CSP **SHALL** monitor the entire identity proofing session through a high-resolution video transmission with the applicant.
	2. The CSP **SHALL** have a live proofing agent participate remotely with the applicant for the evidence collection, evidence validation, and verification steps of the identity proofing process. Data entry of attributes for resolution and enrollment **MAY** be done without the presence of a live proofing agent. 
	4. The CSP **SHALL** require all actions taken by the applicant during the evidence collection, evidence validation, and verification steps to be clearly visible to the remote proofing agent. 
	5. The CSP **SHALL** require that all digital validation and verification of evidence (e.g., via chip or wireless technologies) be performed by integrated scanners and sensors (e.g., embedded fingerprint reader).
	6. All devices used to support interaction between the proofing agent and the applicant**SHALL** be safeguarded from tampering through observation by CSP representatives or monitoring devices (e.g., cameras) and through physical and digital tamper prevention features. 
	7. All devices used to support interaction between the proofing agent and the applicant **SHALL** be protected by appropriate baseline security features comparable to FISMA Moderate controls, including malware protection, admin-specific access controls, and software update processes.
	8. All devices used to support interaction between the proofing agent and the applicant **SHALL** be inspected periodically by trained technicians to deter tampering, modification, or damage.

### Notification of Proofing

Same as IAL1.

### Initial Authenticator Binding

1. The CSP **SHALL** distribute or enroll the applicant's initial authenticator during an onsite attended interaction with a proofing agent. 
2. If the CSP distributes or enrolls the initial authenticator outside of a single, protected session with the user, the CSP **SHALL** compare a biometric sample collected from the applicant to the one collected at the time of proofing, prior to issuance of the authenticator. 
3. The CSP **MAY** request that the applicant bring the identity evidence used during the proofing process to the issuance event to further strengthen the process of binding the authenticators to the applicant. 

~~~
\clearpage
~~~
{:latex-literal="true"}

## Summary of Requirements {#summary}
[Table 1](4_ial.md#table-1) summarizes the requirements for each of the identity assurance levels:

[Table 1. IAL Requirements Summary](4_ial.md#table-1){:name="table-1"}
{:latex-ignore="true"}

{::nomarkdown type="latex"}\AtBeginEnvironment{tabulary}{\small}{:/}

| Process | IAL1 | IAL2 | IAL3 |
|:------------|:-------|:-------|:-------|
| Proofing Types | Remote Unattended <br />{::nomarkdown type="latex"}\par {:/} Remote Attended <br />{::nomarkdown type="latex"}\par {:/} Onsite Unattended <br />{::nomarkdown type="latex"}\par {:/} Onsite Attended | Same as IAL1 | Onsite Attended |
| Evidence Collection | _Unattended:_ <br />{::nomarkdown type="latex"}\par {:/} --1 FAIR or <br />{::nomarkdown type="latex"}\par {:/} --1 STRONG <br />{::nomarkdown type="latex"}\par {:/} _Attended:_ <br />{::nomarkdown type="latex"}\par {:/} --1 FAIR w/ image or <br />{::nomarkdown type="latex"}\par {:/} --1 STRONG | _For all proofing types:_ <br />{::nomarkdown type="latex"}\par {:/} --1 FAIR and 1 STRONG or <br />{::nomarkdown type="latex"}\par {:/} --1 SUPERIOR | --1 STRONG + 1 FAIR or <br />{::nomarkdown type="latex"}\par {:/} --1 SUPERIOR |
| Attribute Collection | All Core Attributes | All Core Attributes | All Core Attributes + Biometric Sample |
| Evidence Validation | _Physical Evidence:_ <br />{::nomarkdown type="latex"}\par {:/} --automated doc auth. <br />{::nomarkdown type="latex"}\par {:/} --visual inspection <br />{::nomarkdown type="latex"}\par {:/} _Digital Evidence:_ <br />{::nomarkdown type="latex"}\par {:/} --interrogation of digital security features | _Physical Evidence:_<br />{::nomarkdown type="latex"}\par {:/} --automated doc. auth. <br />{::nomarkdown type="latex"}\par {:/} --visual inspection <br />{::nomarkdown type="latex"}\par {:/} --physical/tactile inspection <br />{::nomarkdown type="latex"}\par {:/} _Digital Evidence:_  <br />{::nomarkdown type="latex"}\par {:/} --interrogation of digital security features <br />{::nomarkdown type="latex"}\par {:/} _SUPERIOR Evidence:_  <br />{::nomarkdown type="latex"}\par {:/} --Dig. sig. verification | _Physical Evidence:_ <br />{::nomarkdown type="latex"}\par {:/} --automated doc. auth. <br />{::nomarkdown type="latex"}\par {:/} --physical inspection <br />{::nomarkdown type="latex"}\par {:/} --physical/tactile inspection <br />{::nomarkdown type="latex"}\par {:/} _Digital Evidence:_ <br />{::nomarkdown type="latex"}\par {:/} --interrogation of digital security features <br />{::nomarkdown type="latex"}\par {:/} _SUPERIOR Evidence:_<br />{::nomarkdown type="latex"}\par {:/} --Dig. sig. verification |
| Attribute Validation | Confirmation of core attributes against authoritative or credible sources. | Confirmation of core attributes against authoritative or credible sources. <br />{::nomarkdown type="latex"}\par {:/} Confirmation of digitally signed attributes through signature verification. | <br />{::nomarkdown type="latex"}\par {:/} Confirmation of core attributes against authoritative or credible sources. <br />{::nomarkdown type="latex"}\par {:/} Confirmation of digitally signed attributes through digital signature verification. |
| Verification | Verify applicant's ownership of either the FAIR evidence or the STRONG evidence per 4.1.6 | Verify applicant's ownership of all presented evidence using methods provided in 4.2.6 | Verify applicant's ownership of all presented evidence using methods provided in 4.3.6 |
{:latex-table="1" latex-caption="IAL Requirements Summary" latex-columns="p@0.15\textwidth,p@0.25\textwidth,p@0.25\textwidth,p@0.25\textwidth"}

{::nomarkdown type="latex"}\AtBeginEnvironment{tabulary}{\normalsize}{:/}

