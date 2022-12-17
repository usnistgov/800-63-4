---
layout: default.ja
title: Identity Resolution, Validation, and Verification
navOrder: 4
navTitle: Proofing
permalink: /sp800-63a/proofing/
anchor: ipv-section
section: 4
---

# Identity Resolution, Validation, and Verification {#ipv-section}

_This section is normative._

This section provides and overview of the identity proofing and enrollment process as well as requirements to support the resolution, validation, and verification of the identity claimed by an applicant. It also provides guidelines on additional aspects of the identity proofing process.  These requirements are intended to ensure that the claimed identity exists in the real world and that the applicant is the individual associated with that identity. Collectively, the elements of the identity proofing process are designed to ensure that attacks against a CSP's identity service that affect a large number of enrolled subscribers require greater time and cost than the value of the data being protected.

Additionally, these guidelines provide for multiple methods by which resolution, validation, and verification can be completed as well as multiple types of identity evidence that may support the identity proofing process. To the extent practical, CSPs and organizations **SHOULD** enable optionality when implementing their identity proofing services and processes to promote access for those with different means, capabilities, and technology access. At a minimum, this **SHOULD** include accepting multiple types and combinations of identity evidence, supporting multiple data validation sources, enabling multiple methods for verifying identity (e.g., use of trusted referees), multiple channels for engagement (e.g., in-person, remote), and offering assistance mechanisms for applicants (e.g., applicant references).

## Identity Proofing and Enrollment

This document describes the common pattern in which an applicant undergoes an identity proofing and enrollment process whereby their identity evidence and attributes are collected, uniquely resolved to a single identity within a given population or context, then validated and verified. See [[SP800-63]](../_sp800-63/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63"} for details on how to choose the most appropriate IAL. A CSP can then bind these attributes to an authenticator (described in [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}).

The objective of identity proofing is to ensure, to a stated level of certainty, the applicant is who they claim to be. Identity proofing is not conducted to determine suitability or entitlement to benefits. The identity proofing process involves the presentation and validation of the minimum attributes necessary to accomplish identity proofing.  There can be many different sets of attributes that suffice as the minimum, so CSPs choose this set by considering applicants' privacy and the usability, as well as the likely attributes needed in future uses of the digital identity. For example, such attributes, to the extent they are the minimum necessary, could include:

1. Full name
2. Date of birth
3. Home address

This document also provides requirements for CSPs collecting additional information used for purposes other than identity proofing.

~~~
\clearpage
~~~
{:latex-literal="true"}

### Process Flow

_This section is informative._

[Figure 1](sec4_proofing.md#fig-1) outlines the basic flow for identity proofing and enrollment.

[Figure 1. Identity Proofing Process](sec4_proofing.md#fig-1){:name="fig-1"}
{:latex-ignore="true"}

![Illustration of steps in identity proofing and enrollment]({{site.baseurl}}/{{page.collection}}/media/ProofingProcess.png 'Identity Proofing Process'){:style="width:1074px;height:496px;;min-width: 1074px;min-height: 496px;" latex-src="ProofingProcess.png" latex-fig="1" latex-place="h"}

The following provides an example of how a CSP and an applicant might interact during a remote identity proofing process at IAL2:


1. **Resolution**
    1. The CSP collects attributes from the applicant, such as name, address, date of birth, email, and phone number.
    2. The CSP also collects one or more pieces of identity evidence, such as a driver's license or a passport.
    {:.letter-list}
2. **Validation**
    1. The CSP validates the attributes obtained in steps 1a by checking them against authoritative or credible sources.
    2. The CSP validates the authenticity, accuracy, and currency of the presented evidence.
    {:.letter-list}
3. **Verification**
    1. The CSP asks the applicant to take a photo of themself, with liveness checks.
    2. The CSP compares the pictures on the license and the passport to the photo of the live applicant's photo from the previous step and determines they match.
    3. The CSP sends an enrollment code to the validated phone number of the applicant, the applicant provides the enrollment code to the CSP, and the CSP confirms they match, verifying they the applicant is in possession and control of the validated phone number.
    4. The applicant has been successfully identity proofed and can be enrolled into a subscriber account.
    {:.letter-list}

## Identity Resolution {#resolve}

The goal of identity resolution is to use the smallest set of attributes to uniquely distinguish an individual within a given population or context. While identity resolution is the starting point in the overall identity proofing process, to include the initial detection of potential fraud, it in no way represents a complete and successful identity proofing transaction.

## Identity Validation and Identity Evidence Collection {#evidence-collection}

The goal of identity validation is to collect the most appropriate identity evidence and attribute information from the applicant and determine it is authentic, accurate, current, and unexpired. Identity validation is made up of three process steps: 1) collecting the appropriate identity evidence; 2) confirming the evidence is authentic; and, 3) confirming key data contained on the identity evidence is valid, current, and related to a real-life subject.

