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

<!--
In a federated identity scenario, the subscriber does not authenticate directly to the RP. Instead, the federation protocol defines a mechanism for an IdP to generate an assertion associated with a subscriber, generally in response to an explicit request from the RP. The IdP is responsible for authenticating the subscriber (though it may use session management as described in [[SP800-63B]](../_sp800-63b/sec7_session.md#sec7){:latex-href="#ref-SP800-63B"}, Sec. 7). The federation process allows the subscriber to obtain services from multiple RPs without the need to hold or maintain separate authenticators at each RP, a process sometimes known as *single sign-on*.
-->

Federated Identity シナリオにおいて, Subscriber は直接 RP に対して Authenticate を行うことはない.
Federated Protocol が提供するメカニズムによって, IdP は Subscriber に関する Assertion を生成する. これは一般的には RP からの明示的なリクエストに応答する形で行われる.
IdP は Subscriber を Authenticate する責務を担う. (ただし [[SP800-63B]](../_sp800-63b/sec7_session.ja.md#sec7) {:latex-href="#ref-SP800-63B"}, Sec. 7 にあるように Session Management を用いることもある)
Federation プロセスによって, Subscriber は複数の RP に対してそれぞれ独立した Authenticator を管理することなく各 RP のサービスを享受することができる. このプロセスは *Single Sign-on* と呼ばれることもある.

<!--
The subscriber is uniquely identified to the RP by a *federated identifier*, which is a logical combination of the *subject identifier* as asserted by the IdP as well as a unique identifier for the IdP itself. This multi-part identifier pattern is required because different IdPs manage their subject identifiers independently, and could therefore potentially collide in their choices of subject identifiers for different subjects. Therefore, it is imperative that an RP never process the subject identifier without taking into account which IdP issued that subject identifier.
-->

Subscriber は *Federated Identifier* により RP に対して一意に識別される. *Federated Identifier* とは, IdP によって提示される *Subject Identifier* と, IdP 自身を一意に識別する識別子の論理的組み合わせとして表現される.
この複数要素からなる識別子の表現方法により, 異なる IdP 間において各 IdP が各々の Subject Identifier を独立して管理可能となる. このような条件下では異なる Subject に対して Subject Identifier が衝突するリスクが存在するため, このような識別子表現が必要不可欠となる.
RP は Subject Identifier を発行した IdP を考慮することなく Subject Identifier に対して処理を行ってはならない.

<!--
An assertion includes a federated identifier for the subscriber, allowing association of the subscriber with their interactions with the RP over multiple authenticated sessions. Assertions may also include attribute values or derived attribute values that further characterize the subscriber and support authorization decisions at the RP. Additional attributes may also be available outside of the assertion as part of the larger federation protocol. These attribute values and derived attribute values are often used in determining access privileges for attribute-based access control (ABAC) or facilitating a transaction (e.g., providing a shipping address).
-->

Assertion とは, Subscriber の Federated Identifier を含み, 複数の Authenticated Session にまたがって RP とインタラクションを行った Subscriber を紐づけることを可能とするものである.
Assertion には Attribute Value や Derived Attribute Value が含まれることもあり, それらは Subscriber の更なる特徴を示して RP による Authorization 判断の材料となる.
追加の Attribute はより大きな Federation Protocol の一部として Assertion 外で提供されることもある.
これらの Attribute Value や Derived Attribute Value はしばしば Attribute-based Access Control (ABAC) における Access 権限の決定やトランザクション (e.g., 配送先住所の提供) を促進するために用いられる.

<!--
Federation requires relatively complex multiparty protocols that have subtle security and privacy requirements. When evaluating a particular federation structure, it may be instructive to break it down into its component interactions: the subscriber to the IdP, the IdP to the RP, and the subscriber to the RP. Each party in a federation protocol bears specific responsibilities and expectations that must be fulfilled in order for the federated system to function as intended.
-->

Federation は比較的複雑なマルチパーティープロトコルが必要となり, それには繊細なセキュリティおよびプライバシー要件が求められる.
ある特定の Federation 構造を評価する際には, それを個々のインタラクション (Subscriber->IdP, IdP->RP, Subscriber->RP etc.) に分解するとよい.
Federation Protocol における各々のパーティーは特定の責任と期待を負い, それらを満たすことで Federated System が期待通りに機能することとなる.

<!--
The IdP maintains a record for the subscriber that augments the _subscriber account_ defined in [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"} with a set of federation-specific items, including but not limited to the following:
-->

IdP は [[SP800-63A]](../_sp800-63a/sec1_purpose.ja.md#purpose){:latex-href="#ref-SP800-63A"} に定義された _Subscriber Account_ を補強する形で Federation 特有の項目をセットにして Subscriber に関するレコードを管理する. この Federation 特有の項目には以下のようなものが含まれるがこの限りではない.

<!--
- One or more external subject identifiers, for use with a federation protocol
- A set of access rights, detailing which RPs can access which attributes of the subscriber account (such as runtime decisions by the subscriber)
- Federated account usage information
- Additional attributes collected or assigned by the IdP to the subscriber
-->

- Federation Protocol で用いられる1つ以上の External Subject Identifier
- Access 権限のセット. (Subscriber の決定などにより) どの RP が当該 Subscriber Account のどの Attribute に Access できるかを示す.
- Federated アカウントの利用情報
- IdP が Subscriber に対して収集及び付与した追加の Attribute

<!--
The RP often maintains an *RP subscriber account* for the subscriber, which is derived from the augmented subscriber account information disclosed to the RP by the IdP. The RP subscriber account also contains information local to the RP itself, as described in [Sec. 5.4](../sec5_federation.md#rp-account).
-->

RP はしばしば *RP Subscriber Account* を管理する. これは IdP から RP に対して提示された Subscriber Account 情報から導出されたものである.
RP Subscriber Account は RP 自身に閉じた情報も含む. ([Sec. 5.4](../sec5_federation.ja.md#rp-account) 参照)

<!--
The requirements in this document build on the requirements in the other volumes of these guidelines. Authentication between the subscriber and the IdP will be based on the authentication mechanisms presented in [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}, while the federation protocol will convey attributes to the RP established at the IdP using procedures in [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"} (along with other attributes).
-->

本ドキュメントに記載された要件は, 本ガイドラインの他のドキュメントに述べられた要件に基づいたものである.
Subscriber と IdP の間の Authentication は　[[SP800-63B]](../_sp800-63b/sec1_purpose.ja.md#purpose){:latex-href="#ref-SP800-63B"} に記載された Authentication メカニズムに基づいて実施され, Federation Protocol によって RP に伝達される Attribute そのものは (その他の Attribute と共に) [[SP800-63A]](../_sp800-63a/sec1_purpose.ja.md#purpose){:latex-href="#ref-SP800-63A"} に記載された手続きを用いて IdP によって確立される.

<!--
The following table states which sections of the document are normative and which are informative:
-->

本ドキュメンントの各セクションのいずれが normative でありいずれが informative であるかを以下に示す.

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
