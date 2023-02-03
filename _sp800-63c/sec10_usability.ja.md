---
layout: default.ja
title: Usability
navOrder: 10
navTitle: Usability
permalink: /sp800-63c/usability/
anchor: usability
section: 10
---

# Usability Considerations {#usability}

*This section is informative.*

<!--
_Ergonomic of Human-System Interaction — Part 11: Usability: Definitions and Concepts_ [[ISO/IEC9241-11]](references.md#ref-ISO9241) defines usability as the "extent to which a system, product or service can be used by specified users to achieve specified goals with effectiveness, efficiency and satisfaction in a specified context of use." This definition focuses on users, goals, and context of use as key elements necessary for achieving effectiveness, efficiency and satisfaction. A holistic approach considering these key elements is necessary to achieve usability.
-->

_Ergonomic of Human-System Interaction — Part 11: Usability: Definitions and Concepts_ [[ISO/IEC9241-11]](references.md#ref-ISO9241) は Usability を "特定の利用コンテキストにおいて, 特定のユーザーが, あるシステム, プロダクトないしはサービスを利用して, 特定の目標を, どの程度有効的, 効率的かつ満足のいくレベルで達成できるかの度合い" と定義している.
この定義はユーザー, 目標および利用コンテキストを, 有効性, 効率性および満足度の達成に必要な重要要素として捉えている.
Usability を実現するには, これらの重要要素を考慮した総合的なアプローチが必要となる.

<!--
From the usability perspective, one of the major potential benefits of federated identity systems is to address the problem of user fatigue associated with managing multiple authenticators. While this has historically been a problem with usernames and passwords, the increasing need for users to manage many authenticators — whether physical or digital — presents a usability challenge.
-->

Usability の観点からは, Federated Identity Systemの主な潜在的利点の1つとして, 複数の Authenticator 管理に関するユーザーの苦役に対処できることが挙げられる.
歴史的にこれはユーザー名と Password に関して問題となってきたが, ユーザーが多くの Authenticator (物理的なものも Digital なものも) を管理するニーズが高まるについて, Usability の課題が生じている.

<!--
While many other approaches to authentication have been researched extensively and have well-established usability guidelines, federated identity is more nascent and, therefore, lacks the depth and conclusiveness of research findings. As ongoing usability research matures, usability guidelines for federated identity systems will have stronger supporting data. For example, additional data is needed to support guidance on the translation of technical attribute names and values into user-friendly language.
-->

Authentication に対する多くの他のアプローチが広く研究されており, 十分に確立された Usability ガイドラインも存在するが, Federated Identity はまだ初期段階であり, 従って研究結果の深さや決定性に欠けている.
Usability 研究が進展するにつれ, Federated Identity Systemに対する Usability ガイドラインを発展させるより強力なデータを得ることとなろう.
例えば, 技術的な Attribute 名およびその値をユーザーフレンドリーな言語に翻訳するためのガイドラインの発展には, 追加のデータが必要となる.

<!--
As stated in the usability sections in 800-63A and 800-63B, overall user experience is critical to the success of any authentication method. This is especially true for federated identity systems as federation is a less familiar user interaction paradigm for many users. Users' prior authentication experiences may influence their expectations.
-->

800-63A および 800-63B の Usability の章で述べたように, 全体的なユーザーエクスペリエンスはあらゆる Authentication 方法の成功に不可欠である.
Federation は多くのユーザーにとってあまり馴染みのないユーザーインタラクションの形態であるため, これは特に Federated Identity System に当てはまることである.
ユーザーが過去に経験した Authentication のエクスペリエンスは, 彼らの期待に影響を与える可能性もある.

<!--
The overall user experience with federated identity systems should be as smooth and easy as possible. This can be accomplished by following usability standards (such as the ISO 25060 series of standards) and established best practices for user interaction design.
-->

Federated Identity System における全体のユーザーエクスペリエンスは可能な限りスムースかつ容易であるべきである.
これは Usability 標準 (ISO 25060 シリーズの標準など) と確立されたユーザーインタラクションデザインのベストプラクティスに従うことで実現可能である.

<!--
> Note: In this section, the term "users" means "claimants" or "subscribers." The terms "entity" and "entities" refer to the parties of federated systems.
-->

> Note: 本章では "ユーザー" という用語は "Claimant" ないし "Subscriber" を意味し, "主体" という用語は Federated System 内の当事者を表す.

<!--
Guidelines and considerations are described from the users' perspective.
-->

ガイドラインと考慮事項はユーザーの観点から記述されている.

<!--
Accessibility differs from usability and is out of scope for this volume. [[Section508]](references.md#ref-Section508) was enacted to eliminate barriers in information technology and requires federal agencies to make their electronic and information technology public content accessible to people with disabilities. Refer to Section 508 law and standards for accessibility guidance.
-->

Usability とは異なり, アクセシビリティに関しては本書のスコープ外とする.
[[Section508]](references.md#ref-Section508) は情報技術の障壁を取り除くために制定され, 連邦政府機関に対して電子および情報技術の公開コンテンツを障害を持つ人にもアクセスできるように要求している.
アクセシビリティガイドラインに関しては Section 508 の法律および標準を参照のこと.

## General Usability Considerations

<!--
Federated identity systems should:
-->

Federated Identity System は以下を満たすべきである.

<!--
* Minimize user burden (e.g., frustration, learning curve)
  * Minimize the number of user actions required.
  * Allow users to quickly and easily select among multiple subscriber accounts with a single IdP. For example, approaches such as [Account Chooser](https://openid.net/wg/ac/) allow users to select from a list of subscriber accounts they have accessed in the recent past, rather than start the federation process by selecting their IdP from a list of potential IdPs.
  * Balance minimizing user burden with the need to provide sufficient information to enable users to make informed decisions.
-->

* ユーザー障壁 (e.g., フラストレーションや学習カーブ) の最小化
  * 必要なユーザーアクションを最小化すること.
  * ユーザーが単一の IdP において複数の Subscriber Account のなかから素早く簡単に目的の Account を選択可能とすること. 例えば [Account Chooser](https://openid.net/wg/ac/) のようなアプローチは, ユーザーが直近にアクセスした Subscriber Account のリストから Account を選択することを可能にし, 利用可能な IdP のリストから目的の IdP を選ぶところから Federation プロセスをスタートさせる必要性をなくすことができる.
  * ユーザー障壁の最小化とユーザーが情報に基づいた決定を行うに足りる情報の提供のバランスを取ること.

<!--
* Minimize the use of unfamiliar technical jargon and details (e.g., users do not need to know the terms IdP and RP if the basic concepts are clearly explained).
-->

* なじみのない専門用語や詳細の使用を最小限に抑えること. (e.g., 基本的な概念が明確に説明されている場合, ユーザーは IdP や RP という用語を知る必要はない)

<!--
* Strive for a consistent and integrated user experience across the IdP and RP.
-->

* IdP, RP を通じて一貫性のある統合されたユーザーエクスペリエンスを目指すこと.

<!--
* Help users establish an understanding of identity by providing resources to users such as graphics, illustrations, FAQs, tutorials and examples. Resources  should explain how users' information is treated and how transacting parties (e.g., RPs, IdPs, and brokers) relate to each other.
-->

* 図表, イラスト, FAQ, チュートリアルや例示などを提供し, ユーザーが Identity に対する理解を確立できるよう手助けすること. こういったリソースは, ユーザーの情報がどのように取り扱われ, どのように当事者 (e.g., RP, IdP, Broker) が相互にやりとりを行うかを説明すべきである.

<!--
* Provide clear, honest, and meaningful communications to users (i.e., communications should be explicit and easy to understand).
-->

* ユーザーに対して, 明確, 正直かつ意味のあるコミュニケーションを行うこと. (i.e., コミュニケーションは明確で理解しやすいものであるべきである)

<!--
* Provide users online services independent of location and device.
-->

* 位置やデバイスに依存しないオンラインサービスをユーザーに提供すること.

<!--
* Make trust relationships explicit to users to facilitate informed trust decisions. Trust relationships are often dynamic and context dependent. Users may be more likely to trust some IdPs and RPs with certain attributes or transactions more than others. For example, users may be more hesitant to use federated identity systems on websites that contain valuable personal information (such as financial or health). Depending on the perceived sensitivity of users' personal data, users may be less comfortable with social network providers as IdPs since people are often concerned with the broadcasting nature of social networking implementations.
-->

* 信頼関係をユーザーに明示して, 情報に基づいた信頼の決定を容易にすること. 信頼関係はしばしば動的かつコンテキスト依存である. ユーザーは特定の Attribute ないし Transaction に関わる IdP および RP を他より信頼しやすくなることもある. 例えばユーザーは (財務や健康など) 価値の高い Personal Information を持つ Web サイトにおいて Federated Identity を使うことをより躊躇うかもしれない. ユーザーが Personal Data をセンシティブだと認識している度合いによっては, ユーザーはソーシャルネットワークプロバイダーを IdP として使用することを快適に思わないかもしれない. 人々はしばしばソーシャルネットワーク実装がもつブロードキャストの性質を気にしがちである.

<!--
* Follow the usability considerations specified in [[SP800-63A]](../_sp800-63a/sec9_usability.md#sec9){:latex-href="#ref-SP800-63A"}, Sec. 9 for any user-facing information.
-->

* ユーザーの目に留まる情報に関して, [[SP800-63A]](../_sp800-63a/sec9_usability.md#sec9){:latex-href="#ref-SP800-63A"}, Sec. 9 が規定する Usability の考慮事項に従うこと.

<!--
* Clearly communicate how and where to acquire technical assistance. For example, provide users with information such as a link to an online self-service feature, chat sessions or a phone number for help desk support. Avoid redirecting users back and forth among transacting parties (e.g., RPs, IdPs, and brokers) to receive technical assistance.
-->

* 技術的な支援を受ける方法とその場所を明確に伝えること. 例えばオンラインのセルフサービス機能へのリンク, チャット, ヘルプデスクサポートの電話番号などを提供することなどが考えられる. ユーザーが技術的な支援を受けるために関与する当事者間 (e.g., RP, IdP および Broker) をたらい回しにされる事態は避けること.

<!--
* Perform integrative and continuous usability evaluations with representative users and realistic tasks in an appropriate context to ensure success of federated identity systems from the users' perspectives.
-->

* 適切なコンテキストにおける代表的なユーザーと現実的なタスクを前提に, 統合的かつ継続的な Usalibity 評価を実施し, ユーザーの観点から Federated Identity System の成功を保証すること.

## Specific Usability Considerations

<!--
This section addresses the specific usability considerations that have been identified with federated identity systems. This section does not attempt to present exhaustive coverage of all usability factors related to federated identity systems. Rather it is focused on the larger, more pervasive themes in the usability literature, primarily users' perspectives on identity, user adoption, trust, and perceptions of federated identity space. In some cases, implementation examples are provided. However, specific solutions are not prescribed. The implementations mentioned are examples to encourage innovative technological approaches to address specific usability needs. See standards for system design and coding, specifications, APIs, and current best practices (such as OpenID and OAuth) for additional examples. Implementations are sensitive to many factors that prevent a one-size-fits-all solution.
-->

本セクションでは Federated Identity System 固有の Usalibity に関する考慮事項に述べる.
本セクションは Federated Identity System に関する全ての Usability 要素を網羅しようとしているわけではない.
むしろ, Usablity 文献におけるより大きく普遍的なテーマである, Federated Identity System に関連する Identity, ユーザーによる採用, 信頼および理解に対する, 主としてユーザー視点のテーマに焦点を当てている.
場合によっては実装例が示されることもある.
しかしながら, 具体的な解決策が規定されるわけではない.
言及される実装は, 特定の Usability ニーズに対応するための革新的技術アプローチを促すための例に過ぎない.
その他の例については, システム設計とコーディングの標準, 標準仕様, API 標準および現在のベストプラクティス (OpenID や OAuth など) を参照のこと.
実装例は, 1つで全てを解決する万能なソリューションを妨げるような, 多くの要因を含みがちであることに注意.

### User Perspectives on Online Identity

<!--
Even when users are familiar with federated identity systems, there are different approaches to federated identity (especially in terms of privacy and the sharing of information) that make it necessary to establish reliable expectations for how users' data are treated. Users and implementers have different concepts of identity. Users think of identity as logging in and gaining access to their own private space. Implementers think of identity in terms of authenticators and assertions, assurance levels, and the necessary set of identity attributes to provide a service. Given this disconnect between users' and implementers' concepts of identity, it is essential to help users form an accurate concept of identity as it applies to federated identity systems. A good model of identity provides users a foundation for understanding the benefits and risks of federated systems and encourage user adoption and trust of these systems.
-->

ユーザーが Federated Identity System に慣れている場合でも, Federated Identity に対するアプローチは (特にブライバシーや情報共有という面で) さまざまであり, ユーザーのデータがどのように取り扱われるかについての確度の高い期待を確立する必要がある.
ユーザーと実装者では Identity についての概念が異なる.
ユーザーは Identity をログインして自身のプライベートスペースへの Access を得るものだと考えている.
実装者は Identity を Authenticator と Assertion, Assurance Level, およびサービス提供のための必須な Identity Attribute のセットの観点から考える.
このユーザーと実装者の間の Identity に関する概念の違いを考慮すると, Federated Identity System における Identity の正確な概念をユーザーが理解できるようにすることが不可欠である.
良い Identity モデルは Federated System の利点とリスクを理解するための基盤をユーザーに提供し, ユーザーがこういったシステムを採用し信頼することを促すであろう.

<!--
Many properties of identity have implications for how users manage identities, both within and among federations. Just as users manage multiple identities based on context outside of cyberspace, users must learn to manage their identity in a federated environment. Therefore, it must be clear to users how identity and context are used. The following factors should be considered:
-->

Identity の多くの特性は, ユーザーが1つの Federation 内および複数の Federation 間でどのように Identity を管理するかに影響を与える.
ユーザーは, サイバースペース外のコンテキストに基づき複数の Identity を管理しているように, Federated 環境でも自身の Identity を管理する術を学ばなければならない.
従って, Identity とコンテキストがどのように使われるのかがユーザーにとって明確である必要がある.
ここでは以下のような項目を考慮するべきである.

<!--
* Provide users the requisite context and scope in order to distinguish among different user roles. For example, whether the user is acting on their own behalf or on behalf of another, such as their employer.
-->

* ユーザーに, 異なるユーザーロールを区別するために不可欠なコンテキストとスコープを提供する. 例えばユーザーが自信を代表して行動しているのか, 雇用主など別の誰かのの代理として行動しているのかなど.

<!--
* Provide users unique, meaningful, and descriptive identifiers to distinguish among entities such as IdPs, RPs, and accounts. Any such user-facing identifiers are likely to be in addition to identifiers used by the underlying protocols, which are not normally exposed to the user.
-->

* ユーザーに, 一意で意味のあるわかりやすい識別子を提供し, IdP, RP, Account などの主体を区別できるようにする. ユーザーが目にする識別子は, その下で動くプロトコル内で使用される通常ユーザーの目に触れることのない識別子に加えて使用される可能性がある.

<!--
* Provide users with information on data ownership and those authorized to make changes. Identities, and the data associated with them, can sometimes be updated and changed by multiple actors. For example, some healthcare data is updated and owned by the patient, while some data is only updated by a hospital or doctor's practice.
-->

* ユーザーに, データの所有権および変更を行う権限のある人に関する情報を提供する. Identity およびそれに紐づくデータは, 時には複数の関係者に更新, 変更されることがある. 例えば, 医療データは患者によって更新・所有されるものもあれば, 病院または医者によってのみ更新されるものもある.

<!--
* Provide users with the ability to easily verify, view, and update attributes. Identities and user roles are dynamic and not static; they change over time (e.g., age, health, and financial data). The ability to update attributes or make attribute release decisions may or may not be offered at the same time. Ensure the process for how users can change attributes is well known, documented, and easy to perform.
-->

* ユーザーに, Attribute を簡単に検証, 閲覧, 更新するすべを提供する. Identity およびユーザーロールは静的ではなく動的であるため, 時間経過によって変化しうる (e.g., 年齢, 医療情報, 財務情報). Attribute を更新したりその公開を決定する機能は同時に提供されることもあればされないこともある. ユーザーが Attribute を変更可能なプロセスが, 既知でドキュメント化されており容易に実行可能であることを保証すること.

<!--
* Provide users means for updating data, even if the associated entity no longer exists.
-->

* 関連する主体がもはや存在しない場合においても, ユーザーにデータを更新するすべを提供する. 

<!--
* Provide users means to delete their identities completely, removing all information about themselves, including transaction history. Consider applicable audit, legal, or policy constraints that may preclude such action. In certain cases, full deactivation is more appropriate than deletion.
-->

* ユーザーに, 自身の Identity を完全に削除したり, 自身に関する情報を全て削除したりするすべを提供する. これには Transaction 履歴も含む. なお, このようなアクションを妨げる可能性のある監査, 法律ないしポリシー上の制約がないか考慮すること. 場合によっては削除よりも完全な非アクティブ化が適切である.

<!--
* Provide users with clear, easy-to-find, site/application data retention policy information.
-->

* ユーザーに, 明確で容易に発見可能なサイトデータ/アプリケーションデータ保持ポリシーに関する情報を提供すること.

<!--
* Provide users with appropriate anonymity and pseudonymity options, and the ability to switch among such identity options as desired, in accordance with an organization's data access policies.
-->

* ユーザーに, 組織のデータアクセスポリシーに従って, 適切な匿名性および仮名性のオプション, および必要に応じてそのような Identity オプションを切り替えるすべを提供する.

<!--
* Provide means for users to manage each IdP to RP connection, including complete separation as well as the removal of RP access to one or more attributes.
-->

* ユーザーに, IdP から RP への接続を管理するすべを提供する. これには完全な分離や1つ以上の Attribute への RP の Access の削除などが含まれる.

### User Perspectives of Trust and Benefits

<!--
Many factors can influence user adoption of federated identity systems. As with any technology, users may value some factors more than others. Users often weigh perceived benefits versus risks before making technology adoption decisions. It is critical that IdPs and RPs provide users with sufficient information to enable them to make informed decisions. The concepts of trust and tiers of trust — fundamental principles in federated identity systems — can drive user adoption. Finally, a positive user experience may also result in increased user demand for federation, triggering increased adoption by RPs.
-->

多くの要因が, ユーザーによる Federated Identity System の採用に影響を与える可能性がある.
あらゆるテクノロジーに対する場合と同じように, ユーザーはある要素を他より重視する可能性がある.
ユーザーはしばしばテクノロジーの採用を決定する前に, 目に見えるメリットとリスクを比較検討する.
IdP と RP がユーザーに十分な情報提供を行い, ユーザーが情報に基づいた決定を行えるようにすることが重要である.
信頼および信頼の層 (Federated Identity System の基本原則) はユーザーによる採用を促進しうる.
最後に, プジティブなユーザーエクスペリエンスは Federation に対するユーザーの要求を増大させ, RP による採用増加も引き起こす可能性がある.

<!--
This sub-section is focused primarily on user trust and user perceptions of benefits versus risks.
-->

本セクションでは主にユーザーの信頼およびユーザー視点でのメリットとリスクについて述べる.

<!--
To encourage user adoption, IdPs and RPs need to establish and build trust with users and provide them with an understanding of the benefits and risks of adoption. The following factors should be considered:
-->

ユーザーによる採用を促進するため, IdP と RP はユーザーとの間に信頼を確立し, ユーザーがその採用にかかるメリットとデメリットを理解するように促す必要がある.
ここでは以下のような項目を考慮するべきである.

<!--
* Allow users to control their information disclosure and provide explicit consent through the appropriate use of notifications (see [Sec. 9.2](sec9_privacy.md#notice-and-consent)). Balancing the content, size, and frequency of notifications is necessary to avoid thoughtless user click-through.
-->

* 適切な情報利用通知により, ユーザーが自身の情報開示を制御し明示的な同意提供を行えるようにする ([Sec. 9.2](sec9_privacy.md#notice-and-consent) 参照). ユーザーが無意識にクリックしてしまうことを防ぐため, 通知の内容, サイズ, 頻度のバランスを取ること.

<!--
* For attribute sharing, consider the following:
  * Provide a means for users to verify those attributes and attribute values that will be shared. Follow good security practices (see [Sec. 7.3](sec7_presentation.md#protecting-information) and [Sec. 8](sec8_security.md#security)).
  * Enable users to consent to a partial list of attributes, rather than an all-or-nothing approach. Allow users some degree of online access, even if the user does not consent to share all information.
  * Allow users to update their consent to their list of shared attributes.
  * Minimize unnecessary information presented to users. For example, do not display system generated attributes (such as pairwise pseudonymous identifiers) even if they are shared with the RP as part of the authentication response.
  * Minimize user steps and navigation. For example, build attribute consent into the protocols so they're not a feature external to the federated transaction. Examples can be found in standards such as OAuth or OpenID Connect.
  * Provide effective and efficient redress methods such that a user can recover from invalid attribute information claimed by the IdP or collected by the RP.
  * Minimize the number of times a user is required to consent to attribute sharing. Limiting the frequency of consent requests avoids user frustration from multiple requests to share the same attribute.
-->

* Attribute 共有に関しては以下を考慮すること.
  * ユーザーに, 共有される自身の Attribute および Attribute Value を検証するすべを提供する. 優れたセキュリティプラクティスに従うこと ([Sec. 7.3](sec7_presentation.md#protecting-information) および [Sec. 8](sec8_security.md#security) 参照).
  * ユーザーが All-or-nothing ではなく Attribute リストの一部分にのみ同意できるようにすること. ユーザーが全ての情報共有に同意できない場合でも, ある程度のオンラインアクセスを可能にすること.
  * ユーザーが共有されている Attribute リストへの同意を更新できるようにすること.
  * ユーザーに提示される不必要な情報を最小化する. 例えば, たとえそれが RP に Authentication レスポンスの一環として共有されるとしても, システムによって生成された Attribute (Pairwise Pseudonymous Identifier など) は提示しないなど.
  * ユーザのステップとナビゲーションを最小化する. 例えば, Attribute への同意をプロトコルに組み込み, Federated Transaction の外で実現される機能とはしないなど. そういった例は OAuth や OpenID Connect などの標準の中で見られる.
  * 効果的かつ効率的な是正方法を提供し, IdP が提供したり RP が収集した誤った Attribute 情報を是正できるようにすること.
  * ユーザーが Attribute 共有の際に要求される同意回数を最小化する. 同意要求の頻度を制限することで, 同じ Attribute を共有するための複数の要求に対するユーザーのフラストレーションを避けることができる.

<!--
* Collect information for constrained usage only, and minimize information disclosure (see [Sec. 9.3](sec9_privacy.md#minimization)). User trust is eroded by unnecessary and superfluous information collection and disclosure or user tracking without explicit user consent. For example, only request attributes from the user that are relevant to the current transaction, not for all possible transactions a user may or may not access at the RP.
-->

* 限定された用途にのみ情報を収集し, 情報開示を最小化する ([Sec. 9.3](sec9_privacy.md#minimization) 参照). ユーザーの信頼は, 不必要で余分な情報収集や開示, 明示的なユーザー同意なしに行われるトラッキングなどにより損なわれる. 例えば, 現在の Transaction に関連する Attribute のみをユーザーに要求し, ユーザーが RP で取るか取らないかわからないような全ての Transaction で必要な Attribute に関しては要求しないなど.

<!--
* Clearly and honestly communicate potential benefits and risks of using federated identity to users. Benefits that users value include time savings, ease of use, reduced number of passwords to manage, and increased convenience.
-->

* Federated Identity を利用する際の潜在的なメリットおよびリスクについて, 明確かつ誠意を持ってユーザーに伝える. ユーザーが重視するメリットとしては, 時間の節約, 使いやすさ, 管理する Password の数の削減, 利便性の向上などがあろう.

<!--
User concern over risk can negatively influence willingness to adopt federated identity systems. Users may have trust concerns, privacy concerns, security concerns, and single-point-of-failure concerns. For example, users may be fearful of losing access to multiple RPs if a single IdP is unavailable, either temporarily or permanently. Additionally, users may be concerned or confused about learning a new authentication process. In order to foster the adoption of federated identity systems, the perceived benefits must outweigh the perceived risks.
-->

リスクに対するユーザーの懸念は, Federated Identity System の採用に係る意欲に悪影響を与える可能性がある.
ユーザーは, 信頼に関する懸念, プライバシーに関する懸念, セキュリティに関する懸念, および単一障害点に関する懸念を持つ可能性がある.
例えば, ある1つの IdP が一時的または永続的に利用できない場合, ユーザーは複数の RP への Access を失うことを恐れるかもしれない.
さらに, ユーザーは新しい Authentication プロセスを学ぶことに懸念を感じたり混乱する可能性もある.
Federated Identity System の採用を促進するには, ユーザーの目に見えるメリットがユーザーの目に見えるリスクを上回る必要がある.

### User Mental Models and Beliefs

<!--
Users' beliefs and perceptions predispose them to expect certain results and to behave in certain ways. Such beliefs, perceptions, and predispositions are referred to in the social sciences as mental models. For example, people have a mental model of dining out which guides their behavior and expectations at each establishment, such as fast food restaurants, cafeterias, and more formal restaurants. Thus, it is not necessary to be familiar with every establishment to understand how to interact appropriately at each one.
-->

ユーザーの信念と認識により, ユーザーは特定の結果を期待し, 特定の方法で行動する傾向がある.
このような信念, 認識, 傾向は, 社会科学ではメンタルモデルと呼ばれる.
例えば, ファーストフードレストラン, カフェテリア, よりフォーマルなレストランなど, 人々は施設によって異なる外食のメンタルモデルを持ち, それにより彼らのふるまいや期待が導かれる.
従って, ある施設で適切にやりとりする方法を理解するために, 全ての個別の施設に精通している必要はない.

<!--
Assisting users in establishing good and complete mental models of federation allows users to generalize beyond a single specific implementation. If federated identity systems are not designed from users' perspectives, users may form incorrect or incomplete mental models that impact their willingness to adopt these systems. The following factors should be considered:
-->

ユーザーが Federation に関する優れた完全なメンタルモデルを確立することで, ユーザーは単一かつ特定の実装を超えて一般化することができる.
Federated Identity System がユーザー視点で設計されていなければ, ユーザーは不正確かつ不完全なメンタルモデルを形成し, それがユーザーによるシステムの採用意欲に影響を与えるかもしれない.
ここでは以下のような項目を考慮するべきである.

<!--
* Clearly explain the working relationship and information flow among the transacting parties (e.g., RPs, IdPs, and brokers) to avoid user misconceptions. Use the actual names of the entities in the explanation rather than using the generic terms IdPs and RPs.
  * Provide prominent visual cues and information so that users understand why seemingly unrelated entities have a working relationship. For example, users may be concerned with mixing online personal activities with government services due to a lack of understanding of the information flow in federated identity systems.
  * Provide prominent visual cues and information to users about redirection when an RP needs to redirect control from their site to an IdP. For example, display RP branding within the IdP user interface to inform users when they are logging in with their IdP for access to the destination RP.
-->

* ユーザーの誤解を避けるため, やり取りを行う当事者間 (e.g., RP, IdP および Broker) の関係性や情報の流れを明確に説明する. その際は IdP や RP という一般的な用語ではなく, 当該主体の実際の名称を使用すること.
  * 一見無関係に見える主体がなぜ関係性を持っているのかをユーザーが理解できるように, 明確かつ視覚的なヒントや情報を提供する. 例えば, ユーザーは Federated Identity System における情報の流れを理解していないがために, オンラインでの個人的活動と政府のサービスが混ざることに懸念を抱く可能性がある.
  * RP がユーザーを自身のサイトから IdP にリダイレクトさせる必要がある場合, リダイレクトに関する明確かつ視覚的なヒントや情報を提供する. 例えば, IdP ユーザーインターフェース内に RP ブランドを表示し, ユーザーに当該 RP への Access のため IdP にログインしようとしていることを伝えるなど.

<!--
* Provide users with clear and usable ways (e.g., visual assurance) to determine the authenticity of the transacting  parties (e.g., RPs, IdPs, and brokers). This will also help to alleviate user concern over leaving one domain for another, especially if the root domain changes (e.g., .gov to .com). For example, display the URL of the IdP so that the user can verify that they are not being phished by a malicious site.
-->

* ユーザーに, やり取りを行う当事者 (e.g., RP, IdP および Broker) の Authenticity を判断するための明確で利用しやすい手段 (e.g., 視覚的保証など) を提供する. これは, 特にルートドメインが変わる場合 (e.g., .gov から .com へ) など, あるドメインから別のドメインに移動する際のユーザーの懸念を軽減する際にも役に立つものであろう. 例えば, IdP の URL を表示して, ユーザーが悪意あるサイトに Phishing されていないことを検証できるようにするなど.

<!--
* Provide users with clear information, including visual cues, regarding implicit logins and explicit logouts. Depending on the implementation, logging into an RP with a federated account may authenticate users to both the IdP and RP. Users may not realize that ending their session with the RP will not necessarily end their session with the IdP; users will need to explicitly "log out" of the IdP. Users require clear information to remind them if explicit logouts are required to end their IdP sessions.
-->

* ユーザに, 暗黙的なログインと明示的なログアウトに関して, 視覚的なヒントを含む明確な情報を提供する. 実装によっては, Federated Account を用いて RP にログインすると, ユーザーは IdP と RP 双方に Authenticate される可能性がある. ユーザーは RP で Session を終了しても IdP の Session が終了するとは限らないことに気づいていない場合がある. この場合, ユーザーは IdP から明示的に "ログアウト" する必要がある. ユーザーは IdP Session を終了するために明示的なログアウトが必要かどうか確認するための明確な情報を必要とする.