Identity evidence collection supports the identity validation process and consists of two steps: 1) presentation of identity evidence by the identity proofing applicant to the CSP and 2) determination by the CSP that the presented evidence is acceptable. Evidence can be presented as a physical document or a copy, photograph, or scan of a document, or as a digital record. The characteristics for acceptable physical (documentary) identity evidence are presented in [Sec. 4.3.1](sec4_proofing.md#physical-evidence) and the characteristics for acceptable digital evidence are provided in [Sec. 4.3.2](sec4_proofing.md#digital-evidence).

The CSP **SHALL** determine the acceptability of presented identity evidence for identity proofing based on the evidence characteristics in this section.

The characteristics presented in this section are intended to guide CSPs in determining what is acceptable as identity evidence for the identity proofing process and are not an indication of strength of evidence. Once a CSP determines a particular type of evidence is acceptable, a determination must be made as to its strength, as provided in [Sec. 4.3.3](sec4_proofing.md#evidence-strength).

### Characteristics of Acceptable Physical Evidence {#physical-evidence}

Acceptable physical evidence **SHALL** contain all of the following characteristics:

1.	The presented document contains the printed name of the applicant. (See [Sec. 10.1](sec10_equity.md#EquityResolve) - Equity and Resolution - for guidance on dealing with a printed name that varies from the applicant's claimed identity.)
2.	The presented document contains at least one printed reference number.
3.	The presented document contains the printed name of the issuer of the document.
4.	The issuer of the document performed identity proofing of the applicant prior to issuing the document.
5.	There is reasonable assurance that the document was delivered to the intended person.

### Characteristics of Acceptable Digital Evidence {#digital-evidence}

Acceptable digital evidence **SHALL** contain all of the following characteristics:

1.  The presented digital evidence contains the name of the applicant as the subject of the digital information or account. (See [Sec. 10.1](sec10_equity.md#EquityResolve) - Equity and Resolution - for guidance on dealing with a name on digital evidence that varies from the applicant's claimed identity.)
2.  The presented digital evidence contains at least one reference (e.g., account number) or sufficient attributes to bind the digital information to the applicant.
3.  The presented digital evidence contains the name of the issuer of the digital information.
4.  The issuer of the digital evidence performed identity proofing of the applicant prior to issuing the digital evidence.
5.  There is reasonable assurance that the digital evidence was delivered or made accessible to intended person.
6.  If applicable, the presented digital evidence can be verified through authentication at an AAL or FAL commensurate with the assessed IAL.

###  Evidence Strength Requirements {#evidence-strength}

This section defines the requirements for identity evidence at each strength. Strength of identity evidence is determined by three aspects: 1) the issuing rigor; 2) the ability to provide confidence in validation, including accuracy and integrity of attributes; and 3) the ability to provide confidence in the verification of the applicant presenting the evidence. Evidence at all levels of strength must be current and unexpired.

#### Fair Evidence Requirements

In order to be considered FAIR, identity evidence **SHALL** meet _all_ the following requirements:

1.  The issuing source of the evidence confirmed the claimed identity through an identity proofing process.
2.  It can be reasonably assumed that the evidence issuing process would result in the delivery of the evidence to the person to whom it relates.
3.  The evidence contains at least one reference number, a facial portrait, or sufficient attributes to uniquely identify the person to whom it relates.
4.  The evidence has not expired or it expired within the previous six (6) months, or it was issued within the previous six (6) months if it does not contain an expiration date.

#### Strong Evidence Requirements

In order to be considered STRONG, identity evidence **SHALL** meet _all_ the following requirements:

1.  The issuing source of the evidence confirmed the claimed identity through written procedures designed to enable it to form a reasonable belief that it knows the real-life identity of the person. Such procedures are subject to recurring oversight by regulatory or publicly-accountable institutions. For example, the Customer Identification Program guidelines established in response to the USA PATRIOT Act of 2001 or the [[RedFlagsRule]](sec11_references.md#ref-rfr), under Sec. 114 of the Fair and Accurate Credit Transaction Act of 2003 (FACT Act).
2.  There is a high likelihood that the evidence issuing process would result in the delivery of the evidence to the person to whom it relates.
3.  The evidence contains a reference number or other attributes that uniquely identify the person to whom it relates.
4.  The evidence contains a facial portrait or other biometric characteristic of the person to whom it relates.
5.  The evidence includes physical security features that make it difficult to copy or reproduce.
6.  The evidence includes an expiration date and is unexpired.

#### Superior Evidence Requirements

In order to be considered SUPERIOR, identity evidence **SHALL** meet _all_ the following requirements:

1.  The issuing source of the evidence confirmed the claimed identity by following written procedures designed to enable it to have high confidence that the source knows the real-life identity of the subject. Such procedures are subject to recurring oversight by regulatory or publicly accountable institutions.
2.  The issuing source visually identified the applicant and performed further checks to confirm the existence of that person.
3.  The issuing process for the evidence ensured that it was delivered into the possession of the person to whom it relates.
4.  The evidence contains at least one reference number that uniquely identifies the person to whom it relates.
5.  The evidence contains a facial portrait or other biometric characteristic of the person to whom it relates.
6.  The evidence includes digital information that is cryptographically signed.
7.  The evidence includes physical security features that make it difficult to copy or reproduce.
8.  The evidence includes an expiration date and is unexpired.

### Identity Evidence and Attribute Validation

The CSP **SHALL** validate all identity evidence collected to meet evidence collection requirements and all core attribute information required by the CSP identity service.

#### Evidence Validation {#validation}

The CSP **SHALL** validate the authenticity, accuracy, and currency of presented evidence by:

- Confirming the evidence is in the correct format and includes complete information for the identity evidence type.
- Confirming the evidence is not counterfeit and that it as not been tampered with.
- Confirming any security features.

The CSP **SHALL** validate that the evidence is current through confirmation that its expiration date has not passed or that evidence without an expiration date was issued within the previous six (6) months.

The authenticity and accuracy of identity evidence or attribute information that is cryptographically protected can be validated through verification of the digital signature on the evidence or the attribute data objects. The CSP **SHALL** use the public key of the issuing authority of the evidence to verify digitally signed evidence or attribute data objects.

#### Attribute Validation

All core attributes, whether obtained from identity evidence or applicant self-assertion, must be validated. This subsection provides guidance on acceptable methods for validating evidence and collected attributes.

#### Evidence and Attribute Validation Methods

Acceptable methods for validating presented evidence include:

- Visual and tactile inspection by trained personnel for in-person identity proofing,
- Visual inspection by trained personnel for remote identity proofing,
- Automated document validation processes using appropriate technologies,
- Validation of attributes contained on the evidence with an authoritative or credible source.
- Verification of the digital signature protecting digital evidence or attribute data objects using the public key of the issuing authority of the evidence.

#### Validation Sources

Core attributes that are contained on identity evidence that has been validated according to [Sec. 4.3.4.1](sec4_proofing.md#validation) can be considered validated, in which case no further validation is required.

An authoritative source is an entity that can provide or validate the accuracy of identity attribute information through one or more of the following characteristics. An authoritative source:

- Is the original source of the identity attribute(s); or
- Is the issuer of identity evidence containing identity attribute information and the issuer confirmed the claimed identity through documented identity proofing processes that are subject to recurring oversight by regulatory or publicly accountable institutions, such as the Customer Identification Program guidelines established under the [[PatriotAct]](sec11_references.md#ref-PatriotAct); or
- Collected and validated attribute information through an identity proofing process that can confirm the claimed identity through direct interaction with individuals (either in-person or remotely); or
- Has access to evidence and attribute information that can be traced to the issuing source of a piece of identity evidence.

A credible source is an entity that can provide or validate the accuracy of identity evidence and attribute information through one or more of the following characteristics. A credible source:

- Has access to attribute information that was validated through an identity proofing process; or
- Has access to attribute information that can be traced to an authoritative source; or
- Maintains identity attribute information obtained from multiple sources that is checked for data correlation for accuracy, consistency, and currency.

## Identity Verification

The goal of identity verification is to confirm and establish a linkage between the claimed identity and the real-life existence of the applicant engaged in the identity proofing process.

### Identity Verification Methods

The CSP **SHALL** verify the linkage of the claimed identity  to the applicant engaged in the identity proofing process through one or more of the following methods, depending on the IAL identity verification requirements presented in [Sec. 5](sec5_ial.md#ial-section).

- **Enrollment code verification** as specified in [Sec. 5.1.6](sec5_ial.md#EnrollCodes).
- **In-person physical comparison**. The CSP operator and applicant interact in person for the identity proofing event. The CSP operator performs a physical comparison of the facial portrait presented on identity evidence to the face of the applicant engaged in the identity proofing event.
- **Remote (attended and unattended) physical facial image comparison**. The CSP operator performs a physical comparison of the facial portrait presented on identity evidence to the facial image of the applicant engaged in the identity proofing event. The CSP operator may interact directly with the applicant during some or all of the identity proofing event (attended) or may conduct the comparison at a later time (unattended) using a captured video or photograph and the uploaded copy of the evidence. If the comparison is performed at a later time, steps are taken to ensure the captured video or photograph was taken from the live applicant present during the identity proofing event.
- **Automated biometric comparison**. Biometric system comparison may be performed for in-person or remote identity proofing events. The facial portrait, or other biometric characteristic, contained on identity evidence is compared by an automated biometric comparison system to the facial image photograph of the live applicant or other biometric live sample submitted by the applicant during the identity proofing event. The automated biometric comparison system uses a mathematical algorithm for the comparison.
- **Control of a digital account**. An individual is able to demonstrate control of a digital account (e.g., online bank account) or signed digital assertion (e.g., verifiable credentials) through the use of authentication or federation protocols. This may be done in person through presentation of the credential to a device or reader, but is more likely to be done during remote identity proofing sessions.




