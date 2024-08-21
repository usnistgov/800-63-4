---
layout: default
title: Privacy Considerations
navOrder: 8
navTitle: Privacy
permalink: /sp800-63b/privacy/
anchor: sec9
section: 7
---

# Privacy Considerations {#sec9}

*These privacy considerations supplement the guidance in Sec. 4. This section is informative.*

## Privacy Risk Assessment

The authentication requirements in [Sec. 2](2_aal.md#AAL_SEC4) and the optional session monitoring guidelines in [Sec. 5.3](5_session.md#monitoring) require the CSP to conduct a privacy risk assessment for records retention. Such a privacy risk assessment would include:

1. The likelihood that the records retention could create a problem for the subscriber, such as invasiveness or unauthorized access to the information.
2. The impact if such a problem did occur.

CSPs should be able to reasonably justify any response to identified privacy risks, including accepting, mitigating, and sharing the risk. Subscriber consent is a form of sharing the risk. It is therefore only appropriate for use when a subscriber could reasonably be expected to have the capacity to assess and accept the shared risk.

## Privacy Controls

[Section 2.4.3](2_aal.md#aal_privacy) requires CSPs to employ appropriately tailored privacy controls. [[SP800-53]](references.md#ref-SP800-53) provides a set of privacy controls for CSPs to consider when deploying authentication mechanisms, including notices, redress, and other important considerations for successful and trustworthy deployments.

## Use Limitation

[Section 2.4.3](2_aal.md#aal_privacy) requires CSPs to maintain the objectives of predictability (enabling reliable assumptions by individuals, owners, and operators about PII and its processing by an information system) and manageability (i.e., providing the capability for the granular administration of PII, including alteration, deletion, and selective disclosure) commensurate with privacy risks that can arise from the processing of attributes for purposes other than identity proofing, authentication, authorization, or attribute assertion; related fraud mitigation; or to comply with law or legal process [[NISTIR8062]](references.md#ref-NISTIR8062).

CSPs may have various business purposes for processing attributes, including providing non-identity services to subscribers. However, processing attributes for purposes other than those specified at collection can create privacy risks. CSPs can identify appropriate measures that are commensurate with the privacy risks that arise from additional processing. For example, absent applicable laws, regulations, or policies, obtaining consent may not be necessary when processing attributes to provide non-identity services requested by subscribers. However, notices may help subscribers maintain reliable assumptions about the processing (i.e., predictability). Other processing of attributes may carry different privacy risks that call for obtaining consent or allowing subscribers more control over the use or disclosure of specific attributes (i.e., manageability). Subscriber consent must be meaningful. Therefore, as stated in [Sec. 2.4.3](2_aal.md#aal_privacy), when CSPs use consent measures, the subscriber's acceptance of additional uses shall not be a condition of providing authentication services.

Consult the agency SAOP if there are questions about whether the proposed processing falls outside of the scope of the permitted processing or appropriate privacy risk mitigation measures.

## Agency-Specific Privacy Compliance {#agency-privacy}

[Section 2.4.3](2_aal.md#aal_privacy) describes specific compliance obligations for federal CSPs. It is critical to involve the agency SAOP in the earliest stages of digital authentication system development to assess and mitigate privacy risks and advise the agency on compliance requirements, such as whether or not the collection of PII to issue or maintain authenticators triggers the *Privacy Act of 1974* [[PrivacyAct]](references.md#ref-PrivacyAct) or the *E-Government Act of 2002* [[E-Gov]](references.md#ref-E-Gov) requirement to conduct a PIA. For example, concerning the centralized maintenance of biometrics, Privacy Act requirements will likely be triggered and require coverage by a new or existing Privacy Act system of records notice due to the collection and maintenance of PII and any other attributes that are necessary for authentication. The SAOP can similarly assist the agency in determining whether a PIA is required.

These considerations should not be read as a requirement to develop a Privacy Act SORN or PIA for authentication alone. In many instances, a PIA and SORN can encompass the entire digital identity process or include the digital authentication process as part of a larger programmatic PIA that discusses the online services or benefits that the agency is establishing.

Due to the many components of digital authentication, the SAOP needs to be aware of and understand each component. For example, other privacy artifacts may apply to an agency that offers or uses federated CSP or RP services (e.g., Data Use Agreements, Computer Matching Agreements). The SAOP can assist the agency in determining what additional requirements apply. Moreover, a thorough understanding of the individual components of digital authentication will enable the SAOP to assess and mitigate privacy risks through compliance processes or other means.
