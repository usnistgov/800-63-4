---
layout: default
title: Identity Proofing Overview
navOrder: 3
navTitle: Proofing
permalink: /sp800-63a/proofing/
anchor: ipv-section
section: 2
---

# Identity Proofing Overview {#ipv-section}

_This section is normative._

This section provides an overview of the identity proofing and enrollment process, as well as requirements to support the resolution, validation, and verification of the identity claimed by an applicant. It also provides guidelines on additional aspects of the identity proofing process.  These requirements are intended to ensure that the claimed identity exists in the real world and that the applicant is the individual associated with that identity. 

Additionally, these guidelines provide for multiple methods by which resolution, validation, and verification can be accomplished, as well as providing the multiple types of identity evidence that support the identity proofing process. CSPs and organizations **SHALL** provide options when implementing their identity proofing services and processes to promote access for applicants with different means, capabilities, and technology access. These options **SHOULD** include accepting multiple types and combinations of identity evidence; supporting multiple data validation sources; enabling multiple methods for verifying identity; providing multiple channels for engagement (e.g., onsite, remote); and offering assistance mechanisms for applicants (e.g., applicant references). 

CSPs **SHALL** evaluate the risks associated with each identity proofing option offered (e.g., identity proofing types, validation sources, assistance mechanisms) and implement mitigating fraud controls, as appropriate. At a minimum, CSPs **SHALL** design each option such that, in aggregate, the options provide comparable assurance.

## Identity Proofing and Enrollment

The objective of identity proofing is to ensure that, to a stated level of certainty, the applicant involved in the identity proofing process is who they claim to be. This document presents a three-step process for CSPs to identity proof applicants at designated assurance levels. The first step, identity resolution, consists of collecting appropriate identity evidence and attribute information to determine that the applicant is a unique identity in the population served by the CSP and is a real-life person. The second step, identity validation, validates the genuineness, accuracy, and validity of the evidence and attribute information collected in the first step. The third step, identity verification, confirms that the applicant presenting the identity evidence is the same individual to whom the validated evidence was issued and with whom the validated attributes are associated. In most cases, upon successfully identity proofing an applicant to the designated IAL, the CSP establishes a unique subscriber account for the applicant (now a subscriber in the identity service), which allows one or more authenticators to be bound to the proven identity in the account.

Identity proofing can be part of an organization's business processes that support the determination of suitability or entitlement to a benefit or service. While these guidelines provide guidance for appropriate levels of identity assurance, suitability and eligibility determinations for benefits or services are distinct business process decisions from these identity proofing processes and are outside the scope of these guidelines.

### Process Flow

_This subsection is informative._

