---
layout: default
title: Digital Identity Risk Management
navOrder: 5
navTitle: DIRM
permalink: /sp800-63/dirm/
anchor: sec5
section: 5
---

# Digital Identity Risk Management {#sec5}

_This section is normative._

This section provides details on the methodology for assessing digital identity risks for each xAL. This process augments the risk management processes for information and information system risk under NIST guidance for implementing Federal Information Security Modernization Act [[FISMA]](sec8_references.md#ref-FISMA) requirements.

There are 4 steps to the digital identity risk management process:

1.	**Conduct Initial Impact Assessment**: In this step, organizations evaluate their user population and assess the impact of a failure of each function in the identity system (i.e., proofing, authentication, and federation) for their protected application or service against a defined set of impact categories. The outcome of this step is a documented set of impact categories and associated impact levels.
2.	**Select Initial Assurance Levels**: In this step, the impact categories and impact levels are evaluated to determine the appropriate assurance levels to protect the application. The outcome of this step is an identified initial level for each applicable xAL.  
3.	**Tailor and Document Assurance Level Determinations**: In this step, detailed privacy, equity, usability, and threat assessments are conducted to determine the potential impact of the initially selected assurance level on the specific user population and threat environment of the application. The initial assurance level is tailored, compensating or supplemental controls are identified, and all decisions are documented. The outcome is a Digital Identity Acceptance Statement (see [Sec. 5.3.4](sec5_DIRM.md#IDacceptStmt)) with a defined implementable assurance level.
4.	**Continuously Evaluate & Improve**: In this step, information is collected on performance of the identity system across a diverse set of factors based on organization needs and evolving threat vectors. This information is used to determine if the selected assurance level and controls are meeting mission, business, and security needs and to monitor for unintended harms that may have emerged. The outcomes of this step are performance metrics, documented and transparent processes for evaluation and redress, and ongoing improvements to the identity system as needed.

While presented as a “stepwise” approach, there can be many points in the process that require divergence from the sequential order, including the need for iterative cycles between initial task execution and revisiting tasks. For example, the introduction of new regulations or requirements while an assessment is ongoing may require organizations to revisit a step in the process. Additionally new functionality, changes in data usage, and changes to the threat environment may at any point require an organization to revisit steps in the digital identity risk management process.

Organizations **SHOULD** adapt and modify this overall approach to meet organizational processes, governance, and integration with enterprise risk management practices. At a minimum, organizations **SHALL** ensure that each step is executed and the normative mandates and outcomes of each step are completed and documented regardless of operational approach and enabling tools.


## Conduct Initial Impact Assessment {#intlAssess}

The purpose of the initial impact analysis is to identify the potential adverse impacts of failures in identity proofing, authentication, and federation specific to an RP application or service, yielding an initial set of assurance levels. Assessing these areas separately allows organizations maximum flexibility in developing or acquiring a digital identity service that best enables them to successfully deliver on mission objectives.

The impact assessment includes:

- Identifying impacted entities,
- Identifying a set of impact categories for which harms will be assessed,
- Identifying potential harms for each of the impact categories,
- Identifying the levels of impact those potential harms would inflict should failures occur, and
- Assessing the impact of each type of failure (proofing, authentication, and federation) and the resulting impact level to all affected entities.

The output of this assessment is a defined impact level &mdash; High, Moderate, or Low &mdash; for each possible type of failure. This serves as the primary input to the initial assurance level selection.

### Identify Impacted Entities {#impctEnt}

When assessing impacts, an organization needs to determine the entities that will be impacted by the application or transaction under consideration. As mentioned earlier in this guideline, it is imperative to consider the impact on different entities resulting from a failure of the digital identity system. Of particular importance is ensuring that the potential impacts to individuals are considered alongside those of the enterprise.

Accordingly, impact assessments **SHALL** include individuals using the system or application in addition to the organization itself. Additionally, organizations **SHOULD** identify other entities, such as mission partners, communities, and those identified in [[SP800-30]](sec8_references.md#ref-SP800-30), that need to be specifically included based on mission and business needs. At a minimum, agencies **SHALL** document all entities to which impacts will be assessed when conducting their impact analysis.

The outcome of this activity is a list of entities subject to the application or transaction under consideration for whom impacts will be assessed.

### Identify Impact Categories and Potential Harms {#impactCatHarms}

Initial assurance levels for digital transactions **SHALL** be determined by assessing the potential impact of, at a minimum, each of the following categories:

  - Damage to mission delivery
  - Damage to trust or reputation
  - Loss of sensitive information
  - Damage to or loss of economic stability
  - Loss of life or damage to safety, health, or  environmental stability
  - Noncompliance with laws, regulations, and/or contractual obligations

Organizations **SHOULD** include additional impact categories as appropriate based on their mission. Each impact category **SHALL** be documented and consistently applied across different applications assessed by the organization.

Harms are any adverse effects that would be experienced by an entity. They provide a means to more effectively understand the impact categories and how they may apply to specific entities associated with that application. Agencies **SHOULD** consider specific harms for each of the defined impact categories to better inform their impact analysis. Identification of harms for each category **SHALL** be done for each of the entities identified during "entity identification" process.

Examples of harms associated with each category include, but are not limited to:

Damage to mission delivery:

  - Harms to individuals may include the inability to access government services or benefits for which they are eligible.
  - Harms to the organization may include an inability to perform current mission/business functions in a sufficiently timely manner, with sufficient confidence and/or correctness, within planned resource constraints, or an inability, or limited ability, to perform mission/business functions in the future.

Damage to trust or reputation:

  - Harms to individuals may include impersonation or damage to image or reputation.
  - Harms to the organization may include damage to trust relationships, image, or reputation including future, potential trust relationships.

Loss of sensitive information:

  - Harms to individuals includes loss of PII or other sensitive information, which may result in secondary harms such as loss of economic stability, loss of life, physical or psychological injury, impersonation, identity theft, or persistent inconvenience.
  - Harms to the organization may include loss or degradation of intellectual property or other information assets such as classified materials or controlled unclassified information (CUI).

Damage to or loss of economic stability:

  - Harms to individuals may include debts incurred or assets lost as a result of fraud or other harm, damage to or loss of credit, actual or potential employment, or sources of income, and/or other financial loss.
  - Harms to the organization may include costs incurred related to fraud or other criminal activity, loss of assets, devaluation, or loss of business.

Loss of life or damage to safety, health, or environmental stability:

  - Harms to individuals may include death, damage to or loss of physical, mental, or emotional well-being, damage to the environment, or loss of accessible, affordable housing.
  - Harms to the organization may include damage to or loss of the organization's workforce or the impact of unsafe conditions rendering the organization unable to operate or operating at reduced capacity.

Noncompliance with laws, regulations, and/or contractual obligations:

  - Harms to individuals may include damage to or loss of economic stability, safety, privacy, civil liberties, equity, and/or usability due to violations of local, state, and federal laws, regulations, and/or contractual obligations.
  - Harms to the organization may include financial costs, sanctions, liability, etc, due to noncompliance with applicable laws, regulations, contractual requirements, or other requirements in other binding agreements.

The outcome of this activity will be a list of impact categories and harms which will be used to assess impacts to identified entities.

### Identify Potential Impact Levels {#impLvls}

Initial assurance levels for digital transactions are determined by assessing the potential impact a failure would have on each of the categories from [Sec. 5.1.2](sec5_DIRM.md#impactCatHarms) using one of the following potential impact values:

1. Low potential impact: could be expected to have a limited adverse effect
2. Moderate potential impact: could be expected to have a serious adverse effect
3. High potential impact: could be expected to have a severe or catastrophic adverse effect

> Note: If a failure in the identity system causes no measurable consequences for a category, there is no impact.

Each assurance level, IAL, AAL, and FAL (if accepting or asserting a federated identity) **SHALL** be evaluated separately. Ideally, any evaluation will include different viewpoints such as harm to individuals, the organization, other organizations, and the nation as applicable to successful delivery of the organization's mission. Examples of potential impacts in each of the categories include:

**Damage to mission delivery:**

- **Low**: at worst, slight outcome disparities exist between individuals that participate in federally funded programs and those that are eligible but unable to participate, or a limited adverse effect on organizational operations or assets, or public interests. Examples of limited adverse effects are: mission capability degradation to the extent and duration that the organization is able to perform its primary functions with noticeably reduced effectiveness, or minor damage to organizational assets or public interests.
- **Moderate**: at worst, outcome disparities are evident between individuals that participate in federally funded programs and those that are eligible but unable to participate, or a serious adverse effect on organizational operations or assets, or public interests. Examples of serious adverse effects are: significant mission capability degradation to the extent and duration that the organization is able to perform its primary functions with significantly reduced effectiveness; or significant damage to organizational assets or public interests.
- **High**: outcome disparities endure across communities, indicating a systemic pattern of exclusion, avoidance, or other barriers to participation in federally funded programs, or a severe or catastrophic adverse effect on organizational operations or assets, or public interests. Examples of severe or catastrophic effects are: severe mission capability degradation or loss to the extent and duration that the organization is unable to perform one or more of its primary functions; or major damage to organizational assets or public interests.

**Damage to trust and reputation:**

- **Low**: at worst, limited, short-term inconvenience, distress, or embarrassment to any party.
- **Moderate**: at worst, serious short-term or limited long-term inconvenience, distress, or damage to the standing or reputation of any party.
- **High**: severe or serious long-term inconvenience, distress, or damage to the standing or reputation of any party. This is ordinarily reserved for situations with particularly severe effects or which potentially affect many individuals.

**Loss of sensitive information:**

- **Low**: at worst, a limited release of personal, U.S. government sensitive, or commercially sensitive information to unauthorized parties resulting in a loss of confidentiality with a low impact as defined in [[FIPS199]](sec8_references.md#ref-FIPS199).
- **Moderate**: at worst, a release of personal, U.S. government sensitive, or commercially sensitive information to unauthorized parties resulting in loss of confidentiality with a moderate impact as defined in [[FIPS199]](sec8_references.md#ref-FIPS199).
- **High**: a release of personal, U.S. government sensitive, or commercially sensitive information to unauthorized parties resulting in loss of confidentiality with a high impact as defined in [[FIPS199]](sec8_references.md#ref-FIPS199).

**Damage to or loss of economic stability:**

- **Low**: at worst, an insignificant or inconsequential financial loss to any party.
- **Moderate**: at worst, a serious financial loss to any party.
- **High**: severe or catastrophic financial loss to any party.

**Loss of life or damage to safety, health, or environmental stability:**

- **Low**: at worst, minor injury or acute health issue that resolves itself and does not require medical, including mental health, treatment; limited risk of environmental impact in locality where program operations take place.
- **Moderate**: at worst, moderate risk of minor injury or limited risk of injury requiring medical, including mental health, treatment; or the compounding impact of multiple low impact events; moderate risk of environmental impact in locality where program operations take place.
- **High**: a risk of serious injury, trauma, or death; or the compounding impact of multiple moderate impact events; high risk of environmental impact in locality where program operations take place.

**Noncompliance with laws, regulations, and/or contractual obligations:**

- **Low**: at worst, a risk of civil or criminal violations of a nature that would not ordinarily be subject to enforcement efforts, or at worst, an insignificant or inconsequential organization liability.
- **Moderate**: at worst, a risk of civil or criminal violations that may be subject to enforcement efforts, or a serious organization liability.
- **High**: a risk of civil or criminal violations that are of special importance to enforcement programs, or severe or catastrophic organization liability.

### Impact Analysis {#impAnalysis}

The impact analysis helps determine the extent to which risk must be mitigated by the identity proofing, authentication, and federation processes. These determinations drive the relevant choices of applicable technologies and mitigation strategies, rather than the desire for any given technology driving risk determinations.

To determine the appropriate level of assurance of the user's asserted identity, organizations **SHALL** assess the potential risks and identify measures to minimize their impact. Organizations **SHALL** assess the risk of identity proofing, authentication, and federation failures separately to determine the required assurance level for each transaction. This process **SHALL** include consideration of potentially varying impacts of harms to different entities impacted by the digital identity system, as described in [Sec. 5.1.1](sec5_DIRM.md#impctEnt). Business processes, policies, and technologies may help reduce risk. Entities **SHOULD** consider the impact of specific modes of failures related to identity proofing, authentication, and federation this includes, but may not be limited to:  

**Identity Proofing:**

- The impact of providing a service to the wrong subject (e.g., an attacker successfully proofs as someone else).
- The impact of not providing service to an eligible subject due to barriers, including biases, faced by the subject throughout the process of identity proofing.
- The impact of excessive information collection and retention to support identity proofing processes.

**Authentication:**

- The impact of authenticating the wrong subject (e.g., an attacker who compromises or steals an authenticator).
- The impact of failing to authenticate the correct subject due to barriers, including biases, faced by the subject in presenting their authenticator.  

**Federation:**

- The impact of the wrong subject successfully accessing an application, system, or data (e.g., compromising or replaying an assertion).
- The impact of releasing subscriber attributes to the wrong application or system.

Using a worksheet similar to [Table 1](sec5_DIRM.md#table-1) can assist organizations with compiling the information gathered in order to complete the analysis. This kind of analysis would be done for each type of potential failure for identity proofing, authentication, and federation to determine the overall risks to entities interacting with the digital identity system.

[Table 1 Impact Categories](sec5_DIRM.md#table-1){:name="table-1"}
{:latex-ignore="true"}

| Impact Categories | Harm to Individuals | Harm to the Organization | (Other harm categories) | Combined Impact Level |
| :--- | :----: | :----: | :----: | :----: |
| Damage to mission delivery | L / M / H | L / M / H | L / M / H |   |
| Damage to trust or reputation | L / M / H | L / M / H | L / M / H |   |
| Loss of sensitive information | L / M / H | L / M / H | L / M / H |   |
| Damage to or loss of economic stability | L / M / H | L / M / H | L / M / H |   |
| Loss of life or damage to safety, health, or environmental stability | L / M / H | L / M / H | L / M / H |   |
| Noncompliance with laws, regulations, and/or contractual obligations | L / M / H | L / M / H | L / M / H |   |
{:latex-table="1" latex-caption="Impact Categories" latex-columns="p@0.20\textwidth,p@0.15\textwidth,p@0.15\textwidth,p@0.15\textwidth,p@0.15\textwidth"}

The output of this step is a defined impact level for failures of identity proofing, authentication, and federation which serve as the primary input to the initial assurance level selection.

## Select Initial Assurance Levels
The impact analysis serves as a primary input to the process of selecting initial assurance levels for identity proofing, authentication and federation. The assurance levels may differ across these areas based on the analysis of the potential impact of failures in each area. The purpose of these initial assurance levels is to identify baseline digital identity controls and processes, reflected in the requirements and guidelines in the companion volumes of [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP-800-63A"}, [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP-800-63B"}, and [[SP800-63C]](../_sp800-63c/sec1_purpose.md#purpose){:latex-href="#ref-SP-800-63C"}, which will be assessed and tailored based on mission need, cybersecurity risk, and other potential impacts to the organization and users of the digital identity systems.

### Assurance Levels

An organization RP **SHALL** select, based on cybersecurity risk and mission needs, the following individual initial assurance levels:

* **IAL**: The robustness of the identity proofing process to confidently determine the identity of an individual. IAL is selected to mitigate potential identity proofing failures.
* **AAL**: The robustness of the authentication process itself, and the binding between an authenticator and a specific individual's identifier. AAL is selected to mitigate potential authentication failures.
* **FAL**: The robustness of the federation process used to communicate authentication and attribute information (if applicable) to an RP from an IdP. FAL is optional as not all digital systems will leverage federated identity architectures. FAL is selected to mitigate potential federation failures.

### xAL Descriptions

A summary of each of the identity, authenticator, and federation assurance levels is provided below.

When described generically or bundled, these guidelines will refer to IAL, AAL, and FAL as **_xAL_**.

#### Identity Assurance Level

**IAL1**:
IAL1 requires validation of identifying attributes against authoritative or credible sources and use of basic processes to verify the claimed identity of the applicant.

**IAL2**:
IAL2 requires identifying attributes to be supported by strong evidence and validated against authoritative or credible sources and use of processes to verify the claimed identity of the applicant.

**IAL3**:
IAL3 requires identifying attributes to be verified by an authorized CSP representative through examination of physical documentation using an interactive process with a CSP representative.

#### Authentication Assurance Level

**AAL1**:
AAL1 provides some assurance that the claimant controls an authenticator registered to the subscriber. AAL1 requires single-factor authentication using a wide range of available authentication technologies. Successful authentication requires that the claimant prove possession and control of the authenticator through a secure authentication protocol.

**AAL2**:
AAL2 provides high confidence that the claimant controls authenticator registered to the subscriber. Proof of possession and control of two different authentication factors is required through a secure authentication protocol. Approved cryptographic techniques are required at AAL2 and above.

**AAL3**:
AAL3 provides very high confidence that the claimant controls authenticator registered to the subscriber. Authentication at AAL3 is based on proof of possession of a key through a cryptographic authentication protocol capable of resisting phishing attacks.

#### Federation Assurance Level

**FAL1**:
FAL1 allows for the subscriber to log into the RP using an assertion from the IdP that can be verified by the RP as coming from the IdP and targeted for a specific RP. The assertion is protected from modification or construction by an attacker. The trust agreement and registration between the IdP and RP can happen dynamically.

**FAL2**:
FAL2 adds the requirement that the assertion be robust against injection at the RP. One means of this is to have the assertion presented directly to the RP from the IdP instead of passing through an intermediary like a browser. The trust agreement between the IdP and RP cannot happen dynamically, but dynamic registration of the specific IdP and RP can occur at runtime.

**FAL3**:
FAL3 adds the requirement that the subscriber authenticate directly to the RP using a bound authenticator along with presenting the authentication assertion. The presence of this additional authenticator provides a very high assurance to the RP that the party accessing the RP is the party identified in the assertion. The trust agreement and registration cannot be dynamic.

### Initial Assurance Level Selection

The identification and assessment of the potential impacts of failures in identity proofing, authentication, and federation processes informs the organization's digital identity risk management process and the initial selection of assurance levels for those areas. These initial selections are primarily based on cybersecurity risk, but will be tailored, based on mission needs and other potential impacts to the organization, users, and mission partners.

Organizations **SHALL** develop and document a process and governance model for selecting initial assurance levels based on the potential impact of digital identity failures. This section provides guidance on the major elements to include in that process.

#### Selecting Initial IAL {#IAL_CYOA}
The IAL reflects the level of assurance that an applicant holds the claimed real-life identity.  Organizations **SHALL** use a risk-based approach to select the most appropriate identity proofing requirements for their RP application. The impact analysis described in [Sec. 5.3.1](sec5_DIRM.md#impLvls) informs the selection of the initial IAL selection.  This initial selection **SHALL** be tailored, as described in [Sec. 5.3](sec5_DIRM.md#tailor), based on mission needs, risk tolerance, and potential impacts to privacy, equity, and usability, before making a final IAL determination.

The IAL selection does not mean the RP application owner will need to perform the proofing themselves since identity proofing is the function of the CSP.

Not all RP applications will require identity proofing. If the RP application does not require any personal information to execute any digital transactions, the system can operate without identity proofing users of the RP application. If personal information is needed, the RP needs to determine if validated and verified attributes are required or if self-asserted attributes are acceptable. If there are insignificant potential harms from accepting self-asserted attributes, the system may also be able to operate without identity proofing users. In such cases, the identity proofing processes described in [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"} are not applicable to the system.

If an organization determines that identity proofing is necessary, the initial IAL **SHALL** be assessed based on the potential impacts of identity proofing failures.  As described in [Sec. 5.1](sec5_DIRM.md#intlAssess), potential impacts **SHALL** be considered from the perspective of the organization, individuals, other organizations, and the nation, for harms incurred through the use or operation of the RP application. While the organization may not be negatively impacted, the user could be significantly harmed, as could individuals whose privacy or other rights have been violated by the business practices of a service provider. Organizations **SHOULD** consider the worst-case when identifying the overall impact level of the RP application, but may use risk management processes to tailor their initial selection when there are differing impacts.

When assessing the overall impact level of the RP application, the organization **SHOULD** consider impacts to mission delivery separately from other impact categories. Potential failures in the identity proofing process that could lead to harms in mission delivery should be assessed by the organization to determine if the associated impacts would be mitigated or exacerbated by the implementation of more rigorous identity proofing processes. As such, the organization **MAY** exclude the mission delivery category when initially identifying the overall impact level of the RP application, as these impacts will need to be considered in the tailoring process.

The overall impact level assessed by the organization leads to a preliminary selection of the IAL from which further tailoring may be done:

- Low impact: IAL1
- Moderate impact: IAL2
- High impact: IAL3

The preliminary selection assumes that higher potential impacts of failures in the identity proofing process should be mitigated by higher assurance processes. While this is often the case, organizations should consider the specific failures, impact categories, and impacted entities identified as part of the impact analysis to determine if additional tailoring is warranted. For example, if a failure to enroll a legitimate applicant could lead to excessive harm, organizations should assess whether lower-assurance identity proofing processes would be appropriate.

The result of this process, including any additional tailoring, is the initial assessment of the IAL, which will be assessed against additional potential impacts as described in [Sec. 5.3](sec5_DIRM.md#tailor).

#### Selecting Initial AAL {#AAL_CYOA}
The AAL reflects the level of assurance from the authentication process that the claimant is who they claim to be. Organizations **SHALL** use a risk-based approach to select the most appropriate authentication requirements for their RP application. The impact analysis described in [Sec. 5.1.3](sec5_DIRM.md#impLvls) informs the selection of the initial AAL selection.  This initial selection **SHALL** be tailored, as described in [Sec. 5.3](sec5_DIRM.md#tailor), based on mission needs, risk tolerance, and potential impacts to privacy, equity, and usability, before making a final AAL determination.

The AAL selection does not mean the RP application owner will need to issue authenticators themselves.

The initial AAL **SHALL** be assessed based on the potential impacts of authentication failures. As described in [Sec. 5.1](sec5_DIRM.md#intlAssess), potential impacts **SHALL** be considered from the perspective of the organization, individuals, other organizations, and the nation, for harms incurred through the use or operation of the RP application, as the level of harm from a failure could vary significantly across these entities. Organizations **SHOULD** consider the worst-case when identifying the overall impact level of the RP application, but may use risk management processes to tailor their initial selection when there are differing impacts.

When assessing the overall impact level of the RP application, the organization **SHOULD** consider impacts to mission delivery separately from other impact categories. Potential failures in the authentication process that could lead to harms in mission delivery should be assessed by the organization to determine if the associated impacts would be mitigated or exacerbated by the implementation of more rigorous authentication controls. As such, the organization **MAY** exclude the mission delivery category when initially identifying the overall impact level of the RP application, as these impacts will need to be considered in the tailoring process.

The overall impact level assessed by the organization leads to a preliminary selection of the AAL from which further tailoring may be done:

- Low impact: AAL1
- Moderate impact: AAL2
- High impact: AAL3

The preliminary selection assumes that higher potential impacts of failures in the authentication process should be mitigated by higher assurance processes. While this is often the case, organizations should consider the specific failures, impact categories, and impacted entities identified as part of the impact analysis to determine if additional tailoring is warranted. Further, organizations should consider legal, regulatory, or policy requirements that govern digital services. For example, the terms of [[EO13681]](sec8_references.md#ref-EO13681) requiring "that all organizations making personal data accessible to citizens through digital applications require the use of multiple factors of authentication," which would drive the selection of AAL2 or AAL3.

The result of this process, including any additional tailoring, is the initial assessment of the AAL, which will be as assessed against additional potential impacts as described in [Sec. 5.3](sec5_DIRM.md#tailor).

#### Selecting Initial FAL {#FAL_CYOA}
The FAL reflects the level of assurance in identity assertions that convey the results of authentication processes and relevant identity information to RP systems. Organizations **SHALL** use a risk-based approach to select the most appropriate federation requirements for their RP application. The impact analysis described in [Sec. 5.3.1](sec5_DIRM.md#impLvls) informs the selection of the initial FAL selection.  This initial selection **SHALL** be tailored, as described in [Sec. 5.3](sec5_DIRM.md#tailor), based on mission needs, risk tolerance, and potential impacts to privacy, equity, and usability, before making a final FAL determination.

The initial FAL **SHALL** be assessed based on the potential impacts of failures in the presentation or acceptance of assertions in federated identity architectures. Examples of compromise include use of assertion replay to impersonate a valid user or leakage of assertion information through the browser. As described in [Sec. 5.1](sec5_DIRM.md#intlAssess), potential impacts **SHALL** be considered from the perspective of the organization, individuals, other organizations, and the nation, for harms incurred through the use or operation of the RP application, as the level of harm from a failure could vary significantly across these entities. Organizations **SHOULD** consider the worst-case when identifying the overall impact level of the RP application, but may use risk management processes to tailor their initial selection when there are differing impacts.

When assessing the overall impact level of the RP application, the organization **SHOULD** consider impacts to mission delivery separately from other impact categories. Potential failures in federated architectures that could lead to harms in mission delivery **MAY** be assessed by the organization to determine if the associated impacts would be mitigated or exacerbated by the implementation of more rigorous controls by identity providers. As such, the organization may exclude the mission delivery impact category when initially identifying the overall impact level of the RP application, as these impacts will need to be considered in the tailoring process.

The overall impact level assessed by the organization leads to a preliminary selection of the FAL from which further tailoring may be done:

- Low impact: FAL1
- Moderate impact: FAL2
- High impact: FAL3

The preliminary selection assumes that higher potential impacts of failures in federated identity architectures should be mitigated by higher assurance processes. While this is often the case, organizations should consider the specific failures, impact categories, and impacted entities identified as part of the impact analysis to determine if additional tailoring is warranted.

The result of this process, including any additional tailoring, is the initial assessment of the FAL, which will be as assessed against additional potential impacts as described in [Sec. 5.3](sec5_DIRM.md#tailor).

## Tailor and Document Assurance Levels {#tailor}

Tailoring provides a process to modify an initially assessed assurance level or implement compensating controls based on ongoing detailed impact and risk assessments. Organizations **SHOULD** implement the assessed assurance level as defined in these guidelines. However, these guidelines provide flexibility to allow for organizations to meet specific mission needs and address unique risk appetites and considerations. Therefore, organizations **SHALL** establish and document an xAL tailoring process. At a minimum this process:

1. **SHALL** include a structured governance approach to allow for decision-making and conflict resolution.
2. **SHALL** document all decisions in the tailoring process, including the assessed xALs, modified xALs, and compensating controls in the Digital Identity Acceptance Statement (see [Sec. 5.3.4](sec5_DIRM.md#IDacceptStmt)).
3. **SHALL** justify and document all risk-based decisions or modifications to the initially assessed xALs in the Digital Identity Acceptance Statement (see [Sec. 5.3.4](sec5_DIRM.md#IDacceptStmt)).
4. **SHOULD** establish a cross-functional capability to support subject matter analysis of xAL selection impacts in the tailoring process.
5. **SHOULD** be a continuous process that incorporates real world operational data to evaluate the impacts of selected xAL controls.

The tailoring process promotes a structured means to balance risks and impacts in the furtherance of protecting systems, data, and services in a manner that enables mission success while supporting equity, privacy, and usability for individuals.

### Assess Privacy, Equity, Usability and Threats

When selecting and tailoring assurance levels for specific applications, it is critical that insights and inputs to the process extend beyond an initial, static impact assessment. When transitioning from an initial assurance level to the final xAL selection and implementation, organizations **SHALL** conduct detailed assessments of the controls defined at the assurance level to determine potential impacts in their operational environment. At a minimum, organizations **SHALL** assess impacts related to the following areas:

- **Privacy** – to determine unintended consequences to the privacy of individuals that will be subject to the controls at an assessed xAL and of individuals affected by organizational or third-party practices related to the establishment, management, or federation of a digital identity.
- **Equity** – to determine whether implementation of controls may create or maintain inequities across demographics or user groups.
- **Usability** – to determine whether implementation of the selected controls will result in challenges to end-user experience.
- **Threat** – to determine whether the defined assurance level will address specific threats based on environment, threat actors, and known tactics, techniques, and procedures (TTPs).

Additionally, organizations **SHOULD** conduct additional business specific assessments as appropriate to fully represent mission and domain specific considerations not captured here. These assessments **SHALL** be extended to any compensating or supplemental controls as defined in [Sec. 5.3.2](sec5_DIRM.md#IDCompCntls) and [Sec. 5.3.3](sec5_DIRM.md#IDSupCntrls).


### Identify Compensating Controls {#IDCompCntls}

A compensating control is a management, operational, or technical control employed by an organization in lieu of a recommended control in the defined xALs. They are intended, to the greatest degree possible, to address the same risks as the baseline control is intended to address.

Organizations **SHOULD** implement their identity services per the requirements in these guidelines for their tailored assurance level. However, where organizations are unable to implement a specific control associated with their baseline or tailored assurance level, they **MAY** select to implement a compensating control. This control **MAY** be a modification to a digital identity process as defined in these guidelines, but **MAY** also be applied elsewhere in an application, transaction, or service lifecycle. For example:

-	A federal agency could choose to use a federal background investigation and checks, as referenced by  _Personal Identity Verification_ [[FIPS201]](sec8_references.md#ref-FIPS201), to compensate for the identity evidence validation with authoritative sources requirement under these guidelines.
-	An organization could choose to implement stricter auditing and transactional review processes on a payment application where verification processes using weaker forms of identity evidence were accepted due to availability of evidence in the end-user population.

Where compensating controls are implemented, organizations **SHALL** demonstrate comparability of a chosen alternative or document residual risk incurred by deviating from normative requirements. Organizations **SHALL** implement procedures to document both the justification for any departure from normative requirements and detail the compensating controls employed. The inclusion of compensating controls does not imply that an organization must tailor to a lower xAL. The process of tailoring allows for agencies and service providers to make risk-based decisions in how they implement their xALs and provides a mechanism for documenting and communicating decisions through the Digital Identity Acceptance Statement described in [Sec. 5.3.4](sec5_DIRM.md#IDSupCntrls).

### Identify Supplemental Controls {#IDSupCntrls}

Supplemental controls are those that may be added, in addition to those specified in the organizations tailored assurance level, in order to address specific threats or attacks. Organizations **SHOULD** identify and implement supplemental controls where they identify threats that may not be addressed in baseline controls. For example:

- An organization could choose to verify an end user against additional pieces of identity evidence, beyond what is required by the assurance level, due to a high prevalence of fraudulent attempts to complete the proofing process.
- An organization could choose to implement risk-scoring analytics, coupled with re-proofing mechanisms, to confirm a user’s identity when their access attempts exhibit certain risk factors.

Where organizations implement supplemental controls, these **SHALL** be assessed for impacts based on the same factors used to tailor the organization’s assurance level.
Supplemental controls **SHALL** be documented.

### Document Results - The Digital Identity Acceptance Statement {#IDacceptStmt}

The Digital Identity Acceptance Statement documents the results of the digital identity risk management process. This includes the Impact Assessment, Initial Assurance Level Selection, and Tailoring process.

The statement **SHALL** include, at a minimum:

1.	Initial Impact Assessment Results
2.	Initially assessed xAL,
3.	Tailored xAL and rationale, if tailored xAL differs from initially assessed xAL,
4.	All compensating controls and their comparability or residual risk associated with compensating controls
5.	All supplemental controls

Federal agencies **SHOULD** include this information in the system authorization package described in [[SP800-37]](sec8_references.md#ref-SP800-37).

## Continuously Evaluate and Improve

Threat actors adapt, user expectations and needs shift, and missions evolve. As such, risk assessments and identity solutions are not to be set and forgotten. To maintain pace with the constantly shifting environment in which they operate, organizations **SHOULD** implement a continuous evaluation and improvement program that leverages input from people interacting with the identity system. These programs **SHOULD** consider feedback from application performance metrics, threat intelligence, fraud analytics, assessments of equity impacts, privacy impact analysis, and user inputs.

## Cyber, Fraud, and Identity Program Integrity

Typically, identity solutions are the front door for a critical business or service function. Accordingly, they should not operate in a vacuum. Close coordination of identity functions with cybersecurity teams, threat intelligence teams, and program integrity teams can enable a more complete protection of business capabilities, while constantly improving identity solution capabilities. For example, payment fraud data collected by program integrity teams could provide indicators of compromised subscriber accounts and potential weaknesses in identity proofing implementations. Similarly, threat intelligence teams may receive indication of new TTPs that may impact identity proofing, authentication, and federation processes. Organizations **SHOULD** establish consistent mechanisms for the exchange of information between critical security and fraud stakeholders.

Where supporting service providers, such as CSPs, are external, this may be complicated, but **SHOULD** be considered in contractual and legal mechanisms. All data collected, transmitted, or shared **SHALL** be minimized and subject to a detailed privacy and legal
assessment.
