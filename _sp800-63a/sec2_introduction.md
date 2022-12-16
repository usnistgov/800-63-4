---
layout: default
title: Introduction
navOrder: 2
navTitle: Introduction
permalink: /sp800-63a/introduction/
anchor: purpose
section: 2
---

#  Introduction {#intro}

_This section is informative._

One of the challenges of providing online services is being able to associate a set of activities with a single, specific individual. While there are situations where this is not necessary - such as when anonymity or pseudonymity is desirable - there are other situations where it is important to reliably establish an association with a real-life subject. Examples of this include accessing some government services or executing financial transactions. There are also situations where association with a real-life subject is required by regulations (e.g., the financial industry's 'Know Your Customer' requirements) or to establish accountability for high-risk actions (e.g., changing the release rate of water from a dam).

This guidance defines identity proofing as the process of establishing, to some degree of certainty or assurance, a relationship between a subject accessing online services and a real-life person. This document provides guidance for Federal Agencies, third-party Credential Service Providers (CSP), and other organizations that provide identity proofing services.  

The following list states which sections of this document contain normative language and which contain non-normative, informative language.  Where needed to help clarify specific requirements, normative sections often include informative explanations.  See the "Requirements Notation and Conventions" section of this document for clarification on which statements are normative and which are not.  

- 1 Purpose _Informative_
- 2 Introduction _Informative_
- 3 Definitions and Abbreviations _Informative_
- 4 Identity Assurance Level Requirements _Normative_
- 5 Identity Resolution, Validation, and Verification _Normative_
- 6 Subscriber Accounts _Normative_
- 7 Threats and Security Considerations _Informative_
- 8 Privacy Considerations _Informative_
- 9 Usability Considerations _Informative_
- 10 Equity Considerations _Informative_

## Expected Outcomes of Identity Proofing

The expected outcomes of identity proofing include:

* **Identity resolution**: determine that the claimed identity corresponds to a single, unique individual within the context of the population of users the CSP serves;
* **Evidence validation**: confirm that all supplied evidence is genuine, authentic, and unexpired; 
* **Attribute validation**: confirm the accuracy of core attributes;
* **Identity verification**: verify that the claimed identity is associated with the real-life person supplying the identity evidence; and
* **Fraud Prevention**: mitigate attempts to gain fraudulent access to benefits, services, data, or assets. 

## Identity Assurance Levels

Assurance in a subscriber's identity is described using one of the following Identity Assurance Levels (IAL). Each successive IAL builds on the requirements of lower IALs in order to achieve greater assurance.   

**No identity proofing (IAL0)**: There is no requirement to link the applicant to a specific, real-life identity. Any attributes provided in conjunction with the subject's activities are self-asserted and are treated as self-asserted. Self-asserted attributes at IAL0 are neither validated nor verified.

**IAL1**: The identity proofing process supports the real-world existence of the claimed identity. Core attributes are obtained from identity evidence or asserted by the applicant.  All core attributes are validated against authoritative or credible sources and steps are taken to link the attributes to the person undergoing the identity proofing process.    

**IAL2**: IAL2 adds additional rigor to the identity proofing process by requiring the collection of stronger types of evidence and a more rigorous process for validating the evidence and verifying the identity. 

**IAL3**: IAL3 adds the requirement for a trained CSP representative to interact directly with the applicant during the entire identity proofing session, either in person or via a supervised remote identity proofing session.
