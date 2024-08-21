---
layout: default
title: Digital Identity Risk Management
navOrder: 4
navTitle: DIRM
permalink: /sp800-63/dirm/
anchor: sec5
section: 3
---

# Digital Identity Risk Management {#sec5}

_This section is normative._

This section provides details on the methodology for assessing digital identity risks associated with online services and the residual risks to users of the online service, communities impacted by the service, the service provider organization, and its mission and business partners. It offers guidance on selecting usable, equitable, and privacy-enhancing security and anti-fraud controls that mitigate those risks.  Additionally, it emphasizes the importance of continuously evaluating the performance of the selected controls.

The Digital Identity Risk Management (DIRM) process focuses on the identification and management of risks according to two dimensions: (1) risks to the online service that might be addressed by an identity system; and (2) risks from the identity system to be implemented.

The first dimension of risk informs initial assurance level selections and seeks to identify the risks associated with a compromise of the online service that might be addressed by an identity system. For example:

- Identity proofing: What negative impacts would reasonably be expected if an imposter were to gain access to a service or receive a credential using the identity of a legitimate user (e.g., an attacker successfully impersonates someone)?
- Authentication: What negative impacts would reasonably be expected if a false claimant accessed an account that was not rightfully theirs (e.g., an attacker who compromises or steals an authenticator)?
- Federation: What negative impacts would reasonably be expected if the wrong subject successfully accessed an online service, system, or data (e.g., compromising or replaying an assertion)?

All three types of errors can result in the wrong subject successfully accessing an online service, system, or data.

If it is determined that there are risks associated with a compromise of the online service that could be addressed by an identity system, an initial assurance level is selected and the second dimension of risk is then considered. The second dimension of risk seeks to identify the risks posed by the identity system and informs the tailoring process. Tailoring provides a process to modify an initially assessed assurance level, implement compensating or supplemental controls, or modify selected controls based on ongoing detailed risk assessments.

~~~
\clearpage
~~~
{:latex-literal="true"}

For example, assuming that aspects of the identity system are not sufficiently privacy-enhancing, usable, equitable, or able or necessary to address specific real-world threats:

- Identity proofing: What is the impact of not successfully identity proofing and enrolling a legitimate subject due to barriers faced by the subject throughout the process of identity proofing, including biases? What is the impact of falling victim to a breach of information that was excessively collected and retained to support identity proofing processes? What is the impact if the initial IAL does not completely address specific threats, threat actors, and fraud?  
- Authentication: What is the impact of failing to authenticate the correct subject due to barriers faced by the subject in presenting their authenticator, including biases or usability issues? What is the impact if the initial AAL does not completely address targeted account takeover models or specific authenticator types fail to mitigate anticipated attacks?
- Federation: What is the impact of releasing subscriber attributes to the wrong online service or system?

The outcomes of the DIRM process depend on the role that an entity plays within the digital identity model.

1. For **relying parties**, the intent of this process is to determine the assurance levels and any tailoring required to protect online services and the applications, transactions, and systems that comprise or are impacted by those services. This directly contributes to the selection, development, and procurement of CSP services. Federal RPs **SHALL** implement the DIRM process for all online services.
2. For **credential service providers and identity providers**, the intent of this process is to design service offerings that meet the requirements of the defined assurance levels, continuously guard against compromises to the identity system, and meet the needs of RPs.  Whenever a service offering deviates from normative guidance, those deviations must be clearly communicated to the RPs that utilize the service. All CSPs **SHALL** implement the DIRM process for the services they offer and **SHALL** make a Digital Identity Acceptance Statement (DIAS) for each offering available to all current or potential RPs. CSPs **MAY** base their assessment on anticipated or representative digital identity services they wish to support. In creating this risk assessment, CSPs **SHOULD** seek input from real-world RPs on their user populations and their anticipated context.

