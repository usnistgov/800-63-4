---
layout: default.ja
title: Assertions
navOrder: 6
navTitle: Assertions
permalink: /sp800-63c/assertions/
anchor: assertions
section: 6
---

# Assertions {#assertions}

*This section is normative.*

<!--
An assertion used for authentication is a packaged set of attribute values or derived attribute values about or associated with an authenticated subscriber that is passed from the IdP to the RP in a federated identity system. Assertions contain a variety of information, including: assertion metadata, attribute values and derived attribute values about the subscriber, information about the subscriber's authentication at the IdP, and other information that the RP can leverage (e.g., restrictions and validity time window). While the assertion's primary function is to authenticate the user to an RP, the information conveyed in the assertion can be used by the RP for a number of use cases &mdash; for example, authorization or personalization of a website. These guidelines do not restrict RP use cases nor the type of protocol or data payload used to federate an identity, provided the chosen solution meets all mandatory requirements contained herein.
-->

Authentication に用いられる Assertion は, Authentication 対象の Subscriber に関する Attribute Value ないしは Derived Attribute Value のパッケージ化されたセットであり, Federated Identity システムにおいて IdP から RP に伝搬されるものである.
Assertion Metadata, Subscriber の Attribute Value ないしは Derived Attribute Value, IdP における Subscriber の Authentication に関する情報, および RP が活用可能なその他の情報など, Assertion は多様な情報を含んでいる.
Assertion の第一の機能は RP に対してユーザーを Authenticate することだが, Assertion によって伝達される情報は RP がもつ多くのユースケースにおいて利用可能である.
例としては, Authorization や Web サイトのパーソナライゼーションなどが挙げられる.
本ガイドライン群は, ここに指定する必須要件を全て満たしている限り, Identity Federation における RP のユースケースや Protocol やデータペイロードのタイプを制限しない.

<!--
Assertions **SHALL** represent a discrete authentication event of the subscriber at the IdP and **SHALL** be processed as a discrete authentication event at the RP.
-->

Assertion は IdP における Subscriber の個別の Authentication イベントを表現するものとし (**SHALL**), RP はそれを個別の Authentication イベントとして処理するものとする (**SHALL**).

<!--
All assertions **SHALL** include the following attributes:
-->

全ての Assertion には以下の Attribute を含めるものとする (**SHALL**).

<!--
1. Subject identifier: An identifier for the party to which the assertion applies (i.e., the subscriber).
2. Issuer identifier: An identifier for the issuer of the assertion (i.e., the IdP).
3. Audience identifier: An identifier for the party intended to consume the assertion (i.e., the RP).
4. Issuance time: A timestamp indicating when the IdP issued the assertion.
5. Validity time window: A period of time outside of which the assertion **SHALL NOT** be accepted as valid by the RP for the purposes of authenticating the subscriber and starting an authenticated session at the RP. This is usually communicated by means of an expiration timestamp for the assertion in addition to the issuance timestamp.
6. Assertion identifier: A value uniquely identifying this assertion, used to prevent attackers from replaying prior assertions.
7. Signature: Digital signature or message authentication code (MAC), including key identifier or public key associated with the IdP, covering the entire assertion.
8. Authentication time: A timestamp indicating when the IdP last verified the presence of the subscriber at the IdP through a primary authentication event (if available).
9. IAL: Indicator of the IAL of the subscriber account being represented in the assertion, or an indication that no IAL is asserted.
10. AAL: Indicator of the AAL used when the subscriber authenticated to the IdP, or an indication that no AAL is asserted.
11. FAL: An indicator of the IdP's intended FAL of the federation process represented by the assertion.
-->

1. Subject Identifier: Assertion が指し示す当事者 (i.e., Subscriber) の識別子
2. Issuer Identifier: Assertion 発行者 (i.e., IdP) の識別子
3. Audience Identifier: Assertion を利用することが想定された当事者 (i.e., RP) の識別子
4. Issuance Time: IdP が Assertion を発行した時刻を示すタイムスタンプ
5. Validity Time Window: その期間を超えて RP が Subscriber を Authentication する目的で Assertion を有効なものとして受け入れることのない (**SHALL NOT**) よう示す期間. これは通常 Assertion の有効期限タイムスタンプという形で Issuance タイムスタンプとともに伝えられる.
6. Assertion Identifier: 当該 Assertion を一意に識別する値で, 攻撃者が以前の Assertion を Replay することを防止する目的で利用される.
7. Signature: Digital Signature ないしは Message Authentication Code (MAC). IdP に紐づいた鍵の識別子や Public Key を含み, Assertion 全体をカバーするもの.
8. Authentication Time: IdP が最後に (可能であれば) 直接 Authentication イベントを通じて Subscriber の存在確認を行った時刻を示すタイムスタンプ.
9. IAL: Assertion が指し示す Subscriber Account の IAL を示す値, ないしはいかなる IAL も明言されないことを示す値.
10. AAL: IdP が Subscriber を Authenticate した際の AAL を示す値, ないしはいかなる AAL も明言されないことを示す値.
11. FAL: Assertion が指し示す Federation プロセスにおいて IdP が意図する FAL を示す値.

