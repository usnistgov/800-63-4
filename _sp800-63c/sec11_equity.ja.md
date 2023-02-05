---
layout: default.ja
title: Equity Considerations
navOrder: 11
navTitle: Equity
permalink: /sp800-63c/equity/
anchor: equity
section: 11
---

# Equity Considerations {#equity}

_This section is informative._

<!--
Equitable access to the functions of IdPs and RPs is an essential element of a federated identity system. The ability for all subscribers to authenticate reliably is required to provide equitable access to government services, even when using federation technology, as specified in Executive Order 13985, _Advancing Racial Equity and Support for Underserved Communities Through the Federal Government_ [[EO13985]](references.md#ref-EO13985). In assessing equity risks, IdPs and RPs should consider the overall user population served by their federated identity service. Additionally, IdPs and RPs further identify groups of users within the population whose shared characteristics can cause them to be subject to inequitable access, treatment, or outcomes when using that service. The Usability Considerations provided in [Sec. 10](../sec10_usability.md#usability) should also be considered to help ensure the overall usability and equity for all persons using federated identity services.
-->

IdP と RP の機能への公平な Access は, Federated Identity System において不可欠な要素である.
Federation 技術を使用する際も, Executive Order 13985, _Advancing Racial Equity and Support for Underserved Communities Through the Federal Government_ [[EO13985]](references.md#ref-EO13985) に定められている通り, 政府サービスへの公平なアクセスを提供するには, 全ての Subscriber が確実に Authenticate できることが必要である.
Equity に関するリスクを評価する際, IdP と RP は Federated Identity Service の対象となるユーザー母集団全体を考慮する必要がある.
さらに, IdP と RP はそれらのサービスを使用する際に, 共有される特性により不公平な Access, 取り扱い, 結果の対象となりうる母集団中の特定のユーザーグループをより一層認識することとなる.
[Sec. 10](../sec10_usability.md#usability) で述べた Usability 上の考慮事項は, Federated Identity Service を使用する全ての人の全体的な使いやすさと Equity を担保するためにも考慮されるべきである.

<!--
In its role as the verifier, the IdP needs to be aware of equity considerations related to identity proofing, attribute validation, and enrollment as enumerated in [[SP800-63A]](../_sp800-63a/sec11_equity.md#sec11){:latex-href="#ref-SP800-63A"} Sec. 11 and equity considerations concerning authenticators as enumerated in [[SP800-63B]](../_sp800-63b/sec11_equity.md#sec11){:latex-href="#ref-SP800-63B"} Sec. 11. An RP offering FAL3 will also need to be aware of these same authenticator considerations when processing bound authenticators, whether the authenticators are managed at the IdP or RP.
-->

Verifier としての役割を果たす中で, IdP は Identity Proofing, Attribute Validation および Enrollment に対する Equity に関する考慮事項 ([[SP800-63A]](../_sp800-63a/sec11_equity.md#sec11){:latex-href="#ref-SP800-63A"} Sec. 11 参照) および Authenticator に対する Equity に関する考慮事項 ([[SP800-63B]](../_sp800-63b/sec11_equity.md#sec11){:latex-href="#ref-SP800-63B"} Sec. 11 参照) を認識する必要がある.
FAL3 を提供する RP は, Authenticator が IdP に管理されているか RP に管理されているかに関わらず, Bound Authenticator を処理する際にはこれと同じ Authenticator に関する考慮事項を認識する必要がある.

<!--
Since the federation process takes place over a network protocol between multiple active parties, the experience of authenticating using the federation system may present equity problems, such as the following examples:
-->

Federation プロセスは複数のアクティブな当事者間で Network プロトコルを介して行われるため, Federation System を利用した Authentication のエクスペリエンスには Equity の問題が生じ得る. 以下に例を示す.

<!--
* Completing the entire federated transaction without timing out may be difficult for subscribers without a reliable network connection, such as those in rural areas.
* It may be difficult to provide informed consent for a runtime decision regarding the release of attributes for subscribers with intellectual, developmental, learning, or neurocognitive difficulties.
* Systems with sufficient processing power, network access, and other features required to interact with both the IdP and the RP simultaneously may be difficult to afford for some subscribers.
* Subscribers that share devices may find allowlist-based systems difficult to manage securely, as other users of the device could silently gain unintended access to an RP through a session still active at the IdP.
* It could be prohibitively difficult to re-establish an account at the RP for subscribers who lose access to their IdP for any of a variety of reasons.
-->

* 地方に住んでいるなど, 信頼できる Network 接続を持たない Subscriber にとっては, タイムアウトせずに全体の Federated Transaction を完了させるのは困難かもしれない.
* 知的障害, 発達障害, 学習障害または神経認知障害のある Subscriber は, Attribute 開示に関する実行時決定の際に情報に基づく同意を行うことが困難な可能性もある.
* 十分な処理能力, Network Access および IdP と RP の両方と同時に対話するために必要なその他の機能を備えたシステムは, 一部の Subscriber にとっては購入が難しいかもしれない.
* デバイスを共有している Subscriber は, Allowlist ベースのシステムをセキュアに管理するのが難しいと感じる可能性もある. これは当該デバイスの他のユーザーが IdP でまだアクティブな Session を用いて RP への意図しない Access を黙って取得する可能性があるためである.
* さまざまな理由により IdP への Access を失った Subscriber にとって, RP でアカウントを再確立することは非常に困難な場合がある.

<!--
Normative requirements have been established requiring IdPs and RPs to mitigate the problems in this area that are expected to be most common. However, normative requirements are unlikely to have anticipated all potential equity problems. Potential equity problems also will vary for different applications. Accordingly, IdPs and RPs need to provide mechanisms for subscribers to report inequitable authentication requirements and to advise them on potential alternative authentication strategies.
-->

最も一般的であると予想されるこの分野の問題を軽減するため, IdP と RP には規範的要件が確立されている.
しかし規範的要件が全ての潜在的な Equity の問題を想定済であるとは言いづらい.
潜在的な Equity の問題は, アプリケーション毎にも異なる.
従って, IdP と RP は Subscriber が不公平な Authentication 要件を報告し, 潜在的な代替の Authentication 戦略についてアドバイスを行えるようなメカニズムを提供する必要がある.

<!--
This guideline allows the binding of additional federated identifiers to an RP subscriber account to minimize the risk of IdP access loss (see [Sec. 5.4](sec5_federation.md#rp-account)). However, a subscriber might find it difficult to have multiple IdP accounts that are acceptable to the RP at the same time. This inequity can be addressed by having the RP having its own account recovery process that allows for the secure binding and unbinding of multiple federated identifiers from the RP subscriber account.
-->

本ガイドラインは、追加の Federated Identifier を RP Subscriber Account に紐づけることを可能とし, これにより IdP への Access を失った際のリスクが最小化される ([Sec. 5.4](sec5_federation.md#rp-account) 参照).
しかしながら, Subscriber は RP が受け入れることのできる複数の IdP アカウントを同時に持つことが困難である可能性もある.
この不公平性は, RP が独自の Account Recovery プロセスを持ち, RP Subscriber Account と複数の Federated Identifier の紐付けをセキュアに追加・削除可能にすることにより対処可能である.

<!--
RPs need to be aware that not all subscribers will necessarily have access to the same IdPs. The RPs can institute locally authenticated accounts for such subscribers, and later allow binding of those accounts to federated identifiers.
-->

RP は全ての Subscriber が必ずしも同じ IdP への Access を持つとは限らないことを認識する必要がある.
RP はそのような Subscriber に対してローカルで Authenticate された Account を作成し, 後でそれらの Account を Federated Identifier に紐づけることを可能にすることもできる.