This process augments the risk management processes required by the Federal Information Security Modernization Act [[FISMA]](references.md#ref-FISMA). The results of the DIRM impact assessment for the online service may be different from the FISMA impact level for the underlying application or system. Identity process failures may result in different levels of impact for various user groups. For example, the overall assessed FISMA impact level for a payment system may result in a 'FISMA Moderate' impact category due to sensitive financial data processed by the system. However, for individuals who are making guest payments where no persistent account is established, the authentication and proofing impact levels may be lower as associated data may not be retained or made accessible. Agency authorizing officials **SHOULD** require documentation demonstrating adherence to the DIRM process as a part of the Authority to Operate (ATO) for the underlying information system that supports an online service. Agency authorizing officials **SHOULD** require documentation from CSPs demonstrating adherence to the DIRM as part of procurement or ATO processes for integration with CSPs.

There are 5 steps in the DIRM process:

1.  **Define the online service**: As a starting point, the organization documents a description of the online service in terms of its functional scope, the user groups it is intended to serve, the types of online transactions available to each user group, and the underlying data that the online service processes through its interfaces. If the online service is one element of a broader business process, its role is documented, as are the impacts of any data collected and processed by the online service. Additionally, an organization needs to determine the entities that will be impacted by the online service and the broader business process of which it is a part. The outcome is a description of the online service, its users, and the entities that may be impacted by its functionality.
2.	**Conduct initial impact assessment**: In this step, organizations evaluate their user population and assess the impacts of a compromise of the online service that might be addressed by an identity system (i.e., identity proofing, authentication, or federation). Each function of the online service is assessed against a defined set of harms and impact categories. Each user group of the online service is considered separately based on the transactions available to that user group (i.e., the permissions that the group is granted relative to the data and functions of the online service). The outcome of this step is a documented set of impact categories and associated impact levels (i.e., Low, Moderate, or High) for each user group of the online service.
3.	**Select initial assurance levels**: In this step, the impact categories and impact levels are evaluated to determine the initial assurance levels to protect the online service from unauthorized access and fraud. Using the assurance levels, the organization identifies the baseline controls for the IAL, AAL, and FAL for each user group based on the requirements from companion volumes [[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"}, [[SP800-63B]](../_sp800-63b/1_introduction.md#introduction){:latex-href="#ref-SP800-63B"}, and [[SP800-63C]](../_sp800-63c/1_introduction.md#introduction){:latex-href="#ref-SP800-63C"}, respectively. The outcome of this step is an identified initial IAL, AAL, and FAL, as applicable, for each user group.  
4.	**Tailor and document assurance level determinations**: In this step, detailed assessments are conducted or leveraged to determine the potential impact of the initially selected assurance levels and their associated controls on privacy, equity, usability, and resistance to the current threat environment. Tailoring may result in a modification of the initially assessed assurance level, the identification of compensating or supplemental controls, or both. All assessments and final decisions are documented and justified. The outcome is a DIAS (see [Sec. 3.4.4](3_DIRM.md#IDacceptStmt)) with a defined and implementable set of assurance levels and a final set of controls for the online service.
5.	**Continuously evaluate and improve**: In this step, information on the performance of the identity management approach is gathered and evaluated. This evaluation considers a diverse set of factors, including business impacts, effects on fraud rates, and impacts on user communities. This information is crucial in determining if the selected assurance level and controls meet mission, business, security, and &mdash; where applicable &mdash; program integrity needs. It also helps monitor for unintended harms that impact privacy and equitable access. Opportunities for improvement should also be considered by closely monitoring the evolving threat landscape and investigating new technologies and methodologies that can counter those threats or improve usability, equity, or privacy.  The outcomes of this step are performance metrics, documented and transparent processes for evaluation and redress, and ongoing improvements to the identity management approach.

[Fig. 6. High-level diagram of the Digital Identity Risk Management process flow](3_DIRM.md#fig-6){:name="fig-6"}
{:latex-ignore="true"}

![High-level diagram of the Digital Identity Risk Management Process Flow showing the five steps along with major activities and outcomes for each step]({{site.baseurl}}/{{page.collection}}/images/dirm.png 'High-level diagram of the Digital Identity Risk Management Process Flow'){:latex-src="dirm.pdf" latex-fig="6" latex-place="p"}

[Figure 6](3_DIRM.md#fig-6) illustrates the major actions and outcomes for each step of the DIRM process flow. While presented as a "stepwise" approach, there can be many points in the process that require divergence from the sequential order, including the need for iterative cycles between initial task execution and revisiting tasks. For example, the introduction of new regulations or requirements while an assessment is ongoing may require organizations to revisit a step in the process. Additionally, new functionality, changes in data usage, and changes to the threat environment may require an organization to revisit steps in the Digital Identity Risk Management process at any point, including potentially modifying the assurance level and/or the related controls of the online service.

Organizations **SHOULD** adapt and modify this overall approach to meet organizational processes, governance, and enterprise risk management practices. At a minimum, organizations **SHALL** execute and document each step, consult with a representative sample of the online service's user population  to inform the design and performance evaluation of the identity management approach, and complete and document the normative mandates and outcomes of each step regardless of operational approach or enabling tools.

## Define the Online Service {#defServ}
The purpose of defining the online service is to establish a common understanding of the context and circumstances that influence the organization's risk management decisions. The context-rich information ascertained during this step is intended to inform subsequent steps of the DIRM process. The role of the online service is contextualized as part of the broader business environment and associated processes, resulting in a documented description of the online service functionality, user groups and their expectations, data processed and other pertinent details.

RPs **SHALL** develop a description of the online service that includes, at minimum:  

- Organizational mission and business objectives supported by the online service
- Mission and business partner dependencies associated with the online service
- Legal, regulatory, and contractual requirements, including privacy and civil liberties obligations that apply to the online service
- Functionality of the online service and the underlying data that it is expected to process
- User groups that need to have access to the online service as well as the types of online transactions and privileges available to each user group
- User expectations for the online service, including functionality, features, identity verification and authentication options, accessibility and language requirements, and culturally responsive communication alternatives
- The results of any pre-existing DIRA assessments (as an input) and the current state of any pre-existing identity technologies (i.e., proofing, authentication, or federation)
- Across all users served, the estimated availability of forms of identity evidence to support the identity proofing process for services that require identity proofing.

Additionally, an organization needs to determine the entities that will be impacted by the online service and the broader business process of which it is a part. It is imperative to consider the unexpected and undesirable impacts on different entities, populations, or demographic groups that result from an unauthorized user gaining access to the online service due to a failure of the digital identity system. For example, if an attacker obtained unauthorized access to an application that controls a power plant, the actions taken by the bad actor could have devastating environmental impacts on the local populations that live near the facility as well as cause power outages for the localities served by the plant.  

It is important to differentiate between _user groups_ and _impacted entities_ as described in this document. The online service will allow access to a set of users who may be partitioned into a few user groups based on the kind of functionality that is offered to that user group. For example, an income tax filing and review online service may have the following user groups: (i) citizens who need to check on the status of their personal tax returns; (2) tax preparers who file tax returns on behalf of their clients; and (3) system administrators who assign privileges to different groups of users or create new user groups as needed. In contrast, impacted entities include all populations impacted by the online service and its functionality. For example, an online service that allows remote access to control, operate and monitor a water treatment facility may have the following types of impacted entities: (1) populations that drink the water from that water treatment facility; (2) technicians who control and operate the water treatment facility; (3) the organization that owns and operates the facility; and (4) auditors and other officials who provide oversight of the facility and its compliance with applicable regulations.

Accordingly, impact assessments **SHALL** include individuals who use the online application as well as the organization itself. Additionally, organizations **SHOULD** identify other entities (e.g., mission partners, communities, and those identified in [[SP800-30]](references.md#ref-SP800-30)) that need to be specifically included based on mission and business needs. At a minimum, agencies **SHALL** document all impacted when conducting their impact assessments.

**The output of this step is a documented description of the online service including a list of entities that are impacted by the functionality provided by the online service. This information will serve as a basis and establish the context for effectively applying the impact assessments as detailed in the following sections.**

## Conduct Initial Impact Assessment {#intlAssess}

This step of the DIRM process addresses the first dimension of risk (i.e., risks to the identity system) and seeks to identify the risks to the online service that might be addressed by an identity system.

The purpose of the initial impact assessment is to identify the potential adverse impacts of failures in identity proofing, authentication, and federation that are specific to an online service, yielding an initial set of assurance levels. RPs **SHOULD** consider historical data and results from user focus groups when performing this step.
The impact assessment **SHALL** include:

- Identifying a set of impact categories and the potential harms for each impact category,
- Identifying the levels of impact, and
- Assessing the level of impact for each user group.

The level of impact for each user group identified in [Sec. 3.1](3_DIRM.md#defServ) **SHALL** be considered separately based on the transactions available to that user group. Assessing the user groups separately allows organizations maximum flexibility in selecting and implementing an identity approach and assurance levels that are appropriate for each user group.

**The output of this assessment is a defined impact level (i.e., Low, Moderate, or High) for each user group. This serves as the primary input to the initial assurance level selection. The effort focuses on defining and documenting the impact assessment to promote consistent application across an organization.**

### Identify Impact Categories and Potential Harms {#impactCatHarms}

Initial assurance levels for online services **SHALL** be determined by assessing the potential impact of &mdash; at a minimum &mdash; each of the following categories:

- Degradation of mission delivery
- Damage to trust, standing or reputation
- Unauthorized access to information
- Financial loss or financial liability
- Loss of life or danger to human safety, human health, or environmental health

Organizations **SHOULD** include additional impact categories, as appropriate, based on their mission and business objectives. Each impact category **SHALL** be documented and consistently applied when implementing the DIRM process across different online services offered by the organization.

Harms refer to any adverse effects that would be experienced by an entity. They provide a means to effectively understand the impact categories and how they may apply to specific entities impacted by the online service. For each impact category, agencies **SHALL** consider potential harms for each of the impacted entities identified in [Sec. 3.1](3_DIRM.md#defServ).

Examples of harms associated with each category include, but are not limited to:

- Degradation of mission delivery:
  - Harms to individuals may include the inability to access government services or benefits for which they are eligible.
  - Harms to the organization (including the organization offering the online service as well as organizations supported by the online service) may include an inability to perform current mission/business functions in a sufficiently timely manner, with sufficient confidence and/or correctness, or within planned resource constraints or an inability or limited ability to perform mission/business functions in the future.
- Damage to trust, standing or reputation:
  - Harms to individuals may include damage to image or reputation as a result of impersonation.
  - Harms to the organization may include damage to reputation resulting in damage to existing trust relationships, image, or reputation or the inability to forge future, potential trust relationships.
- Unauthorized access to information:
  - Harms to individuals may include breach of PII or other sensitive information, which may result in secondary harms such as financial loss, loss of life, physical or psychological injury, impersonation, identity theft, or persistent inconvenience.
  - Harms to the organization may include exfiltration, deletion, degradation, or exposure of intellectual property or unauthorized disclosure of other information assets such as classified materials or controlled unclassified information (CUI).
- Financial loss or liability:
  - Harms to individuals may include debts incurred or assets lost as a result of fraud or other harm, damage to or loss of credit, actual or potential employment, or sources of income, loss of accessible affordable housing and/or other financial loss.
  - Harms to the organization may include costs related to fraud or other criminal activity, loss of assets, devaluation, or loss of business.
- Loss of life or danger to human safety, human health, or environmental health:
  - Harms to individuals may include death; damage to or loss of physical, mental, or emotional well-being; or impact to environmental health that could result in uninhabitability of the local environment and require some level of intervention to address potential or actual damage.
  - Harms to the organization may include damage to or loss of the organization's workforce or the impact of unsafe conditions that render the organization unable to operate or reduce its capacity to operate.

**The outcome of this activity will be a list of impact categories and harms that will be used to assess impacts on entities identified in [Sec. 3.1](3_DIRM.md#defServ).**

### Identify Potential Impact Levels {#impLvls}

Initial assurance levels for digital transactions are determined by assessing the potential level of impact caused by a compromise of the online service that might be addressed by an identity system for each of the impact categories selected for consideration by the organization (from [Sec. 3.2.1](3_DIRM.md#impactCatHarms)). Impact levels can be assigned using one of the following potential impact values:

- **Low**: Could be expected to have a limited adverse effect
- **Moderate**: Could be expected to have a serious adverse effect
- **High**: Could be expected to have a severe or catastrophic adverse effect

In this step, the impact of access by an unauthorized individual **SHALL** be considered for each user group, each impact category, and each of the impacted entities. Examples of potential impacts in each of the categories are provided below. However, to provide a more objective basis for impact level assignments, organizations **SHOULD** develop thresholds and examples for the impact levels for each impact category. Where this is done, particularly with specifically defined quantifiable values, these thresholds **SHALL** be documented and used consistently in the DIRM assessments across an organization to allow for a common understanding of risks.

- **Degradation of mission delivery:**
  - **Low**:  Expected to result in limited mission capability degradation such that the organization is still able to perform its primary functions but with noticeably reduced effectiveness.
  - **Moderate**: Expected to result in serious mission capability degradation such that the organization is still able to perform its primary functions but with significantly reduced effectiveness.
  - **High**: Expected to result in severe or catastrophic mission capability degradation or loss over a duration such that the organization is unable to perform one or more of its primary functions.
- **Damage to trust, standing or reputation:**
  - **Low**: Expected to result in limited, short-term inconvenience, distress, or embarrassment to any party.
  - **Moderate**: Expected to result in serious short-term or limited long-term inconvenience, distress, or damage to the standing or reputation of any party.
  - **High**: Expected to result in severe or serious long-term inconvenience, distress, or damage to the standing or reputation of any party; ordinarily reserved for situations with particularly severe effects or that potentially affect many individuals.
- **Unauthorized access to information:**
  - **Low**: Expected to have a limited adverse effect on organizational operations, organizational assets, or individuals as defined in [[FIPS199]](references.md#ref-FIPS199).
  - **Moderate**: Expected to have a serious adverse effect on organizational operations, organizational assets, or individuals as defined in [[FIPS199]](references.md#ref-FIPS199).
  - **High**: Expected to have a severe or catastrophic adverse effect on organizational operations, organizational assets, or individuals as defined in [[FIPS199]](references.md#ref-FIPS199).
- **Financial loss or financial liability:**
  - **Low**: Expected to result in limited financial loss or liability to any party.
  - **Moderate**: Expected to result in a serious financial loss or liability to any party.
  - **High**: Expected to result in severe or catastrophic financial loss or liability to any party.
- **Loss of life or danger to human safety, human health, or environmental health:**
  - **Low**: Expected to result in minor injury or an acute health issue that resolves itself and does not require medical attention, including mental health treatment; or an impact to environmental health that requires at most some limited intervention to prevent further or reverse existing damage.
  - **Moderate**: Expected to result in moderate risk of minor injury or limited risk of injury that requires medical attention, including mental health treatment; an impact to environmental health that results in a period of uninhabitability and requires intervention to prevent further or reverse existing damage; or the compounding impacts of multiple low-impact events.
  - **High**: Expected to result in serious injury, trauma, or death; impacts to environmental health that results in long-term or permanent uninhabitability and require significant intervention to prevent further or reverse existing damage, if possible; or the compounding impacts of multiple moderate impact events.

This guidance provides three impact levels. However, agencies **MAY** define more granular impact levels and develop their own methodologies for their initial impact assessment activities.

### Impact Analysis {#impAnalysis}

The impact analysis considers the level of impact (i.e., Low, Moderate or High) of compromises of the online service that might be addressed by the identity system functions (i.e., identity proofing, authentication, and federation). The impact analysis considers the following dimensions:

- User groups [Sec. 3.1](3_DIRM.md#defServ)
- Impacted entities [Sec. 3.1](3_DIRM.md#defServ)
- Impact categories [Sec. 3.2.1](3_DIRM.md#impactCatHarms)
- Impact levels [Sec. 3.2.2](3_DIRM.md#impLvls)

If there is no harm or impact for a given impact category for any entity, the impact level can be marked as None.

For each user group, the impact analysis **SHALL** consider the level of impact for each impact category for each type of impacted entity. Because different sets of transactions are available to each user group, it is important to consider each user group separately for this analysis.

For example, for an online service that allows for the control, operation and monitoring of a water treatment facility, each group of users (e.g., technicians who control and operate the facility, auditors and monitoring officials, system administrators, etc.) is considered separately based on the transactions available to that user group through the online service. In other words, the impact analysis tries to determine if a bad actor obtained unauthorized access to the online service as a member of a user group and performed some nefarious actions and the level of impact (i.e., Low, Moderate or High) on various impacted entities (e.g., citizens who drink the water, the organization that owns the facility, auditors, monitoring officials, etc.) for each of the impact categories being considered.

The impact analysis **SHALL** be performed for each user group that has access to the online service.  For each impact category, the impact level is estimated for each impacted entity as a result of a compromise of the online service caused by failures in the identity management functions.

**The output of this impact analysis is a set of impact levels for each user group that** **SHALL** **be documented in a suitable format for further analysis in accordance with the next subsection below.**

### Determine Combined Impact Level for Each User Group {#combLevel}
The impact assessment level results for each user group generated from the previous step are combined to establish a single impact level for that user group. This single impact level represents the risks to impacted entities that result from a compromise of identity proofing, authentication, and/or federation functions for that user group.

Organizations can apply a variety of methods for this combinatorial analysis to determine the effective impact level for each user group. Some options include:

 - Using a high-water mark approach across the various impact categories and impacted entities to derive the effective impact level
 - Assigning different weights to different impact categories and/or impacted entities and taking an average to derive the effective impact level
 - Some other combinatorial logic that aligns with the organization's mission and priorities

Organizations **SHALL** document the approach they use to combine their impact assessment into an overall impact score for each of their defined user groups and **SHALL** apply it consistently across all its online services. At the conclusion of the combinatorial analysis, organizations **SHALL** document the impact for each user group.

**The outcome of this step is an effective impact level for each user group due to a compromise of the identity management system functions (i.e., identity proofing, authentication, federation).**

## Select Initial Assurance Levels and Baseline Controls
The initial impact analysis of the last step yields an effective impact level (i.e., Low, Moderate, or High) that serves as a primary input to the process of selecting the initial assurance levels for identity proofing, authentication, and federation for each user group.

The purpose of the initial assurance level is to identify baseline digital identity controls (including process and technology elements) for each identity management function, from the requirements and guidelines in the companion volumes [[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"}, [[SP800-63B]](../_sp800-63b/1_introduction.md#introduction){:latex-href="#ref-SP800-63B"}, and [[SP800-63C]](../_sp800-63c/1_introduction.md#introduction){:latex-href="#ref-SP800-63C"}.

The initial set of digital identity controls and processes selected will be assessed and tailored in Step 4 based on potential risks generated by the identity management system.

### Assurance Levels

Depending on the functionality and deployed architecture of the online service, it may require the support of one or more of the identity management functions (i.e., identity proofing, authentication, and federation). The strength of these functions is described in terms of assurance levels. The RP **SHALL** identify the types of assurance levels that apply to their online service from the following:

* **IAL**: The robustness of the identity proofing process to determine the identity of an individual. The IAL is selected to mitigate risks that result from potential identity proofing failures.
* **AAL**: The robustness of the authentication process itself, and the binding between an authenticator and a specific individual's identifier. The AAL is selected to mitigate risks that result from potential authentication failures.
* **FAL**: The robustness of the federation process used to communicate authentication and attribute information to an RP from an IdP. The FAL is selected to mitigate risks that result from potential federation failures.

### Assurance Level Descriptions

A summary of each of the xALs is provided below. While high-level descriptions of the assurance levels are provided in this subsection, readers of this guidance are encouraged to refer to companion volumes [[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"}, [[SP800-63B]](../_sp800-63b/1_introduction.md#introduction){:latex-href="#ref-SP800-63B"}, and [[SP800-63C]](../_sp800-63c/1_introduction.md#introduction){:latex-href="#ref-SP800-63C"} for normative guidelines and requirements for each assurance level.

#### Identity Assurance Level

- **IAL1**:
Supports the real-world existence of the claimed identity. Core attributes are obtained from identity evidence or asserted by the applicant. All core attributes are validated against authoritative or credible sources and steps are taken to link the attributes to the person undergoing the identity proofing process.

- **IAL2**:
IAL2 adds rigor by requiring the collection of additional evidence and a more rigorous process for validating the evidence and verifying the identity.

- **IAL3**:
 IAL3 adds the requirement for a trained CSP representative (i.e., proofing agent) to interact directly with the applicant as part of an on-site attended identity proofing session as well as the collection of at least one biometric.

[Table 1. IAL Summary](3_DIRM.md#table-1){:name="table-1"}
{:latex-ignore="true"}

| IAL | Control Objectives |
|-----|:------------------:|
| IAL1 | Limit highly scalable attacks; provide protection against synthetic identity. Provide protections against attacks using compromised PII.|
| IAL2 | Limit scaled and targeted attacks. Provide protections against basic evidence falsification and evidence theft. Provide protections against basic social engineering. |
| IAL3 | Limit sophisticated attacks. Provide protections against advanced evidence falsification, theft, and repudiation. Provide protection against advanced social engineering attacks. |
{:latex-table="1" latex-caption="IAL Summary" latex-columns="p@0.15\textwidth,p@0.75\textwidth"}

#### Authentication Assurance Level

- **AAL1**:
AAL1 provides a basic level of confidence that the claimant controls an authenticator bound to the subscriber account being authenticated. AAL1 requires only single-factor authentication using a wide range of available authentication technologies. However, it is recommended that online services assessed at AAL1 offer multi-factor authentication options. Successful authentication requires that the claimant prove possession and control of the authenticator.

- **AAL2**:
AAL2 provides high confidence that the claimant controls one or more authenticators bound to the subscriber account being authenticated. Proof of possession and control of two distinct authentication factors is required. A phishing-resistant authentication option must be offered for online services assessed at AAL2.

- **AAL3**:
AAL3 provides very high confidence that the claimant controls one or more authenticators bound to the subscriber account being authenticated. Authentication at AAL3 is based on the proof of possession of a key through the use of a public-key cryptographic protocol. AAL3 authentication requires a hardware-based authenticator with a non-exportable private key and a phishing-resistant authenticator; the same device may fulfill both requirements. In order to authenticate at AAL3, claimants are required to prove possession and control of two distinct authentication factors.

[Table 2. AAL Summary](3_DIRM.md#table-2){:name="table-2"}
{:latex-ignore="true"}

| AAL  | Control Objectives |
|------|:--------------------:|
| AAL1 | Provide minimal protections against attacks. Deter password focused attacks. |
| AAL2 | Support multifactor authentication. Offer phishing-resistant options. |
| AAL3 |Provide phishing resistance and verifier compromise protections. |
{:latex-table="2" latex-caption="AAL Summary" latex-columns="p@0.15\textwidth,p@0.75\textwidth"}


#### Federation Assurance Level

- **FAL1**:
FAL1 allows a subscriber to authenticate to the RP using an assertion from an IdP in a federation protocol. FAL1 provides assurance that the assertion came from a specific IdP and was intended for a specific RP.

- **FAL2**:
FAL2 additionally requires that the trust agreement between the IdP and RP be established prior to the federation transaction, and that the RP have robust protections against injection of assertions from attackers.

- **FAL3**:
FAL3 additionally requires the subscriber to authenticate directly to the RP with a bound authenticator and present the assertion from the IdP. Additionally, the IdP and RP establish their identities and cryptographic key material with each other through a highly trusted process that is often manual.

[Table 3. AAL Summary](3_DIRM.md#table-3){:name="table-3"}
{:latex-ignore="true"}

| FAL | Control Objectives |
|-----|--------------------|
| FAL1 | Provide protections against forged assertions.|
| FAL2 | Provide protections against forged assertions and injection attacks. |
| FAL3 | Provide protection against IdP compromise. |
{:latex-table="3" latex-caption="FAL Summary" latex-columns="p@0.15\textwidth,p@0.75\textwidth"}

### Initial Assurance Level Selection

The overall impact level for each user group is used as the basis for the selection of the initial assurance level and related technical and process controls for the digital identity functions for the organization's online service under assessment. These initial assurance levels and control selections are primarily based on the impacts arising from failures within the digital identity functions that allow an unauthorized entity to gain access to the online service. The initial assurance levels and controls will be further assessed and tailored, as appropriate, in the next step of the DIRM process.

Organizations **SHALL** develop and document a process and governance model for selecting initial assurance levels and controls based on the potential impact of failures in the digital identity approach. This section provides guidance on the major elements to include in that process.

While online service providers must assess and determine the xALs that are appropriate for protecting their applications, the selection of these assurance levels does not mean that the online service provider must implement the controls independently. Based on the identity model that the online service provider chooses to implement, some or all of the assurance levels may be implemented by an external entity such as a third-party CSP or IdP.

#### Selecting Initial IAL {#IAL_CYOA}

Before selecting an initial assurance level, RPs must determine if identity proofing is needed for the users of their online services. Identity proofing is not required if the online service does not require any personal information to execute digital transactions. If personal information is needed, the RP needs to determine if validated attributes are required or if self-asserted attributes are acceptable. The system may also be able to operate without identity proofing if the potential harms from accepting self-asserted attributes are insignificant. In such cases, the identity proofing processes described in [[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"} are not applicable to the system.

~~~
\clearpage
~~~
{:latex-literal="true"}

If the online service does require identity proofing, an initial IAL is selected through a simple mapping process, as follows:

 - Low impact: IAL1
 - Moderate impact: IAL2
 - High impact: IAL3

The organization **SHALL** document whether identity proofing is required for their application and, if it is, **SHALL** select an initial IAL for each user group based on the effective impact level determination from [Sec. 3.2.4](3_DIRM.md#combLevel).

The IAL reflects the level of assurance that an applicant holds the claimed real-life identity. The initial selection assumes that higher potential impacts of failures in the identity proofing process should be mitigated by higher assurance processes.

#### Selecting Initial AAL {#AAL_CYOA}

Not all online services require authentication. Online services that offer access to public information and do not utilize subscriber accounts do not necessarily need to implement authentication mechanisms. However, authentication is needed for online services that do offer access to personal information, protected information, or subscriber accounts. In addition to the impact assessments mandated by these guidelines, when making decisions regarding the application of authentication assurance levels and authentication mechanisms, it is important that organizations consider legal, regulatory, or policy requirements that govern online services. For example,  [EO13681] states "that all organizations making personal data accessible to citizens through digital applications require the use of multiple factors of authentication," which requires a minimum selection of AAL2 for applications meeting those criteria.

If the online service requires an authenticator to be implemented, an initial AAL is selected through a simple mapping process, as follows:

 - Low impact: AAL1
 - Moderate impact: AAL2
 - High impact: AAL3

The organization **SHALL** document whether authentication is needed for their online service and, if it is, **SHALL** select an initial AAL for each user group based on the effective impact level determination from [Sec. 3.2.4](3_DIRM.md#combLevel).

The AAL reflects the level of assurance that the claimant is the same individual to whom the credential or authenticator was issued. The initial selection assumes that higher potential impacts of failures in the authentication process should be mitigated by higher assurance processes.

#### Selecting Initial FAL {#FAL_CYOA}

Identity federation brings many benefits including a convenient user experience that avoids redundant, costly, and often time-consuming identity processes. The benefits of federation through a general-purpose IdP model or a subscriber-controlled wallet model are covered in [Sec. 5 of [SP800-63C]](../_sp800-63c/5_subscriberidp.md#wallet){:latex-href="#ref-SP800-63C"}. However, not all online services will be able to make use of federation, whether for risk-based reasons or due to legal or regulatory requirements. Consistent with [[M-19-17]](references.md#ref-M-19-17), federal agencies that operate online services **SHOULD** implement federation as an option for user access.

If the online service implements identity federation, an initial FAL is selected through a simple mapping process, as follows:

 - Low impact: FAL1
 - Moderate impact: FAL2
 - High impact: FAL3

The organization **SHALL** document whether federation will be used for their online service and, if it is, **SHALL** select an initial FAL for each user group based on the effective impact level determination from [Sec. 3.2.4](3_DIRM.md#combLevel).

The FAL reflects the level of assurance in identity assertions that convey the results of authentication processes and relevant identity information to RP online services. The preliminary selection assumes that higher potential impacts of failures in federated identity architectures should be mitigated by higher assurance processes.

### Identify Baseline Controls {#baseControls}

The selection of the initial assurance levels for each of the applicable identity functions (i.e., IAL, AAL, and FAL) serves as the basis for the selection of the baseline digital identity controls from the guidelines in companion volumes [[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"}, [[SP800-63B]](../_sp800-63b/1_introduction.md#introduction){:latex-href="#ref-SP800-63B"}, and [[SP800-63C]](../_sp800-63c/1_introduction.md#introduction){:latex-href="#ref-SP800-63C"}. As described in [Sec. 3.4](3_DIRM.md#tailor), the baseline controls include technology and process controls that will be assessed against additional potential impacts.

The output of this step **SHALL** include the relevant xALs and controls for each user group, as follows:

 - Initial IAL and related technology and process controls from [[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"}
 - Initial AAL and related technology and process controls from [[SP800-63B]](../_sp800-63b/1_introduction.md#introduction){:latex-href="#ref-SP800-63B"}
 - Initial FAL and related technology and process controls from [[SP800-63C]](../_sp800-63c/1_introduction.md#introduction){:latex-href="#ref-SP800-63C"}

## Tailor and Document Assurance Levels {#tailor}

The second dimension of risk addressed by the Digital Identity Risk Management process focuses on risks from the identity management system. These risks inform the tailoring process and seeks to identify the risks and unintended consequences that result from the initial selection of xALs and the related technical and process controls in [Sec. 3.3.4](3_DIRM.md#baseControls).

Tailoring provides a process to modify an initially assessed assurance level and implement compensating or supplemental controls based on ongoing detailed risk assessments. It provides a pathway for flexibility and enables organizations to achieve risk management objectives that align with their specific context, users, and threat environment. This process focuses on assessing for unintended risks and equity, privacy, and usability impacts, and specific environmental threats. It does not prioritize any specific risk area or outcomes for agencies. Making decisions that balance different types of risks to meet organizational outcomes remains the responsibility of organizations.  Organizations **SHOULD** employ tailoring with the objective of aligning of digital identity controls to their specific context, users, and threat environment.

Within the tailoring step, organizations **SHALL** focus on impacts to mission delivery due to the implementation of identity management controls that result in disproportionate impact on marginalized or historically underserved populations. Organizations **SHALL** consider not only the possibility of certain intended subjects failing to access the online service, but also the burdens, frustrations, and frictions experienced as a result of the identity management controls.

As a part of the tailoring process, organizations **SHALL** review the impact assessment documentation and practice statements[^Practice] from CSPs and IdPs that they use or intend to use. However, organizations **SHALL** also conduct their own analysis to ensure that the organization's specific mission and the communities being served by the online service are given due consideration for tailoring purposes. As a result the organization may require their chosen CSP to strengthen or provide optionality in the implementation of certain controls to address risks and unintended impacts to the organization's mission and the communities served.

[^Practice]: Further information on practice statements and their contents can be found in Section 3.1 of SP800-63A.

To promote interoperability and consistency across organizations, third-party CSPs **SHOULD** implement their (assessed or tailored) xALs consistent with the normative guidance in this document. However, these guidelines provide flexibility to allow organizations to tailor the initial xALs and related controls to meet specific mission needs, address unique risk appetites, and provide secure and accessible online services. In doing so, CSPs **MAY** offer and organizations **MAY** utilize tailored sets of controls that differ from the normative statements in this guidance.

~~~
\clearpage
~~~
{:latex-literal="true"}

Therefore, organizations **SHALL** establish and document an xAL tailoring process. At a minimum this process:

- **SHALL** follow a documented governance approach to allow for decision-making.
- **SHALL** document all decisions in the tailoring process, including the assessed xALs, modified xALs, and supplemental and compensating controls in the Digital Identity Acceptance Statement (see [Sec. 3.4.4](3_DIRM.md#IDacceptStmt)).
- **SHALL** justify and document all risk-based decisions or modifications to the initially assessed xALs in the Digital Identity Acceptance Statement (see [Sec. 3.4.4](3_DIRM.md#IDacceptStmt)).
- **SHOULD** establish a cross-functional capability to support subject matter analysis of xAL selection impacts in the tailoring process (e.g., subject matter experts who can speak about risks and considerations related to privacy, usability, fraud and impersonation impacts, equity, and other germane areas).
- **SHOULD** be a continuous process that incorporates real-world operational data to evaluate the impacts of selected xAL controls.

The tailoring process promotes a structured means of balancing risks and impacts in the furtherance of protecting online services, systems, and data in a manner that enables mission success while supporting equity, privacy, and usability for individuals.

### Assess Privacy, Equity, Usability and Threat Resistance

When selecting and tailoring assurance levels for specific online services, it is critical that insights and inputs to the process extend beyond the initial impact assessment in [Sec. 3.2](3_DIRM.md#intlAssess). When transitioning from the initial assurance level selection in [Sec. 3.3.4](3_DIRM.md#baseControls) to the final xAL selection and implementation, organizations **SHALL** conduct detailed assessments of the controls defined for the initially selected xALs to identify potential impacts in the operational environment.

At a minimum, organizations **SHALL** assess the impacts and potential unintended consequences related to the following areas:

- **Privacy** – Identify unintended consequences to the privacy of individuals that will be subject to the controls at an assessed xAL and of individuals affected by organizational or third-party practices related to the establishment, management, or federation of a digital identity. Privacy assessments **SHOULD** leverage existing Privacy Threshold Assessments (PTAs) and Privacy Impact Assessments (PIAs) as inputs to the privacy assessment process. However, as the goal of the privacy assessment is to identify privacy risks that arise from the initial assurance level selection, additional assessments and evaluations that are specific to the baseline controls for the assurance levels may be required for the underlying information system.
- **Equity** – Determine whether implementation of the initial assurance levels may create, maintain, or exacerbate inequities across communities. Equity assessments **SHALL** evaluate impacts on the communities being served by considering factors such as: proficiency with and access to technology, the availability of end devices with required technical capabilities (e.g., cameras), shared computing or device scenarios, housing status, access to internet, internet speed, family income bracket, credit score, disability status, sex, skin tone, age, native language, English fluency, and education. The intent of this assessment is to mitigate potential impacts on marginalized and historically underserved groups and limit disproportionate impacts from the requirements of the identity management functions.
- **Usability** – Determine whether implementation of the initial assurance levels will result in challenges to the end-user experience. Usability assessments **SHALL** consider usability impacts that result from the identity management controls to ensure that they do not cause undue burdens, frustrations, or frictions for the communities served and that there are pathways to provide accessibility to users of all capabilities.
- **Threat Resistance** – Determine whether the defined assurance level and related controls will address specific threats to the online service based on the operational environment, its threat actors, and known tactics, techniques, and procedures (TTPs). Threat assessments **SHALL** consider specific and known threats, threat actors, and TTPs within the implementation environment for the identity management functions. For example, certain benefits programs may be more subject to familial threats or collusion. Supplemental controls **MAY** need to be implemented to address specific threats within communities served by the online service. Conversely, agencies **MAY** tailor their assessed xAL down or modify their baseline controls if their threat assessment indicates that a reduced threat posture is appropriate based on their environment.

Organizations **SHOULD** leverage consultation and feedback to ensure that the tailoring process addresses the constraints of the entities and communities served.  Organizations **MAY** establish mechanisms through which civil society organizations that work with marginalized groups can provide input on the impacts felt or likely to be felt.

Additionally, organizations **SHOULD** conduct additional business-specific assessments as appropriate to fully represent mission- and domain-specific considerations not captured here. These assessments **SHALL** be extended to any compensating or supplemental controls as defined in [Sec. 3.4.2](3_DIRM.md#IDCompCntls) and [Sec. 3.4.3](3_DIRM.md#IDSupCntrls).

**The outcome of this step is a set of risk assessments for privacy, equity, usability, threat resistance and other dimensions that informs the tailoring of the initial assurance levels and the selection of compensating and supplemental controls.**

### Identify Compensating Controls {#IDCompCntls}

A compensating control is a management, operational, or technical control employed by an organization in lieu of a normative control in the defined xALs. They are intended to address the same risks as the baseline control is intended to address to the greatest degree practicable.

Organizations **MAY** choose to implement a compensating control when they are unable to implement a baseline control or when a risk assessment indicates that a compensating control sufficiently mitigates risk in alignment with organizational risk tolerance. This control **MAY** be a modification to the normative statements as defined in these guidelines, but **MAY** also be applied elsewhere in an application, digital transaction, or service lifecycle. For example:

-	A federal agency could choose to use a federal background investigation and checks, as referenced by _Personal Identity Verification_ [[FIPS201]](references.md#ref-FIPS201), to compensate for the identity evidence validation with authoritative sources requirement under these guidelines.
-	An organization could choose to implement stricter auditing and transactional review processes on a payment application where verification processes using weaker forms of identity evidence were accepted due to the lack of required evidence in the end-user population.

Where compensating controls are implemented, organizations **SHALL** document the compensating control, the rationale for the deviation, comparability of the chosen alternative, and resulting residual risk (if any). CSPs and IDPs who implement compensating controls **SHALL** communicate this information to all potential RPs prior to integration to allow the RP to assess and determine the acceptability of the compensating controls for their use cases.

The process of tailoring allows agencies and service providers to make risk-based decisions regarding how they implement their xALs and related controls. It also provides a mechanism for documenting and communicating decisions through the Digital Identity Acceptance Statement described in
[Sec. 3.4.4](3_DIRM.md#IDacceptStmt).

### Identify Supplemental Controls {#IDSupCntrls}

Supplemental controls are those that may be added to further strengthen the baseline controls specified for the organization's selected assurance levels. Organizations **SHOULD** identify and implement supplemental controls to address specific threats in the operational environment that may not be addressed by the baseline controls. For example:

- To complete the proofing process, an organization could choose to verify an end user against additional pieces of identity evidence, beyond what is required by the assurance level, due to a high prevalence of fraudulent attempts.
- An organization could restrict users to only phishing-resistant authentication at AAL2.
- An organization could choose to implement risk-scoring analytics, coupled with re-proofing mechanisms, to confirm a user's identity when their access attempts exhibit certain risk factors.

Any supplemental controls **SHALL** be assessed for impacts based on the same factors used to tailor the organization's assurance level and **SHALL** be documented.

### Digital Identity Acceptance Statement (DIAS) {#IDacceptStmt}

Organizations **SHALL** develop a Digital Identity Acceptance Statement (DIAS) to document the results of the Digital Identity Risk Management process for each online service managed by the organization. A CSP/IdP **SHALL** make their DIAS and practice statements available to RPs. RPs who intend to use a particular CSP/IdP **SHALL** review the latter's DIAS and practice statements and incorporate relevant information into the organization's DIAS for each online service.

The DIAS **SHALL** include, at a minimum:

-	Initial impact assessment results,
- Initially assessed xALs,
- Tailored xAL and rationale, if the tailored xAL differs from the initially assessed xAL,
- All compensating controls with their comparability or residual risk, and
- All supplemental controls.

Federal agencies **SHOULD** include this information in the information system authorization package described in [[NISTRMF]](references.md#ref-NIST-RMF).

## Continuously Evaluate and Improve {#sec5.5}

Threat actors adapt; user capabilities, expectations, and needs shift; seasonal surges occur; and missions evolve. As such, risk assessments and identity solutions must be continuously improved. In addition to keeping pace with the threat and technology environment, continuous improvement is a critical tool for illustrating programmatic gaps that &mdash; if unaddressed &mdash; may hinder the implementation of identity management systems in a manner that balances risk management objectives. For instance, an organization may determine that a portion of the target population intended to be served by the online service does not have access to affordable high-speed internet services needed to support remote identity proofing. The organization could address this gap with a program that implements local proofing capabilities within the community or by offering appointments with proofing agents who will meet the individual at an address that is more accessible and convenient, such as their local community center, closest post office, an affiliated business partner facility, or the individual's home.

To address the shifting environment in which they operate and more rapidly address service capability gaps, organizations **SHALL** implement a continuous evaluation and improvement program that leverages input from end users who have interacted with the identity management system as well as performance metrics for the online service. This program **SHALL** be documented, including the metrics that are collected, the sources of data required to enable performance evaluation, and the processes in place for taking timely actions based on the continuous improvement process. This program and its effectiveness **SHOULD** be assessed on a defined basis to ensure that outcomes are being achieved and that programs are addressing issues in a timely manner.

Additionally, organizations **SHALL** monitor the evolving threat landscape to stay informed of the latest threats and fraud tactics. Organizations **SHALL** regularly assess the effectiveness of current security measures and fraud detection capabilities against the latest threats and fraud tactics.

### Evaluation Inputs
To fully understand the performance of their identity system, organizations will need to identify critical inputs to their evaluation process. At a minimum these **SHALL** include:

- Integrated CSP, IdP, and authenticator functions as well as validation, verification, and fraud management systems as appropriate.
- Customer feedback mechanisms such as complaint processes, help-desk statistics, and other user feedback (e.g., surveys, interviews, or focus groups)
- Threat analysis, threat reporting, and threat intelligence feeds as available to the organization.
- Fraud trends, fraud investigation results, and fraud metrics as available to the organization.
- The results of ongoing equity assessments, privacy assessments, and usability assessments.

Organizations **SHALL** document their metrics, reporting requirements, and data inputs for any CSP, IdP, or other integrated identity services to ensure that expectations are appropriately communicated to partners and vendors.

### Performance Metrics
The exact metrics available to organizations will vary based on the technologies, architectures, and deployment patterns they follow. Additionally, what is available and what is useful may vary over time. Therefore, these guidelines do not attempt to define a comprehensive set of metrics for all scenarios. [Table 4](3_DIRM.md#table-4) provides a set of recommended metrics that organizations **SHOULD** capture as part of their continuous evaluation program. However, organizations are not constrained by this table and **SHOULD** implement metrics that are not defined here based on their specific systems, technology, and program needs. In [Table 4](3_DIRM.md#table-4), all references to unique users include both legitimate users and imposters.

[Table 4. Performance Metrics](3_DIRM.md#table-4){:name="table-4"}
{:latex-ignore="true"}

| Title | Description | Type |
| ----- | ----------- | ---- |
| Pass Rate (Overall) | Percentage of unique users who successfully proof. | Proofing |
| Pass Rate (Per Proofing Type) |	Percentage of unique users who successfully proof for each offered type (i.e., Remote Unattended, Remote Attended, Onsite Attended, Onsite Unattended). |	Proofing |
| Fail Rate (Overall) |	Percentage of unique users who start the identity proofing process but are unable to successfully complete all the steps.| Proofing |
| Estimated Adjusted Fail Rate | Percentage adjusted to account for digital transactions that are terminated based on suspected fraud. | Proofing |
| Fail Rate (Per Proofing Type) | Percentage of unique users who do not complete proofing due to a process failure for each offered type (i.e., Remote Unattended, Remote Attended, Onsite Attended, Onsite Unattended) | Proofing |
| Abandonment Rate (Overall) | Percentage of unique users who start the identity proofing process, but do not complete it without failing a process. | Proofing |
| Abandonment Rate (Per Proofing Type) | Percentage of unique users who start a specific type of identity proofing process, but do not complete it without failing a process. | Proofing |
| Failure Rates (Per Proofing Process Step) |	Percentage of unique users who are unsuccessful at completing each identity proofing step in a CSP process. | Proofing |
| Completion (Times Per Proofing Type) | Average time that it takes a user to complete each defined proofing type offered as part of an identity service. |	Proofing |
| Authenticator Type Usage | Percentage of subscribers who have an active authenticator by each type available. |	Authentication |
| Authentication Failures	| Percentage of authentication events that fail (not to include attempts that are successful after re-entry of an authenticator output). | Authentication |
| Account Recovery Attempts |	The number of account or authenticator recovery processes initiated by subscribers | Authentication |
| Confirmed Fraud |	Percentage of digital transactions that are confirmed to be fraudulent through investigation or self-reporting. | Fraud |
| Suspected Fraud |	Percentage of digital transactions that are suspected of being fraudulent. |	Fraud |
| Reported Fraud | Percentage of digital transactions reported to be fraudulent by users. | Fraud |
| Fraud (Per Proofing Type | Number of digital transactions that are suspected, confirmed, and reported by each available type of proofing. | Fraud |
| Fraud (Per Authentication Type) |	Number of digital transactions suspected, confirmed, and reported by each available type of authentication |	Fraud |
| Help Desk Calls |	Number of calls received by the CSP or identity service. | Customer Support |
| Help Desk Calls (Per Type) | Number of calls received related to each offered service (e.g., proofing failures, authenticator resets, complaints) | Customer Support |
| Help Desk Resolution Times | Average length of time it takes to resolve a complaint or help desk ticket. | Customer Support |
| Customer Satisfaction Surveys	| The results of customer feedback surveys conducted by CSPs, RP, or both. | User Experience |
| Redress requests | The number of redress requests received related to the identity management system. | User Experience |
| Redress resolution times | The average time it takes to resolve redress requests related to the identity management system. | User Experience |
{:latex-table="4" latex-caption="Performance Metrics" latex-longtable="true" latex-columns="p@0.25\textwidth,p@0.50\textwidth,p@0.28\textwidth"}

The data used to generate continuous evaluation metrics may not always reside with the identity program or the organizational entity responsible for identity management systems. The intent of these metrics is not to establish redundant processes but to integrate with existing data sources whenever possible to collect information that is critical to identity program evaluation. For example, customer service representative (CSR) teams may already have substantial information on customer requests, complaints, or concerns. Identity management systems would be expected to coordinate with these teams to acquire the information needed to discern identity management system-related complaints or issues.

### Measurement in Support of Equity Assessments and Outcomes

A primary purpose of continuous improvement is to improve equity and accessibility outcomes for different user populations. As a result, the metrics collected by organizations **SHOULD** be further evaluated to provide insights into the performance of their identity management systems for their supported communities and demographics. Where possible, these efforts **SHOULD** avoid the collection of additional personal information and instead use informed analysis of proxy data to help provide indicators of potential disparities. This can include comparing and filtering the metrics to identify deviations in performance across different user populations based on other available data such as zip code, geographic region, age, or sex.

Organizations are encouraged to consult the OMB Report _A Vision for Equitable Data:  Recommendations from the Equitable Data Working Group_ [[EO13985-vision]](references.md#ref-EO13985-vision) for guidance on incorporating performance metrics into equity assessments across demographic groups and generating disaggregated statistical estimates to assess equitable performance outcomes.

## Redress {#redress}

An important part of designing services that support a wide range of populations is the inclusion of processes to adjudicate issues and provide redress[^redress] as warranted. Service failures, disputes, and other issues tend to arise as part of normal operations, and their impact can vary broadly, from minor inconveniences to major disruptions or damage. Barriers to access, as well as cybersecurity incidents and data breaches, have real-world consequences for affected individuals. Furthermore, the same issue experienced by one person or community as an inconvenience can have a disproportionately damaging impacts on other individuals and communities, particularly those that are currently experiencing other harms or barriers. Left unchecked, these issues can result in harms that exacerbate existing inequities and allow systemic cycles of exclusion to continue.

[^redress]: Redress generally refers to a remedy that is made after harm occurs.

To enable equitable access to critical services while deterring identity-related fraud and cybersecurity threats, it is essential for organizations to plan for potential issues and to design redress approaches that aim to be fair, transparent, easy for legitimate claimants to navigate, and resistant to exploitation attempts.

Understanding when and how harms might be occurring is a critical first step for organizations to take informed action. Continuous evaluation and improvement programs can play a key role in identifying instances and patterns of potential harm. Moreover, there may be business processes in place outside of those established to support identity management that can be leveraged as part of a comprehensive approach to issue adjudication and redress. Beyond these activities, additional practices can be implemented to ensure that users of identity management systems are able to voice their concerns and have a path to redress. Requirements for these practices include:

- RPs and CSPs **SHALL** enable people to convey grievances and seek redress through an issue handling process that is documented, accessible, trackable, and usable by all people, and whose instructions are easy to find on a public-facing website.
- RPs and CSPs **SHALL** institute a governance model, including documented roles and responsibilities, for implementing this issue handling process.
- The issue handling process **SHALL** be implemented as a dedicated function that includes:
    - Procedures for the impartial review of evidence pertinent to issues;
    - Procedures for requesting and collecting additional evidence that informs the issues; and
    - Procedures to expeditiously resolve issues and determine corrective action.
- RPs and CSPs **SHALL** make human support personnel available to intervene and override issue adjudication outputs generated by algorithmic support mechanisms, such as chatbots.
- RPs and CSPs **SHALL** educate support personnel on issue handling procedures for the digital identity management system, the avenues for redress, and the alternatives available to gain access to services.
- RPs and CSPs **SHALL** implement a process for  personnel and technologies that provides support functions to report major barriers that end users face and commonly expressed grievances. This process **SHALL** enable tracing (e.g., who/what is reported) and tracking (e.g. progress/state of action taken).
- RPs and CSPs **SHALL** incorporate findings derived from the issue handling process into continuous evaluation and improvement activities.

Organizations are encouraged to consider these and other emerging redress practices. Prior to adopting any new redress practice, including supporting technology, organizations **SHOULD** test the practice with target populations to avoid the introduction of unintended consequences, particularly those that may counteract or contradict the goals associated with redress.

## Cybersecurity, Fraud, and Identity Program Integrity

Identity solutions should not operate in a vacuum. Close coordination of identity functions with teams that are responsible for cybersecurity, privacy, threat intelligence, fraud detection, and program integrity can enable a more complete protection of business capabilities, while constantly improving identity solution capabilities. For example, payment fraud data collected by program integrity teams could provide indicators of compromised subscriber accounts and potential weaknesses in identity proofing implementations. Similarly, threat intelligence teams may learn of new TTPs that Could impact identity proofing, authentication, and federation processes. Organizations **SHALL** establish consistent mechanisms for the exchange of information between critical internal security and fraud stakeholders. Organizations **SHOULD** do the same for external stakeholders and identity services that are part of the protection plan for their online services.

When supporting identity service providers (e.g., CSPs) are external to an organization, the exchange of data related to security, fraud, and other RP functions may be complicated by regulation or policy. However, establishing the necessary mechanisms and guidelines to enable effective information-sharing **SHOULD** be considered in contractual and legal mechanisms. All data collected, transmitted, or shared **SHALL** be minimized and subject to a detailed privacy and legal assessment by the generating entity.

This section is meant to address coordination and integration with various organizational functional teams to achieve better outcomes for the identity functions. Ideally, such coordination is performed throughout the risk management process and operations lifecycle. Companion volumes [[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"}, [[SP800-63B]](../_sp800-63b/1_introduction.md#introduction){:latex-href="#ref-SP800-63B"}, and [[SP800-63C]](../_sp800-63c/1_introduction.md#introduction){:latex-href="#ref-SP800-63C"} provide specific fraud mitigation requirements related to each of the identity functions.

## Artificial Intelligence (AI) and Machine Learning (ML) in Identity Systems

Identity solutions have used and will continue to use AI and ML for multiple purposes, such as improving the performance of biometric matching systems, documenting authentication, detecting fraud, and even assisting users (e.g., chatbots). The potential applications of AI/ML are extensive. They also introduce distinct risks and potential issues, including disparate outcomes, biased outputs, and the exacerbation of existing inequities and access issues.

The following requirements apply to all uses of AI and ML regardless of how they are used in identity systems:

- All uses of AI and ML **SHALL** be documented and communicated to organizations that rely on these systems. The use of integrated technologies that leverage AI and ML by CSPs, IdPs, or verifiers **SHALL** be disclosed to all RPs that make access decisions based on information from these systems.
- All organizations that use AI and ML **SHALL** provide information to any entities that use their technology on the methods and techniques used for training their models, a description of the data sets used in training, information on the frequency of model updates, and the results of all testing completed on their algorithms.
- All organizations that use AI and ML systems or rely on services that use these systems **SHALL** implement _NIST AI Risk Management Framework_ ([[NISTAIRMF]](references.md#ref-NISTAIRMF)) to evaluate the risks that may be introduced by the use of AI and ML.
4.	All organizations that use AI and ML **SHALL** consult [[SP1270]](references.md#ref-SP1270), _Towards a Standard for Managing Bias in Artificial Intelligence_.

NIST continues to advance efforts to promote safe and trustworthy AI implementations through a number of venues. In particular, the U.S. AI Safety Institute, housed at NIST [[US-AI-Safety-Inst]](references.md#ref-US-AI-Safety-Inst), is creating a portfolio of safety-focused resources, guidance, and tools that can improve how organizations assess, deploy, and manage their AI systems. Organizations are encouraged to follow the U.S. AI Safety Institute's efforts and make use of their resources.
