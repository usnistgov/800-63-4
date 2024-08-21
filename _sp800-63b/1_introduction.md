---
layout: default
title: Introduction
navOrder: 2
navTitle: Introduction
permalink: /sp800-63b/introduction/
anchor: introduction
section: 1
---

# Introduction {#introduction}

_This section is informative._

Authentication is the process of determining the validity of one or more authenticators used to claim a digital identity by establishing that a subject attempting to access a digital service is in control of the secrets used to authenticate. If return visits are applicable to a service, successful authentication provides reasonable risk-based assurance that the subject accessing the service today is the same as the one who previously accessed the service. One-time services (where the subscriber will only ever access the service once) do not necessarily require the issuance of authenticators to support persistent digital authentication.

The authentication of claimants is central to the process of associating a subscriber with their online activity as recorded in their *subscriber account*, which is maintained by a *credential service provider* (CSP). Authentication is performed by verifying that the claimant controls one or more *authenticators* (called *tokens* in some earlier editions of SP 800-63) associated with a given subscriber account. The authentication process is conducted by a *verifier*, which is a role of the CSP or &mdash; in federated authentication &mdash; of an identity provider (IdP). Upon successful authentication, the verifier asserts an *identifier* to the relying party (RP). Optionally, the verifier may assert additional attributes to the RP.

This document provides recommendations on types of authentication processes, including choices of authenticators, that may be used at various *Authentication Assurance Levels* (AALs). It also provides recommendations on events that may occur during the lifetime of authenticators, including initial issuance, maintenance, and invalidation in the event of loss or theft of the authenticator.

This technical guideline applies to the digital authentication of subjects to systems over a network. It also requires that verifiers and RPs participating in authentication protocols be authenticated to claimants to assure the identity of the services with which they are authenticating. It does not address the authentication of a person for physical access (e.g., to a building). However, some credentials used for digital access may also be used for physical access authentication as described in [[SP800-116]](references.md#ref-SP-800-116).

AALs characterizes the strength of an authentication transaction as an ordinal category. Stronger authentication (i.e., a higher AAL) requires malicious actors to have better capabilities and to expend greater resources to successfully subvert the authentication process. Authentication at higher AALs can effectively reduce the risk of attacks. A high-level summary of the technical requirements for each of the AALs is provided below; see [Sec. 2](2_aal.md#AAL_SEC4) and [Sec. 3](3_authenticators.md#AAL_SEC5) of this document for specific normative requirements.

**Authentication Assurance Level 1**: AAL1 provides basic confidence that the claimant controls an authenticator bound to the subscriber account being authenticated. AAL1 requires only single-factor authentication using a wide range of available authentication technologies. However, it is recommended that applications assessed at AAL1 offer multi-factor authentication options. Successful authentication requires that the claimant prove possession and control of the authenticator.

**Authentication Assurance Level 2**: AAL2 provides high confidence that the claimant controls one or more authenticators bound to the subscriber account being authenticated. Proof of the possession and control of two distinct *authentication factors* is required. Applications assessed at AAL2 must offer a phishing-resistant authentication option.

**Authentication Assurance Level 3**: AAL3 provides very high confidence that the claimant controls one or more authenticators bound to the subscriber account being authenticated. Authentication at AAL3 is based on the proof of possession of a key through the use of a public-key cryptographic protocol. AAL3 authentication requires a hardware-based authenticator with a non-exportable private key and a phishing-resistant authenticator (see [Sec. 3.2.5](3_authenticators.md#verifimpers)); the same device may fulfill both requirements. To authenticate at AAL3, claimants are required to prove possession and control of two distinct authentication factors.

When a session has been authenticated at a given AAL and a higher AAL is required, an authentication process may also provide step-up authentication to raise the session's AAL.

## Notations

This guideline uses the following typographical conventions in text:

- Specific terms in **CAPITALS** represent normative requirements. When these same terms are not in **CAPITALS**, the term does not represent a normative requirement. 
    - The terms "**SHALL**" and "**SHALL NOT**" indicate requirements to be strictly followed in order to conform to the publication and from which no deviation is permitted.
    - The terms "**SHOULD**" and "**SHOULD NOT**" indicate that among several possibilities, one is recommended as particularly suitable without mentioning or excluding others, that a certain course of action is preferred but not necessarily required, or that (in the negative form) a certain possibility or course of action is discouraged but not prohibited.
    - The terms "**MAY**" and "**NEED NOT**" indicate a course of action that is permissible within the limits of the publication.
    - The terms "**CAN**" and "**CANNOT**" indicate a material, physical, or causal possibility and capability or &mdash; in the negative &mdash; the absence of that possibility or capability.

## Document Structure

This document is organized as follows. Each section is labeled as either normative (i.e., mandatory for compliance) or informative (i.e., not mandatory).

- Section 1 introduces the document. This section is _informative_.
- Section 2 describes requirements for Authentication Assurance Levels. This section is _normative_.
- Section 3 describes requirements for authenticator and verifier requirements. This section is _normative_.
- Section 4 describes requirements for authenticator event management. This section is _normative_.
- Section 5 describes requirements for session management. This section is _normative_.
- Section 6 provides security considerations. This section is _informative_.
- Section 7 provides privacy considerations. This section is _informative_.
- Section 8 provides usability considerations. This section is _informative_.
- Section 9 provides equity considerations. This section is _informative_.
- The References section lists publications that are referred to in this document. This section is _informative_.
- Appendix A discusses the strength of passwords. This appendix is _informative_.
- Appendix B discusses syncable authenticators. This appendix is _normative_.
- Appendix C contains a selected list of abbreviations used in this document. This appendix is _informative_.
- Appendix D contains a glossary of selected terms used in this document. This appendix is _informative_.
- Appendix E contains a summarized list of changes in this document's history. This appendix is _informative_.
