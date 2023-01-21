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

<!--
 Depending on the specifics of the protocol, the RP and the IdP communicate with each other in two ways, which lends to two different ways in which an assertion can be passed from the IdP to the RP:
-->

プロトコルによっては, RP と IdP が相互通信を行う方法には2つの種類が存在する.
それにより Assertion を IdP から RP に提示する方法も2つ存在することとなる.

<!--
 - The *front channel*, through redirects involving the subscriber and the subscriber's browser; or
 - The *back channel*, through a direct connection between the RP and IdP, not involving the subscriber directly.
-->

- *Front Channel* という, Subscriber および Subscriber のブラウザのリダイレクトを介したもの
- *Back Channel* という, Subscriber が直接関与することのない RP と IdP の直接通信を介したもの

<!--
There are tradeoffs with each model, but each requires the proper validation of the assertion. Assertions **MAY** also be proxied to facilitate federation between IdPs and RPs using different presentation methods, as discussed in detail in [Sec. 5.1.3](sec5_federation.md#proxied).
-->

それぞれのモデルにはトレードオフがあるが, どちらも適切な Assertion の検証を必要とする.
Assertion は, [Sec. 5.1.3](sec5_federation.ja.mdmd#proxied) で述べたように, IdP-RP 間の Federation 促進のため, 上記とはまたの提示方法を用いて Proxy されることもある (**MAY**).

## Back-Channel Presentation {#back-channel}

<!--
In the *back-channel* presentation model, the subscriber is given an assertion reference to present to the RP, generally through the front channel. The assertion reference itself contains no information about the subscriber and **SHALL** be resistant to tampering and fabrication by an attacker. The RP presents the assertion reference to the IdP, usually along with authentication of the RP itself, to fetch the assertion.
-->

*Back Channel* 提示モデルでは, Subscriber は Assertion Reference を提示され, それを RP に提示する. この際は通常 Front Channel を介して提示が行われる.
Assertion Reference 自体は Subscriber に関する情報を持たず, Attacker による改変や偽造を防止するものでなければならない (**SHALL**).
RP は Assertion Reference を IdP に提示し, 通常はその際同時に RP 自身の Authentication も行いつつ, Assertion を取得する.

[Figure 12. Back-channel Presentation](sec7_presentation.md#fig-63cSec7-Figure1){:name="fig-12"}
{:latex-ignore="true"}

![Diagram of the back-channel presentation model for communicating assertions to the RP.]({{site.baseurl}}/{{page.collection}}/media/back-channel.png 'Back-channel Presentation'){:style="width:614px;height:600px;;min-width:614px;min-height:600px;" latex-src="back-channel.png" latex-fig="12" latex-place="h"}

<!--
As shown in [Figure 12](sec7_presentation.md#fig-12), the back-channel presentation model consists of three steps:
-->

[Figure 12](sec7_presentation.ja.md#fig-12) に示す通り, Back Channel 提示モデルは3つのステップからなる.

<!--
1. The IdP sends an assertion reference to the subscriber through the front channel.
2. The subscriber sends the assertion reference to the RP through the front channel.
3. The RP presents the assertion reference and its RP credentials to the IdP through the back channel. The IdP validates the credentials and returns the assertion.
-->

1. IdP が Front Channel を介して Subscriber に Assertion Reference を送信する.
2. Subscriber が Front Channel を介して RP に Assertion Reference を送信する.
3. RP が Back Channel を介して Assertion Reference と RP 自身の Credential を IdP に提示する. IdP は当該 Credential を検証し Assertion を返却する.

<!--
The assertion reference:
-->

Assertion Reference の要件を以下に示す.

<!--
 1. **SHALL** be limited to use by a single RP.
 2. **SHALL** be single-use.
 3. **SHALL** be time limited, and **SHOULD** have a lifetime of no more than a small number of minutes in length.
 4. **SHALL** be presented along with authentication of the RP to the IdP.
 5. **SHALL** contain at least 128 bits of entropy.
-->

1. 利用できる RP を単一に制限する (**SHALL**).
2. 利用できる回数を1度きりに制限する (**SHALL**).
3. 有効期限を定め (**SHALL**), そのライフタイムは数分以内にすべきである (**SHOULD**).
4. 提示の際には IdP に対する RP の Authentication を必要とする (**SHALL**).
5. 128 bit 以上のエントロピーを持つ (**SHALL**).

~~~
\clearpage
~~~
{:latex-literal="true"}

<!--
In this model, the RP directly requests the assertion from the IdP, minimizing chances of interception and manipulation by a third party (including the subscriber themselves).
-->

このモデルでは, RP は IdP に直接 Assertion を要求する. 従って3rd-party (Subscriber 自身を含む) により傍受されたり改ざんされるリスクは最小化される.

<!--
This method also facilitates the RP querying the IdP for additional attributes about the subscriber not included in the assertion itself, since back-channel communication can continue to occur after the initial authentication transaction has been completed without sending the user back to the IdP. This query occurs using an identity API, as described in [Sec. 6.3](sec6_assertions.md#s-identity-api).
-->

この手法では, RP が IdP に対して Assertion 自体には含まれていない Subscriber の追加の Attribute を照会すること促進する.
Back Channel 通信は, 最初の Authentication Transaction が完了した後も, ユーザーを IdP に送り返すことなく継続して実施可能であることがその要因である.
この照会は [Sec. 6.3](sec6_assertions.ja.md#s-identity-api) で述べた Identity API を介して行われる.

<!--
More network transactions are required in the back-channel method, but the information is limited to only those parties that need it. Since an RP is expecting to get an assertion only from the IdP directly, the attack surface is reduced. Consequently, it is more difficult to inject assertions directly into the RP and this presentation method is recommended for FAL2 and above.
-->

Back Channel 手法ではより多くの Network Transaction が必要になるが, 情報を受け取るのはそれを必要としている主体のみに限定される.
RP は IdP から直接 Assertion を受け取ることとなるため, Attack の可能性がある箇所も削減される.
したがって, Assertion を RP に対して直接インジェクトすることはより困難になるため, この提示方法は FAL2 以上で推奨される.

<!--
The RP **SHALL** protect itself against injection of manufactured or captured assertion references by use of cross-site scripting protection or other accepted techniques.
-->

RP は, Cross-site Scripting 対策やその他の一般的防御策を用いて, Assertion Reference のインジェクションや偽造, 傍受からの防御策を施さねばならない (**SHALL**).

<!--
Conveyance of the assertion reference from the IdP to the subscriber, as well as from the subscriber to the RP, **SHALL** be made over an authenticated protected channel. Conveyance of the assertion reference from the RP to the IdP, as well as the assertion from the IdP to the RP, **SHALL** be made over an authenticated protected channel.
-->

IdP から Subscriber への Assertion Reference の送信は, Subscriber から RP への Assertion Reference の送信と同様に, Authenticated Protected Channel を介して行わねばならない (**SHALL**).
RP から IdP への Assertion Reference の送信も, IdP から RP への Assertion の送信と同様に, Authenticated Protected Channel を介して行わねばならない (**SHALL**).

<!--
When assertion references are presented, the IdP **SHALL** verify that the party presenting the assertion reference is the same party that requested the authentication. The IdP can do this by requiring the RP to authenticate itself when presenting the assertion reference to the IdP or through other similar means (see [[RFC7636]](references.md#ref-RFC7636) for one protocol's method of dynamic RP verification).
-->

Assertion Reference を提示する際, IdP は Assertion Reference を提示する相手が Authentication を要求している相手と同一であることを検証せねばならない (**SHALL**).
IdP は, RP が IdP に Assertion Reference を提示際に Authentication を要求したり, その他の類似手段 (あるプロトコルにおける動的 RP 検証方法については [[RFC7636]](references.ja.md#ref-RFC7636) を参照) によりこれを実現できる.

<!--
Note that in a federation proxy described in [Sec. 5.1.3](sec5_federation.md#proxied), the IdP audience restricts the assertion reference and assertion to the proxy, and the proxy restricts any newly-created assertion references or assertions to the downstream RP.
-->

[Sec. 5.1.3](sec5_federation.ja.md#proxied) の Federation Proxy においては, IdP は Assertion Reference および Assertion に関して Proxy を相手とした Audience Restriction を施し, Proxy が新たに生成した Assertion Reference および Assertion に関して下流の RP を相手とした Audience Restriction を施すことに注意.

~~~
\clearpage
~~~
{:latex-literal="true"}

## Front-Channel Presentation {#front-channel}

<!--
In the *front-channel* presentation model, the IdP creates an assertion and sends it to the subscriber after successful authentication. The assertion is presented by the subscriber to authenticate to the RP, usually through mechanisms within the subscriber's browser such as redirects.
-->

*Front Channel* 提示モデルでは, IdP は Subscriber の Authentication 成功後に Assertion を生成しそれを Subscriber に送信する.
Subscriber は RP に対して Authentication を行うため当該 Assertion を提示する.
これは通常 Subscriber のブラウザ内でリダイレクト等のメカニズムを介して行われる.

[Figure 13. Front-channel Presentation](sec7_presentation.ja.md#fig-13){:name="fig-13"}
{:latex-ignore="true"}

![Diagram of the front-channel presentation model for communicating assertions to the RP.]({{site.baseurl}}/{{page.collection}}/media/front-channel.png 'Front-channel Presentation'){:style="width:686px;height:600px;;min-width:686px;min-height:600px;" latex-src="front-channel.png" latex-fig="13" latex-place="h"}

<!--
An assertion is visible to the subscriber in the front-channel method, which could potentially cause leakage of system information included in the assertion. Further, it is possible but more awkward in this model for the RP to query the IdP for additional attributes after the presentation of the assertion using an identity API, as described in [Sec. 6.3](sec6_assertions.md#s-identity-api).
-->

Front Channel 手法では, Assertion は Subscriber により閲覧可能である.
よって Assertion に含まれるシステム情報は潜在的に漏洩しうる.
さらにこのモデルでは, [Sec. 6.3](sec6_assertions.ja.md#s-identity-api) で述べたように, RP が IdP に Assertion 提示後に Identity API を通じて追加の Attribute を照会することも, 可能ではあるがよりやりにくくなる.

<!--
Since the assertion is under the subscriber's control, the front-channel presentation method also allows the subscriber to submit a single assertion to unintended parties, perhaps by a browser replaying an assertion at multiple RPs. Even if the assertion is audience-restricted and rejected by unintended RPs, its presentation at unintended RPs could lead to leaking information about the subscriber and their online activities. Though it is possible to intentionally create an assertion designed to be presented to multiple RPs, this method can lead to lax audience restriction of the assertion itself, which in turn could lead to privacy and security breaches for the subscriber across these RPs. Such multi-RP use is not recommended. Instead, RPs are encouraged to fetch their own individual assertions.
-->

Assertion は Subscriber の管理下に置かれるため, Front Channel 提示手法では Subscriber が単一の Assertion を期待されていない相手に送りつけることも可能となる. これはおそらくブラウザを介して複数の RP に当該 Assetion を Replay することで行われるであろう.
たとえ Assertion が Audience Restriction により保護されており期待されない RP から拒絶されるとしても, 期待されない RP に提示されるということそのものが, Subscriber に関する情報および Subscriber のオンラインアクティビティの漏洩に繋がる可能性がある.
複数の RP に提示されることを意図して Assertion を生成することも可能であるが, この方法では Assertion 自体の Audience Restriction を緩めることにつながりかねず, 対象 RP 間で Subscriber のプライバシーおよびセキュリティ侵害に繋がる可能性もある.
このような複数 RP での利用は推奨されず, 代わりに RP は個々に独自の Assertion を取得することが推奨される.

<!--
The RP **SHALL** protect itself against injection of manufactured or captured assertions by use of cross-site scripting protection and other accepted techniques.
-->

RP は, Cross-site Scripting 対策やその他の一般的防御策を用いて, Assertion のインジェクションや偽造, 傍受からの防御策を施さねばならない (**SHALL**).

<!--
Conveyance of the assertion from the IdP to the subscriber, as well as from the subscriber to the RP, **SHALL** be made over an authenticated protected channel.
-->

IdP から Subscriber への Assertion の送信は, Subscriber から RP への Assertion の送信と同様に, Authenticated Protected Channel を介して行わねばならない (**SHALL**).

<!--
Note that in a federation proxy described in [Sec. 5.1.3](sec5_federation.md#proxied), the IdP audience restricts the assertion to the proxy, and the proxy restricts any newly-created assertions to the downstream RP.
-->

[Sec. 5.1.3](sec5_federation.ja.md#proxied) の Federation Proxy においては, IdP は Assertion に関して Proxy を相手とした Audience Restriction を施し, Proxy が新たに生成した Assertion に関して下流の RP を相手とした Audience Restriction を施すことに注意.

## Protecting Information {#protecting-information}

<!--
Communications between the IdP and the RP **SHALL** be protected in transit using an authenticated protected channel. Communications between the subscriber and either the IdP or the RP (usually through a browser) **SHALL** be made using an authenticated protected channel.
-->

IdP と RP の間の通信は, Authenticated Protected Channel を使用して転送中に保護しなければならない (**SHALL**).
Subscriber と IdP ないし RP の間の通信 (通常はブラウザを介して行われる) もまた, Authenticated Protected Channel を用いて実施せねばならない (**SHALL**).

<!--
Note that the IdP may have access to information that may be useful to the RP in enforcing security policies, such as device identity, location, system health checks, and configuration management. If so, it may be a good idea to pass this information along to the RP within the bounds of the subscriber's privacy preferences described in [Sec. 9.2](sec9_privacy.md#notice).
-->

IdP は RP がセキュリティポリシー適用に際して役立てることができる情報への Access を持っていることもありえる.
これには Device Identity 情報, 位置情報, システムのヘルスチェック情報, 構成管理情報などが含まれる.
こういう情報を持っている場合, [Sec. 9.2](sec9_privacy.ja.md#notice) に述べるように, Subscriber のプライバシー設定の範囲内でそれらを RP に送信することは良いアイデアであろう.

<!--
Additional attributes about the user **MAY** be included outside of the assertion itself by use of authorized access to an identity API as discussed in [Sec. 6.3](sec6_assertions.md#s-identity-api). Splitting user information in this manner can aid in protecting user privacy and allow for limited disclosure of identifying attributes on top of the essential information in the authentication assertion itself.
-->

[Sec. 6.3](sec6_assertions.ja.md#s-identity-api) で述べたように, ユーザーに関する追加の Attribute を Assertion 外で Identity API への認可された Access を用いて提供することもできる (**MAY**).
このようにユーザー情報を分離することで, ユーザーのプライバシーを保護し, Authentication Assertion 自体に必須情報を含めた上で, 識別可能な Attribute の開示を最小化することもできる.

<!--
The RP **SHALL**, where feasible, request derived attribute values rather than full attribute values as described in [Sec. 9.3](sec9_privacy.md#minimization). The IdP **SHALL** support derived attribute values to the extent possible.
-->

RP は, [Sec. 9.3](sec9_privacy.ja.md#minimization) にあるように, 可能な限り完全な Attribute Value より Derived Attribute Value を要求しなければならない (**SHALL**).
IdP は Derived Attribute Value を可能な限りサポートしなければならない (**SHALL**).
