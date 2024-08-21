---
layout: default
title: Introduction
navOrder: 2
navTitle: Introduction
permalink: /sp800-63/introduction/
anchor: introduction
section: 1
---

# Introduction {#introduction}

*This section is informative.*

The rapid proliferation of online services over the past few years has heightened the need for reliable, equitable, secure, and privacy-protective digital identity solutions. A digital identity is always unique in the context of an online service. However, a person may have multiple digital identities and while a digital identity may relay a unique and specific meaning within the context of an online service, the real-life identity of the individual behind the digital identity may not be known. When confidence in a person's real-life identity is not required to provide access to an online service, organizations may use anonymous or pseudonymous accounts. In all other use cases, a digital identity is intended to demonstrate trust between the holder of the digital identity and the person, organization, or system on the other side of the online service. However, this process can present challenges. There are multiple opportunities for mistakes, miscommunication, impersonation, and other attacks that fraudulently claim another person's digital identity. Additionally, given the broad range of individual needs, constraints, capacities, and preferences, online services must be designed with equity, usability, and flexibility to ensure broad and enduring participation and access to digital devices and services.

Digital identity risks are dynamic and exist along a continuum; consequently, organizations' digital identity risk management approach should seek to manage risks using outcome-based approaches that are designed to meet the organization's unique needs. This guidance defines specific assurance levels which operate as baseline control sets designed to provide a common point for organizations seeking to address identity-related risks. Assurance levels provide multiple benefits, including a starting point for agencies in their risk management journey and a common structure for supporting interoperability between different entities. It is, however, impractical to create assurance levels that can comprehensively address the entire spectrum of risks, threats, or considerations and organization will face when deploying an identity solution. For this reason, these guidelines promote a risk-oriented approach to digital identity solution implementation rather than a compliance-oriented approach, and organizations are encouraged to tailor their control implementations based on the processes defined in these guidelines.

Additionally, risks associated with digital identity stretch beyond the potential impacts to the organization providing online services. These guidelines endeavor to account for risks to individuals, communities, and other organizations more robustly and explicitly. Organizations should consider how digital identity decisions that prioritize security might affect, or need to accommodate, the individuals who interact with the organization's programs and services. Privacy, equity, and usability for individuals should be considered along with security. Additionally, organizations should consider their digital identity approach alongside other mechanisms for identity management, such as those used in call centers and in-person interactions. By taking a human-centric and continuously informed approach to mission delivery, organizations have an opportunity to incrementally build trust with the variety of populations they serve, improve customer satisfaction, identify issues more quickly, and provide individuals with culturally appropriate and effective redress options.

The composition, models, and availability of identity services has significantly changed since the first version of SP 800-63 was released, as have the considerations and challenges of deploying secure, private, usable, and equitable services to diverse user communities. This revision addresses these challenges by clarifying requirements based on the function that an entity may serve under the overall digital identity model.

