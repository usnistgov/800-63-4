---
layout: cover
title: "NIST SP 800-63 Digital Identity Guidelines"
description: "NIST Special Publication 800-63 Digital Identity Guidelines"
permalink: /
---

## Call for Comments on Second Public Draft of Revision 4

NIST requests comments on the draft fourth revision to the four-volume suite of Special Publication 800-63, *Digital Identity Guidelines*.  This publication presents the process and technical requirements for meeting the digital identity management assurance levels specified in each volume. They also provide considerations for enhancing privacy, equity, and usability of digital identity solutions and technology. 

NIST requests that all comments be submitted by __11:59pm Eastern Time on October 7, 2024__. Please submit your comments to <dig-comments@nist.gov>. See the [Note to Reviewers](#ntr) section below for specific topics about which NIST is seeking your feedback. NIST will review all comments and make them available at the [NIST Identity and Access Management website](https://www.nist.gov/identity-access-management). Commenters are encouraged to use the comment template provided on the [NIST Computer Security Resource Center website](https://csrc.nist.gov/publications/detail/sp/800-63/4/draft).

## Available Online {#online-versions}

The online versions of the four volumes of draft SP 800-63-4 are available at:

<ul class="audiences">
<li>
  <div>
    <a href="sp800-63.html"><img src="assets/63.png" alt="SP 800-63-4" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63.html">SP 800-63-4</a></h3>
  <h6>Digital Identity Guidelines</h6>
</li>
<li>
  <div>
    <a href="sp800-63a.html"><img src="assets/63a.png" alt="SP 800-63A-4" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63a.html">SP 800-63A</a></h3>
  <h6>Identity Proofing & Enrollment</h6>
</li>
<li>
  <div>
    <a href="sp800-63b.html"><img src="assets/63b.png" alt="SP 800-63B-4" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63b.html">SP 800-63B</a></h3>
  <h6>Authentication & Authenticator Management</h6>
</li>
<li>
  <div>
    <a href="sp800-63c.html"><img src="assets/63c.png" alt="SP 800-63C-4" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63c.html">SP 800-63C</a></h3>
  <h6>Federation & Assertions</h6>
</li>
</ul>



PDF versions of these documents are available on the [NIST Computer Security Resource Center](https://csrc.nist.gov/publications/detail/sp/800-63/4/draft).

## Background {#background}

In December 2022, NIST released the Initial Public Draft (IPD) of SP 800-63, Revision 4. Over the course of a 119-day public comment period, the authors received exceptional feedback from a broad community of interested entities and individuals. The input from nearly 4,000 specific comments has helped advance the improvement of these Digital Identity Guidelines in a manner that supports NIST's critical goals of providing foundational risk management processes and requirements that enable the implementation of secure, private, equitable, and accessible identity systems. All of the submitted comments are available online at the [SP 800-63 Public Comments archive](https://pages.nist.gov/800-63-Public-Comments/). Based on this initial wave of feedback, several substantive changes have been made across all of the volumes. These changes include but are not limited to the following:

1.  Updated text and context setting for risk management. Specifically, the authors have modified the process defined in the IPD to include a context-setting step of defining and understanding the online service that the organization is offering and intending to potentially protect with identity systems.
2.  Added recommended continuous evaluation metrics. The continuous improvement section introduced by the IPD has been expanded to include a set of recommended metrics for holistically evaluating identity solution performance. These are recommended due to the complexities of data streams and variances in solution deployments.
3.  Expanded fraud requirements and recommendations. Programmatic fraud management requirements for credential service providers and relying parties now address issues and challenges that may result from the implementation of fraud checks.
4.  Restructured the identity proofing controls. There is a new taxonomy and structure for the requirements at each assurance level based on the means of providing the proofing: Remote Unattended, Remote Attended (e.g., video session), Onsite Unattended (e.g., kiosk), and Onsite Attended (e.g., in-person).
5.  Integrated syncable authenticators. In April 2024, NIST published interim guidance for syncable authenticators. This guidance has been integrated into SP 800-63B as normative text and is provided for public feedback as part of the Revision 4 volume set.
6.  Added user-controlled wallets to the federation model. Digital wallets and credentials (called "attribute bundles" in SP 800-63C) are seeing increased attention and adoption. At their core, they function like a federated IdP, generating signed assertions about a subject. Specific requirements for this presentation and the emerging context are presented in SP 800-63C-4.

The rapid proliferation of online services over the past few years has heightened the need for reliable, equitable, secure, and privacy-protective digital identity solutions.
Revision 4 of NIST Special Publication SP 800-63, *Digital Identity Guidelines*, intends to respond to the changing digital landscape that has emerged since the last major revision of this suite was published in 2017, including the real-world implications of online risks. The guidelines present the process and technical requirements for meeting digital identity management assurance levels for identity proofing, authentication, and federation, including requirements for security and privacy as well as considerations for fostering equity and the usability of digital identity solutions and technology.

Based on the feedback provided in response to the June 2020 Pre-Draft Call for Comments, research into real-world implementations of the guidelines, market innovation, and the current threat environment, this draft seeks to:

- Address comments received in response to the IPD of Revision 4 of SP 800-63
- Clarify the text to address the questions and issues raised in the public comments
- Update all four volumes of SP 800-63 based on current technology and market developments, the changing digital identity threat landscape, and organizational needs for digital identity solutions to address online security, privacy, usability, and equity

NIST is specifically interested in comments and recommendations on the following topics:

1.	Risk Management and Identity Models

    - Is the "user controlled" wallet model sufficiently described to allow entities to understand its alignment to real-world implementations of wallet-based solutions such as mobile driver's licenses and verifiable credentials?
    - Is the updated risk management process sufficiently well-defined to support an effective, repeatable, real-world process for organizations seeking to implement digital identity system solutions to protect online services and systems?

2.  Identity Proofing and Enrollment

    - Is the updated structure of the requirements around defined types of proofing sufficiently clear? Are the types sufficiently described?
    - Are there additional fraud program requirements that need to be introduced as a common baseline for CSPs and other organizations?
    - Are the fraud requirements sufficiently described to allow for appropriate balancing of fraud, privacy, and usability trade-offs?
    - Are the added identity evidence validation and authenticity requirements and performance metrics realistic and achievable with existing technology capabilities?

3.	Authentication and Authenticator Management

    - Are the syncable authenticator requirements sufficiently defined to allow for reasonable risk-based acceptance of syncable authenticators for public and enterprise-facing uses?
    - Are there additional recommended controls that should be applied? Are there specific implementation recommendations or considerations that should be captured?
    - Are wallet-based authentication mechanisms and "attribute bundles" sufficiently described as authenticators? Are there additional requirements that need to be added or clarified?

5.	Federation and Assertions

    - Is the concept of user-controlled wallets and attribute bundles sufficiently and clearly described to support real-world implementations? Are there additional requirements or considerations that should be added to improve the security, usability, and privacy of these technologies?

6.	General

    - What specific implementation guidance, reference architectures, metrics, or other supporting resources could enable more rapid adoption and implementation of this and future iterations of the Digital Identity Guidelines?
    - What applied research and measurement efforts would provide the greatest impacts on the identity market and advancement of these guidelines?
  
Reviewers are encouraged to comment and suggest changes to the text of all four draft volumes of the SP 800-63-4 suite. NIST requests that all comments be submitted by 11:59pm Eastern Time on October 7th, 2024. Please submit your comments to <mailto:dig-comments@nist.gov>. NIST will review all comments and make them available on the [NIST Identity and Access Management website](https://www.nist.gov/identity-access-management). Commenters are encouraged to use the comment template provided on the NIST Computer Security Resource Center website for responses to these notes to reviewers and for specific comments on the text of the four-volume suite.


**NOTE: All comments and responses are subject to release under the Freedom of Information Act (FOIA).  A call for patent claims is included on page ii of each draft. For additional information, see the [Information Technology Laboratory (ITL) Patent Policy &mdash; Inclusion of Patents in ITL Publications](https://www.nist.gov/itl/publications-0/itl-patent-policy-inclusion-patents-itl-publications).**
