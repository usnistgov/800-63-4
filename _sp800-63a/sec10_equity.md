---
layout: default
title: Equity
navOrder: 10
navTitle: Equity
permalink: /sp800-63a/equity/
anchor: equity
section: 10

---

# Equity Considerations {#equity}

_This section is informative._

This section is intended to provide guidance to CSPs for assessing the risks associated with inequitable access, treatment, or outcomes for individuals using its identity services, as required in [Sec. 5.1.3](sec5_ial.md#EquityReqs). It provides a non-exhaustive list of potential areas in the identity proofing process that may be subject to inequities, as well as possible mitigations that can be applied. CSPs can use this section as a starting point for considering where the risks for inequitable access, treatment, or outcomes exist within its identity service. It is not intended that the below guidance be considered a definitive, all-inclusive list of associated equity risks to identity services.

In assessing equity risks, a CSP starts by considering the overall user population served by its identity proofing and enrollment service. Additionally, the CSP further identifies groups of users within the population whose shared characteristic(s) can cause them to be subject to inequitable access, treatment, or outcomes when using that service. CSPs are encouraged to assess the effectiveness of any mitigations by evaluating their impacts on the affected user group(s). The usability considerations provided in [Sec. 9](sec9_usability.md#usability) should also be considered when applying equity risk mitigations to help improve the overall usability and equity for all persons using an identity service. 

## Equity and Identity Resolution {#EquityResolve}

Identity resolution involves collecting the minimum set of attributes to be able to distinguish the claimed identity as a single, unique individual within the population served by the identity service. Attributes are obtained from presented identity evidence, applicant self-assertion, and/or back-end attribute providers.

This section provides a set of possible problems and mitigations with the inequitable access, treatment, or outcomes associated with the identity resolution process:

**Description: The identity service design requires an applicant to enter their name using a Western name format (e.g., first name, last name, optional middle name).**

Possible mitigations include: 

1. Analyzing possible name configurations and determine how all names can be accurately accommodated using the name fields 
2. Providing easy-to-find and use guidance to users on how to enter all names using the name fields  


**Description: The identity service cannot accommodate applicants whose name, gender, or other attributes have changed and are not consistently reflected on the presented identity evidence or match what is in the attribute verifier's records.**

Possible mitigations include:

1. Providing Trusted Referees ([Sec. 5.1.9.1](sec5_ial.md#TrustedRefs)) who can make risk-based decisions based on the specific applicant circumstances
2. Allowing for the use of Applicant References ([Sec. 5.1.9.2](sec5_ial.md#ApplicantRefs)) who can vouch for the difference in attributes  


## Equity and Identity Validation {#EquityValidation}

Identity evidence and core attribute validation involves confirming the genuineness, currency, and accuracy of presented identity evidence and the accuracy of any additional attributes. These outcomes are accomplished by comparison of the evidence and attributes against data held by authoritative or credible sources. When considered together with the identity resolution phase, the result of successful validation phase is the confirmation, to some level of confidence, that the claimed identity exists in the real world.

This section provides a set of possible problems and mitigations with the inequitable access, treatment, or outcomes associated with the evidence and attribute validation process: 


**Description: Certain user groups do not possess the necessary minimum evidence to meet the requirements of a given IAL.**

Possible mitigations include: 

1. Providing Trusted Referees ([Sec. 5.1.9.1](sec5_ial.md#TrustedRefs)) who can make risk-based decisions based on the specific applicant circumstances
2. Allowing for the use of Applicant References ([Sec. 5.1.9.2](sec5_ial.md#ApplicantRefs)) who can vouch for the applicant


**Description: Records held by authoritative and credible sources (e.g., mobile network operators and phone number verifiers) are insufficient to support the validation of core attributes or presented evidence for applicants belonging to certain user groups.**   

Possible mitigations include: 

1. Providing Trusted Referees ([Sec. 5.1.9.1](sec5_ial.md#TrustedRefs)) who can make risk-based decisions based on the specific applicant circumstances
2. Employing alternative authoritative or credible sources


**Description: Records held by authoritative and credible sources may include inaccurate or false information about persons who are the victims of identity fraud.** 

Possible mitigations include: 

1. Providing Trusted Referees ([Sec. 5.1.9.1](sec5_ial.md#TrustedRefs)) who can make risk-based decisions based on the specific applicant circumstances
2. Allowing for the use of Applicant References ([Sec. 5.1.9.2](sec5_ial.md#ApplicantRefs)) who can vouch for the difference in attributes



## Equity and Identity Verification {#EquityVerification}

Identity verification involves proving the binding between the applicant undergoing the identity proofing process and the validated, real-world identity established through the identity resolution and validation steps. It most often involves collecting a picture (facial image capture) of the applicant taken during the identity proofing event and comparing it a photograph contained on a presented and validated piece of identity evidence.

This section provides a set of possible problems and mitigations with the inequitable treatment or outcomes associated with the identity verification phase: 


**Description: Image capture technologies lack the ability to capture certain skin tones or facial features of sufficient quality to perform a comparison.**   

Possible mitigations include: 

1. Employing robust image capture technologies that are able to accommodate different skin tones, facial features, and lighting situations
2. Conducting operational testing to determine if the image capture technologies have introduced unintentional biases
3. Providing risk-based alternative processes that compensate for residual bias and technological limitations


**Description: Facial coverings worn for religious purposes impede the ability to capture a facial image of an applicant.**  

Possible mitigations include: 

1. Providing Trusted Referees ([Sec. 5.1.9.1](sec5_ial.md#TrustedRefs)) who can make risk-based decisions based on the specific applicant circumstances.
2. Providing alternative ways to accomplish identity verification, such as an in-person proofing.  


**Description: When using 1:1 facial image comparison technologies, biased facial comparison algorithms may result in false non-matches.**

Possible mitigations include: 

1. Using algorithms that are independently tested for consistent performance across demographic groups and image types
3. Supporting alternative processes to compensate for residual bias and technological limitations
4. Conducting ongoing quality monitoring and operational testing to identify performance variances are identified across demographic groups and implementing corrective actions as needed (e.g., updated algorithms, machine learning, etc.)


**Description: When employing physical facial image comparison performed by CSP operators, human biases and inconsistencies in making facial comparisons may result in false non-matches.**

Possible mitigations include:

1. Defining policy and procedures aimed at reducing/eliminating the inequitable treatment of applicants by CSP operators/agents
2. Rigorously training and certifying of operators
3. Conducting ongoing quality monitoring and taking corrective actions when biases, or inequitable treatments or outcomes, are identified

## Equity and User Experience {#EquityUser}

The Usability Considerations section of this document ([Sec. 9](sec9_usability.md#usability)) provides CSPs with guidance on how to provide applicants with a smooth, positive identity proofing experience. In addition to the specific considerations provided in Sec. 9, this section provides CSPs with additional considerations when considering the equity of their user experience.



**Description: Lack of access to needed technology (e.g. connected mobile device or computer), or difficulties in using required technologies, unduly burdens some user groups.** 

Possible mitigations include: 

1. Allowing the use of helpers who assist applicants, who are otherwise able to meet the identity proofing requirements, in the use of the required technologies and activities
2. Allowing the use of publicly-available devices (e.g., computers or tablets) and providing online help resources for completing the identity proofing process on a non-applicant-owned computer or device 
3. Providing in-person proofing options


**Description: The remote or in-person identity proofing process presents challenges for persons with disabilities.**

Possible mitigations for remote identity proofing include: 

1. Providing Trusted Referees ([Sec. 5.1.9.1](sec5_ial.md#TrustedRefs)) who are trained to communicate and assist people with a variety of needs or disabilities (e.g., fluent in sign language) 
2. Allowing for the use of Applicant References ([Sec. 5.1.9.2](sec5_ial.md#ApplicantRefs))
3. Supporting the use of accessibility and other technologies, such as audible instructions, screen readers and voice recognition technologies

Possible mitigations for in-person identity proofing include:

1. Providing trained operators who are trained to communicate and assist people with a variety of needs or disabilities (e.g., fluent in sign language) 
2. Choosing equipment and workstations that can be adjusted to different heights and angles
3. Selecting locations that are convenient and comply with ADA accessibility guidelines 