Additionally, this publication provides instruction for credential service providers (CSPs), verifiers, and relying parties (RPs), that supplement the *NIST Risk Management Framework* [[NISTRMF]](references.md#ref-NIST-RMF) and its component special publications. It describes the risk management processes that organizations should follow to implement digital identity services and expands upon the NIST RMF by outlining how equity and usability considerations should be incorporated. It also highlights the importance of considering impacts, not only on enterprise operations and assets, but also on individuals, other organizations, and &mdash; more broadly &mdash; society. Furthermore, digital identity management processes for identity proofing, authentication, and federation typically involve processing personal information, which can present privacy risks. Therefore, these guidelines include privacy requirements and considerations to help mitigate potential associated privacy risks.

Finally, while these guidelines provide organizations with technical requirements and recommendations for establishing, maintaining, and authenticating the digital identity of subjects who access digital systems over a network, additional support options outside of the purview of information technology teams may be needed to address barriers and adverse impacts, foster equity, and successfully deliver on mission objectives.

## Scope and Applicability

This guidance applies to all online services for which some level of digital identity is required, regardless of the constituency (e.g., residents, business partners, and government entities). For this publication, "person" refers only to natural persons.

These guidelines primarily focus on organizational services that interact with external users, such as residents accessing public benefits or private-sector partners accessing collaboration spaces. However, it also applies to federal systems accessed by employees and contractors. The *Personal Identity Verification (PIV) of Federal Employees and Contractors* standard [[FIPS201]](references.md#ref-FIPS201) and its corresponding set of Special Publications and organization-specific instructions extend these guidelines for the federal enterprise, by providing additional technical controls and processes for issuing and managing Personal Identity Verification (PIV) Cards, binding additional authenticators as derived PIV credentials, and using federation architectures and protocols with PIV systems.

Online services not covered by this guidance include those associated with national security systems as defined in 44 U.S.C. § 3552(b)(6). Private-sector organizations and state, local, and tribal governments whose digital processes require varying levels of digital identity assurance may consider the use of these standards where appropriate.

These guidelines address logical access to online systems, services, and applications. They do not specifically address physical access control processes. However, the processes specified in these guidelines can be applied to physical access use cases where appropriate. Additionally, these guidelines do not explicitly address some subjects including, but not limited to, machine-to-machine authentication, interconnected devices (e.g., Internet of Things (IoT) devices), or access to Application Programming Interfaces (APIs) on behalf of subjects.

## How to Use This Suite of SPs

These guidelines support the mitigation of the negative impacts of errors that occur during the identity system functions of identity proofing, authentication, and federation. [Sec. 3](3_DIRM.md#sec5), Digital Identity Risk Management, provides details on the risk assessment process and how the results of the risk assessment and additional context inform the selection of controls to secure the identity proofing, authentication, and federation processes. Controls are selected by determining the assurance level required to mitigate each applicable type of digital identity error for a particular service based on risk and mission.

Specifically, organizations are required to individually select assurance levels[^xALs] that correspond to each function being performed:

- Identity Assurance Level (IAL) refers to the identity proofing process.
- Authentication Assurance Level (AAL) refers to the authentication process.
- Federation Assurance Level (FAL) refers to the federation process when the RP is connected to a CSP or an IdP through a federated protocol.

[^xALs]: When described generically or bundled, these guidelines will refer to IAL, AAL, and FAL as ***xAL***.

SP 800-63 is organized as the following suite of volumes:

- SP 800-63 *Digital Identity Guidelines* provides the digital identity models, risk assessment methodology, and process for selecting assurance levels for identity proofing, authentication, and federation. _SP 800-63 contains both normative and informative material._
- [[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"}: provides requirements for identity proofing and the enrollment of applicants, either remotely or in-person, that wish to gain access to resources at each of the three IALs. It details the responsibilities of CSPs with respect to establishing and maintaining subscriber accounts and binding CSP issued or subscriber-provided authenticators to the subscriber account.
_SP 800-63A contains both normative and informative material._
- [[SP800-63B]](../_sp800-63b/1_introduction.md#introduction){:latex-href="#ref-SP800-63B"} provides requirements for authentication processes, including choices of authenticators, that may be used at each of the three AALs. It also provides recommendations on events that may occur during the lifetime of authenticators, including invalidation in the event of loss or theft.
_SP 800-63B contains both normative and informative material._
- [[SP800-63C]](../_sp800-63c/1_introduction.md#introduction){:latex-href="#ref-SP800-63C"} provides requirements on the use of federated identity architectures and assertions to convey the results of authentication processes and relevant identity information to an agency application. This volume offers privacy-enhancing techniques for sharing information about a valid, authenticated subject, and describes methods that allow for strong multi-factor authentication (MFA) while the subject remains pseudonymous to the online service.
_SP 800-63C contains both normative and informative material._

## Enterprise Risk Management Requirements and Considerations {#ERMreqs}

Effective enterprise risk management is multidisciplinary by design and involves the consideration of diverse sets of factors and equities. In a digital identity risk management context, these factors include, but are not limited to, information security, privacy, equity, and usability. It is important for risk management efforts to weigh these factors as they relate to enterprise assets and operations, individuals, other organizations, and society.

During the process of analyzing factors relevant to digital identity, organizations may determine that measures outside of those specified in this publication are appropriate in certain contexts (e.g., where privacy or other legal requirements exist or where the output of a risk assessment leads the organization to determine that additional measures or alternative procedural safeguards are appropriate). Organizations, including federal agencies, may employ compensating or supplemental controls that are not specified in this publication. They may also consider partitioning the functionality of an online service to allow less sensitive functions to be available at a lower level of assurance in order to improve equity and access without compromising security.

The considerations detailed below support enterprise risk management efforts and encourage informed, inclusive, and human-centered service delivery. While this list of considerations is not exhaustive, it highlights a set of cross-cutting factors that are likely to impact decision-making associated with digital identity management.

### Security, Fraud, and Threat Prevention

It is increasingly important for organizations to assess and manage digital identity security risks, such as unauthorized access due to impersonation. As organizations consult this guidance, they should consider potential impacts to the confidentiality, integrity, and availability of information and information systems that they manage and that their service providers and business partners manage on behalf of the individuals and communities that they serve.

Federal agencies implementing these guidelines are required to meet statutory responsibilities, including those under the _Federal Information Security Modernization Act (FISMA) of 2014_ [[FISMA]](references.md#ref-FISMA) and related NIST standards and guidelines. NIST recommends that non-federal organizations implementing these guidelines follow comparable standards (e.g., ISO 27001) to ensure the secure operation of their digital systems.

FISMA requires federal agencies to implement appropriate controls to protect federal information and information systems from unauthorized access, use, disclosure, disruption, or modification. The NIST RMF [[NISTRMF]](references.md#ref-NIST-RMF) provides a process that integrates security, privacy, and cyber supply-chain risk management activities into the system development life cycle. It is expected that federal agencies and organizations that provide services under these guidelines have already implemented the controls and processes required under FISMA and associated NIST risk management processes and publications.

The controls and requirements encompassed by the identity, authentication, and Federation Assurance Levels under these guidelines augment, but do not replace or alter, the information and information system controls determined under FISMA and the RMF.

It is increasingly important for organizations to assess and manage identity-related fraud risks associated with identity proofing and authentication processes. As organizations consult this guidance, they should consider the evolving threat environment, the availability of innovative anti-fraud measures in the digital identity market, and the potential impact of identity-related fraud. This is particularly important with respect to public-facing online services where the impact of identity-related fraud on e-government service delivery, public trust, and agency reputation can be substantial. This version enhances measures to combat identity theft and identity-related fraud by repurposing IAL1 as a new assurance level, updating authentication risk and threat models to account for new attacks, providing new options for phishing resistant authentication, introducing requirements to prevent automated attacks against enrollment processes, and preparing for new technologies (e.g., mobile driver's licenses and verifiable credentials) that can leverage strong identity proofing and authentication.


### Privacy

When designing, engineering, and managing digital identity systems, it is imperative to consider the potential of that system to create privacy-related problems for individuals when processing (e.g., collection, storage, use, and destruction) personally identifiable information (PII) and the potential impacts of problematic data actions. If a breach of PII or a release of sensitive information occurs, organizations need to ensure that the privacy notices describe, in plain language, what information was improperly released and, if known, how the information was exploited.

Organizations need to demonstrate how organizational privacy policies and system privacy requirements have been implemented in their systems. These guidelines recommend that organizations employ the full set of legal and regulatory mandates that may affect their users and technology providers including:

- The *NIST Privacy Framework* [[NISTPF]](references.md#ref-NIST-PF), which enables privacy engineering practices that support privacy by design concepts and helps organizations protect individuals' privacy.
- The *[[PrivacyAct]](references.md#ref-PrivacyAct) of 1974, 2020 Edition* which established a set of fair information practices for the collection, maintenance, use, and disclosure of information about individuals that is maintained by federal agencies in systems of records.
- *OMB Guidance for Implementing the Privacy Provisions of the E-Government Act of 2002* [[M-03-22]](references.md#ref-M-03-22), which describes the Privacy Impact Assessments that are supported by the privacy risk assessments that are required for PII processing or storing.
- [[SP800-53]](references.md#ref-SP800-53) *Security and Privacy Controls for Information Systems and Organizations* , which lists privacy controls that can be implemented to mitigate the risks identified in the privacy risk and impact assessments.
- [[SP800-122]](references.md#ref-SP800-122) *Guide to Protecting the Confidentiality of Personally Identifiable Information (PII)*, which assists federal agencies in understanding what PII is, the relationship between protecting the confidentiality of PII, privacy, and the Fair Information Practices, and safeguards for protecting PII.

Furthermore, each volume of SP 800-63, ([[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"}, [[SP800-63B]](../_sp800-63b/1_introduction.md#introduction){:latex-href="#ref-SP800-63B"}, and [[SP800-63C]](../_sp800-63c/1_introduction.md#introduction){:latex-href="#ref-SP800-63C"}) contains a specific section providing detailed privacy guidance and considerations for the implementation of the processes, controls, and requirements presented in that volume as well as normative requirements on data collection, retention, and minimization.

### Equity

Equity has been defined as "the consistent and systematic fair, just, and impartial treatment of all individuals, including individuals who belong to underserved communities that have been denied such treatment" [[EO13985]](references.md#ref-EO13985). Incorporating equity considerations when designing or operating a digital identity service helps ensure a person's ability to engage in an online service, such as accessing a critical service like healthcare. Accessing online services is often dependent on a person's ability to present a digital identity and use the required technologies successfully and safely. Many populations are either unable to successfully present a digital identity or face a higher degree of burden in navigating online services than their more privileged peers. In a public service context, this poses a direct risk to successful mission delivery. In a broader societal context, challenges related to digital access can exacerbate existing inequities and continue systemic cycles of exclusion for historically marginalized and underserved groups.


To support the continuous evaluation and improvement program described in [Sec. 3](3_DIRM.md#sec5), it is important to maintain awareness of existing inequities faced by served populations and potential new inequities or disparities between populations that could be caused or exacerbated by the design or operation of digital identity systems. This can help identify the opportunities, processes, business partners, and multi-channel identity proofing and service delivery methods that best support the needs of those populations while also managing privacy, security, and fraud risks.

Further, section 508 of the Rehabilitation Act of 1973 (2011) [[Section508]](references.md#ref-Section508) was enacted to eliminate barriers in information technology and require federal agencies to make electronic and information technologies accessible to people with disabilities. While these guidelines do not directly assert requirements from [[Section508]](references.md#ref-Section508), federal agencies and their identity service providers are expected to design online  services and systems with the experiences of people with disabilities in mind to ensure that accessibility is prioritized.  

### Usability

Usability refers to the extent to which a system, product, or service can be used to achieve goals with effectiveness, efficiency, and satisfaction in a specified context of use. Usability also supports major objectives such as equity, service delivery, and security. Like equity, usability requires an understanding of the people who interact with a digital identity system or process, as well as their unique goals and context of use.

Readers of this guidance should take a holistic approach to considering the interactions that each user will engage in throughout the process of enrolling in and authenticating to a service. Throughout the design and development of a digital identity system or process, it is important to conduct usability evaluations with demographically representative users, from all communities served and perform realistic scenarios and tasks in appropriate contexts of use. Additionally, following usability guidelines and considerations can help organizations meet customer experience goals articulated in federal policy [[EO14058]](references.md#ref-EO14058). Digital identity management processes should be designed and implemented so that it is easy for users to do the right thing, hard to do the wrong thing, and easy to recover when the wrong thing happens.

## Notations

This guideline uses the following typographical conventions in text:

- Specific terms in **CAPITALS** represent normative requirements. When these same terms are not in **CAPITALS**, the term does not represent a normative requirement.
    - The terms "**SHALL**" and "**SHALL NOT**" indicate requirements to be followed strictly in order to conform to the publication and from which no deviation is permitted.
    - The terms "**SHOULD**" and "**SHOULD NOT**" indicate that among several possibilities, one is recommended as particularly suitable without mentioning or excluding others, that a certain course of action is preferred but not necessarily required, or that (in the negative form) a certain possibility or course of action is discouraged but not prohibited.
    - The terms "**MAY**" and "**NEED NOT**" indicate a course of action that is permissible within the limits of the publication.
    - The terms "**CAN**" and "**CANNOT**" indicate a material, physical, or causal possibility and capability or &mdash; in the negative &mdash; the absence of that possibility or capability.

~~~
\clearpage
~~~
{:latex-literal="true"}

## Document Structure

This document is organized as follows. Each section is labeled as either normative (i.e., mandatory for compliance) or informative (i.e., not mandatory).

- Section 1 provides an introduction to the document. This section is _informative_.
- Section 2 describes a general model for digital identity. This section is _informative_.
- Section 3 describes the digital identity risk model. This section is _normative_.
- The References section contains a list of publications that are cited in this document. This section is _informative_.
- Appendix A contains a selected list of abbreviations used in this document. This appendix is _informative_.
- Appendix B contains a glossary of selected terms used in this document. This appendix is _informative_.
- Appendix C contains a summarized list of changes in this document's history. This appendix is _informative_.
