---
layout: default.ja
title: Introduction
navOrder: 2
navTitle: Introduction
permalink: /sp800-63c/introduction/
anchor: introduction
section: 2
---

# Introduction {#introduction}

*This section is informative.*

<!--
Federation is a process that allows for the conveyance of authentication attributes and subscriber attributes across networked systems. In a federation scenario, the CSP provides a service known as an identity provider, or IdP. The IdP acts as a verifier for authenticators issued by the CSP. The IdP sends a message, called an assertion, about this authentication event to the RP. The RP receives the assertion provided by the IdP and uses it for authentication and authorization decisions, but the RP does not verify the authenticator directly.
-->

Federation とは, Authentication イベントに関する Attribute および Subscriber に関する Attribute を Network 化されたシステム間で伝播することを可能とするプロセスである.
Federation シナリオでは, CSP は Identity Provider (IdP) と呼ばれるサービスを提供する.
IdP は CSP が発行する Authenticator に対する Verifier となる.
IdP は Assertion と呼ばれる Authentication イベントに関するメッセージを RP に送信する.
RP は IdP に提示された Assertion を受け取り自身の Authentication および Authorization の決定に用いるが, RP 自身が Authenticator を直接 Verify することはない.

<!--
Assertions are verifiable statements from an IdP to an RP that represent an authentication event for a subscriber. Federation is generally used when the RP and the IdP are not a single entity or are not under common administration, though federation can be applied within a single security domain for a variety of reasons. The RP uses the information in the assertion to identify the subscriber and make authorization decisions about their access to resources controlled by the RP.
-->

Assertion は IdP から RP に対して提示される Verify 可能なステートメントであり, Subscriber に対する Authentication イベントを表現している.
一般的に Federation は RP と IdP が単一主体ではなく, 共通の主体の管理下にあるものでもない場合に用いられるが, さまざまな理由により同一セキュリティドメイン下のサービスに対して適用されることもある.
RP は Assertion に含まれる情報を用いて Subscriber を識別し, RP の管理下にあるリソースへの当該 Subscriber の Access に対する Authorization 判断を下す.

In a federated identity scenario, the subscriber does not authenticate directly to the RP. Instead, the federation protocol defines a mechanism for an IdP to generate an assertion associated with a subscriber, generally in response to an explicit request from the RP. The IdP is responsible for authenticating the subscriber (though it may use session management as described in [[SP800-63B]](../_sp800-63b/sec7_session.md#sec7){:latex-href="#ref-SP800-63B"}, Sec. 7). The federation process allows the subscriber to obtain services from multiple RPs without the need to hold or maintain separate authenticators at each RP, a process sometimes known as *single sign-on*.

The subscriber is uniquely identified to the RP by a *federated identifier*, which is a logical combination of the *subject identifier* as asserted by the IdP as well as a unique identifier for the IdP itself. This multi-part identifier pattern is required because different IdPs manage their subject identifiers independently, and could therefore potentially collide in their choices of subject identifiers for different subjects. Therefore, it is imperative that an RP never process the subject identifier without taking into account which IdP issued that subject identifier.

An assertion includes a federated identifier for the subscriber, allowing association of the subscriber with their interactions with the RP over multiple authenticated sessions. Assertions may also include attribute values or derived attribute values that further characterize the subscriber and support authorization decisions at the RP. Additional attributes may also be available outside of the assertion as part of the larger federation protocol. These attribute values and derived attribute values are often used in determining access privileges for attribute-based access control (ABAC) or facilitating a transaction (e.g., providing a shipping address).

Federation requires relatively complex multiparty protocols that have subtle security and privacy requirements. When evaluating a particular federation structure, it may be instructive to break it down into its component interactions: the subscriber to the IdP, the IdP to the RP, and the subscriber to the RP. Each party in a federation protocol bears specific responsibilities and expectations that must be fulfilled in order for the federated system to function as intended.

The IdP maintains a record for the subscriber that augments the _subscriber account_ defined in [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"} with a set of federation-specific items, including but not limited to the following:

- One or more external subject identifiers, for use with a federation protocol
- A set of access rights, detailing which RPs can access which attributes of the subscriber account (such as runtime decisions by the subscriber)
- Federated account usage information
- Additional attributes collected or assigned by the IdP to the subscriber

The RP often maintains an *RP subscriber account* for the subscriber, which is derived from the augmented subscriber account information disclosed to the RP by the IdP. The RP subscriber account also contains information local to the RP itself, as described in [Sec. 5.4](../sec5_federation.md#rp-account).

The requirements in this document build on the requirements in the other volumes of these guidelines. Authentication between the subscriber and the IdP will be based on the authentication mechanisms presented in [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}, while the federation protocol will convey attributes to the RP established at the IdP using procedures in [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"} (along with other attributes).

The following table states which sections of the document are normative and which are informative:

- 1 Purpose _Informative_
- 2 Introduction _Informative_
- 3 Definitions and Abbreviations _Informative_
- 4 Federation Assurance Level (FAL)  _Normative_
- 5 Federation  _Normative_
- 6 Assertion  _Normative_
- 7 Assertion Presentation  _Normative_
- 8 Security _Informative_
- 9 Privacy Considerations _Informative_
- 10 Usability Considerations _Informative_
- 11 Equity Considerations _Informative_
- 12 Examples _Informative_
- References _Informative_
