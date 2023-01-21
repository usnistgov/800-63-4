---
layout: default.ja
title: Security
navOrder: 8
navTitle: Security
permalink: /sp800-63c/security/
anchor: security
section: 8
---

# Security {#security}

*This section is informative.*

<!--
Since the federated authentication process involves coordination between multiple components, including the CSP which now acts as an IdP, there are additional opportunities for attackers to compromise federated identity transactions. This section summarizes many of the attacks and mitigations applicable to federation.
-->

Federated Authentication プロセスでは, IdP として動作する CSP を含む複数のコンポーネント間の協調動作が行われるため, Attacker が Federated Identity Transaction を侵害する機会は増大する.
本章では, Federation において起こりうる Attack およびその対応策についてまとめる.

## Federation Threats

<!--
As in non-federated authentication, attackers' motivations are typically to gain access (or a greater level of access) to a resource or service provided by an RP. Attackers may also attempt to impersonate a subscriber. Rogue or compromised IdPs, RPs, user agents (e.g., browsers), and parties outside of a typical federation transaction are potential attackers. To accomplish their attack, they might intercept or modify assertions and assertion references. Further, two or more entities may attempt to subvert federation protocols by directly compromising the integrity or confidentiality of the assertion data. For the purpose of these types of threats, any authorized parties who attempt to exceed their privileges are considered attackers.
-->

Federation を用いない Authentication と同様に, Attacker のモチベーションは通常リソースや RP が提供するサービスへの Access (またはより高レベルの Access) を得ることにある.
また Attacker は Subscriber になりすまそうとする可能性もある.
不正または侵害された IdP, RP, ユーザーエージェント (e.g., ブラウザ) および典型的 Federation Transaction 外の関係者は, 潜在的に Attacker たりえる.
こういった Attack を成功させるため, Attacker は Assertion や Assertion Rerefernce を傍受または改ざんする可能性もある.
さらには, 2つ以上の主体が Federation Protocol 自体を転覆させるべく, Assertion データの Integrity および Confidentiality を侵害しようとすることもあろう.
こういったタイプの脅威を目的とする場合, その権限を超えて行動しようと試みるいかなる Authorized Party もが Attacker とみなされる.

