---
layout: default
title: Equity Considerations
navOrder: 11
navTitle: Equity
permalink: /sp800-63b/equity/
anchor: sec11
section: 11
---

# Equity Considerations {#sec11}

_This section is informative._

Accurate and equitable authentication service is an essential element of a digital identity system. While the accuracy aspects of authentication are largely the subject of the security requirements found elsewhere in this document, the ability for all subscribers to authenticate reliably is required to provide equitable access to government services as specified in Executive Order 13985, "Advancing Racial Equity and Support for Underserved Communities Through the Federal Government" [[EO13985]](references.md#ref-EO13985). In assessing equity risks, a CSP should consider the overall user population served by its authentication service. Additionally, the CSP further identifies groups of users within the population whose shared characteristic(s) can cause them to be subject to inequitable access, treatment, or outcomes when using that service. The usability considerations provided in [Sec. 10](sec10_usability.md#sec10) should also be considered to help ensure the overall usability and equity for all persons using authentication services. 

A primary aspect of equity is that the CSP needs to anticipate the needs of its subscriber population and offer authenticator options that are suitable for that population. Some examples of authenticator suitability problems are as follows:

* SMS-based out-of-band authentication may not be usable for subscribers in rural areas where mobile phone service is not available.
* OTP devices may be difficult for subscribers with vision difficulties to read.
* Out-of-band authentication secrets sent via a voice telephone call may be difficult for subscribers with hearing difficulties to understand.
* Facial matching algorithms may less effectively match facial characteristics of subscribers of some ethnicities.
* The cost of hardware-based authenticators may be beyond the means of some subscribers.
* Accurate manual entry of memorized secrets may be difficult for subscribers with some mobility and dexterity-related physical disabilities.
* The use of certain authenticator types may be challenging for subscribers with some disabilities such as intellectual, developmental, learning, and neurocognitive difficulties.

Normative requirements have been established requiring CSPs to mitigate the problems in this area that are expected to be most common. However, it is not feasible to anticipate all potential equity problems. Potential equity problems also will vary for different applications. Accordingly, CSPs need to provide mechanisms for subscribers to report inequitable authentication requirements and to advise them on potential alternative authentication strategies.

This guideline recommends the binding of additional authenticators to minimize the need for account recovery (see [Sec. 6.1.2.3](sec6_lifecycle.md#replacement)). However, a subscriber might find it difficult to purchase a second hardware-based authenticator as a backup. This inequity can be addressed by making inexpensive authenticators such as look-up secrets (see [Sec. 5.1.2](sec5_authenticators.md#lookupsecrets)) available for use in the event of a primary authenticator failure or loss.

CSPs need to be responsive to subscribers that experience authentication challenges that cannot be solved using authenticators they currently support. This might involve supporting a new authenticator type or allowing federated authentication through a trusted service that meets the needs of the subscriber.