---
layout: default
title: Introduction
navOrder: 2
navTitle: Introduction
permalink: /sp800-63/introduction/
anchor: intro
section: 2
---

# Introduction {#intro}

*This section is informative.*

As the line between the virtual world and physical world blurs, and as digital and internet-enabled technologies continue to proliferate and connect, it is imperative that developers and consumers alike understand this changing hybrid ecosystem - including its associated opportunities and risks. Engagement across this ecosystem is often determined by an individual's ability and willingness to establish a digital identity - the unique representation of a person engaged in an online transaction.

A digital identity is always unique in the context of a digital service but does not always uniquely identify a person in all contexts. Further, while a digital identity may relay unique and specific meaning within the context of a digital service, the real-life identity of the individual behind the digital identity may not be known. For the purpose of this publication, a "person" refers to natural persons only (i.e., not all legal persons.)

Establishing a digital identity is intended to demonstrate trust between the holder of the digital identity and the person, organization, or system on the other side of the digital transaction. However, this process can present challenges. As in relationships and transactions in the physical world, there are multiple opportunities for mistakes, miscommunication, impersonation, and other attacks that fraudulently claim another person's digital identity. Additionally, given the broad range of individual needs, constraints, capacities, and preferences, digital services must be designed with equity and flexibility in mind to ensure broad and enduring participation.

Risks associated with digital identity stretch beyond the potential impacts to enterprises and should be incorporated into enterprise decision-making. This publication endeavors to more robustly and explicitly account for risks to individuals, communities, and other organizations. Specifically, while using this guidance, organizations should consider how decisions related to digital identity that prioritize organizational cybersecurity objectives might affect or need to accommodate other objectives, such as those related to privacy, equity, usability, and other indicators of mission and business performance that center the experiences of the individuals interacting with programs and services. By taking a human-centered and continuously informed approach to mission delivery, organizations have an opportunity to incrementally build trust with the variety of populations they serve, improve customer satisfaction, identify issues more quickly, and provide individuals with effective and culturally appropriate redress options.

These guidelines lay out a model for federal programs and other organizations to assess and manage risks associated with digital identity systems, including the processes, policies, data, people, and technologies that support digital identity management. The model is supported by a series of processes: identity proofing, authentication, and federation. The identity proofing process establishes that a subject is a specific physical person. The digital authentication process determines the validity of one or more authenticators used to claim a digital identity and establishes confidence that a subject attempting to access a digital service: (1) is in control of the technologies being used for authentication, and (2) is the same subject that previously accessed the service. Finally, the federation process allows for identity information to be shared in support of authentication across systems.

The composition, model, and availability of identity services has significantly changed since the first version of SP 800-63 was released, as have the considerations and challenges of deploying secure, private, and equitable services to diverse user communities. This revision addresses these challenges while facilitating the new models and architectures for identity services that have developed by clarifying requirements based on the function an entity may serve under the overall digital identity model.

