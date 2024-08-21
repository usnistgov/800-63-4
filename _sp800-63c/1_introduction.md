---
layout: default
title: Introduction
navOrder: 2
navTitle: Introduction
permalink: /sp800-63c/introduction/
anchor: introduction
section: 1
---

# Introduction {#introduction}

*This section is informative.*

Federation is a process that enables the subscriber account defined in [[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"} to be used with an RP that does not verify one of the authenticators bound to the subscriber account. Instead, a service known as an identity provider, or IdP, makes the subscriber account available through a federation protocol to the relying party, or RP. The IdP sends a verifiable statement, called an assertion, about the subscriber account to the RP, triggered by an authentication event of the subscriber. The RP verifies the assertion provided by the IdP and creates an authenticated session with the subscriber, granting the subscriber access to the RP's functions.

The IdP works in one of two modes:

- As a verifier for authenticators bound to the subscriber account as described in [[SP800-63B]](../_sp800-63b/1_introduction.md#introduction){:latex-href="#ref-SP800-63B"} (see details in [Sec. 4](4_generalidp.md#GenIdP)), or 
- As a subscriber-controlled device onboarded by the CSP, often known as a digital wallet (see details in [Sec. 5](5_subscriberidp.md#wallet)).

The federation process allows the subscriber to obtain services from multiple RPs without the need to hold or maintain separate authenticators at each RP, a process sometimes known as *single sign-on*. The federation process also is generally the preferred approach to authentication when the RP and the subscriber account are not administered together under a common security domain, since the RP does not need to verify an authenticator in the subscriber account. Even so, federation can be still applied within a single security domain for a variety of benefits including centralized account management and technical integration.

The federation process can be facilitated by additional parties acting in other roles, such as a federation authority to facilitate the trust agreements in place and federation proxies to facilitate the protocol connections.

## Notations

This guideline uses the following typographical conventions in text:

- Specific terms in **CAPITALS** represent normative requirements. When these same terms are not in **CAPITALS**, the term does not represent a normative requirement. 
    - The terms "**SHALL**" and "**SHALL NOT**" indicate requirements to be followed strictly in order to conform to the publication and from which no deviation is permitted.
    - The terms "**SHOULD**" and "**SHOULD NOT**" indicate that among several possibilities, one is recommended as particularly suitable without mentioning or excluding others, that a certain course of action is preferred but not necessarily required, or that (in the negative form) a certain possibility or course of action is discouraged but not prohibited.
    - The terms "**MAY**" and "**NEED NOT**" indicate a course of action permissible within the limits of the publication.
    - The terms "**CAN**" and "**CANNOT**" indicate a possibility and capability&mdash;whether material, physical, or causal&mdash;or, in the negative, the absence of that possibility or capability.

## Document Structure

This document is organized as follows. Each section is labeled as either normative (i.e., mandatory for compliance) or informative (i.e., not mandatory).

- Section 1 provides an introduction to the document. This section is _informative_.
- Section 2 describes requirements for Federation Assurance Levels. This section is _normative_.
- Section 3 describes general requirements for federation systems. This section is _normative_.
- Section 4 describes requirements for general-purpose IdPs. This section is _normative_.
- Section 5 describes requirements for subscriber-controlled wallets. This section is _normative_.
- Section 6 provides security considerations. This section is _informative_.
- Section 7 provides privacy considerations. This section is _informative_.
- Section 8 provides usability considerations. This section is _informative_.
- Section 9 provides equity considerations. This section is _informative_.
- Section 10 provides additional example scenarios. This section is _informative_.
- References contains a list of publications referred to from this document. This section is _informative_.
- Appendix A contains a selected list of abbreviations used in this document. This appendix is _informative_.
- Appendix B contains a glossary of selected terms used in this document. This appendix is _informative_.
- Appendix C contains a summarized list of changes in this document's history. This appendix is _informative_.
