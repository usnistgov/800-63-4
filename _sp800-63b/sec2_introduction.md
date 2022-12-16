---
layout: default
title: Introduction
navOrder: 2
navTitle: Introduction
permalink: /sp800-63b/introduction/
anchor: sec2
section: 2
---

# Introduction {#sec2}

_This section is informative._

Digital authentication is the process of determining the validity of one or more authenticators used to claim a digital identity. Authentication establishes that a subject attempting to access a digital service is in control of the technologies used to authenticate. For services in which return visits are applicable, successfully authenticating provides reasonable risk-based assurances that the subject accessing the service today is the same as the one who accessed the service previously.

The ongoing authentication of subscribers is central to the process of associating a subscriber with their online activity (i.e., with their _subscriber account_). Subscriber authentication is performed by verifying that the claimant controls one or more *authenticators* (called *tokens* in some earlier versions of SP 800-63) associated with a given subscriber account. A successful authentication results in the assertion of a pseudonymous or non-pseudonymous identifier and optionally other identity information to the relying party (RP).

This document provides recommendations on types of authentication processes, including choices of authenticators, that may be used at various *authentication assurance levels* (AALs). It also provides recommendations on the lifecycle of authenticators, including revocation in the event of loss or theft.

This technical guideline applies to digital authentication of subjects to systems over a network. It does not address the authentication of a person for physical access (e.g., to a building), though some credentials used for digital access may also be used for physical access authentication. This technical guideline also requires that federal systems and service providers participating in authentication protocols be authenticated to subscribers.

The AAL characterizes the strength of an authentication transaction as an ordinal category. Stronger authentication (a higher AAL) requires malicious actors to have better capabilities and to expend greater resources in order to successfully subvert the authentication process. Authentication at higher AALs can effectively reduce the risk of attacks. A high-level summary of the technical requirements for each of the AALs is provided below; see [Sec. 4](sec4_aal.md#AAL_SEC4) and [Sec. 5](sec5_authenticators.md#AAL_SEC5) of this document for specific normative requirements.

**Authentication Assurance Level 1**: AAL1 provides some assurance that the claimant controls an authenticator bound to the subscriber account. AAL1 requires either single-factor or multi-factor authentication using a wide range of available authentication technologies. Successful authentication requires that the claimant prove possession and control of the authenticator through a secure authentication protocol.

**Authentication Assurance Level 2**: AAL2 provides high confidence that the claimant controls one or more authenticators bound to the subscriber account. Proof of possession and control of two different authentication factors is required through secure authentication protocols. Approved cryptographic techniques are required at AAL2 and above.

**Authentication Assurance Level 3**: AAL3 provides very high confidence that the claimant controls one or more authenticators bound to the subscriber account. Authentication at AAL3 is based on proof of possession of a key through a cryptographic protocol. AAL3 authentication requires a hardware-based authenticator and a phishing-resistant authenticator (see [Sec. 5.2.5](sec5_authenticators.md#verifimpers)); the same device may fulfill both these requirements. In order to authenticate at AAL3, claimants are required to prove possession and control of two distinct authentication factors through secure authentication protocols. Approved cryptographic techniques are required.

The following list states which sections of the document are normative and which are informative:

- 1 Purpose _Informative_
- 2 Introduction _Informative_
- 3 Definitions and Abbreviations _Informative_
- 4 Authentication Assurance Levels  _Normative_
- 5 Authenticator and Verifier Requirements  _Normative_
- 6 Authenticator Lifecycle Management  _Normative_
- 7 Session Management  _Normative_
- 8 Threat and Security Considerations _Informative_
- 9 Privacy Considerations _Informative_
- 10 Usability Considerations _Informative_
- 11 Equity Considerations _Informative_
- References _Informative_
- Appendix A Strength of Memorized Secrets _Informative_
- Appendix B Change Log _Informative_