[Figure 1](2_proofing.md#fig-1) provides an illustrative example of the three-step identity proofing process.

[Fig. 1. Identity Proofing Process](2_proofing.md#fig-1){:name="fig-1"}
{:latex-ignore="true"}

![Illustration of steps in identity proofing and enrollment]({{site.baseurl}}/{{page.collection}}/images/ProofingProcess.png 'Identity Proofing Process'){:latex-src="ProofingProcess.pdf" latex-fig="1" latex-place="h"}

The following steps present a common workflow example for IAL2 remote identity proofing, which is intended to illustrate the workflow steps for this example. These steps are not intended to represent a normative processing workflow model.

1. **Resolution**

	- The CSP captures one or more pieces of identity evidence, such as a driver's license, mobile driver's license, or passport.
	- The CSP collects any additional attributes, as needed, from the applicant to supplement those contained on the presented identity evidence. 
   
3. **Validation**

	- The CSP confirms the presented evidence is authentic, accurate, and valid (e.g., not revoked).
	- The CSP validates the attributes obtained in step 1 by checking them against authoritative or credible validation sources.{::nomarkdown type="latex"}\clearpage {:/}
   
5. **Verification**

	- The CSP employs one of the IAL2 Verifcation Pathways to confirm the applicant is the genuine owner of the presented identity evidence.

	**Enrollment**

	Upon the successful completion of the three identity proofing steps, a notification of proofing is sent to a validated address, and the applicant can be enrolled into a subscriber account with the CSP, as described in Section 5. A subscriber account includes at least one validated address (e.g., phone number, mailing address) that can be used to communicate with the subscriber about their account. Additionally, one or more authenticators are bound to the proven identity in the subscriber account.

### Identity Proofing Roles {#ProofingRoles}

To support the delivery of identity proofing that meets the various needs of applicants and risk scenarios, different individuals would be expected to play different roles within the proofing process. To support the consistent implementation of these guidelines, the following identity proofing roles are defined: 

1.	**Proofing Agent** - An agent of the CSP who is trained to attend identity proofing sessions, either onsite or remotely, and make limited, risk-based decisions – such as visually inspecting identity evidence and making a determination that the evidence has not been altered. 
2.	**Trusted Referee** - An agent of the CSP who is trained to make risk-based decisions regarding an applicant's identity proofing case when that applicant is unable to meet expected requirements of a defined IAL proofing process. Unlike a Proofing Agent (although a trusted referee may also fulfill this role), the level of training is expected to be more substantial to include training to detect deception and signs of social engineering, in addition to the ability to support validation and verification through physical inspection of the evidence and visual comparison of the applicant to a reference facial image. Requirements for trusted referees are contained in [Sec. 3.1.13.1](3_ialgen.md#TRs).
  > **Note:** Trusted referees differ from proofing agents in that trusted referees receive additional training and resources to support exception handling scenarios, including when applicants do not possess the required identity evidence or the attributes on the evidence do not all match the claimed identity (e.g., due to a recent name or address change). 
3.	**Applicant Reference** - A representative of the applicant who can vouch for the identity of the applicant, specific attributes related to the applicant, or conditions relative to the context of the individual (e.g., emergency status, homelessness). This individual does not act on behalf of the applicant in the identity proofing process but is a resource that can be called on to support claims of identity. Requirements for applicant references are contained in [Sec. 3.1.13.3](3_ialgen.md#ARs).
4.	**Process Assistants** - An individual who provides support for the proofing process but does not support decision making or risk-based evaluation (e.g., translation, transcription, or accessibility support). Process assistants may be provided by the CSP or the applicant. 

CSPs **SHALL** identify which of above roles are applicable to their identity service and **SHALL** provide training and support resources consistent with the requirements and expectations provided in [Sec. 3](3_ialgen.md#ial-general).

### Identity Proofing Types {#ProofingTypes}

The ability to provide resolution, validation, and verification as part of an identity proofing process is delivered through a combination of technologies, communication channels, and identity proofing roles to support the diverse users, communities, and relying parties CSPs serve. The types of proofing can be categorized based on two specific factors – whether they are attended and where they take place.

1. **Remote Unattended Identity Proofing** – Identity proofing conducted where the resolution, validation, and verification processes are completely automated and interaction with a proofing agent is not required.  The location and devices used in the proofing process are not controlled by the CSP.
2. **Remote Attended Identity Proofing** – Identity proofing conducted where the applicant completes resolution, validation, and verification steps through a secure video session with a proofing agent. The location and devices used in the proofing process are not controlled by the CSP.
3. **Onsite Unattended Identity Proofing** -  Identity proofing conducted where an individual interacts with a controlled workstation or kiosk, but interaction with a proofing agent is not required. The process is fully automated, but at a physical location and on devices approved by the CSP.
4. **Onsite Attended Identity Proofing** - Identity proofing conducted in a physical setting where the applicant completes the entire identity proofing process - to include resolution, validation, and verification – in the presence of a proofing agent. The proofing agent may be co-located with the user or interact with the user via a kiosk or device. The physical location and devices are all approved by the CSP.   
   
Requirements at each assurance level are structured to allow CSPs to implement different combinations of proofing types to meet the requirements of different assurance levels (as appropriate). CSPs that offer IAL1 & IAL2 services **SHALL** provide a Remote Unattended identity proofing process and **SHALL** offer at-least one attended identity proofing process option. CSPs that offer IAL1 & IAL2 services **SHOULD** support identity proofing processes that allow for the applicant to transition between proofing types in the event an applicant is unsuccessful with one type (e.g., allow an applicant who fails remote unattended to transition to remote attended). 

## Core Attributes {#CoreAttributes}

The identity proofing process involves the presentation and validation of the minimum attributes necessary to accomplish identity proofing - this includes what is needed to complete resolution, validation, and verification. While the necessary core attributes for a given use case will change based on the nature of the community being served, the following attributes **SHOULD** be collected by CSPs to support the proofing process: 

- **First Name**: The applicant's given name.
- **Middle Name or Initial**: The applicant's middle name or initial if available.
- **Last Name**: The applicant's last name or family name as appropriate.
- **Government Identifier**: A unique identifier which is associated with the applicant in government records (e.g., SSN, TIN, Driver's License #).
- **Physical Address**: A physical address to which the applicant can receive communications related to the proofing process; or a **Digital Address**: A digital address (e.g., phone or email) to which the applicant can receive communications related to the proofing process. 

Additional attributes may be added to these as required by the CSP and RP. The CSP and RP **SHALL** document all core attributes in trust agreements and practice statements. Following a privacy risk assessment, a CSP **MAY** request additional attributes that are not required to complete identity proofing, but that may support other RP business processes. See [Sec. 3.1.3](3_ialgen.md#PrivacyReqs) for details on privacy requirements for requesting additional attributes. 

## Identity Resolution {#resolve}

The goal of identity resolution is to use the smallest possible set of attributes to uniquely and accurately distinguish an individual within a given population or context. This step involves comparing an applicant's collected attributes to those stored in records for users served by the CSP. While identity resolution is the starting point in the overall identity proofing process, to include the initial detection of potential fraud, it in no way represents a complete and successful identity proofing process.

## Identity Validation and Identity Evidence Collection {#evidence-collection}

The goal of identity validation is to collect the most appropriate identity evidence from the applicant and determine that it is genuine (not altered or forged), accurate (the pertinent data is correct, current, and related to the applicant), and valid. 

> **Note:** This document uses the term "valid" rather than expired in recognition that evidence can remain a useful means to prove identity, even if it is expired or was issued outside a determined timeframe. 

Identity evidence collection supports the identity validation process and consists of two steps: 1) the presentation of identity evidence by the identity proofing applicant to the CSP and 2) the determination by the CSP that the presented evidence meets the applicable strength requirements. 

###  Evidence Strength Requirements {#evidence-strength}

This section defines the requirements for identity evidence at each strength. The strength of a piece of identity evidence is determined by: 

1. The issuing rigor, 
2. The ability to provide confidence in validation, including accuracy and authenticity checks, and 
3. The ability to provide confidence in the verification of the applicant presenting the evidence. 
	
[Appendix A](A_evidence.md#EvidenceExamples) of this document provides a non-exhaustive list of possible evidence types, grouped by strength. 

#### Fair Evidence Requirements

To be considered FAIR, identity evidence **SHALL** meet _all_ the following requirements:

1. The issuing source of the evidence confirmed the claimed identity through a process designed to enable it to form a belief that it knows the real-life identity of the person. For example, evidence issued by financial institutions that have customer identity verification obligations under the Customer Identification Program (CIP) Rule implementing Section 326 of the USA PATRIOT Act of 2001, or that have obligations to establish an Identity Theft Prevention Program under the Red Flags Rule and Guidelines, implemented under Sec. 114 of the Fair and Accurate Credit Transaction Act of 2003 (FACT Act).

~~~
\clearpage
~~~
{:latex-literal="true"}


2.  It is likely that the evidence-issuing process would result in the delivery of the evidence to the person to whom it relates, such as delivery to a postal address.
3.  The evidence contains the name of the claimed identity.
4.  The evidence contains at least one reference number, a facial portrait, or sufficient attributes to uniquely identify the person to whom it relates.
5.	The evidence contains physical (e.g., security printing, optically variable features, holograms) or digital security features that make it difficult to reproduce.
6.	The information on the evidence is able to be validated by an authoritative or credible source. 
7.	The evidence is able to be verified through an approved method, as provided in [Sec. 2.4.2.2](2_proofing.md#validation-methods).

#### Strong Evidence Requirements

In order to be considered STRONG, identity evidence **SHALL** meet _all_ the following requirements:

1.  The issuing source of the evidence confirmed the claimed identity by following written procedures designed to enable it to have high confidence that it knows the real-life identity of the subject. Additionally, these procedures are subject to recurring oversight by regulatory or publicly accountable institutions, such as states, the federal government, and some regulated industries.  Such procedures would include, but not be limited to, identity proofing at IAL2 or above.
2.  It is likely that the evidence-issuing process would result in the delivery of the evidence to the person to whom it relates, such as delivery to a postal address.
3.  The evidence contains the name of the claimed identity.
4.  The evidence contains a reference number or other attributes that uniquely identify the person to whom it relates.
5.  The evidence contains a facial portrait or other biometric characteristic of the person to whom it relates.
6.  The evidence includes physical security features or digital security features that make it difficult to copy or reproduce.
7.  The information on the evidence is able to be validated by an authoritative or credible source.
8.  The evidence is able to be validated through an approved method, as provided in [Sec. 2.4.2.2](2_proofing.md#validation-methods).
	
#### Superior Evidence Requirements

In order to be considered SUPERIOR, identity evidence **SHALL** meet _all_ the following requirements:

1.  The issuing source of the evidence confirmed the claimed identity by following written procedures designed to enable it to have high confidence that the source knows the real-life identity of the subject. Additionally, these procedures are subject to recurring oversight by regulatory or publicly accountable institutions, such as states and the federal government, and some regulated industries.  Such procedures would include, but not be limited to, identity proofing at IAL2 or above.
2.  The identity evidence contains attributes and data objects that are cryptographically protected and can be validated through verification of a digital signature applied by the issuing source.
3.  The issuing source had the subject participate in an attended enrollment and identity proofing process that confirmed their physical existence. 
4.  It is likely that the evidence-issuing process would result in the delivery of the evidence to the person to whom it relates, such as delivery to a postal address.
5.  The evidence contains the name of the claimed identity.
6.  The evidence contains at least one reference number that uniquely identifies the person to whom it relates.
7.  The evidence contains a facial portrait or other biometric characteristic of the person to whom it relates.
8.  If the evidence is physical, then evidence includes security features that make it difficult to copy or reproduce.
9.  The evidence is able to be verified through an approved method, as provided in [Sec. 2.4.2.2](2_proofing.md#validation-methods).

### Identity Evidence and Attribute Validation 

Identity evidence validation involves examining the presented evidence to confirm it is authentic (not forged or altered), accurate (the information on the evidence is correct), and valid (unexpired or within the CSP's defined timeframe for issuance or expiration). Attribute validation involves confirming the accuracy of the core attributes, whether obtained from presented evidence or self-asserted. The following subsections provide the acceptable methods for evidence and attribute validation.  

#### Evidence Validation {#validation}

The CSP **SHALL** validate the authenticity, accuracy, and validity of presented evidence by confirming:

- The evidence is in the correct format and includes complete information for the identity evidence type;
- The evidence is not counterfeit and that it has not been tampered with;
- Any security features; and
- The information on the evidence is accurate.

#### Evidence Validation Methods {#validation-methods}

Acceptable methods for validating presented evidence include:

- Visual and tactile inspection by trained personnel for onsite identity proofing;
- Visual inspection by trained personnel for remote identity proofing;
- Automated document validation processes using appropriate technologies; and
- Cryptographic verification of the source and integrity of digital evidence, or attribute data objects.

#### Attribute Validation

The CSP **SHALL** validate all core attributes, as described in [Sec. 2.2](2_proofing.md#CoreAttributes), whether obtained from identity evidence or self-asserted by the applicant, with an authoritative or credible source, as in [Sec. 2.4.2.4](2_proofing.md#ValidSources).

#### Validation Sources {#ValidSources}

The CSP **SHALL** use authoritative or credible sources that meet the following criteria.

An authoritative source is the issuing source of identity evidence or attributes, or has direct access to the information maintained by issuing sources, such as state DMVs for driver's license data and the Social Security Administration for Social Security Cards and Social Security Numbers. An authoritative source may also be one that provides or enables direct access to issuing sources of evidence or attributes, such as the American Association of Motor Vehicle Administrators' Driver's License Data Verification (DLDV) Service. 

A credible source is an entity that can provide or validate the accuracy of identity evidence and attribute information. In addition to being subject to regulatory oversight (such as the Fair Credit Reporting Act (FCRA)), a credible source has access to attribute information that can be traced to an authoritative source, or maintains identity attribute information obtained from multiple sources that is correlated for accuracy, consistency, and currency. Examples of credible sources are credit bureaus that are subject to the FCRA.   

## Identity Verification

The goal of identity verification is to establish, to a specified level of confidence, the linkage between the claimed validated identity and the real-life applicant engaged in the identity proofing process. In other words, verification provides assurance that the applicant presenting the evidence is the rightful owner of that evidence.

### Identity Verification Methods {#verification}

The CSP **SHALL** verify the linkage of the claimed identity to the applicant engaged in the identity proofing process through one or more of the following methods. [Section 4](4_ial.md#ial-section) provides acceptable verification methods at each IAL.

- **Confirmation Code Veriﬁcation.** The individual is able to demonstrate control of a piece of identity evidence through the return of a confirmation code, consistent with the requirements speciﬁed in [Sec. 3.1.8](3_ialgen#ConfirmCodes).
- **Authentication and Federation Protocols.** The individual is able to demonstrate control of a digital account (e.g., online bank account) or signed digital assertion (e.g., veriﬁable credentials) through the use of authentication or federation protocols. This may be done in person, through presentation of the credential to a device or reader, but can also be done during remote identity prooﬁng sessions.
- **Micro Transaction.** An individual is able to demonstrate control of a piece of evidence by returning a value based on a micro transaction made between the CSP and the issuing source of the evidence (e.g., bank account). 
- **Onsite-In-person (Attended) visual facial image comparison.** The proofing agent and applicant interact for the identity prooﬁng event. The proofing agent performs a visual comparison of the facial portrait presented on identity evidence to the face of the applicant engaged in the identity prooﬁng event.
- **Remote (Attended or Unattended) visual facial image comparison.** The proofing agent performs a visual comparison of the facial portrait presented on identity evidence, or stored by the issuing source, to the facial image of the applicant engaged in the identity prooﬁng event. The proofing agent may interact directly with the applicant during some or all of the identity prooﬁng event (attended) or may conduct the comparison at a later time (unattended) using a captured video or photograph and the uploaded copy of the evidence. If the comparison is performed at a later time, steps are taken to ensure the captured video or photograph was taken from the live applicant present during the identity prooﬁng event.
- **Automated (Unattended) biometric comparison.** Automated biometric comparison, such as facial recognition or other fully automated algorithm-driven biometric comparison, **MAY** be performed for onsite or remote identity proofing events. The facial image or other biometric characteristic (e.g., fingerprints, palm prints, iris and retina patterns, voiceprints, or vein patterns) on the identity evidence, or stored in authoritative records, is compared to the facial image in a photograph of the live applicant or other biometric live sample collected from the applicant during the identity proofing event.

Knowledge-based verification (KBV) or knowledge-based authentication **SHALL NOT** be used for identity verification. 