Additionally, this publication provides instruction for credential service providers (CSPs), verifiers, and relying parties (RPs) and it describes the risk management processes that organizations should follow for implementing digital identity services and that supplement the *NIST Risk Management Framework* [[NISTRMF]](sec8_references.md#ref-NIST-RMF) and its component special publications. The publication expands upon the NIST RMF by outlining how equity and usability considerations should be incorporated into digital identity risk management processes and it highlights the importance of considering impacts, not only on the enterprise operations and assets, but also on individuals, other organizations, and, more broadly, society. Further, while digital authentication supports privacy protection by mitigating risks of unauthorized access to individuals' information, given that identity proofing, authentication, authorization, and federation often involve the processing of individuals' information, these functions can also create privacy risks. These guidelines, therefore, include privacy requirements and considerations to help mitigate potential associated privacy risks.

Finally, while this publication provides organizations with technical requirements and recommendations for establishing, maintaining, and authenticating the digital identity of subjects in order to access digital systems over a network, additional support options outside the purview of information technology teams may need to be provided to address barriers and adverse impacts, foster equity, and successfully deliver on mission objectives.

## Scope & Applicability

Not all digital services require identity proofing or authentication; however, this guidance applies to all online transactions for which some level of digital identity is required, regardless of the constituency (e.g., citizens, business partners, and government entities).

These guidelines primarily focus on organizational services that interact with external users, such as citizens accessing public benefits or private sector partners accessing collaboration spaces. However, it also applies to federal systems accessed by employees and contractors. The *Personal Identity Verification (PIV) of Federal Employees and Contractors* standard [[FIPS201]](sec8_references.md#ref-FIPS201) and its corresponding set of special publications and organization-specific instructions, extend these guidelines for the federal enterprise, providing additional technical controls and processes for issuing and managing Personal Identity Verification (PIV) cards, binding additional authenticators as derived PIV credentials, and using federation architectures and protocols with PIV systems.

Transactions not covered by this guidance include those associated with national security systems as defined in 44 U.S.C. § 3542(b)(2). Private sector organizations and state, local, and tribal governments whose digital processes require varying levels of digital identity assurance may consider the use of these standards where appropriate.

Additionally, these technical guidelines do not address the identity of subjects for physical access (e.g., to buildings), though some identities used for online transactions may also be used for physical access. Additionally, this revision of these guidelines does not explicitly address device identity, often referred to as machine-to-machine (such as router-to-router) authentication or interconnected devices, commonly referred to as the internet of things (IoT), although these guidelines are written to refer to generic subjects wherever possible to leave open the possibility for applicability to devices. Furthermore, these guidelines do not address authorization of access to Application Programming Interfaces (APIs) on behalf of subjects.

## How to Use this Suite of SPs

These guidelines support the mitigation of the negative impacts induced by a digital identity error by separating the individual elements of digital identity into discrete, component parts. For non-federated systems, agencies will select two components, referred to as *Identity Assurance Level (IAL)* and *Authentication Assurance Level (AAL)*. For federated systems, a third component, *Federation Assurance Level (FAL)*, is included. [Sec. 5, Digital Identity Risk Management](sec5_DIRM.md#sec5) provides details on the risk assessment process and how the results of the risk assessment, with additional context, inform organizational selection of IAL, AAL, and FAL combinations based on risk and mission.

By conducting appropriate risk management for business, security, and privacy, side-by-side with mission needs, organizations will select IAL, AAL, and FAL as distinct options. Specifically, organizations are required to individually select levels corresponding to each function being performed. While many systems could have the same numerical level for each IAL, AAL, and FAL, this is not a requirement and organizations should not assume they will be the same in any given system or application.

The components of identity assurance detailed in these guidelines are as follows:

* **IAL** refers to the identity proofing process.
* **AAL** refers to the authentication process.
* **FAL** refers to the federation process, when the RP is connected through a federated protocol.

> Note: When described generically or bundled, these guidelines will refer to IAL, AAL, and FAL as ***xAL***.

SP 800-63 is organized as the following suite of volumes:

SP 800-63 *Digital Identity Guidelines*: Provides the risk assessment methodology and an overview of general identity frameworks, using authenticators, credentials, and assertions together in a digital system, and a risk-based process of selecting assurance levels. _SP 800-63 contains both normative and informative material._

[[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"}: Provides requirements for enrollment and identity proofing of applicants, either remotely or in person, that wish to gain access to resources at each of the three identity assurance levels (IALs). It details the responsibilities of Credential Service Providers (CSPs) with respect to establishing and maintaining subscriber accounts and binding authenticators (either CSP-issued or subscriber-provided) to the subscriber account.
_SP 800-63A contains both normative and informative material._

[[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}: Provides recommendations on types of authentication processes, including choices of authenticators, that may be used at each of the three authentication assurance levels (AALs). It also provides recommendations on the lifecycle of authenticators, including invalidation in the event of loss or theft.
_SP 800-63B contains both normative and informative material._

[[SP800-63C]](../_sp800-63c/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63C"}: Provides requirements on the use of federated identity architectures and assertions to convey the results of authentication processes and relevant identity information to an agency application. Further, this volume offers privacy-enhancing techniques to share information about a valid, authenticated subject, and describes methods that allow for strong multi-factor authentication (MFA) while the subject remains pseudonymous to the digital service.
_SP 800-63C contains both normative and informative material._

## Enterprise Risk Management Requirements and Considerations {#ERMreqs}

Effective enterprise risk management is multidisciplinary by default and involves the consideration of a diverse set of factors and equities. In a digital identity risk management context, these factors include, but are not limited to, information security, privacy, equity, and usability. It is important for risk management efforts to weigh these factors as they relate not only to enterprise assets and operations but also to individuals, other organizations, and society more broadly.

During the process of analyzing factors relevant to digital identity, organizations may determine that measures outside of those specified in this publication are appropriate in certain contexts, for instance where privacy or other legal requirements exist or where the output of a risk assessment leads the organization to determine that additional measures or other process safeguards are appropriate. Organizations, including federal agencies, may employ compensating or supplemental controls not specified in this publication. They may also consider partitioning the functionality of a digital service to allow less sensitive functions to be available at a lower level of assurance.

The considerations detailed below support enterprise risk management efforts and encourage informed, inclusive, and human-centric service delivery. While this list of considerations is not exhaustive, it highlights a set of cross-cutting factors likely to impact decision-making associated with digital identity management.

### Security

It is increasingly important for enterprise organizations to assess and manage digital identity security risks, such as unauthorized access, availability issues, impersonation, and other types of fraudulent claims, as well as institute strong identity governance practices. As organizations consult this guidance, they should consider potential impacts to the confidentiality, integrity, and availability of information and information systems that they manage and that their service providers and business partners manage on behalf of the individuals and communities that they serve.

Federal agencies implementing these guidelines need to adhere to their statutory responsibilities, including those under the _Federal Information Security Modernization Act (FISMA) of 2014_ [[FISMA]](sec8_references.md#ref-FISMA) and related NIST standards and guidelines. NIST recommends that non-federal organizations implementing these guidelines follow equivalent standards to ensure the secure operation of their digital systems.

FISMA requires federal agencies to implement appropriate controls to protect federal information and information systems from unauthorized access, use, disclosure, disruption, or modification. The NIST RMF [[NISTRMF]](sec8_references.md#ref-NIST-RMF) provides a process that integrates security, privacy, and cyber supply chain risk management activities into the system development life cycle. It is expected that federal agencies and organizations that provide services under these guidelines have already implemented the controls and processes required under FISMA and associated NIST risk management processes and publications.

The controls and requirements encompassed by the identity, authentication, and federation assurance levels under these guidelines augment, but do not replace or alter, the information and information system controls as determined under FISMA and the RMF.

### Privacy

When designing, engineering, and managing digital identity systems, it is imperative to consider the potential of that system to create privacy-related problems for individuals when processing PII &mdash; a problematic data action &mdash; and the potential impact of the problematic data action should it occur. Additionally, by focusing on the privacy engineering objectives of predictability, manageability, and disassociability, organizations can determine the types of capabilities a given system may need to be able to demonstrate how organizational privacy policies and system privacy requirements have been implemented.

The *Privacy Act of 1974, 2010 Edition*, [[PrivacyAct]](sec8_references.md#ref-PrivacyAct) established a set of fair information practices for the collection, maintenance, use, and disclosure of information about individuals that is maintained by federal agencies in systems of records.

When designing and implementing digital identity management processes and systems, privacy risk assessments are required for PII processing under these guidelines. Such privacy risk assessments can be used to support Privacy Impact Assessments under *OMB Guidance for Implementing the Privacy Provisions of the E-Government Act of 2002* [[M-03-22]](sec8_references.md#ref-M-03-22) as well as to select controls from NIST Special Publication 800-53, *Security and Privacy Controls for Information Systems and Organizations* [[SP800-53]](sec8_references.md#ref-SP800-53). Further, each volume of 800-63 (63A, 63B, and 63C) contains a specific section providing detailed privacy requirements and considerations for the implementation of the processes, controls, and requirements presented in that volume.

### Equity

As defined in Executive Order 13985, *Advancing Racial Equity and Support for Underserved Communities Through the Federal Government* [[EO13985]](sec8_references.md#ref-EO13985), equity refers to the consistent and systematic fair, just, and impartial treatment of all individuals, including individuals who belong to underserved communities that have been denied such treatment, such as Black, Latino, and Indigenous and Native American persons, Asian Americans and Pacific Islanders, and other persons of color; members of religious minorities; lesbian, gay, bisexual, transgender, and queer (LGBTQ+) persons; persons with disabilities; persons who live in rural areas; and persons otherwise adversely affected by persistent poverty or inequality.

A person's ability to engage in an online transaction, such as accessing a critical service like healthcare, is often dependent on their ability to successfully and safely present a digital identity. Given the broad disparities that exist in the U.S. society and globally, many people are either unable to successfully present a digital identity, or they face a higher degree of burden in navigating online services than their more privileged peers, leaving them locked out of critical services or broader participation in the online world. In a public service context, this poses a direct risk to successful mission delivery. In a broader societal context, challenges related to digital access can exacerbate existing inequities and continue systemic cycles of exclusion for historically marginalized and underserved groups.

Readers of this guidance are encouraged to consider existing inequities faced by the populations they serve to identify opportunities to design or operate digital identity systems and processes in ways that best support their needs. Readers are also encouraged to consider any potential or actual impact to the experiences and outcomes of these populations, including disparities between populations, caused by the design or operation of digital identity systems.

For federal agencies implementing these guidelines, EO 13985 directs federal agencies to identify underserved communities for the programs and services that they provide and to determine and address any systemic barriers to underserved communities to provide equitable access to those programs and services. In alignment with the direction set by EO 13985, federal agencies should determine potential barriers communities and individuals may face to enrollment in and access to online benefits and services. They should also  identify whether programmatic changes may be necessary to advance equity.

### Usability

Usability refers to the extent to which a system, product, or service can be used by specified users to achieve specified goals with effectiveness, efficiency, and satisfaction in a specified context of use.

Similar to equity, usability requires an understanding of the people interacting with a digital identity system or process, as well as their unique goals and context of use. To provide an effective, efficient, and satisfactory experience, readers of this guidance should take a holistic approach to considering the interactions that each user will engage in throughout the process of enrolling in and authenticating to a service. Throughout the design and development lifecycle of a digital identity system or process, it is important to conduct usability evaluation with representative users performing realistic scenarios and tasks in appropriate context of use.

Digital identity management processes should be designed and implemented so it is easy for users to do the right thing, hard to do the wrong thing, and easy to recover when the wrong thing happens.
