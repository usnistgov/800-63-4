---
layout: default.ja
title: Security
navOrder: 7
navTitle: Security
permalink: /sp800-63a/security/
anchor: security
section: 7
---

# Threats and Security Considerations {#security}

_This section is informative._

Effective protection of identity proofing processes requires the layering of security controls and processes throughout a transaction with a given applicant. To achieve this, it is necessary to understand where and how threats can arise and compromise enrollments. There are three general categories of threats to the identity proofing process:

 * **Impersonation**: where an attacker attempts to pose as another, legitimate, individual (e.g., identity theft)

 * **False or Fraudulent Representation**: where an attacker may create a false identity or false claims about an identity (e.g., synthetic identity fraud)

 * **Infrastructure**: where attackers may seek to compromise confidentiality, availability, and integrity of the infrastructure, data, software, or people supporting the CSPs identity proofing process (e.g., distributed denial of service, insider threats)

This section focuses on impersonation and false or fraudulent representation threats, as infrastructure threats are addressed by traditional computer security controls (e.g., intrusion protection, record keeping, independent audits) and are outside the scope of this document. For more information on security controls, see [[SP800-53]](sec11_references.md#ref-SP800-53), _Recommended Security and Privacy Controls for Federal Information Systems and Organizations_.


[Table 2 Enrollment and Identity Proofing Threats](sec7_security.md#table-2){:name="table-2"}
{:latex-ignore="true"}

| Attack/Threat |Description | Example |
|---------------|------------------------|------------------|
|Automated Enrollment Attempts|Attackers leverage scripts and automated processes to rapidly generate large volumes of enrollments| Bots leverage stolen data to submit benefits claims.|
|Evidence Falsification | Attacker creates or modifies evidence in order claim an identity| A fake driver’s license is used as evidence.|
|Synthetic Identity fraud | Attacker fabricates evidence of identity that is not associated with a real person| Opening a credit cards in a fake name to create a credit file.|
|Fraudulent Use of Identity (Identity Theft)| Attacker fraudulently uses another individuals identity or identity evidence | An individual uses a stolen passport.|
|Social Engineering| Attacker convinces a legitimate applicant to provide identity evidence or complete the identity proofing process under false pretenses| An individual submits their identity evidence to an attacker posing as a potential employer.|
|False Claims| Attacker associates false attributes or information with a legitimate identity| An individual claims benefits from a state in which they do not reside.|
{:latex-table="2" latex-caption="Enrollment and Identity Proofing Threats" latex-columns="p@0.25\textwidth,p@0.35\textwidth,p@0.25\textwidth"}


## Threat Mitigation Strategies

Threats to the enrollment and identity proofing process are summarized in [Table 2](sec7_security.md#table-2). Related mechanisms that assist in mitigating the threats identified above are summarized in [Table 3](sec7_security.md#table-3). These mitigations should not be considered comprehensive but a summary of mitigations detailed more thoroughly at each Identity Assurance Level and applied based on the risk assessment processes detailed in [[SP800-63]](../_sp800-63/sec5_DIRM.md#sec5){:latex-href="#ref-SP800-63"} Sec. 5.


[Table 3 Enrollment and Issuance Threat Mitigation Strategies](sec7_security.md#table-3){:name="table-3"}
{:latex-ignore="true"}

| Threat/Attack | Mitigation Strategies | Normative Reference(s) |
|-------------------|-------------------------|------------------------|
|Automated Enrollment Attempts | CSP implements Web Application Firewall (WAF) controls and bot detection technology.CSP implements out-of-band engagement (e.g., enrollment codes). CSP implements biometric verification and liveness detection mechanism to determine genuine presence of an applicant. CSP implements traffic and network analysis capabilities to identify indications or malicious traffic | 5.3.1, 5.4.1, 5.5.1 |
|Evidence Falsification | CSP validates core attributes with authoritative or credible sources.  CSP checks physical or digital security features of the presented evidence. | 4.3, 5.3.2, 5.3.3, 5.4.2, 5.4.3, 5.5.2, 5.5.3 |
|Synthetic Identity fraud | CSP collects multiple pieces of identity evidence to support the proofing process. CSP validates core attributes with authoritative or credible sources. CSP verifies identity through biometric comparison of the applicant to validated identity evidence or biometric data provided by an authoritative or credible source. | 4.3, 4.3, 5.3.2, 5.3.3, 5.3.4, 5.4.2, 5.4.3, 5.4.4, 5.5.2, 5.5.3, 5.5.4 |
|Fraudulent Use of Identity (Identity Theft)| CSP verifies identity through biometric comparison of the applicant to validated identity evidence or biometric data provide by an authoritative or credible source. CSP implements presentation attack detection measures to confirm the genuine presence of the individual to whom the identity evidence belongs. CSP implements out-of-band engagement (e.g., enrollment codes) and notice of proofing. CSP conducts checks of vital statistics repositories (e.g., Death Master File).CSP implements fraud,  transaction, and behavioral analysis capabilities to identify indicators of potentially malicious account establishment. | 5.1.1, 5.3.4, 5.4.4, 5.5.4 |
|Social Engineering| CSP conducts training of Trusted Referees to identify indications of coercion or distress. CSP provides out-of-band engagement and notice of proofing to validated address. CSP provides information and communication to end users on common threats and schemes. | 5.1.6, 5.1.7, 5.1.9 |
|False Claims| CSP implements geographic restrictions on traffic. CSP validates core attributes and RP requested business attributes with authoritative or credible sources.| 5.1.1, 5.3.2, 5.3.3, 5.4.2, 5.4.3, 5.5.2, 5.5.3 |
{:latex-table="3" latex-caption="Enrollment and Issuance Threat Mitigation Strategies" latex-columns="p@0.20\textwidth,p@0.65\textwidth,p@0.15\textwidth"}


## Collaboration with Adjacent Programs

Identity proofing services typically serve as the front door for critical business or service functions. Accordingly, these services should not operate in a vacuum. Close coordination of identity proofing and CSP functions with cybersecurity teams, threat intelligence teams, and program integrity teams can enable a more complete protection of business capabilities while constantly improving identity proofing capabilities. For example, payment fraud data collected by program integrity teams could provide indicators of compromised subscriber accounts and potential weaknesses in identity proofing implementations. Similarly, threat intelligence teams may receive indications of new tactics, techniques, and procedures that may impact identity proofing processes. CSPs and RPs should seek to establish consistent mechanisms for the exchange of information between critical security and fraud stakeholders. Where the CSP is external, this may be complicated, but should be considered in contractual and legal mechanisms. All data collected, transmitted, or shared should be minimized and subject to a detailed privacy and legal assessment.