[Table 2 Federation Threats](sec8_security.md#table-2){:name="table-2"}
{:latex-ignore="true"}

<!--
| Federation Threats/Attacks  | Description  | Examples |
|---------------------------------|------------------|--------------|
| Assertion Manufacture or Modification | The attacker generates a false assertion | Compromised IdP asserts identity of a claimant who has not properly authenticated |
| | The attacker modifies an existing assertion | Compromised proxy that changes AAL of an authentication assertion |
| Assertion Disclosure | Assertion visible to third party | Network monitoring reveals subscriber address of record to an outside party |
| Assertion Repudiation by the IdP | IdP later claims not to have signed transaction | User engages in fraudulent credit card transaction at RP, IdP claims not to have logged them in |
| Assertion Repudiation by the Subscriber | Subscriber claims not to have performed transaction | User agreement (e.g., contract) cannot be enforced |
| Assertion Redirect | Assertion can be used in unintended context | Compromised user agent passes assertion to attacker who uses it elsewhere |
| Assertion Reuse | Assertion can be used more than once with same RP | Intercepted assertion used by attacker to authenticate their own session |
| Assertion Substitution | Attacker uses an assertion intended for a different subscriber | Session hijacking attack between IdP and RP |
{:latex-table="2" latex-caption="Federation Threats" latex-columns="p@0.20\textwidth,p@0.35\textwidth,p@0.35\textwidth"}
-->

| Federation Threats/Attacks  | 説明  | 具体例 |
|---------------------------------|------------------|--------------|
| Assertion Manufacture or Modification | Attacker が Assertion を偽造する. | 侵害された IdP が, 正しく Authenticate されていない Claimant の Identity を主張する. |
| | Attacker が既存 Assertion を改ざんする. | 侵害された Proxy が Authentication Assertion の AAL を変更する. |
| Assertion Disclosure | Assertion が3rd-partyに漏洩する. | Network 監視を通じて Subscriber の登録住所が部外者に漏洩する. |
| Assertion Repudiation by the IdP | IdP が事後になって Transaction に署名していないと主張する. | ユーザーが RP において不正なクレジットカード取引を行った際, IdP が自身はユーザーをログインさせていないと主張する. |
| Assertion Repudiation by the Subscriber | Subscriber が Transaction を実行していないと主張する. | ユーザー同意 (e.g., 契約) が履行不能になる. |
| Assertion Redirect | Assertion が想定されていないコンテキストで利用される. | 侵害されたユーザーエージェントが Assertion を Attacker に送信し, Attacker がそれを別の場所で利用する. |
| Assertion Reuse | Assertion が同じ RP に対して複数回利用される. | 傍受された Assertion を利用して Attacker が自身の Session を Authenticate する. |
| Assertion Substitution | Attacker が異なる Subscriber 向けの Assertion を利用する. | IdP と RP の間で Session Hijacking Attack が成立する. |
{:latex-table="2" latex-caption="Federation Threats" latex-columns="p@0.20\textwidth,p@0.35\textwidth,p@0.35\textwidth"}


## Federation Threat Mitigation Strategies

<!--
Mechanisms that assist in mitigating the above threats are identified in [Table 3](sec8_security.md#table-3).
-->

上記の脅威に対する対策を [Table 3](sec8_security.ja.md#table-3) にまとめる.

[Table 3 Mitigating Federation Threats](sec8_security.md#table-3){:name="table-3"}
{:latex-ignore="true"}

<!--
| Federation Threat/Attack | Threat Mitigation Mechanisms | Normative Reference(s) |
|------------------------------|----------------------------------|---|
| Assertion Manufacture or Modification | Cryptographically sign the assertion at IdP and verify at RP | [4.1](sec4_fal.md#key-mgmt), [6](sec6_assertions.md#assertions) |
| | Send assertion over an authenticated protected channel authenticating the IdP | [7.1](sec7_presentation.md#back-channel), [7.2](sec7_presentation.md#front-channel) |
| | Include a non-guessable random identifier in the assertion | [6.2.1](sec6_assertions.md#assertion-id) |
| Assertion Disclosure | Send assertion over an authenticated protected channel authenticating the RP | [7.1](sec7_presentation.md#back-channel), [7.2](sec7_presentation.md#front-channel) |
| | Encrypt assertion for a specific RP (may be accomplished by use of a mutually authenticated protected channel) | [6.2.3](sec6_assertions.md#encrypted-assertion) |
| Assertion Repudiation by the IdP | Cryptographically sign the assertion at the IdP with a key that supports non-repudiation; verify signature at RP | [6.2.2](sec6_assertions.md#signed-assertion) |
| Assertion Repudiation by the Subscriber | Issue assertions with bound authenticators; proof of possession of bound authenticator verifies subscriber's participation to the RP | [6.1.2](sec6_assertions.md#boundauth) |
| Assertion Redirect | Include identity of the RP ("audience") for which the assertion is issued in its signed content; RP verifies that they are intended recipient | [6](sec6_assertions.md#assertions), [7.1](sec7_presentation.md#back-channel), [7.2](sec7_presentation.md#front-channel) |
| Assertion Reuse | Include an issuance timestamp with short validity period in the signed content of the assertion; RP verifies validity | [6](sec6_assertions.md#assertions), [7.1](sec7_presentation.md#back-channel), [7.2](sec7_presentation.md#front-channel) |
| | RP keeps track of assertions consumed within a configurable time window to ensure that a given assertion is not used more than once. | [6.2.1](sec6_assertions.md#assertion-id) |
| Assertion Substitution | Ensure that assertions contain a reference to the assertion request or some other nonce that was cryptographically bound to the request by the RP | [6](sec6_assertions.md#assertions) |
| | Send assertions in the same authenticated protected channel as the request, such as in the back-channel model |[7.1](sec7_presentation.md#back-channel)|
{:latex-table="3" latex-caption="Mitigating Federation Threats" latex-columns="p@0.20\textwidth,p@0.55\textwidth,p@0.15\textwidth"}
-->

| Federation Threat/Attack | Threat Mitigation Mechanisms | Normative Reference(s) |
|------------------------------|----------------------------------|---|
| Assertion Manufacture or Modification | IdP が暗号論的に Assertion に署名し, RP がそれを検証する. | [4.1](sec4_fal.md#key-mgmt), [6](sec6_assertions.md#assertions) |
| | Assertion の送信に IdP を Authenticate する Authenticated Protected Channel を利用する. | [7.1](sec7_presentation.md#back-channel), [7.2](sec7_presentation.md#front-channel) |
| | Assertion に推測不可能でランダムな識別子を含める. | [6.2.1](sec6_assertions.md#assertion-id) |
| Assertion Disclosure | Assertion の送信に RP を Authenticate する Authenticated Protected Channel を利用する. | [7.1](sec7_presentation.md#back-channel), [7.2](sec7_presentation.md#front-channel) |
| | Assertion を特定の RP に向けて暗号化する. (双方向の Authenticated Protected Channel を用いて達成可能) | [6.2.3](sec6_assertions.md#encrypted-assertion) |
| Assertion Repudiation by the IdP | IdP が否認防止可能な鍵を用いて暗号論的に Assertion に署名し, RP がそれを検証する. | [6.2.2](sec6_assertions.md#signed-assertion) |
| Assertion Repudiation by the Subscriber | Bound Authenticator に紐づく Assertion を発行し, Bound Authenticator の保持証明により Subscriber が RP に関与していることを検証する. | [6.1.2](sec6_assertions.md#boundauth) |
| Assertion Redirect | Assertion 発行先の RP ("Audience") の Identity を Assertion に含め, RP がそれを検証する. | [6](sec6_assertions.md#assertions), [7.1](sec7_presentation.md#back-channel), [7.2](sec7_presentation.md#front-channel) |
| Assertion Reuse | 短い有効期間と共に発行日時を Assertion の署名対象コンテンツとして含め, RP がそれを検証する. | [6](sec6_assertions.md#assertions), [7.1](sec7_presentation.md#back-channel), [7.2](sec7_presentation.md#front-channel) |
| | RP は一定の設定期間内に利用された Assertion を追跡し, 当該 Assertion が複数回り用されていないことを保証する. | [6.2.1](sec6_assertions.md#assertion-id) |
| Assertion Substitution | Assertion が Assertion 要求への参照や RP のリクエストに暗号論的に紐づけられたなんらかの Nonce を含むことを保証する. | [6](sec6_assertions.md#assertions) |
| | Assertion をリクエストと同じ Authenticated Protected Channel を介して送信する. Back Channel モデル等がこれにあたる. |[7.1](sec7_presentation.md#back-channel)|
{:latex-table="3" latex-caption="Mitigating Federation Threats" latex-columns="p@0.20\textwidth,p@0.55\textwidth,p@0.15\textwidth"}