<!--
If the assertion is used at FAL3 with a bound authenticator as described in [Sec. 6.1.2](sec6_assertions.md#boundauth), the assertion **SHALL** include the following:
-->

[Sec. 6.1.2](sec6_assertions.ja.md#boundauth) に後述のように Assertion が FAL3 で Bound Authenticator とともに用いられる場合, Assertion は以下を含むものとする (**SHALL**).

<!--
1. Authenticator binding: The public key, key identifier, or other identifier of subscriber-held bound authenticator (for IdP-managed bound authenticators) or indicator that an RP-managed bound authenticator is required for verification of this assertion.
-->

1. Authenticator Binding: Public Key, 鍵の識別子, その他の Subscriber が保持する Bound Authenticator (IdP が管理するもの) の識別子, ないしは RP が管理する Bound Authenticator が Assertion 検証に要求されることを示す値.

<!--
Assertions **MAY** also include additional items, including the following information:
-->

Assertion は以下に示すような追加の項目を含んでもよい (**MAY**).

<!--
1. Attribute values and derived attribute values: Information about the subscriber.
2. Attribute metadata: Additional information about one or more subscriber attributes, such as those described in NIST Internal Report 8112 [[NISTIR8112]](references.md#ref-nistir8112).
-->

1. Attribute Value および Derived Attribute Value: Subscriber に関する情報.
2. Attribute Metadata: Subscriber Attribute に関する1つ以上の追加情報. NIST Internal Report 8112 [[NISTIR8112]](references.ja.md#ref-nistir8112) 例示あり.

<!--
Assertions **SHOULD** specify the AAL when an authentication event is being asserted and IAL when identity proofed attributes (or values derived from those attributes) are being asserted.
-->

Assertion は, Authentication Event を示す場合は AAL を, Identity Proofing を経た Attribute を示す場合は IAL を指定すべきである (**SHOULD**).

<!--
All metadata within the assertion **SHALL** be validated by the RP upon receipt:
-->

RP は Assertion を受け取ったらそこに含まれる全てのメタデータを検証すること (**SHALL**).

<!--
- *Issuer verification*: ensuring the assertion was issued by the IdP the RP expects it to be from.
- *Signature validation*: ensuring the signature of the assertion is valid and corresponds to a key belonging to the IdP sending the assertion.
- *Time validation*: ensuring the expiration and issue times are within acceptable limits of the current timestamp.
- *Audience restriction*: ensuring this RP is the intended recipient of the assertion.
-->

- *Issuer Verification*: Assertion が RP の期待する IdP により発行されたものであることを保証すること.
- *Signature Verification*: Assertion の署名が有効かつ Assertion を送信した IdP の鍵によるものであることを保証すること.
- *Time Validation*: 現在時刻と照らし合わせて有効期限と発行日時が許容範囲に収まっていることを保証すること.
- *Audience Restriction*: Assertion の受け取り先として当該 RP が意図されていることを保証すること.

<!--
An RP **SHALL** treat subject identifiers as not inherently globally unique. Instead, the value of the assertion's subject identifier is usually in a namespace under the assertion issuer's control. This allows an RP to talk to multiple IdPs without incorrectly conflating subjects from different IdPs.
-->

RP は Subject Identifier を本質的にグローバルにユニークではないものとして扱うこと (**SHALL**).
Assertion 内の Subject Identifier は通常 Assertion 発行者の管理下にあるネームスペース内の値である.
これにより, RP は異なる IdP から受け取った Subject を誤って混同することなく複数の IdP と対話可能になる.

<!--
Assertions **MAY** include additional attributes about the subscriber. [Section 6.2.3](sec6_assertions.md#encrypted-assertion) contains privacy requirements for presenting attributes in assertions. The RP **MAY** be given limited access to an identity API as discussed in [Sec. 6.3](#s-identity-api) along with the assertion, which the RP can use to fetch additional identity attributes for the subscriber.
-->

Assertion は Subscriber のその他の Attribute を含んでもよい (**MAY**).
Assertion に含めて Attribute を提示するためのプライバシー要件については [Section 6.2.3](sec6_assertions.ja.md#encrypted-assertion) で述べる.
RP には Assertion に加えて [Sec. 6.3](#s-identity-api) で述べた Identity API への限定的 Access が与えられることもあり (**MAY**), RP はこの API を利用して Subscriber に関する追加の Identity Attribute を取得可能となる.

<!--
Although details vary based on the exact federation protocol in use, an assertion represents a discrete login event to the RP. The validity time window of an assertion is related to but separate from any session management at the IdP or RP. Specifically, an assertion is created during an authenticated session at the IdP, and processing an assertion creates an authenticated session at the RP. After the IdP creates the assertion, the validity of the IdP's session is independent of the validity of the assertion. If a request comes to the IdP for a repeated authentication while the session is still valid at the IdP, this results in a new and separate assertion being created with its own validity time window. Similarly, after the RP consumes the assertion, the validity of the RP's session is independent of the validity of the assertion. Access granted to an identity API is likewise independent of the validity of the assertion or the lifetime of the authenticated session at the RP. See [Sec. 5.3](sec5_federation.md#federation-session) for more information on session management.
-->

Federation Protocol によって詳細はさまざまであるが, Assertion は個々の RP へのログインイベントを表現する.
Assertion の Validity Time Window は IdP ないし RP の Session 管理に関連はするが分離したものである.
特に Assertion は IdP における認証済 Session 中に生成され, Assertion を処理することで RP における認証済 Session が生成される.
IdP が Assertion を生成した後は, IdP の Session の有効性と Assertion の有効性は独立したものとなる.
IdP における Session が有効なうちに再度 IdP が Authentication 要求を受け取った場合, その結果として新たな独立した Assertion が独自の Validity Time Window のもと生成される.
同様に, RP が Assertion を消費した後は, RP の Session と Assertion の有効性は独立したものとなる.
Identity API に対して付与された Access もまた, Assertion の有効性や RP の認証済 Session の有効期間とは独立したものである.
Session 管理についての詳細は [Sec. 5.3](sec5_federation.ja.md#federation-session) を参照のこと.

<!--
The assertion's validity time window is the time between its issuance and its expiration. This window needs to be large enough to allow the RP to process the assertion and create a local application session for the subscriber, but should not be longer than necessary for such establishment. Long-lived assertions have a greater risk of being stolen or replayed; a short assertion validity time window mitigates this risk. Assertion validity time windows **SHALL NOT** be used to limit the session at the RP. See [Sec. 5.3](sec5_federation.md#federation-session) for more information.
-->

Assertion の Validity Time Window はその発行日時と有効期限の間の期間である.
この値は RP が Assertion を処理して Subscriber に対して ローカルのアプリケーション Session を生成するに足りるものである必要がある一方, 必要以上に長くあるべきではない.
長期間有効な Assertion は詐取されたり Replay されるリスクを高め, Validity Time Window を短くするとそのリスクは低減される.
Assertion の Validity Time Window は RP における Session を制限するために用いてはならない (**SHALL NOT**).
詳細は [Sec. 5.3](sec5_federation.ja.md#federation-session) を参照のこと.

## Assertion Binding  {#assertion-binding}

<!--
Assertion binding can be classified based on whether presentation by a claimant of an assertion is sufficient for binding to the party currently in session with the RP as the subscriber, or if the RP requires additional proof through the successful presentation of an authenticator bound to the subscriber.
-->

Assertion Binding は, Claimant による Assertion の提示が Subscriber として RP に Session を保持している当事者と紐づけるに足りるかどうかや, RP が Subscriber に紐づけられた Authenticator の提示を通じた追加の証明を必要とするかどうかに基づいて分類できる.

### Bearer Assertions  {#bearer}

<!--
A bearer assertion can be presented by any party as proof of the bearer's identity. Similarly, a bearer assertion reference can be presented by any party to the RP and used by the RP to fetch an assertion; the assertion in this instance is also considered a bearer assertion. If an attacker can capture or manufacture a valid assertion or assertion reference representing a subscriber and can successfully present that assertion or reference to the RP, then the attacker could be able to impersonate the subscriber at that RP.
-->

Bearer Assertion は, いかなる当事者であれ自身の Identity の証明として提示することが可能なものである.
Bearer Assertion Reference も同様に, いかなる当事者でも RP に提示し RP に Assertion を取得させることができる.
そうやって取得された Assertion も Bearer Assertion として扱われる.
Attacker が Subscriber に関する有効な Assertion ないし Assertion Reference を詐取ないし偽造して成功裡に RP に提示できる場合, Attacker は RP に対して Subscriber になりすますことが可能となる.

<!--
Note that mere possession of a bearer assertion or reference is not always enough to impersonate a subscriber. For example, if an assertion is presented in the back-channel federation model (described in [Sec. 7.1](sec7_presentation.md#back-channel)), additional controls **MAY** be placed on the transaction (such as identification of the RP and assertion injection protections) that help further protect the RP from fraudulent activity.
-->

Bearer Assertion ないしは Bearer Assertion Referende を保持するだけでは, 常に Subscriber になりすますのに十分であるとは限らないことに注意すること.
例えば, Assertion が Back-channel Federation Model ([Sec. 7.1](sec7_presentation.ja.md#back-channel) に後述) によって提示される場合, Transaction に追加の統制が課されることもある (**MAY**).
例としては RP の識別や Assertion インジェクションにたいする保護策などが考えられる.
これらは RP を不正なアクティビティから保護する追加の対策となる.

### Bound Authenticators {#boundauth}

<!--
A bound authenticator is an authenticator presented to the RP by the subscriber alongside the assertion. In proving possession of the bound authenticator to the RP, the subscriber also proves with a certain degree of assurance that they are the rightful subject of the assertion. It is more difficult for an attacker to use a stolen assertion issued to a subscriber since the attacker would need to steal the bound authenticator as well as the assertion and be able to present them together. Furthermore, use of a bound authenticator protects the RP against malicious or compromised IdPs through the use of independent authentication.
-->

Bound Authenticator とは Subscriber が Assertion とともに RP に提示する Authenticator である.
RP に Bound Authenticator を保持していることを証明するため, Subscriber は Assertion の正当な Subject であるということを一定の確度を持って証明する.
これにより, Attacker は Assertion に加え Bound Authenticator も詐取・提示することが必要になるため, Attacker が Subscriber 向けに発行された Assertion を詐取して利用することはより困難になる.
さらに Bound Authenticator は独立した Authentication により RP を不正もしくは侵害された IdP から保護する.

<!--
A bound authenticator **SHALL** be unique per subscriber at the RP such that two subscribers cannot present the same authenticator for their separate RP subscriber accounts. All bound authenticators **SHALL** be phishing resistant. Consequently, subscriber-chosen values such as a memorized secret cannot be used as bound authenticators.
The RP **SHALL** accept authentication from a bound authenticator only in the context of processing an assertion. Consequently, the subscriber can not use a bound authenticator to log into the RP directly, bypassing the IdP in the process.
-->

Bound Authenticator は RP において Subscriber 毎に一意であるものとし (**SHALL**), 異なる Subscriber は同じ Authenticator をそれぞれの RP Subscriber Account に対して提示することができないようにすること.
全ての Bound Authenticator は Phishing 耐性を持つこと (**SHALL**).
従って, Memorized Secret のような Subscriber が選択した値は Bound Authenticator としては利用できない.
RP は Assertion を保持したコンテキストでのみ Bound Authenticator による Authentication を受け入れること (**SHALL**).
従って, Subscriber は Bound Authenticator を使って IdP におけるプロセスをバイパスして直接 RP にログインすることはできない.

<!--
A bound authenticator can be managed by either the IdP or the RP under different circumstances, as detailed in the sections below. An FAL3 assertion contains an indication of whether the IdP expects the subscriber to present a specific IdP-managed bound authenticator or an RP-managed bound authenticator at the RP to reach FAL3.
-->

次節で詳述の通り, Bound Authenticator はさまざまな条件のもと IdP ないし RP のいずれかによって管理されうる.
FAL3 の Assertion は, IdP が Subscriber に特定の IdP 管理の Bound Authenticator を提示することを期待するか, RP において FAL3 に足りる RP 管理の Bound Authenticator を提示することを期待するかを指定する値を含む.

#### IdP-Managed Bound Authenticators

<!--
When the bound authenticator is managed by the IdP as in [Fig. 9](sec6_assertions.md#fig-9), a unique identifier for the authenticator (such as its public key) **SHALL** be included in the assertion presented to the RP. The RP **SHALL** prompt the subscriber to prove possession of the identified bound authenticator.
-->

[Fig. 9](sec6_assertions.ja.md#fig-9) のように Bound Authenticator が IdP によって管理されている場合, RP に提示される Assertion には Authenticator を一意に示す識別子 (Authenticator の Public Key など) を含めることとする (**SHALL**).
また RP は Subscriber に指定された Bound Authenticator の保持証明を求めること (**SHALL**).

[Figure 9. IdP-Managed Bound Authenticators](sec6_assertions.md#fig-9){:name="fig-9"}
{:latex-ignore="true"}

![Diagram illustrating the use of bound authenticators managed at the IdP.]({{site.baseurl}}/{{page.collection}}/media/IdP-Managed-Bound-Auth.png 'IdP-Managed Bound Authenticators'){:latex-src="IdP-Managed-Bound-Auth.pdf" latex-fig="9" latex-place="h"}

<!--
An IdP-managed bound authenticator **MAY** be distinct from the primary authenticator the subscriber uses to authenticate to the IdP. Bound authenticators managed at the IdP **SHALL** be phishing resistant and **SHALL** be independently dereferenceable by the RP based on a mutually-trusted security framework, such as a public-key infrastructure. When processing an IdP-managed bound authenticator for the first time, the RP **SHOULD** verify whether the authenticator being presented is appropriate to be associated with the subscriber account, such as through account resolution from the attributes in the authenticator's presented information.
-->

IdP が管理する Bound Authenticator は Subscriber が IdP に対して Authenticate する際に用いるプライマリな Authenticator とは異なるものでよい (**MAY**).
IdP が管理する Bound Authenticator は Phishing 耐性を持ち (**SHALL**), Public Key Infrastructure などの相互信頼セキュリティフレームワークに基づいて RP により個別に参照解除可能でなければならない (**SHALL**).
初めて IdP 管理の Bound Authenticator を処理する際, RP は Authenticator が提示する情報に含まれる Attribute を用いて Account 解決を行うなどして, 提示された Authenticator が Subscriber Account に関連づけられるに適切かどうかを検証するべきである (**SHOULD**).

<!--
For example, a subscriber could have a smart card loaded with a certificate, which is a multi-factor cryptographic device. Since the certificate can be presented to both the IdP and the RP, the IdP can include an identifier for the certificate in the FAL3 assertion to the RP. The RP would then prompt the subscriber to present the certificate from their smart card in order to reach FAL3.
-->

例えば, Subscriber が Certificate が読み込まれた Smart Card を持っているとする.
この Smart Card は Multi-factor Cryptographic Device である.
Certificate は IdP にも RP にも提示可能であるため, IdP は RP に向けた FAL3 の Assertion に Certificate の識別子を含めることができる.
すると RP は Subscriber に Smart Card 内の Certificate の提示を求め, FAL3 を満たすことができる.

<!--
"Holder of Key" (HoK) assertions are one example of IdP-managed bound authenticators, since the IdP knows the subscriber's key to be used at the RP and includes the key information in the assertion presented to the RP.
-->

"Holder of Key" (HoK) Assertion は IdP 管理の Bound Authenticator の一例である.
この例では IdP は RP で使用される Subscriber の鍵を知っており, RP に提示する Assertion に鍵情報を含める.

~~~
\clearpage
~~~
{:latex-literal="true"}

#### RP-Managed Bound Authenticators

<!--
When the bound authenticator is managed by the RP as in [Fig. 10](sec6_assertions.md#fig-10), the IdP **SHALL** include an indicator in the assertion that the assertion is to be used with a bound authenticator at FAL3. The unique identifier for the authenticator (such as its public key) **SHALL** be stored in the RP subscriber account.
-->

[Fig. 10](sec6_assertions.ja.md#fig-10) のように Bound Authenticator が RP によって管理されている場合, IdP は Assertion に当該 Assertion が FAL3 で Bound Authenticator とともに利用されることを示す値を含めることとする (**SHALL**).
Authenticator を一意に示す識別子 (Authenticator の Public Key など) は RP Subscriber Account 内に保存すること (**SHALL**).

[Figure 10. RP-Managed Bound Authenticators](sec6_assertions.md#fig-10){:name="fig-10"}
{:latex-ignore="true"}

![Diagram illustrating the use of bound authenticators managed at the RP.]({{site.baseurl}}/{{page.collection}}/media/RP-Managed-Bound-Auth.png 'RP-Managed Bound Authenticators'){:latex-src="RP-Managed-Bound-Auth.pdf" latex-fig="10" latex-place="h"}

<!--
Before an RP can successfully accept an FAL3 assertion, the RP subscriber account must include a bound authenticator. These authenticators can be provided by either the RP or the subscriber, with slightly different requirements applying to the initial binding of the authenticator to the RP subscriber account in each case.
-->

RP は FAL3 Assertion を成功裡に受け入れるには, 事前に RP Subscriber Account に Bound Authenticator が保存されていなければならない.
これらの Authenticator は RP ないしは Subscriber のどちらかにより提示されうる.
どちらが提示するかによって, 初回の RP Subscriber Account への Authenticator 紐付け処理にかかる要件は微妙に異なる.

<!--
For RP-provided authenticators, the administrator of the RP **SHALL** issue the authenticator to the subscriber directly for use with an FAL3 login. The administrator of the RP **SHALL** store a unique identifier for the bound authenticator in the RP subscriber account. The administrator of the RP **SHALL** determine through independent means that the party to which the authenticator is issued is the identified subject of the RP subscriber account.
-->

RP が提示する Authenticator に関しては, RP の管理者が FAL3 で Subscriber をログインさせた状態で Subscriber に直接 Authenticator を発行しなければならない (**SHALL**).
RP の管理者は, RP Subscriber Account に Bound Authenticator の一意な識別子を保存しなければならない (**SHALL**).
さらに, RP の管理者は, 独自に Authenticator を発行する相手が RP Subscriber Account の Subject であることを確認しなければならない (**SHALL**).

<!--
For subscriber-provided authenticators, if no bound authenticators are associated with the RP subscriber account, the RP **SHALL** perform a binding ceremony to establish the connection between the authenticator, the subscriber, and the RP subscriber account as shown in [Fig. 11](sec6_assertions.md#fig-11). The RP **SHALL** first establish an authenticated session using federation with an assertion that meets all the other requirements of FAL3, including an indication that the assertion is intended for use at FAL3 with an RP-managed bound authenticator. The subscriber **SHALL** immediately be prompted to present and authenticate with the proposed authenticator. Upon successful presentation of the authenticator, the RP **SHALL** store a unique identifier for the authenticator (such as its public key) and associate this with the RP subscriber account associated with the federated identifier. If the subscriber fails to successfully present an appropriate authenticator, the binding ceremony fails. The binding ceremony session **SHALL** have a timeout of five minutes or less. The session used during the ceremony is not an authenticated session for the purposes of logging in. Upon successful completion of the binding ceremony, the RP **SHALL** immediately request a new assertion from the IdP at FAL3, including prompting the subscriber for the newly-bound authenticator.
-->

Subscriber が提示する Authenticator に関しては, RP Subscriber にひとつも Bound Authenticator が紐づいていない場合, RP は [Fig. 11](sec6_assertions.ja.md#fig-11) のように Authenticator, Subscriber および RP Subscriber Account の間の紐付け確立のために Binding セレモニーを実施しなければならない (**SHALL**).
RP はまず FAL3 の Bound Authenticator に関するもの以外の要件を満たす Assertion を用いた Federation により認証済 Session を確立する. 当該 Assertion には RP 管理の Bound Authenticator により FAL3 で利用されることが期待されることを示す値が含まれる.
次に Subscriber はその直後に提案された Authenticator を提示し Authenticate する.
Authenticator の提示が成功すると, RP は Authenticator の一意な識別子 (Public Key 等) を保存し, それを Federated Identifier が指し示す RP Subscriber Account に紐づける (**SHALL**).
Subscriber が適切な Authenticator を提示することができない場合, Binding セレモニーは失敗する.
Binding セレモニーの Session は5分以内にタイムアウトさせなければならない (**SHALL**).
セレモニー中の Session はログイン目的の認証済 Session とはならない.
Binding セレモニーが成功すると, RP は直後に IdP に対して FAL3 の新たな Assertion を要求すること (**SHALL**).
その際 Subscriber には新たに登録した Bound Authenticator の提示が求められる.

[Figure 11. Binding Ceremony](sec6_assertions.md#fig-11){:name="fig-11"}
{:latex-ignore="true"}

![Sequence diagram of the steps involved in the binding ceremony used for bound authenticators managed at the RP and provided by the subscriber.]({{site.baseurl}}/{{page.collection}}/media/Binding-Ceremony.png 'Binding Ceremony'){:latex-src="Binding-Ceremony.pdf" latex-fig="11" latex-place="h"}

<!--
An RP **MAY** allow a subscriber to bind multiple subscriber-provided authenticators at FAL3. If this is the case, and the RP subscriber account has one or more existing bound authenticators, the binding ceremony makes use of the existing ability to reach FAL3. The subscriber **SHALL** first be prompted to present an existing bound authenticator to reach FAL3. Upon successful authentication, the RP **SHALL** immediately prompt the subscriber for the newly-bound authenticator.
-->

RP は Subscriber に複数の FAL3 の Subscriber 提示の Authenticator 紐付けを許可してもよい (**MAY**).
その場合、RP Subscriber Account は一つ以上の既存の Bound Authenticator を持ち, Binding セレモニーは既存のものを使い FAL3 で行うことができる.
Subscriber はまず最初に既存の Bound Authenticator を提示して FAL3 に到達する.
Authentication 成功直後に RP は Subscriber に新たな Bound Authenticator を要求する.

<!--
An RP **MAY** allow a subscriber to unbind a bound subscriber-provided authenticator from their RP subscriber account, thereby removing the ability to use that authenticator for FAL3. When a bound authenticator is unbound, the RP **SHALL** terminate all current FAL3 sessions for the subscriber and **SHALL** require reauthentication of the subscriber from the IdP. Note that in many cases, a subscriber will need to unbind a bound authenticator to account for a lost or compromised authenticator, and the subscriber will therefore not have access to the authenticator during the unbinding process.
-->

RP は Subscriber に RP Subscriber Account からの Subscriber 提示の Authenticator 紐付け解除を許可してもよい (**MAY**).
紐付けを解除すると当該 Authenticator を用いて FAL3 を達成することはできなくなる.
Bound Authenticator の紐付けが解除された際, RP は Subscriber の全ての既存 FAL3 Session を Terminate し (**SHALL**), Subscriber に IdP での Reauthentication を要求すること (**SHALL**).
多くの場合, Subscriber は, Authenticator を紛失したり Authenticator が侵害された際に Bound Authenticator を Account から紐付け解除する必要があることに注意すること. 従って, Subscriber は紐付け解除プロセス中には当該 Authenticator への Access を持たないことにも注意.

~~~
\clearpage
~~~
{:latex-literal="true"}

<!--
The RP **SHALL** notify the subscriber through an out-of-band mechanism, and **SHOULD** notify the IdP using a shared signaling system (see [Sec. 5.7](sec5_federation.md#shared-signals)), if any of the following events occur:
-->

RP は, 以下のようなイベントが発生した際は, Out-of-band な手段で Subscriber に通知し (**SHALL**), IdP にも Shared Signaling システム ([Sec. 5.7](sec5_federation.ja.md#shared-signals) 参照) を通じて通知を行うべきである (**SHALL**).

<!--
- A new authenticator is bound to the RP subscriber account.
- An existing bound authenticator is unbound from the RP subscriber account.
-->

- 新たな Authenticator が RP Subscriber Account に紐づけられた.
- 既存の Bound Authenticator が RP Subscriber Account から紐付け解除された.

<!--
For example, a subscriber could have a single factor cryptographic device as an authenticator. This authenticator uses name-based phishing resistance so the IdP and RP would see different keys when used in each location. The RP can use a binding ceremony as described here to allow the subscriber to use this device as a bound authenticator at FAL3. The RP will prompt the subscriber for this authenticator whenever it sees an assertion for this subscriber at FAL3 from the IdP.
-->

例えば, Subscriber は Single Factor Cryotographic Device を Authenticator として保持しうる.
この Authenticator は名前ベースの Phishing 耐性を持ち, IdP と RP はそれぞれ異なる鍵を受け取る.
RP は, ここで述べた Binding セレモニーを用いて, Subscriber がこのデバイスを FAL3 の Bound Authenticator として使うことを許可することができる.
RP は IdP から Subscriber に関する FAL3 の Assertion を受け取るたびに, Subscriber にこの Authenticator の提示を求めることになろう.

#### Processing Bound Authenticators

<!--
When the RP receives an assertion associated with a bound authenticator, the subscriber proves possession of the bound authenticator directly to the RP. The primary authentication at the IdP and the federated authentication at the RP are processed separately. While the subscriber could use the same authenticator during the primary authentication at the IdP and as the bound authenticator at the RP, there is no assumption that these will be the same.
-->

RP が Boud Authenticator とともに Assertion を受け取る際, Subscriber は RP に直接 Bound Authenticator の保持証明を行う.
IdP におけるプライマリ Authentication および RP における Federated Authentication は別々に処理される.
Subscriber は IdP におけるプライマリ Authentication でも RP における Bound Authenticator と同じ Authenticator を使うことができるが, それぞれが同じものであるということはなんら想定されない.

<!--
The following requirements apply to all assertions associated with a bound authenticator:
-->

以下の要件は Bound Authenticator と関連づけられた全ての Assertion に適用される.

<!--
1. The subscriber **SHALL** prove possession of the bound authenticator to the RP, in addition to presentation of the assertion itself.
2. If the authenticator is managed at the IdP, reference to a given authenticator found within an assertion **SHALL** be trusted at the same level as all other information within the assertion.
3. If the authenticator is managed at the IdP, the assertion **SHALL NOT** include an unencrypted private or symmetric key to be used as an authenticator with the presentation.
4. The RP **SHALL** process and validate the assertion in addition to the bound authenticator.
5. Failure to authenticate with the bound authenticator **SHALL** result in an error at the RP.
-->

1. Subscriber は RP に対して Assertion そのものの提示に加え Bound Authenticator の保持証明を行うこと (**SHALL**).
2. Authenticator が IdP で管理されている場合, Assertion 内に含まれる当該 Authenticator の参照は Assertion 内のその他の全ての情報を同じレベルで信頼すること (**SHALL**).
3. Authenticator が IdP で管理されている場合, Assertion は提示時に Authenticator として使われる Private Key ないし Symmetric Key を暗号化せずに含んではならない (**SHALL NOT**).
4. RP は Bound Authenticator に加えて Assertion も処理, 検証すること (**SHALL**).
5. Bound Authenticator を用いた Authentication が失敗した場合, RP 側でエラーになること (**SHALL**).

## Assertion Protection

<!--
Independent of the binding mechanism (discussed in [Sec. 6.1](sec6_assertions.md#assertion-binding)) or the federation model used to obtain them (described in [Sec. 5.1](sec5_federation.md#trust-agreement)), assertions **SHALL** include a set of protections to prevent attackers from manufacturing valid assertions or reusing captured assertions at disparate RPs. The protections required are dependent on the details of the use case being considered, and specific protections are listed here.
-->

Binding メカニズム ([Sec. 6.1](sec6_assertions.md#assertion-binding)) やその取得に用いる Federation モデル ([Sec. 5.1](sec5_federation.md#trust-agreement)) とは別に, Assertion は有効な Assertion を偽装したり取得した Assertion を他の RP に対して再利用する攻撃に対する保護策を持たねばならない (**SHALL**).
必要な保護策は考慮されるユースケースの詳細に依存する. 具体的な保護策を以下に示す.

### Assertion Identifier {#assertion-id}

<!--
Assertions **SHALL** be sufficiently unique to permit unique identification by the target RP. Assertions **MAY** accomplish this by use of an embedded nonce, issuance timestamp, assertion identifier, or a combination of these or other techniques.
-->

Assertion は対象の RP が一意に区別可能である必要がある (**SHALL**).
これは Nonce, Issuance Timestamp, Assertion Identifier ないしこれらおよびその他のテクニックの組み合わせにより実現可能である (**MAY**).

### Signed Assertion {#signed-assertion}

<!--
Assertions **SHALL** be cryptographically signed by the issuer (IdP). The RP **SHALL** validate the digital signature or MAC of each such assertion based on the issuer's key. This signature **SHALL** cover the entire assertion, including its identifier, issuer, audience, subject, and expiration.
-->

Assertion は Issuer (IdP) に暗号論的に署名されなければならない (**SHALL**).
RP は Issuer の鍵にもとづいて各 Assertion の Digital Signature ないし MAC を検証しなければならない.
この署名は Assertion Identifier, Issuer, Audience, Subject および Expiration を含む Assertion 全体をカバーすること (**SHALL**).

<!--
The assertion signature **SHALL** either be a digital signature using asymmetric keys or a MAC using a symmetric key shared between the RP and issuer. Shared symmetric keys used for this purpose by the IdP **SHALL** be independent for each RP to which they send assertions, and are normally established during registration of the RP. Public keys for verifying digital signatures **SHALL** be transferred to the RP in a secure manner, and **MAY** be fetched by the RP in a secure fashion at runtime, such as through an HTTPS URL hosted by the IdP. Approved cryptography **SHALL** be used.
-->

Assertion の署名は Asymmetric Key を用いた Digital Signature か Symmetric Key を用いた MAC のどちらかでなければならない (**SHALL**).
この目的のために IdP が用いる Shared Symmetric Key は, Assertion 送信先の RP 毎に固有でなければならなず (**SHALL**), 通常は RP の Registration 時に確立される.
Digital Signature を検証するための Public Key はセキュアな手段により RP に送信されなければならず (**SHALL**), RP が実行時に IdP のホストする HTTPS URL を介するなどセキュアな方法で取得することも可能である (**MAY**).
また Approved Cryptography を利用せねばならない (**SHALL**).

### Encrypted Assertion {#encrypted-assertion}

<!--
Encrypted assertions protect the contents of the assertion from being read by unintended parties, ensuring that only the targeted RP is able to read the assertion. Encrypting assertions provides two primary benefits: the assertion contents cannot be seen by any party other than the intended RP, and the assertion cannot be used by any RP other than the targeted one.
-->

Encrypted Assertion は Assertion のコンテンツを想定外の当事者に閲覧されることを防止し, 対象の RP のみが Assertion を閲覧できることを保証する.
Assertion の暗号化には, 主に2つの利点がある.
1つめは Assertion コンテンツが対象 RP 以外から閲覧できないということ, 2つめは対象の RP 以外の RP は当該 Assertion を利用できないということである.

<!--
When encrypting assertions, the IdP **SHALL** encrypt the contents of the assertion using either the RP's public key or a shared symmetric key. Shared symmetric keys used for this purpose by the IdP **SHALL** be independent for each RP to which they send assertions, and are normally established during registration of the RP. Public keys for encryption **SHALL** be securely transferred to the IdP and **MAY** be fetched by the IdP in a secure fashion at runtime, such as through an HTTPS URL hosted by the RP.
-->

Assertion を暗号化する際, IdP は RP の Public Key ないしは Shared Symmetric Key を用いて Assertion コンテンツを暗号化しなければならない (**SHALL**).
この目的のために IdP が用いる Shared Symmetric Key は, Assertion 送信先の RP 毎に固有でなければならなず (**SHALL**), 通常は RP の Registration 時に確立される.
暗号化に用いる Public Key はセキュアな手段により IdP に送信されなければならず (**SHALL**), IdP が実行時に RP のホストする HTTPS URL を介するなどセキュアな方法で取得することも可能である (**MAY**).

<!--
All encryption of assertions **SHALL** use approved cryptography.
-->

全ての Assertion 暗号化には Approved Cryptography を利用すること (**SHALL**).

<!--
When personally-identifiable information is included in the assertion and the assertion is handled by intermediaries such as a browser, the federation protocol **SHALL** encrypt assertions to protect the sensitive information in the assertion from leaking to unintended parties. For example, a SAML assertion can be encrypted using XML-Encryption, or an OpenID Connect ID Token can be encrypted using JSON Web Encryption (JWE).
-->

Assertion に Personally Identifiable Information が含まれかつ Assertion がブラウザなどの中間者に取り扱われる場合, Federation Protocol は Assertion を暗号化し Assertion に含まれるセンシティブな情報を予期せぬ当事者に漏洩しないよう保護しなければならない (**SHALL**).
例えば SAML Assertion は XML-Encryption を用いて暗号化することができるし, OpenID Connect ID Token は JSON Web Encryption (JWE) を用いて暗号化することができる.

### Audience Restriction

<!--
Assertions **SHALL** use audience restriction techniques to allow an RP to recognize whether or not it is the intended target of an issued assertion. All RPs **SHALL** check that the audience of an assertion contains an identifier for their RP to prevent the injection and replay of an assertion generated for one RP at another RP.
-->

Assertion には Audience Restriction 技術を適用し, RP に自信がその Assertion の発行対象として想定されているか認識できるようにしなければならない (**SHALL**).
全ての RP は, ある RP が別の RP に Assertion をインジェクトしたり Replay したりすることを防止するため, Assertion の Audience が自身の識別子を含んでいることをチェックしなければならない (**SHALL**).

### Pairwise Pseudonymous Identifiers {#ppi}

<!--
In some circumstances, it is desirable to prevent the subscriber account from being easily linked at multiple RPs through use of a common identifier. A pairwise pseudonymous identifier (PPI) allows an IdP to provide multiple distinct federated identifiers to different RPs for a single subscriber account. This prevents different RPs from colluding together to track the subscriber using the federated identifier.
-->

状況によっては, 共通の識別子を用いて複数の RP にまたがって Subscriber Account をリンクすることを防ぎたい場合がある.
Pairwise Pseudonymous Identifier (PPI) は, IdP が単一の Subscriber Account に関して異なる RP に異なる Federated Identifier を提供することを可能にする.
これにより異なる RP が共謀して Federated Identifier を用いて Subscriber をトラックすることを防止できる.

#### General Requirements

<!--
When using pairwise pseudonymous identifiers within the assertions generated by the IdP for the RP, the IdP **SHALL** generate a different federated identifier for each RP as described in [Sec. 6.2.5.2](sec6_assertions.md#ppi-gen) below.
-->

IdP が RP に対して生成する Assertion 内で Pairwise Pseudonymous Identifier を用いる際, IdP は [Sec. 6.2.5.2](sec6_assertions.ja.md#ppi-gen) に後述の通り各 RP に異なる Federated Identifier を生成しなければならない (**SHALL**).

<!--
When PPIs are used with RPs alongside attributes, it may still be possible for multiple colluding RPs to re-identify a subscriber by correlation across systems using these identity attributes. For example, if two independent RPs each see the same subscriber identified with different pairwise pseudonymous identifiers, they could still determine that the subscriber is the same person by comparing the name, email address, physical address, or other identifying attributes carried alongside the pairwise pseudonymous identifier in the respective assertions. Privacy policies **SHOULD** prohibit such correlation, and pairwise pseudonymous identifiers can increase effectiveness of these policies by increasing the administrative effort in managing the attribute correlation.
-->

RP に対して Attribute とともに PPI を用いる場合, 共謀する複数の RP が Identity Attribute に基づいて複数のシステムにまたがって名寄せを行うことで, Subscriber を再識別することは依然起こりうる.
例えば2つの独立した RP が各々異なる Pairwise Pseudonymous Identifier が指し示す同一の Subscriber を見ている場合, これらの RP は依然として, 各自の Assertion 内に Pairwise Pseudonymous Identifier と共に伝搬される Subscriber の氏名, Email Address, 住所やその他の識別可能な Attribute により, 当該 Subscriber が同一人物であると特定することもありうる.
このような名寄せはプライバシーポリシーで禁止すべきであり (**SHOULD**), Pairwise Pseudonymous Identifier は Attribute の名寄せに関する管理作業を増大させることによってこういったポリシーの効果を高めることも可能である.

<!--
Note that in a proxied federation model, the initial IdP may be unable to generate a pairwise pseudonymous identifier for the ultimate RP, since the proxy could blind the IdP from knowing which RP is being accessed by the subscriber. In such situations, the pairwise pseudonymous identifier is generally established between the IdP and the federation proxy itself. The proxy, acting as an IdP, can itself provide pairwise pseudonymous identifiers to downstream RPs. Depending on the protocol, the federation proxy may need to map the pairwise pseudonymous identifiers back to the associated identifiers from upstream IdPs in order to allow the identity protocol to function. In such cases, the proxy will be able to track and determine which pairwise pseudonymous identifiers represent the same subscriber at different RPs. The proxy **SHALL NOT** disclose the mapping between the pairwise pseudonymous identifier and any other identifiers to a third party or use the information for any purpose other than federated authentication, related fraud mitigation, to comply with law or legal process, or in the case of a specific user request for the information.
-->

Proxied Federation モデルでは, 最初の IdP が末端の RP に対して Pairwise Pseudonymous Identifier を生成することは不可能な場合もあることに注意すること.
Proxy は IdP に対して Subscriber が Access しようとしている RP を隠すこともある.
このような状況下では, Pairwise Pseudonymous Identifier は通常 IdP と Federation Proxy 自身の間で確立される.
Proxy は IdP として動作することで自身の Pairwise Pseudonymous Identifier を下流の RP に提供することができる.
プロトコルによっては, Identity Protocol が機能するために, Federation Proxy が Pairwise Pseudonymous Identifier から上流の IdP が発行したそれに紐づく識別子を逆引きすることが必要な場合もある.
そのような場合, Proxy はどの Pairwise Pseudonymous Identifier が異なる RP のどの同一の Subscriber を示しているか特定, 追跡が可能となる.
Proxy は, Pairwise Pseudonymous Identifier とその他のいかなる識別子との間のマッピングについても 3rd-party に開示してはならず, 当該情報を Federated Authentication, それに関連する不正防止, 法律ないし法的プロセスへの準拠, 当該情報に対する特別なユーザー要求への応答を除き, その他の目的で利用してはならない (**SHALL NOT**).

#### Pairwise Pseudonymous Identifier Generation {#ppi-gen}

<!--
Pairwise pseudonymous identifiers **SHALL** contain no identifying information about the subscriber. They **SHALL** also be unguessable by a party having access to some information identifying the subscriber. Pairwise pseudonymous identifiers **MAY** be generated randomly and assigned to subscribers by the IdP or **MAY** be derived from other subscriber information if the derivation is done in an irreversible, unguessable manner (e.g., using a keyed hash function with a secret key).
-->

Pairwise Pseudonymous Identifier にはいかなる Subscriber の識別情報をも含めないこと (**SHALL**).
さらに Pairwise Pseudonymous Identifier はなんらかの Subscriber の識別情報を持つ当事者により推測可能でもないこと (**SHALL**).
Pairwise Pseudonymous Identifier は IdP によってランダムに生成され Subscriber に割り当てることもできるし (**MAY**), 不可逆かつ推測不可能な方法で導出可能 (e.g., Secret Key を用いた鍵付きハッシュなど) であれば Subscriber に関するその他の情報から導出することもできる (**MAY**).

<!--
Normally, the identifiers **SHALL** only be known by and used by one pair of endpoints (e.g., IdP-RP). An IdP **MAY** generate the same identifier for a subscriber at multiple RPs at the request of those RPs, provided:
-->

通常は, この識別子は1組のエンドポイントにのみ知られ, 使われうるものとする (**SHALL**).
IdP は以下の条件を満たす複数の RP により要求された場合は, 同じ Subscriber に同じ識別子を生成してもよい (**MAY**).

<!--
* The trust agreement stipulates a shared pseudonymous identifier for a specific family of RPs;
* The authorized party consents to and is notified of the use of a shared pseudonymous identifier;
* Those RPs have a demonstrable relationship that justifies an operational need for the correlation, such as a shared security domain or shared legal ownership; and
* All RPs sharing an identifier consent to being correlated in such a manner (i.e., one RP cannot request to have another RP's PPI without that other RP's knowledge and consent).
-->

* 特定の RP 群に対して Pseudonymous Identifier を共有可能であることが Trust Agreement に規定されている.
* Authorized Party が Pseudonymous Identifier の共有について同意し, かつその利用に関して通知されている.
* これらの RP 群が, 互いにセキュリティドメインを共有していたり同一の法的所有権のもとにあるなど, 運用上の名寄せの必要性を正当化するような関係性にある.
* 識別子を共有するすべての RP がこのような方法で名寄せ可能な関係性になることに同意する. (i.g., ある RP が他の RP の認知および同意なしに他の RP の PPI を要求することはできない.)

<!--
The RPs **SHALL** conduct a privacy risk assessment to consider the privacy risks associated with requesting a common identifier. See [Sec. 9.2](sec9_privacy.md#notice) for further privacy considerations.
-->

RP は Privacy Risk Assessment を行い共有識別子の要求に関するプライバシーリスクについて検討すること (**SHALL**).
さらなるプライバシー上の考慮事項は [Sec. 9.2](sec9_privacy.ja.md#notice) を参照.

<!--
The IdP **SHALL** ensure that only intended RPs are correlated; otherwise, a rogue RP could learn of the pseudonymous identifier for a set of correlated RPs by fraudulently posing as part of that set.
-->

IdP は意図した RP だけが名寄せ可能な状態になることを保証すること (**SHALL**).
さもなくば, 不正な RP が, 名寄せ可能な状態にある RP 群に向けた Pseudonymous Identifier を, その RP 群の一員を装い知り得ることになる.

## Identity APIs {#s-identity-api}

<!--
Attributes about the subscriber, including profile information, **MAY** be provided to the RP through a protected _attribute API_ known as the _identity API_. The RP is granted limited access to the identity API during the federation transaction, in concert with the assertion. For example, in OpenID Connect, the UserInfo Endpoint provides a standardized identity API for fetching attributes about the subscriber. This API is protected by an OAuth 2.0 Access Token, which is issued to the RP along with OpenID Connect's assertion, the ID Token. The use of identity APIs along with federation assertions has several advantages for the overall security, privacy, and efficiency of the federation system.
-->

プロフィール情報を含む Subscriber に関する Attribute は, _Identity API_ とも呼ばれる保護された _Attribute API_ から提供されうる (**MAY**).
RP は Federation Transaction 中に Assertion と合わせて Identity API への限定 Access を許可される.
例えば OpenID Connect では UserInfo Endpoint が標準の Identity API として Subscriber Attribute の取得に用いられる.
この API は OAuth 2.0 Access Token により保護され, この Access Token は OpenID Connect の Assertion である ID Token と共に RP に発行される.
Federation Assertion に加えて Identity API の利用することには, 全体のセキュリティ, プライバシーおよび Federation システムの効率性において幾つかの利点がある.

<!--
By making attributes available at an identity API, the IdP no longer has to use the assertion to convey as much information to the RP. This not only means that sensitive attributes do not have to be carried in the assertion itself, it also makes the assertion smaller and easier to process by the RP. The contents of the assertion can then be limited to essential fields (e.g., unique subject identifiers) and information about the immediate authentication event being asserted.
-->

Attribute を Identity API から取得可能とすることで, IdP は Assertion に大量の情報を含めて RP に送信する必要はなくなる.
これはセンシティブな Attribute を Assertion 自身に含めなくてよくなるというだけでなく, Assertion をより小さく RP に処理しやすいものにするという意味もある.
それにより, Assertion のコンテンツは, 必須項目 (e.g., Subject Identifier) と当該 Authentication イベントを示す情報に限定されうる.

<!--
The RP often caches attributes provided by the IdP in an RP subscriber account, discussed in [Sec. 5.4](../sec5_federation.md#rp-account). Attributes provided in the assertion are passed on every login, and since the RP does not know the identity of the subscriber before the attribute is requested, the IdP is incentivized to include as much information as possible in the assertion itself. However, most of a subscriber's attributes will not change in between subsequent logins, making this information redundant. As a consequence, most of these more-stable attributes can instead be made available through an identity API that is called by the RP only when necessary. The IdP can indicate in the assertion when the last time the subscriber's attributes have been updated in the subscriber account, allowing the RP to decide if it needs to fetch the attributes anew or if those in the RP subscriber account are sufficient.
-->

[Sec. 5.4](../sec5_federation.ja.md#rp-account) で述べたように, RP はしばしば RP Subscriber Account に IdP から提供された Attribute をキャッシュする.
Assertion 内の Attribute は全てのログイン時に伝搬され, RP は Attribute を要求する前段階では Subscriber の Identity を知らないため, IdP は Assertion 自身に可能な限り多くの情報を含めるインセンティブを持つことになる.
しかしながら大抵の Subscriber Attribute は連続するログイン間で不変であり, この情報は冗長となる.
結果として, これらの変化の少ない属性のほとんどは, Assertion に含める代わりに必要に応じて RP が Identity API を介して取得すれば十分となる.
IdP は Assertion 内で当該 Subscriber Account に関する Subscriber Attribute の最終更新時間を示すことも可能で, そうすることで RP は Attribute を新たに取得する必要があるか RP Subscriber Account に保存されている情報で足りるかを判断することができる.

<!--
Access to the identity API **SHALL** be time limited. The time limitation is separate from the validity time window of the assertion and the lifetime of the authenticated session at the RP. Access to an identity API by the RP without an associated valid assertion **SHALL NOT** be sufficient for the establishment of an authenticated session at the RP.
-->

Identity API への Access には有効期限がある.
この有効期限は Assertion の Validity Time Window とは独立しており, RP の認証済 Session の有効期限からも独立している.
RP が Identity API に Access できるからといって, 関連する有効な Assertion がない場合は, RP での認証済 Session の確立に必要な条件を満たしたものとしてはならない (**SHALL NOT**).

<!--
A given identity API deployment is expected to be capable of providing attributes for all subscribers for whom the IdP can create assertions. However, when access to the identity API is granted within the context of a federation transaction, the attributes provided by an identity API **SHALL** be associated with only the single subscriber identified in the associated assertion. If the identity API is hosted by the IdP, the returned attributes **SHALL** include the subject identifier for the subscriber. This allows the RP to positively correlate the assertion's subject to the returned attributes. Note that when access to an attribute API is provided as part of pre-provisioning of RP subscriber accounts as discussed in [Sec. 5.4.1](sec5_federation.md#provisioning), the RP is usually granted blanket access to the identity API outside the context of the federated transaction and these requirements do not apply.
-->

Identity API 実装は, IdP が Assertion を生成できる全ての Subscriber に関する Attribute を提供できることが期待される.
しかしながら, Federation Transaction のコンテキス内で Identity API への Access が許可された場合, その Identity API が提供する Attribute は当該 Assertion が指し示す Subscriber のもののみとすること (**SHALL**).
IdP が Identity API をホストする場合, 返却される Attribute には Subscriber の Subject Identifier を含めること (**SHALL**).
これにより RP は Assertion Subject を返却された Attribute に確実に紐づけることができる.
なお, [Sec. 5.4.1](sec5_federation.ja.md#provisioning) で述べたように, Attribute API への Access が RP Subscriber Account の Pre-provisioning の一環として提供される場合, RP は通常 Federation Transaction コンテキスト外で Identity API への全面的な Access を許可され, 上記要件は適用されないことに注意.

### Attribute Providers {#s-attribute-providers}

<!--
While most attribute APIs used in federation are hosted as part of the IdP, it is also possible for the IdP to grant access to identity APIs hosted by external attribute providers. These services provide attributes about the subscriber in addition to those made available directly from the IdP.
-->

Federation において, 大抵の Attribute API は IdP の一部としてホストされるが, IdP が外部の Attribute Provider にホストされる Identity API への Access を許可することも可能である.
こういったサービスは, IdP が直接提供できるもの以外にも Subscriber に関する Attribute を提供することができる.

<!--
When the IdP grants access to an attribute provider, the IdP is making an explicit statement that the information returned from the attribute provider is associated with the subscriber identified in the associated assertion. For the purposes of the trust agreement, the IdP is the responsible party for the accuracy and content of the attribute API.
-->

IdP が Attribute Provider への Access を許可する場合, IdP は Attribute Provider から返却された情報が, 関連づけられた Assertion により識別される Subscriber に紐づいたものであることを明示する.
Trust Agreement においては, IdP が Attribute API から返却されるコンテンツの正確性に責任を負う当事者となる.

<!--
The attributes returned by the attribute provider are assumed to be independent of those returned directly from the IdP, and as such **MAY** use different identifiers, formats, or schemas. The RP **SHALL** verify that the identified attribute provider is capable of providing the kinds of attributes that are present, under the auspices of the applicable trust agreement.
-->

Attribute Provider に返却された Attribute は IdP が直接返却する Attribute とは独立したものと想定される.
従って異なる識別子, フォーマットおよびスキーマを利用することも可能である (**MAY**).
RP は当該 Attribute Provider が適切な Trust Agreement の保護のもとでそういった類の実在する Attribute を提供するに足りることを検証すること (**SHALL**).

<!--
For example, an IdP could provide access to a subscriber's medical license information as part of the federation process. Instead of the IdP asserting the license status directly, the IdP provides the RP access to a record for the subscriber at a medical licensure agency. The RP can make a strong association between the current subscriber and the license record, even though the license record will not likely use the same subject identifier that the IdP does in this case.
-->

例えば, IdP が Federation プロセスの一環で Subscriber の医師免許情報への Access を提供しうるとする.
この時 IdP は, 当該ライセンスのステータスを直接示す代わりに, RP に医師免許機関における Subscriber のレコードへの Access を許可するとする.
この場合, ライセンスレコードは IdP が使用する Subject Identifier を使用していないこともあり得るが, RP は当該 Subscriber とライセンスレコードとの間に強力な関連付けを行うことができる.