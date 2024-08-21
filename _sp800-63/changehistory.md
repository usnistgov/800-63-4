---
layout: default
title: Change Log
navOrder: 8
navTitle: Change Log
permalink: /sp800-63/changelog/
anchor: changelog
section: C
---

# Change Log {#changelog}

## SP 800-63-1

NIST SP 800-63-1 updated NIST SP 800-63 to reflect current authenticator (then referred to as "token") technologies and restructured it to provide a better understanding of the digital identity architectural model used here. Additional (minimum) technical requirements were specified for the CSP, protocols used to transport authentication information, and assertions if implemented within the digital identity model.

## SP 800-63-2

NIST SP 800-63-2 was a limited update of SP 800-63-1 and substantive changes were made only in Sec. 5, *Registration and Issuance Processes*. The substantive changes in the revised draft were intended to facilitate the use of professional credentials in the identity proofing process, and to reduce the need to send postal mail to an address of record to issue credentials for level 3 remote registration. Other changes to Sec. 5 were minor explanations and clarifications.

## SP 800-63-3

NIST SP 800-63-3 is a substantial update and restructuring of SP 800-63-2. SP 800-63-3 introduces individual components of digital authentication assurance &mdash; AAL, IAL, and FAL &mdash; to support the growing need for independent treatment of authentication strength and confidence in an individual's claimed identity (e.g., in strong pseudonymous authentication). A risk assessment methodology and its application to IAL, AAL, and FAL has been included in this guideline. It also moves the whole of digital identity guidance covered under SP 800-63 from a single document describing authentication to a suite of four documents (to separately address the individual components mentioned above) of which SP 800-63-3 is the top-level document.

Other areas updated in 800-63-3 include:

- Renamed to _Digital Identity Guidelines_ to properly represent the scope includes identity proofing and federation, and to support expanding the scope to include device identity, or machine-to-machine authentication in future revisions.
- Changed terminology, including the use of *authenticator* in place of *token* to avoid conflicting use of the word *token* in assertion technologies.
-	Updated authentication and assertion requirements to reflect advances in both security technology and threats.
-	Added requirements on the storage of long-term secrets by verifiers.
-  Restructured identity proofing model.
-	Updated requirements regarding remote identity proofing.
-	Clarified the use of independent channels and devices as "something you have".
-	Removed pre-registered knowledge tokens (authenticators), with the recognition that they are special cases of (often very weak) passwords.
-	Added requirements regarding account recovery in the event of loss or theft of an authenticator.
-	Removed email as a valid channel for out-of-band authenticators.
-   Expanded discussion of reauthentication and session management.
-   Expanded discussion of identity federation; restructuring of assertions in the context of federation.

## SP 800-63-4

NIST SP 800-63-4 has substantial updates and re-organization from SP 800-63-3. Updates to 800-63-4 include:

- Expanded security and privacy considerations and added equity and usability considerations.
- Updated digital identity models and added a user-controlled wallet federation model that addresses the increased attention and adoption of digital wallets and attribute bundles.
- Expanded digital identity risk management process to include definition of the protected online services, user groups, and impacted entities.
- A more descriptive introduction to establish the context of the DIRM process, the two dimensions of risk it addresses, and the intended outcomes. This context-setting step includes defining and understanding the online service that the organization is offering and intending to protect with identity systems.
- Expanded digital identity risk management process to include definition of the protected online services, user groups, and impacted entities.
- Updated digital identity risk management process for additional assessments for tailoring initial baseline control selections.
- Added performance metrics for the continuous evaluation of digital identity systems.
- Added a new subsection on redress processes and requirements.
- Added a new Artificial Intelligence subsection to address the use of Artificial Intelligence in digital identity services.
