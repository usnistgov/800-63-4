---
layout: default
title: Equity
navOrder: 10
navTitle: Equity
permalink: /sp800-63a/equity/
anchor: equity
section: 9
---

# Equity Considerations {#equity}

_This section is informative._

This section is intended to provide guidance to CSPs and RPs for assessing the risks associated with inequitable access, treatment, or outcomes for individuals using its identity services, as required in [Sec. 3.1.4](3_ialgen.md#EquityReqs). It provides a non-exhaustive list of potential areas in the identity proofing process that may be subject to inequities, as well as possible mitigations that can be applied. CSPs and RPs can use this section as a starting point for considering where the risks for inequitable access, treatment, or outcomes exist within its identity service. It is not intended that the below guidance be considered a definitive, all-inclusive list of associated equity risks to identity services.

In assessing equity risks, CSPs and RPs start by considering the overall user population served by its online service. Additionally, CSPs and RPs further identify groups of users within the population whose shared characteristic(s) can cause them to be subject to inequitable access, treatment, or outcomes when using that service. CSPs and RPs are encouraged to assess the effectiveness of any mitigations by evaluating their impacts on the affected user group(s). The usability considerations provided in [Sec. 8](8_usability.md#usability) should also be considered when applying equity risk mitigations to help improve the overall usability and equity for all persons using an identity service. 

Pursuant to Executive Order 13985 [[EO13985]](references.md#ref-EO13985), _Advancing Racial Equity and Support for Underserved Communities Through the Federal Government_, OMB published its _Study to Identify Methods to Assess Equity: Report to the President_ [[OMB-Equity]](references.md#ref-OMB-Equity) which identified "the best methods, consistent with applicable law, to assist agencies in assessing equity with respect to race, ethnicity, religion, income, geography, gender identity, sexual orientation, and disability." CSPs and RPs are encouraged to consult this study when determining which approaches and methods they will use to assess the equity of their identity services. 

It is intended that remote identity proofing can broaden usability and accessibility for enrollment into online identity services. The following subsections present considerations for some identity proofing processes that may create risks of inequitable treatment for some groups and individuals and present the use of trusted referees to help to mitigate such risks associated with remote identity proofing. However, it is important that the use of trusted referees do not create additional risks of exclusion among groups who may lack internet access or who do not have easy access to smartphones or computing devices. Providing in-person options for trusted referees can help ensure that those impacted by the digital divide are still able to access services offered by the CSP or RP.

Additionally, CSPs and RPs should assess whether implementing these considerations could introduce delays to the identity proofing process and employ appropriate methods, such as online scheduling tools or additional staffing for peak demand times, to mitigate these delays.  

It is also intended that the considerations and mitigations provided in this section will be proactively employed and result in a more equitable identity proofing experience for the population served by the identity service. CSPs are expected to continuously monitor the performance of their service and to make remedial updates, as appropriate. This includes policies and processes for redressing user reports of inequitable access, treatment, or outcomes of the service.

## Identity Resolution and Equity {#EquityResolve}

Identity resolution involves collecting the minimum set of attributes to be able to distinguish the claimed identity as a single, unique individual within the population served by the identity service. Attributes are obtained from the presented identity evidence, applicant self-assertion, and/or back-end attribute providers.

This section provides a set of possible problems and mitigations with the inequitable access, treatment, or outcomes associated with the identity resolution process:

**Description: The identity service design requires an applicant to enter their name using a Western name format (e.g., first name, last name, optional middle name).**

Possible mitigations include: 

1. Analyzing possible name configurations and determining how all names can be accurately accommodated using the name fields 
2. Providing easy-to-find and use guidance to users on how to enter all names using the name fields 
3. Accepting reasonable name variations (for example, to allow for differences in name order, multiple surnames, etc.)
4. Providing the option for applicants to switch to an attended (onsite or remote) workflow option

**Description: The identity service cannot accommodate applicants whose name, gender, or other attributes have changed and are not consistently reflected on the presented identity evidence or match what is in the attribute verifier's records.**

Possible mitigations include:

1. Providing trusted referees ([Sec. 3.1.13.1](3_ialgen.md#TRs)) who can make risk-based decisions based on the specific applicant circumstances
2. Allowing for the use of applicant references ([Sec. 3.1.13.3](3_ialgen.md#ARs)) who can vouch for the differences in attributes
3. Providing an easily accessible list of acceptable evidence in support of the updated attribute, such as a marriage certificate 
4. Accepting reasonable name variations (for example, to allow for differences in name order, multiple surnames, hyphenation, or recent name changes)  

## Identity Validation and Equity {#EquityValidation}

Identity evidence and core attribute validation involves confirming the genuineness, currency, and accuracy of the presented identity evidence and the accuracy of any additional attributes. These outcomes are accomplished by comparison of the evidence and attributes against data held by authoritative or credible sources. When considered together with the identity resolution phase, the result of successful validation phase is the confirmation, to some level of confidence, that the claimed identity exists in the real world.

This section provides a set of possible problems and mitigations with the inequitable access, treatment, or outcomes associated with the evidence and attribute validation process: 


**Description: Certain user groups do not possess the necessary minimum evidence to meet the requirements of a given IAL.**

Possible mitigations include: 

1. Providing trusted referees ([Sec. 3.1.13.1](3_ialgen.md#TRs)) who can make risk-based decisions based on the specific applicant circumstances
2. Allowing for the use of applicant references ([Sec. 3.1.13.3](3_ialgen.md#ARs)), such as the parent of a minor child, who can vouch for the applicant
3. Ensuring that the selected IAL is not higher than necessary to be commensurate with the risk of the digital service offering
4. RPs offering a limited set of functionality or options for users identity proofed at lower IALs

**Description: Records held by authoritative and credible sources are insufficient to support the validation of core attributes or presented evidence for applicants belonging to certain user groups, such as those who self-exclude themselves from programs and services due to fears of surveillance or other concerns that might result in a record of their association.**   

Possible mitigations include: 

1. Providing trusted referees ([Sec. 3.1.13.1](3_ialgen.md#TRs)) who can make risk-based decisions based on the specific applicant circumstances
2. Allowing the use of applicant references ([Sec. 3.1.13.3](3_ialgen.md#ARs)) who can vouch for the difference in attributes
3. Employing multiple authoritative or credible sources

**Description: Records held by authoritative and credible sources may include inaccurate or false information about persons who are the victims of identity fraud.** 

Possible mitigations include: 

1. Providing trusted referees ([Sec. 3.1.13.1](3_ialgen.md#TRs)) who can make risk-based decisions based on the specific applicant circumstances
2. Allowing the use of applicant references ([Sec. 3.1.13.3](3_ialgen.md#ARs)) who can vouch for the difference in attributes
3. Employing multiple authoritative or credible sources

## Identity Verification and Equity {#EquityVerification}

Identity verification involves proving the binding between the applicant undergoing the identity proofing process and the validated, real-world identity established through the identity resolution and validation steps. It most often involves collecting a picture (facial image capture) of the applicant taken during the identity proofing event and comparing it to a photograph contained on a presented and validated piece of identity evidence.

This section provides a set of possible problems and mitigations with the inequitable treatment or outcomes associated with the identity verification phase: 


**Description: Facial image capture technologies lack the ability to capture certain skin tones or facial features of sufficient quality to perform a comparison.**   

Possible mitigations include: 

1. Employing robust image capture technologies, with high performing algorithms, which have been demonstrated to accommodate different skin tones, facial features, and lighting situations 
2. Conducting operational testing of image capture technologies to determine if they function equitably across ethnicity, race, sex assigned at birth, and other demographic factors and upgrading, as needed, to correct for inequities
3. Providing guidance to the applicant about how to improve the lighting or conditions for image capture
4. Providing risk-based alternative processes, such as Trusted Referees ([Sec. 3.1.13.1](3_ialgen.md#TRs)), that compensate for residual bias and technological limitations
5. Providing the option for applicants to use CSP-controlled kiosks, which employ state-of-the-art facial and biometric capture technologies
5. Providing the option for applicants to switch to an attended workflow option

**Description: For biometric comparison involving facial images, facial coverings worn for religious purposes may impede the ability to capture a facial image of an applicant. For biometric comparison involving other biometric characteristics, demographic factors may impede the ability to capture a usable biometric sample, such as age affecting the capability to collect a usable fingerprint.**  

Possible mitigations include: 

1. Providing trusted referees ([Sec. 3.1.13.1](3_ialgen.md#TRs)) who can make risk-based decisions based on the specific applicant circumstances.
2. Providing alternative ways to accomplish identity verification, such as an in-person proofing.
3. Offering alternative biometric collection and comparison capabilities.  


**Description: When using 1:1 facial image comparison technologies, biased facial comparison algorithms may result in false non-matches.**

Possible mitigations include: 

1. Using algorithms that are independently tested for consistent performance across demographic groups and image types
3. Supporting alternative processes to compensate for residual bias and technological limitations
4. Conducting ongoing quality monitoring and operational testing to identify performance variances across demographic groups and implementing corrective actions as needed (e.g., updated algorithms, machine learning, etc.)


**Description: When employing visual facial image comparison performed by agents of the CSP (proofing agents or trusted referees), human biases and inconsistencies in making facial comparisons may result in false non-matches.**

Possible mitigations include:

1. Defining policy and procedures aimed at reducing/eliminating the inequitable treatment of applicants by CSP agents
2. Rigorously training and certifying CSP agents
3. Conducting ongoing quality monitoring and taking corrective actions when biases, inequitable treatments, or outcomes are identified

## User Experience and Equity {#EquityUser}

The Usability Considerations section of this document ([Sec. 8](8_usability.md#usability)) provides CSPs with guidance on how to provide applicants with a smooth, positive identity proofing experience. In addition to the specific considerations provided in [Sec. 8](8_usability.md#usability), this section provides CSPs with additional considerations when considering the equity of their user experience.


**Description: Lack of access to the needed technology (e.g. connected mobile device or computer), or difficulties in using the required technologies, unduly burdens some user groups.** 

Possible mitigations include: 

1. Allowing the use of process assistants who assist applicants, who are otherwise able to meet the identity proofing requirements, in the use of the required technologies and activities
2. Allowing the use of publicly-available devices (e.g., computers or tablets) and providing online help resources for completing the identity proofing process on a non-applicant-owned computer or device 
3. Providing in-person proofing options
4. Employing technologies, such as auto capture, that simplify the uploading of identity evidence and facial images


**Description: The remote or in-person identity proofing process presents challenges for persons with disabilities.**

Possible mitigations for remote identity proofing include: 

1. Providing trusted referees ([Sec. 3.1.13.1](3_ialgen.md#TRs)) who are trained to communicate and assist people with a variety of needs or disabilities (e.g., fluent in sign language) 
2. Allowing for the use of applicant references ([Sec. 3.1.13.3](3_ialgen.md#ARs))
3. Supporting the use of accessibility and other technologies, such as audible instructions, screen readers and voice recognition technologies
4. Allowing the use of process assistants to assist applicants, who are otherwise able to meet the identity proofing requirements, in the use of the required technologies and activities

Possible mitigations for in-person identity proofing include:

1. Providing trained operators who are trained to communicate and assist people with a variety of needs or disabilities (e.g., fluent in sign language) 
2. Choosing equipment and workstations that can be adjusted to different heights and angles
3. Selecting locations that are convenient and comply with ADA accessibility guidelines 


