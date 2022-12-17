---
layout: cover
title: "NIST SP 800-63 Digital Identity Guidelines (翻訳版)"
description: "NIST Special Publication 800-63 Digital Identity Guidelines (翻訳版)"
---

## Call for Comments on Initial Public Draft of Revision 4

NIST requests comments on the draft fourth revision to the four-volume suite of Special Publication 800-63, *Digital Identity Guidelines*.  This publication presents the process and technical requirements for meeting the digital identity management assurance levels specified in each volume. They also provide considerations for enhancing privacy, equity, and usability of digital identity solutions and technology.

NIST requests that all comments be submitted by __11:59pm Eastern Time on March 24, 2023__. Please submit your comments to <dig-comments@nist.gov>. See the [Note to Reviewers](#ntr) section below for specific topics about which NIST is seeking your feedback. NIST will review all comments and make them available at the [NIST Identity and Access Management website](https://www.nist.gov/identity-access-management). Commenters are encouraged to use the comment template provided on the [NIST Computer Security Resource Center website](https://csrc.nist.gov/publications/detail/sp/800-63/4/draft).

## Available Online {#online-versions}

The online versions of the four volumes of draft SP 800-63-4 are available at:

<ul class="audiences">
<li>
  <div>
    <a href="sp800-63.ja.html"><img src="assets/63.png" alt="SP 800-63-4" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63.ja.html">SP 800-63-4</a></h3>
  <h6>Digital Identity Guidelines</h6>
</li>
<li>
  <div>
    <a href="sp800-63a.ja.html"><img src="assets/63a.png" alt="SP 800-63A-4" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63a.ja.html">SP 800-63A</a></h3>
  <h6>Enrollment & Identity Proofing</h6>
</li>
<li>
  <div>
    <a href="sp800-63b.ja.html"><img src="assets/63b.png" alt="SP 800-63B-4" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63b.ja.html">SP 800-63B</a></h3>
  <h6>Authentication & Lifecycle Management</h6>
</li>
<li>
  <div>
    <a href="sp800-63c.ja.html"><img src="assets/63c.png" alt="SP 800-63C-4" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63c.ja.html">SP 800-63C</a></h3>
  <h6>Federation & Assertions</h6>
</li>
</ul>



PDF versions of these documents are available on the [NIST Computer Security Resource Center](https://csrc.nist.gov/publications/detail/sp/800-63/4/draft).

## Background {#background}
The rapid proliferation of online services over the past few years has heightened the need for reliable, equitable, secure, and privacy-protective digital identity solutions.

Revision 4 of NIST Special Publication 800-63, Digital Identity Guidelines, intends to respond to the changing digital landscape that has emerged since the last major revision of this suite was published in 2017 &mdash; including the real-world implications of online risks. The guidelines present the process and technical requirements for meeting digital identity management assurance levels for identity proofing, authentication, and federation, including requirements for security and privacy as well as considerations for fostering equity and the usability of digital identity solutions and technology.

Taking into account feedback provided in response to our [June 2020 Pre-Draft Call for Comments](https://csrc.nist.gov/publications/detail/sp/800-63/4/archive/2020-06-08), as well as research conducted into real-world implementations of the guidelines, market innovation, and the current threat environment, this draft seeks to:
1. **Advance Equity:** This draft seeks to expand upon the risk management content of previous revisions and specifically mandates that agencies account for impacts to individuals and communities in addition to impacts to the organization. It also elevates risks to mission delivery – including challenges to providing services to all people who are eligible for and entitled to them – within the risk management process and when implementing digital identity systems. Additionally, the guidance now mandates continuous evaluation of potential impacts across demographics, provides biometric performance requirements, and additional parameters for the responsible use of biometric-based technologies, such as those that utilize face recognition.
2. **Emphasize Optionality and Choice for Consumers:** In the interest of promoting and investigating additional scalable, equitable, and convenient identify verification options, including those that do and do not leverage face recognition technologies, this draft expands the list of acceptable identity proofing alternatives to provide new mechanisms to securely deliver services to individuals with differing means, motivations, and backgrounds. The revision also emphasizes the need for digital identity services to support multiple authenticator options to address diverse consumer needs and secure account recovery.
3. **Deter Fraud and Advanced Threats:** This draft enhances fraud prevention measures from the third revision by updating risk and threat models to account for new attacks, providing new options for phishing resistant authentication, and introducing requirements to prevent automated attacks against enrollment processes. It also opens the door to new technology such as mobile driver’s licenses and verifiable credentials.
4. **Address Implementation Lessons Learned:** This draft addresses areas where implementation experience has indicated that additional clarity or detail was required to effectively operationalize the guidelines. This includes re-working the federation assurance levels, providing greater detail on Trusted Referees, clarifying guidelines on identity attribute validation sources, and improving address confirmation requirements.

## Note to Reviewers {#ntr}
We need your help! These are DRAFT documents and, as such, will continue to evolve based on your feedback.

NIST is specifically interested in comments on and recommendations for the following topics:

**Identity Proofing and Enrollment**

- NIST sees a need for inclusion of an unattended, fully remote Identity Assurance Level (IAL) 2 identity proofing workflow that provides security and convenience, but does not require face recognition. Accordingly, NIST seeks input on the following questions:
    - What technologies or methods can be applied to develop a remote, unattended IAL2 identity proofing process that demonstrably mitigates the same risks as the current IAL2 process?
    - Are these technologies supported by existing or emerging technical standards?
    - Do these technologies have established metrics and testing methodologies to allow for assessment of performance and understanding of impacts across user populations (e.g., bias in artificial intelligence)?
- What methods exist for integrating digital evidence (e.g., Mobile Driver’s Licenses, Verifiable Credentials) into identity proofing at various identity assurance levels?
- What are the impacts, benefits, and risks of specifying a set of requirements for CSPs to establish and maintain fraud detection, response, and notification capabilities?
    - Are there existing fraud checks (e.g., date of death) or fraud prevention techniques (e.g., device fingerprinting) that should be incorporated as baseline normative requirements? If so, at what assurance levels could these be applied?
    - How might emerging methods such as fraud analytics and risk scoring be further researched, standardized, measured, and integrated into the guidance in the future?
    - What accompanying privacy and equity considerations should be addressed alongside these methods?
- Are current testing programs for liveness detection and presentation attack detection sufficient for evaluating the performance of implementations and technologies?
- What impacts would the proposed biometric performance requirements for identity proofing have on real-world implementations of biometric technologies?

**Risk Management**

- What additional guidance or direction can be provided to integrate digital identity risk with enterprise risk management?
- How might equity, privacy, and usability impacts be integrated into the assurance level selection process and digital identity risk management model?
- How might risk analytics and fraud mitigation techniques be integrated into the selection of different identity assurance levels? How can we qualify or quantify their ability to mitigate overall identity risk?

**Authentication and Lifecycle Management**

- Are emerging authentication models and techniques – such as FIDO passkey, Verifiable Credentials, and mobile driver’s licenses – sufficiently addressed and accommodated, as appropriate, by the guidelines? What are the potential associated security, privacy, and usability benefits and risks?
- Are the controls for phishing resistance as defined in the guidelines for AAL2 and AAL3 authentication clear and sufficient?
- How are session management thresholds and reauthentication requirements implemented by agencies and organizations? Should NIST provide thresholds or leave session lengths to agencies based on applications, users, and mission needs?
- What impacts would the proposed biometric performance requirements for this volume have on real-world implementations of biometric technologies?

**Federation and Assertions**

- What additional privacy considerations (e.g., revocation of consent, limitations of use) may be required to account for the use of identity and provisioning APIs that had not previously been discussed in the guidelines?
- Is the updated text and introduction of “bound authenticators” sufficiently clear to allow for practical implementations of federation assurance level (FAL) 3 transactions? What complications or challenges are anticipated based on the updated guidance?

**General**

- Is there an element of this guidance that you think is missing or could be expanded?
- Is any language in the guidance confusing or hard to understand? Should we add definitions or additional context to any language?
- Does the guidance sufficiently address privacy?
- Does the guidance sufficiently address equity?
    - What equity assessment methods, impact evaluation models, or metrics could we reference to better support organizations in preventing or detecting disparate impacts that could arise as a result of identity verification technologies or processes?
- What specific implementation guidance, reference architectures, metrics, or other supporting resources may enable more rapid adoption and implementation of this and future iterations of the Digital Identity Guidelines?
- What applied research and measurement efforts would provide the greatest impact on the identity market and advancement of these guidelines?



**NOTE: All comments and responses are subject to release under the Freedom of Information Act (FOIA).  A call for patent claims is included on page ii of each draft. For additional information, see the [Information Technology Laboratory (ITL) Patent Policy &mdash; Inclusion of Patents in ITL Publications](https://www.nist.gov/itl/publications-0/itl-patent-policy-inclusion-patents-itl-publications).**
