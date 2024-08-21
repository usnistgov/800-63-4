---
layout: default
title: Equity Considerations
navOrder: 10
navTitle: Equity
permalink: /sp800-63c/equity/
anchor: equity
section: 9
---

# Equity Considerations {#equity}

_This section is informative._

Equitable access to the functions of IdPs and RPs is an essential element of a federated identity system. The ability for all subscribers to authenticate reliably is required to provide equitable access to government services, even when using federation technology, as specified in Executive Order 13985, _Advancing Racial Equity and Support for Underserved Communities Through the Federal Government_ [[EO13985]](references.md#ref-EO13985). In assessing equity risks, IdPs and RPs should consider the overall user population served by their federated identity service. Additionally, IdPs and RPs further identify groups of users within the population whose shared characteristics can cause them to be subject to inequitable access, treatment, or outcomes when using that service. The Usability Considerations provided in [Sec. 8](../8_usability.md#usability) should also be considered to help ensure the overall usability and equity for all persons using federated identity services.

In its role as the verifier, the IdP needs to be aware of equity considerations related to identity proofing, attribute validation, and enrollment as enumerated in [[SP800-63A] Sec. 9](../_sp800-63a/9_equity.md#sec11){:latex-href="#ref-SP800-63A"} and equity considerations concerning authenticators as enumerated in [[SP800-63B] Sec. 9](../_sp800-63b/9_equity.md#sec11){:latex-href="#ref-SP800-63B"}. An RP offering FAL3 will also need to be aware of these same authenticator considerations when processing bound authenticators and holder-of-key assertions.

Since the federation process takes place over a network protocol between multiple active parties, the experience of authenticating using the federation system may present equity problems, such as the following examples:

* Completing the entire federation transaction without timing out may be difficult for subscribers without a reliable network connection, such as those in rural areas.
* It may be difficult to provide informed consent for a runtime decision regarding the release of attributes for subscribers with intellectual, developmental, learning, or neurocognitive difficulties.
* Systems with sufficient processing power, network access, and other features required to interact with both the IdP and the RP simultaneously may be too costly or beyond some subscribers' technological skill to access or use.
* Subscribers that share devices may find allowlist-based systems difficult to manage securely, as other users of the device could silently gain unintended access to an RP through a session still active at the IdP.
* It could be prohibitively difficult to re-establish an account at the RP for subscribers who lose access to their IdP for any of a variety of reasons.

Additionally, subscribers in disadvantaged populations could be more susceptible to monitoring and tracking through federation systems, as discussed in [Sec. 7](7_privacy.md#privacy).
If the IdP knows the subscriber is part of a disadvantaged population, the IdP could specifically target the subscriber by profiling them and their access to the set of RPs, and use the data gathered against the subscriber.
Alternatively, the IdP could learn that that the subscriber is part of a disadvantaged population by watching the RP connections. For example, if the IdP sees that the subscriber logs into social services, the IdP has learned things about the subscriber's socioeconomic status that were not disclosed  to the IdP. The IdP could then use this to unfairly target the subscriber and provide a lower quality of service.
Additionally, subscribers in disadvantaged populations are at a greater risk of having their data correlated between a set of colluding RPs. For example, a set of RPs could share subscriber attributes and behavior among them in order to justify denial of the RP's services to the subscriber.
As such, IdPs and RPs are encouraged to use privacy-enhancing techniques equally across subscriber populations.

When consent dialogs and notifications are sent to users, the content of these should be tailored to different subscriber populations in order to facilitate subscriber understanding and avoid thoughtless click-through.

IdPs are required to disclose the method of proofing used for each subscriber as recorded in the subscriber account. This includes all available forms of proofing and exception processes, and possibly compensating controls, as defined in the trust agreement. IdPs and CSPs should not single out subscribers who have had to make use of exception handling or compensating controls beyond the proofing information contained in their subscriber account to avoid bias processing against certain subscriber populations.

Since federation transactions are intended to cross security domain boundaries, discrepancies between the interests of the IdP and the RP could pose additional considerations. This difference in requirements has to be addressed in the trust agreement that governs the connection between these parties, and practices such as transparent reporting can help address some forms of disparities. Furthermore, the availability of alternative IdPs (for the RP) and RPs (for the IdP) for a given service can help enhance the equity of the system overall. For example in a public-private partnership, if a private IdP is used to access a federal RP, or a federal IdP is used to access a private RP, the public and private systems could be driven by different motivations and bound by different requirements in terms of equity, accessibility, and transparency. 

Normative requirements have been established requiring IdPs and RPs to mitigate the problems in this area that are expected to be most common. However, normative requirements are unlikely to have anticipated all potential equity problems. Potential equity problems also will vary for different applications. Accordingly, IdPs and RPs need to provide mechanisms for subscribers to report inequitable authentication requirements and to advise them on potential alternative authentication strategies.

This guideline allows the binding of additional federated identifiers to an RP subscriber account to minimize the risk of IdP access loss (see [Sec. 3.7](3_federation.md#rp-account)). However, a subscriber might find it difficult to have multiple IdP accounts that are acceptable to the RP at the same time. This inequity can be addressed by having the RP having its own account recovery process that allows for the secure linking of multiple federated identifiers to the RP subscriber account.

RPs need to be aware that not all subscribers will necessarily have access to the same IdPs. The RPs can institute locally authenticated accounts for such subscribers, and later allow binding of those accounts to federated identifiers.
