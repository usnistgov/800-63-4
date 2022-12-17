---
layout: default.ja
title: Assertion Presentation
navOrder: 7
navTitle: Presentation
permalink: /sp800-63c/presentation/
anchor: presentation
section: 7
---

# Assertion Presentation {#presentation}

*This section is normative.*

 Depending on the specifics of the protocol, the RP and the IdP communicate with each other in two ways, which lends to two different ways in which an assertion can be passed from the IdP to the RP:

 - The *front channel*, through redirects involving the subscriber and the subscriber's browser; or
 - The *back channel*, through a direct connection between the RP and IdP, not involving the subscriber directly.

There are tradeoffs with each model, but each requires the proper validation of the assertion. Assertions **MAY** also be proxied to facilitate federation between IdPs and RPs using different presentation methods, as discussed in detail in [Sec. 5.1.3](sec5_federation.md#proxied).

## Back-Channel Presentation {#back-channel}

In the *back-channel* presentation model, the subscriber is given an assertion reference to present to the RP, generally through the front channel. The assertion reference itself contains no information about the subscriber and **SHALL** be resistant to tampering and fabrication by an attacker. The RP presents the assertion reference to the IdP, usually along with authentication of the RP itself, to fetch the assertion.

[Figure 12. Back-channel Presentation](sec7_presentation.md#fig-63cSec7-Figure1){:name="fig-12"}
{:latex-ignore="true"}

![Diagram of the back-channel presentation model for communicating assertions to the RP.]({{site.baseurl}}/{{page.collection}}/media/back-channel.png 'Back-channel Presentation'){:style="width:614px;height:600px;;min-width:614px;min-height:600px;" latex-src="back-channel.png" latex-fig="12" latex-place="h"}

As shown in [Figure 12](sec7_presentation.md#fig-12), the back-channel presentation model consists of three steps:

1. The IdP sends an assertion reference to the subscriber through the front channel.
2. The subscriber sends the assertion reference to the RP through the front channel.
3. The RP presents the assertion reference and its RP credentials to the IdP through the back channel. The IdP validates the credentials and returns the assertion.

The assertion reference:

 1. **SHALL** be limited to use by a single RP.
 2. **SHALL** be single-use.
 3. **SHALL** be time limited, and **SHOULD** have a lifetime of no more than a small number of minutes in length.
 4. **SHALL** be presented along with authentication of the RP to the IdP.
 5. **SHALL** contain at least 128 bits of entropy.

~~~
\clearpage
~~~
{:latex-literal="true"}

In this model, the RP directly requests the assertion from the IdP, minimizing chances of interception and manipulation by a third party (including the subscriber themselves).

This method also facilitates the RP querying the IdP for additional attributes about the subscriber not included in the assertion itself, since back-channel communication can continue to occur after the initial authentication transaction has been completed without sending the user back to the IdP. This query occurs using an identity API, as described in [Sec. 6.3](sec6_assertions.md#s-identity-api).

More network transactions are required in the back-channel method, but the information is limited to only those parties that need it. Since an RP is expecting to get an assertion only from the IdP directly, the attack surface is reduced. Consequently, it is more difficult to inject assertions directly into the RP and this presentation method is recommended for FAL2 and above.

The RP **SHALL** protect itself against injection of manufactured or captured assertion references by use of cross-site scripting protection or other accepted techniques.

Conveyance of the assertion reference from the IdP to the subscriber, as well as from the subscriber to the RP, **SHALL** be made over an authenticated protected channel. Conveyance of the assertion reference from the RP to the IdP, as well as the assertion from the IdP to the RP, **SHALL** be made over an authenticated protected channel.

When assertion references are presented, the IdP **SHALL** verify that the party presenting the assertion reference is the same party that requested the authentication. The IdP can do this by requiring the RP to authenticate itself when presenting the assertion reference to the IdP or through other similar means (see [[RFC7636]](references.md#ref-RFC7636) for one protocol's method of dynamic RP verification).

Note that in a federation proxy described in [Sec. 5.1.3](sec5_federation.md#proxied), the IdP audience restricts the assertion reference and assertion to the proxy, and the proxy restricts any newly-created assertion references or assertions to the downstream RP.

~~~
\clearpage
~~~
{:latex-literal="true"}

## Front-Channel Presentation {#front-channel}

In the *front-channel* presentation model, the IdP creates an assertion and sends it to the subscriber after successful authentication. The assertion is presented by the subscriber to authenticate to the RP, usually through mechanisms within the subscriber's browser such as redirects.

[Figure 13. Front-channel Presentation](sec7_presentation.md#fig-13){:name="fig-13"}
{:latex-ignore="true"}

![Diagram of the front-channel presentation model for communicating assertions to the RP.]({{site.baseurl}}/{{page.collection}}/media/front-channel.png 'Front-channel Presentation'){:style="width:686px;height:600px;;min-width:686px;min-height:600px;" latex-src="front-channel.png" latex-fig="13" latex-place="h"}

An assertion is visible to the subscriber in the front-channel method, which could potentially cause leakage of system information included in the assertion. Further, it is possible but more awkward in this model for the RP to query the IdP for additional attributes after the presentation of the assertion using an identity API, as described in [Sec. 6.3](sec6_assertions.md#s-identity-api).

Since the assertion is under the subscriber's control, the front-channel presentation method also allows the subscriber to submit a single assertion to unintended parties, perhaps by a browser replaying an assertion at multiple RPs. Even if the assertion is audience-restricted and rejected by unintended RPs, its presentation at unintended RPs could lead to leaking information about the subscriber and their online activities. Though it is possible to intentionally create an assertion designed to be presented to multiple RPs, this method can lead to lax audience restriction of the assertion itself, which in turn could lead to privacy and security breaches for the subscriber across these RPs. Such multi-RP use is not recommended. Instead, RPs are encouraged to fetch their own individual assertions.

The RP **SHALL** protect itself against injection of manufactured or captured assertions by use of cross-site scripting protection and other accepted techniques.

Conveyance of the assertion from the IdP to the subscriber, as well as from the subscriber to the RP, **SHALL** be made over an authenticated protected channel.

Note that in a federation proxy described in [Sec. 5.1.3](sec5_federation.md#proxied), the IdP audience restricts the assertion to the proxy, and the proxy restricts any newly-created assertions to the downstream RP.

## Protecting Information {#protecting-information}

Communications between the IdP and the RP **SHALL** be protected in transit using an authenticated protected channel. Communications between the subscriber and either the IdP or the RP (usually through a browser) **SHALL** be made using an authenticated protected channel.

Note that the IdP may have access to information that may be useful to the RP in enforcing security policies, such as device identity, location, system health checks, and configuration management. If so, it may be a good idea to pass this information along to the RP within the bounds of the subscriber's privacy preferences described in [Sec. 9.2](sec9_privacy.md#notice).

Additional attributes about the user **MAY** be included outside of the assertion itself by use of authorized access to an identity API as discussed in [Sec. 6.3](sec6_assertions.md#s-identity-api). Splitting user information in this manner can aid in protecting user privacy and allow for limited disclosure of identifying attributes on top of the essential information in the authentication assertion itself.

The RP **SHALL**, where feasible, request derived attribute values rather than full attribute values as described in [Sec. 9.3](sec9_privacy.md#minimization). The IdP **SHALL** support derived attribute values to the extent possible.
