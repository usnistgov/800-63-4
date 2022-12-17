---
layout: default.ja
title: Privacy
navOrder: 8
navTitle: Privacy
permalink: /sp800-63a/privacy/
anchor: privacy-section-header
section: 8
---

# Privacy Considerations {#privacy-section-header}

_This section is informative._

These privacy considerations provide additional information in implementing the requirements set forth in [Sec. 5.1.2](sec5_ial.md#PrivacyReqs).

## Collection and Data Minimization

The guidelines permit the collection of only the PII necessary to validate the existence of the claimed identity and associate the claimed identity to the applicant, based on best available practices for appropriate identity resolution, validation, and verification. Collecting unnecessary PII can create confusion regarding why information not being used for the identity proofing service is being collected. This leads to invasiveness or overreach concerns, which can lead to loss of applicant trust. Further, PII retention can become vulnerable to unauthorized access or use. Data minimization reduces the amount of PII vulnerable to unauthorized access or use, and encourages trust in the identity proofing process.

### Social Security Numbers

These guidelines permit the CSP collection of the SSN as an attribute for use in identity resolution. However, over-reliance on the SSN can contribute to misuse and place the applicant at risk of harm, such as through identity theft. Nonetheless, the SSN may facilitate identity resolution for CSPs, in particular federal agencies that use the SSN to correlate an applicant to agency records. This document recognizes the role of the SSN as an attribute and makes appropriate allowance for its use. Knowledge of the SSN is not sufficient to serve as identity evidence.

Where possible, CSPs and agencies should consider mechanisms to limit the proliferation and exposure of SSNs during the identity proofing process. This is particularly pertinent where the SSN is communicated to third party providers during attribute validation processes. To the extent possible, privacy protective techniques and technologies should be applied to reduce the risk of an individual’s SSN being exposed, stored, or maintained by third party systems. Examples of this could be the use of attribute claims (e.g., yes/no responses from a validator) to confirm the validity of a SSN without requiring it to be unnecessarily transmitted and stored by the third party. As with all attributes in the identity proofing process, the value and risk of each attribute being processed is subject to a privacy risk assessment and for federal agencies the PIA and SORN. The SSN should only be collected where it is necessary to support resolution associated with the applications assurance and risk levels.

## Notice and Consent {#consent}

The guidelines require the CSP to provide explicit notice to the applicant at the time of collection regarding the purpose for collecting and maintaining a record of the attributes necessary for identity proofing, including whether such attributes are voluntary or mandatory in order to complete the identity proofing transactions, and the consequences for not providing the attributes.

An effective notice will take into account user experience design standards and research, and an assessment of privacy risks that may arise from the collection. Various factors should be considered, including incorrectly inferring that applicants understand why attributes are collected, that collected information may be combined with other data sources, etc. An effective notice is never only a pointer leading to a complex, legalistic privacy policy or general terms and conditions that applicants are unlikely to read or understand.

## Use Limitation

The guidelines require CSPs to use measures to maintain the objectives of predictability (enabling reliable assumptions by individuals, owners, and operators about PII and its processing by an information system) and manageability (providing the capability for granular administration of PII, including alteration, deletion, and selective disclosure) commensurate with privacy risks that can arise from the processing of attributes for purposes other than identity proofing, authentication, authorization, or attribute assertion, related fraud mitigation, or to comply with law or legal process [[NISTIR8062]](sec11_references.md#ref-NISTIR8062).

CSPs may have various business purposes for processing attributes, including providing non-identity services to subscribers. However, processing attributes for other purposes than those disclosed to a subject can create additional privacy risks. CSPs can determine appropriate measures commensurate with the privacy risk arising from the additional processing. For example, absent applicable law, regulation or policy, it may not be necessary to get consent when processing attributes to provide non-identity services requested by subscribers, although notices may help subscribers maintain reliable assumptions about the processing (predictability). Other processing of attributes may carry different privacy risks that call for obtaining consent or allowing subscribers more control over the use or disclosure of specific attributes (manageability). Subscriber consent needs to be meaningful; therefore, when CSPs do use consent measures, they cannot make acceptance by the subscriber of additional uses a condition of providing the identity service.

Consult your SAOP if there are questions about whether the proposed processing falls outside the scope of the permitted processing or the appropriate privacy risk mitigation measures.

## Redress

The guidelines require the CSP to provide effective mechanisms for redressing applicant complaints or problems arising from the identity proofing, and make the mechanisms easy for applicants to find and access.

The Privacy Act requires federal CSPs that maintain a system of records to follow procedures to enable applicants to access and, if incorrect, amend their records. Any Privacy Act Statement should include a reference to the applicable SORN(s) (see [Sec. 5.1.2](sec5_ial.md#PrivacyReqs)), which provide the applicant with instructions on how to make a request for access or correction. Non-federal CSPs should have comparable procedures, including contact information for any third parties if they are the source of the information.

CSPs should make the availability of alternative methods for completing the process clear to applicants (e.g., in person at a customer service center) in the event an applicant is unable to establish their identity and complete the registration process online.

> Note: If the identity proofing process is not successful, CSPs should inform the applicant of the procedures to address the issue but should not inform the applicant of the specifics of why the registration failed (e.g., do not inform the applicant, "Your SSN did not match the one that we have on record for you"), as doing so could allow fraudulent applicants to gain more knowledge about the accuracy of the PII.


## Privacy Risk Assessment

The guidelines require the CSP to conduct a privacy risk assessment. In conducting a privacy risk assessment, CSPs should consider:

1. The likelihood that the action it takes (e.g., additional verification steps or records retention) could create a problem for the applicant, such as invasiveness or unauthorized access to the information; and
2. The impact if a problem did occur. CSPs should be able to justify any response it takes to identified privacy risks, including accepting the risk, mitigating the risk, and sharing the risk. The use of applicant consent should be considered a form of sharing the risk, and therefore should only be used when an applicant could reasonably be expected to have the capacity to assess and accept the shared risk.

## Agency-Specific Privacy Compliance

The guidelines cover specific compliance obligations for federal CSPs. It is critical to involve your agency's SAOP in the earliest stages of digital authentication system development to assess and mitigate privacy risks and advise the agency on compliance requirements, such as whether or not the PII collection to conduct identity proofing triggers the Privacy Act of 1974 [[PrivacyAct]](sec11_references.md#ref-PrivacyAct) or the E-Government Act of 2002 [[E-Gov]](sec11_references.md#ref-E-Gov) requirement to conduct a Privacy Impact Assessment. For example, with respect to identity proofing, it is likely that the Privacy Act requirements will be triggered and require coverage by either a new or existing Privacy Act system of records due to the collection and maintenance of PII or other attributes necessary to conduct identity proofing.

The SAOP can similarly assist the agency in determining whether a PIA is required. These considerations should not be read as a requirement to develop a Privacy Act SORN or PIA for identity proofing alone; in many cases it will make the most sense to draft a PIA and SORN that encompasses the entire digital identity lifecycle or includes the identity proofing process as part of a larger, programmatic PIA that discusses the program or benefit to which the the agency is establishing online access.

Due to the many components of the digital identity lifecycle, it is important for the SAOP to have an awareness and understanding of each individual component. For example, other privacy artifacts may be applicable to an agency offering or using proofing services such as Data Use Agreements, Computer Matching Agreements, etc. The SAOP can assist the agency in determining what additional requirements apply. Moreover, a thorough understanding of the individual components of digital authentication will enable the SAOP to thoroughly assess and mitigate privacy risks either through compliance processes or by other means.

