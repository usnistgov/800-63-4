---
layout: default
title: Equity Considerations
navOrder: 10
navTitle: Equity
permalink: /sp800-63b/equity/
anchor: sec11
section: 9
---

# Equity Considerations {#sec11}

_This section is informative._

Accurate and equitable authentication service is an essential element of a digital identity system. While the accuracy aspects of authentication are primarily the subject of the security requirements found elsewhere in this document, the ability for all subscribers to reliably authenticate is required to provide equitable access to government services, as specified in Executive Order 13985, *Advancing Racial Equity and Support for Underserved Communities Through the Federal Government* [[EO13985]](references.md#ref-EO13985). When assessing equity risks, a CSP should consider the overall user population for its authentication service. Additionally, the CSP further identifies groups of users within the population whose shared characteristics may cause them to be subject to inequitable access, treatment, or outcomes when using that service. [Section 8](8_usability.md#sec10) describes considerations to help ensure the overall usability and equity for all persons who use authentication services. 

A primary aspect of equity is that the CSP needs to anticipate the needs of its subscriber population and offer authenticator options that are suitable for that population. Some examples of authenticator suitability problems are:

* SMS-based out-of-band authentication may not be usable for subscribers in rural areas without mobile phone service.
* OTP authenticators may be difficult for subscribers with vision issues to read.
* Out-of-band authentication secrets sent via a voice telephone call may be difficult for subscribers with hearing difficulties to understand.
* Facial matching algorithms may not match the facial characteristics of all ethnicities or those wearing glasses equally well.
* Some subscribers may be missing fingers, have degraded fingerprints (e.g., from working with chemicals or extensively using their hands), or have dexterity problems that interfere with fingerprint collection.
* The cost of hardware-based authenticators may be beyond the means of some subscribers.
* Accurate manual entry of passwords may be difficult for subscribers with mobility and dexterity-related physical disabilities.
* Certain authenticator types may be challenging for subscribers with intellectual, developmental, learning, or neurocognitive difficulties.
* Lower-income subscribers are less likely to have up-to-date devices that are required by some authentication modes.
* Lower-income subscribers may be limited to the use of a smartphone and, therefore, may be unable to use USB-connected authenticators.
* Subscribers with less technological skill may need help to enter OTP codes from one device to another.
* Older subscribers may need help with the small form factor of some authenticators.
* Subscribers experiencing addiction, sexual exploitation, or other trauma may struggle to remember passwords or activation secrets.

While CSPs are required to mitigate the common and expected problems in this area, it is not feasible to anticipate all potential equity problems, which will vary for different applications. Accordingly, CSPs need to provide mechanisms for subscribers to report inequitable authentication requirements and advise them on potential alternative authentication strategies.

This guideline recommends the binding of additional authenticators to minimize the need for account recovery (see [Sec. 4.2](4_events.md#recovery)). However, a subscriber may need help to purchase a second hardware-based authenticator as a backup. This inequity can be addressed by making inexpensive authenticators such as look-up secrets (see [Sec. 3.1.2](3_authenticators.md#lookupsecrets)) available for use in the event of an authenticator failure or loss.

CSPs need to be responsive to subscribers who experience authentication challenges that cannot be solved using the authenticators that they currently support. This might involve supporting a new authenticator type or allowing federated authentication through a trusted service that meets the subscriber's needs.
