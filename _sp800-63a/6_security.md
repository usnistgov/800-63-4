---
layout: default
title: Security
navOrder: 7
navTitle: Security
permalink: /sp800-63a/security/
anchor: security
section: 6
---

# Threats and Security Considerations {#security}

_This section is informative._

Effective protection of identity proofing processes requires the layering of security controls and processes throughout a transaction with a given applicant. To achieve this, it is necessary to understand where and how threats can arise and compromise enrollments. There are three general categories of threats to the identity proofing process: 

 * **Impersonation**: where an attacker attempts to pose as another, legitimate, individual (e.g., identity theft)
  
 * **False or Fraudulent Representation**: where an attacker may create a false identity or false claims about an identity (e.g., synthetic identity fraud)
  
 * **Infrastructure**: where attackers may seek to compromise confidentiality, availability, and integrity of the infrastructure, data, software, or people supporting the CSP's identity proofing process (e.g., distributed denial of service, insider threats)
  
This section focuses on impersonation and false or fraudulent representation threats, as infrastructure threats are addressed by traditional computer security controls (e.g., intrusion protection, record keeping, independent audits) and are outside the scope of this document. For more information on security controls, see [[SP800-53]](references.md#ref-SP800-53), _Recommended Security and Privacy Controls for Federal Information Systems and Organizations_.


[Table 2. Identity Proofing and Enrollment Threats](6_security.md#table-2){:name="table-2"}
{:latex-ignore="true"}

| Attack/Threat |Description | Example |
|---------------|------------------------|------------------|
|Automated Enrollment Attempts|Attackers leverage scripts and automated processes to rapidly generate large volumes of enrollments| Bots leverage stolen data to submit benefits claims.|
|Evidence Falsification | Attacker creates or modifies evidence in order to claim an identity| A fake driver's license is used as evidence.| 
|Synthetic Identity fraud | Attacker fabricates evidence of identity that is not associated with a real person| Opening a credit card in a fake name to create a credit file.|
|Fraudulent Use of Identity (Identity Theft)| Attacker fraudulently uses another individual's identity or identity evidence | An individual uses a stolen passport.|
|Social Engineering| Attacker convinces a legitimate applicant to provide identity evidence or complete the identity proofing process under false pretenses| An individual submits their identity evidence to an attacker posing as a potential employer.|
|False Claims| Attacker associates false attributes or information with a legitimate identity| An individual falsely claims residence in a state in order to obtain a benefit that is available only to state residents.|
|Video or Image Injection Attack| Attacker creates a fake video feed of an individual associated with a real person| A deepfake video is used to impersonate an individual portrayed on a stolen driver's license.|
{:latex-table="2" latex-caption="Identity Proofing and Enrollment Threats" latex-columns="p@0.25\textwidth,p@0.35\textwidth,p@0.25\textwidth"}


## Threat Mitigation Strategies

Threats to the enrollment and identity proofing process are summarized in [Table 2](6_security.md#table-2). Related mechanisms that assist in mitigating the threats identified above are summarized in [Table 3](6_security.md#table-3). These mitigations should not be considered comprehensive but a summary of mitigations detailed more thoroughly at each Identity Assurance Level and applied based on the risk assessment processes detailed in [Sec. 3 of [SP800-63]](../_sp800-63/3_DIRM.md#sec5){:latex-href="#ref-SP800-63"}.


[Table 3. Identity Proofing and Enrollment Threat Mitigation Strategies](6_security.md#table-3){:name="table-3"}
{:latex-ignore="true"}

{::nomarkdown type="latex"}\AtBeginEnvironment{tabulary}{\small}{:/}

| Threat/Attack | Mitigation Strategies | Normative Reference(s) |
|-------------------|-------------------------|------------------------|
|Automated Enrollment Attempts | Web Application Firewall (WAF) controls and bot detection technology. Out-of-band engagement (e.g., confirmation codes). Biometric verification and liveness detection mechanisms. Traffic and network analysis capabilities to identify indications or malicious traffic. | 3.1.5, 3.1.8, 3.1.11 |
|Evidence Falsification | Validation of core attributes with authoritative or credible sources. Validation of physical or digital security features of the presented evidence. | 4.1.4 & 4.1.5 (IAL1), 4.2.4 & 4.2.5 (IAL2), 4.3.4 & 4.3.5 (IAL3) |
|Synthetic Identity Fraud | Collection of identity evidence. Validation of core attributes with authoritative or credible sources. Biometric comparison of the applicant to validated identity evidence or biometric data. Checks against vital statistics repositories (e.g., Death Master File). | 3.1.2.1, 4.1.2, 4.1.5, & 4.1.6 (IAL1), 4.2.2, 4.2.5, & 4.2.6 (IAL2), 4.3.2, 4.3.5, & 4.3.6 (IAL3) |
|Fraudulent Use of Identity (Identity Theft)| Biometric comparison of the applicant to validated identity evidence or biometric data. Presentation attack detection measures to confirm the genuine presence of applicant. Out-of-band engagement (e.g., confirmation codes) and notice of proofing. Checks against vital statistics repositories (e.g., Death Master File). Fraud, transaction, and behavioral analysis capabilities to identify indicators of potentially malicious account establishment. | 3.1.2.1, 3.1.8, 3.1.10, 3.1.11, 4.1.6 (IAL1), 4.2.6 (IAL2), 4.3.6 (IAL3) |
|Social Engineering| Training of trusted referees to identify indications of coercion or distress. Out-of-band engagement and notice of proofing to validated address. Provide information and communication to end users on common threats and schemes. Offer onsite in-person attended identity proofing option.  | 2.1.3, 3.1.8, 3.1.110, 3.1.13.1, 8.4 |
|False Claims| Geographic restrictions on traffic. Validation of core attributes with authoritative or credible sources.| 3.1.2.1, 4.1.5 (IAL1), 4.2.5 (IAL2), 4.3.5 (IAL3) |
|Video or Image Injection Attack| Use of a combination of active and passive PAD. Use of authenticated protected channels for communications between devices and servers running matching. Authentication of biometric sensors where feasible. Monitoring and analysis of incoming video and image files to detect signs of injection.| 3.1.8 |
{:latex-table="3" latex-caption="Identity Proofing and Enrollment Threat Mitigation Strategies" latex-columns="p@0.15\textwidth,p@0.55\textwidth,p@0.20\textwidth"}

{::nomarkdown type="latex"}\AtBeginEnvironment{tabulary}{\normalsize}{:/}

## Collaboration with Adjacent Programs 

Identity proofing services typically serve as the front door for critical business or service functions. Accordingly, these services should not operate in a vacuum. A close coordination of identity proofing and CSP functions with cybersecurity teams, threat intelligence teams, and program integrity teams can enable a more complete protection of business capabilities while constantly improving identity proofing capabilities. For example, payment fraud data collected by program integrity teams could provide indicators of compromised subscriber accounts and potential weaknesses in identity proofing implementations. Similarly, threat intelligence teams may receive indications of new tactics, techniques, and procedures that may impact identity proofing processes. CSPs and RPs should seek to establish consistent mechanisms for the exchange of information between critical security and fraud stakeholders. Where the CSP is external, this may be complicated, but should be addressed through contractual and legal mechanisms, to include technical and interoperability considerations. All data collected, transmitted, or shared should be minimized and subject to a detailed privacy and legal assessment.
