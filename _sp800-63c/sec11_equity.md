---
layout: default
title: Equity Considerations
navOrder: 11
navTitle: Equity
permalink: /sp800-63c/equity/
anchor: equity
section: 11
---

# Equity Considerations {#equity}

_This section is informative._

Equitable access to the functions of IdPs and RPs is an essential element of a federated identity system. The ability for all subscribers to authenticate reliably is required to provide equitable access to government services, even when using federation technology, as specified in Executive Order 13985, _Advancing Racial Equity and Support for Underserved Communities Through the Federal Government_ [[EO13985]](references.md#ref-EO13985). In assessing equity risks, IdPs and RPs should consider the overall user population served by their federated identity service. Additionally, IdPs and RPs further identify groups of users within the population whose shared characteristics can cause them to be subject to inequitable access, treatment, or outcomes when using that service. The Usability Considerations provided in [Sec. 10](../sec10_usability.md#usability) should also be considered to help ensure the overall usability and equity for all persons using federated identity services.

In its role as the verifier, the IdP needs to be aware of equity considerations related to identity proofing, attribute validation, and enrollment as enumerated in [[SP800-63A]](../_sp800-63a/sec11_equity.md#sec11){:latex-href="#ref-SP800-63A"} Sec. 11 and equity considerations concerning authenticators as enumerated in [[SP800-63B]](../_sp800-63b/sec11_equity.md#sec11){:latex-href="#ref-SP800-63B"} Sec. 11. An RP offering FAL3 will also need to be aware of these same authenticator considerations when processing bound authenticators, whether the authenticators are managed at the IdP or RP.

Since the federation process takes place over a network protocol between multiple active parties, the experience of authenticating using the federation system may present equity problems, such as the following examples:

* Completing the entire federated transaction without timing out may be difficult for subscribers without a reliable network connection, such as those in rural areas.
* It may be difficult to provide informed consent for a runtime decision regarding the release of attributes for subscribers with intellectual, developmental, learning, or neurocognitive difficulties.
* Systems with sufficient processing power, network access, and other features required to interact with both the IdP and the RP simultaneously may be difficult to afford for some subscribers.
* Subscribers that share devices may find allowlist-based systems difficult to manage securely, as other users of the device could silently gain unintended access to an RP through a session still active at the IdP.
* It could be prohibitively difficult to re-establish an account at the RP for subscribers who lose access to their IdP for any of a variety of reasons.

Normative requirements have been established requiring IdPs and RPs to mitigate the problems in this area that are expected to be most common. However, normative requirements are unlikely to have anticipated all potential equity problems. Potential equity problems also will vary for different applications. Accordingly, IdPs and RPs need to provide mechanisms for subscribers to report inequitable authentication requirements and to advise them on potential alternative authentication strategies.

This guideline allows the binding of additional federated identifiers to an RP subscriber account to minimize the risk of IdP access loss (see [Sec. 5.4](sec5_federation.md#rp-account)). However, a subscriber might find it difficult to have multiple IdP accounts that are acceptable to the RP at the same time. This inequity can be addressed by having the RP having its own account recovery process that allows for the secure binding and unbinding of multiple federated identifiers from the RP subscriber account.

RPs need to be aware that not all subscribers will necessarily have access to the same IdPs. The RPs can institute locally authenticated accounts for such subscribers, and later allow binding of those accounts to federated identifiers.
