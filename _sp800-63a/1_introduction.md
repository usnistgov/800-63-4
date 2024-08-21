---
layout: default
title: Introduction
navOrder: 2
navTitle: Introduction
permalink: /sp800-63a/introduction/
anchor: introduction
section: 1
---

#  Introduction {#introduction}

_This section is informative._

One of the challenges of providing online services is being able to associate a set of activities with a single, known individual. While there are situations where this is not necessary, there are other situations where it is important to reliably establish an association with a real-life subject. Examples of this include accessing government services and executing financial transactions. There are also situations where association with a real-life subject is required by regulations (e.g., the financial industry's 'Customer Identification Program' requirements) or to establish accountability for high-risk actions (e.g., changing the release rate of water from a dam).

This guidance defines identity proofing as the process of establishing, to some degree of assurance, a relationship between a subject accessing online services and a real-life person. This document provides guidance for Federal Agencies, third-party Credential Service Providers (CSP), and other organizations that provide or use identity proofing services.  

## Expected Outcomes of Identity Proofing

The expected outcomes of identity proofing include:

* **Identity resolution**: Determine that the claimed identity corresponds to a single, unique individual within the context of the population of users served by the CSP or online service.
* **Evidence validation**: Confirm that supplied evidence is genuine, authentic, and valid. 
* **Attribute validation**: Confirm the accuracy of the core attributes. Core attributes are the minimum set required for identity proofing.
* **Identity verification**: Confirm that the claimant is the genuine owner of the presented evidence and attributes.
* **Identity enrollment**: Enroll the identity proofed applicant in the CSP's identity service as a subscriber.
* **Fraud mitigation**: Detect, respond to, and prevent access to benefits, services, data, or assets using a fraudulent identity. 

Identity proofing services are expected to incorporate privacy-enhancing principles, such as data minimization, as well as employ good usability practices, to minimize the burden on applicants while still accomplishing the expected outcomes.  

## Identity Assurance Levels

Assurance (confidence) in a subscriber's identity is established using the processes associated with the defined Identity Assurance Levels (IAL). Each successive IAL builds on the requirements of lower IALs in order to achieve increased assurance. 

**No identity proofing**: There is no requirement to link the applicant to a specific, real-life person. Any attributes provided in conjunction with the subject's activities are self-asserted or are treated as self-asserted. Evidence is not validated and attributes are neither validated nor verified.

**IAL1**: The identity proofing process supports the real-world existence of the claimed identity and provides some assurance that the applicant is associated with that identity. Core attributes are obtained from identity evidence or self-asserted by the applicant.  All core attributes (see [Sec. 2.2](2_proofing.md#CoreAttributes)) are validated against authoritative or credible sources and steps are taken to link the attributes to the person undergoing the identity proofing process. Identity proofing is performed using remote or onsite processes, with or without the attendance of a CSP representative (proofing agent or trusted referee). Upon the successful completion of identity proofing, the applicant is enrolled into a subscriber account and any authenticators, including subscriber-provided authenticators, can then be bound to the account. IAL1 is designed to limit highly scalable attacks, provide protection against synthetic identities, and provide protections against attacks using compromised PII. 

**IAL2**: IAL2 adds additional rigor to the identity proofing process by requiring the collection of additional evidence and a more rigorous process for validating the evidence and verifying the identity. In addition to those threats addressed by IAL1, IAL2 is designed to limit scaled and targeted attacks, provide protections against basic evidence falsification and evidence theft, and provide protections against basic social engineering tactics.

**IAL3**: IAL3 adds the requirement for a trained CSP representative (proofing agent) to interact directly with the applicant, as part of an on-site attended identity proofing session, and the collection of at least one biometric. The successful on-site identity proofing session concludes with the enrollment of the applicant into a subscriber account and the delivery of one or more authenticators associated (bound) to that account. IAL3 is designed to limit more sophisticated attacks, provide protections against advanced evidence falsification, theft, and repudiation, and provide protection against more advanced social engineering tactics.
  
~~~
\clearpage
~~~
{:latex-literal="true"}

## Notations

This guideline uses the following typographical conventions in text:

- Specific terms in **CAPITALS** represent normative requirements. When these same terms are not in **CAPITALS**, the term does not represent a normative requirement. 
    - The terms "**SHALL**" and "**SHALL NOT**" indicate requirements to be followed strictly in order to conform to the publication and from which no deviation is permitted.
    - The terms "**SHOULD**" and "**SHOULD NOT**" indicate that among several possibilities, one is recommended as particularly suitable without mentioning or excluding others, that a certain course of action is preferred but not necessarily required, or that (in the negative form) a certain possibility or course of action is discouraged but not prohibited.
    - The terms "**MAY**" and "**NEED NOT**" indicate a course of action permissible within the limits of the publication.
    - The terms "**CAN**" and "**CANNOT**" indicate a possibility and capability&mdash;whether material, physical, or causal&mdash;or, in the negative, the absence of that possibility or capability.

## Document Structure

This document is organized as follows. Each section is labeled as either normative (i.e., mandatory for compliance) or informative (i.e., not mandatory).

- Section 1 provides an introduction to the document. This section is _informative_.
- Section 2 describes requirements for identity proofing. This section is _normative_.
- Section 3 describes general requirements for IALs. This section is _normative_.
- Section 4 describes requirements for specific IALs. This section is _normative_.
- Section 5 describes subscriber accounts. This section is _normative_.
- Section 6 provides security considerations. This section is _informative_.
- Section 7 provides privacy considerations. This section is _informative_.
- Section 8 provides usability considerations. This section is _informative_.
- Section 9 provides equity considerations. This section is _informative_.
- References contains a list of publications referred to from this document. This section is _informative_.
- Appendix A provides a non-exhaustive list of types of identity evidence, grouped by strength. This appendix is _informative_.
- Appendix B contains a selected list of abbreviations used in this document. This appendix is _informative_.
- Appendix C contains a glossary of selected terms used in this document. This appendix is _informative_.
- Appendix D contains a summarized list of changes in this document's history. This appendix is _informative_.
