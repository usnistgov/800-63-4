---
layout: default.ja
title: Digital Identity Risk Management
navOrder: 5
navTitle: DIRM
permalink: /sp800-63/dirm/
anchor: sec5
section: 5
---

# Digital Identity Risk Management {#sec5}

_This section is normative._

<!-- This section provides details on the methodology for assessing digital identity risks for each xAL. This process augments the risk management processes for information and information system risk under NIST guidance for implementing Federal Information Security Modernization Act [[FISMA]](sec8_references.md#ref-FISMA) requirements. -->

本セクションでは, 各 xAL の Digital Identity リスクを評価するための手法の詳細を示す. このプロセスは, Federal Information Security Modernization Act [[FISMA]](sec8_references.md#ref-FISMA) 要件を満たすための NIST ガイダンスに基づく情報および情報システムの Risk Management プロセスを補強するものである. 

<!-- There are 4 steps to the digital identity risk management process: -->

Digital Identity の Risk Management には4つのステップが存在する. 

<!-- 1.	**Conduct Initial Impact Assessment**: In this step, organizations evaluate their user population and assess the impact of a failure of each function in the identity system (i.e., proofing, authentication, and federation) for their protected application or service against a defined set of impact categories. The outcome of this step is a documented set of impact categories and associated impact levels. -->

1.	**初期 Impact Assessment の実施**. このステップでは, 組織はユーザ母集団を評価し, 定義された影響カテゴリーのセットに対して, 保護対象のアプリケーションまたはサービスに対する Identity システムの各機能（例えば Proofing, Authentication, Federation）の障害がもたらす影響を評価する. このステップの成果は, 文書化された一連の影響カテゴリーと関連する影響レベルである. 

<!-- 2.	**Select Initial Assurance Levels**: In this step, the impact categories and impact levels are evaluated to determine the appropriate assurance levels to protect the application. The outcome of this step is an identified initial level for each applicable xAL. -->

2.	**初期 Assurance Levels の選択**: このステップでは, アプリケーションを保護するための適切な Assurance Level を決定するために, 影響カテゴリーと影響度の評価を行う. このステップの成果は, 該当する各 xAL の特定された初期レベルである. 

<!-- 3.	**Tailor and Document Assurance Level Determinations**: In this step, detailed privacy, equity, usability, and threat assessments are conducted to determine the potential impact of the initially selected assurance level on the specific user population and threat environment of the application. The initial assurance level is tailored, compensating or supplemental controls are identified, and all decisions are documented. The outcome is a Digital Identity Acceptance Statement (see [Sec. 5.3.4](sec5_DIRM.md#IDacceptStmt)) with a defined implementable assurance level. -->

3.	**Assurance Level の決定の調整と文書化**: このステップでは, Privacy, Equity, Usability, 及び脅威に関する詳細なアセスメントを実施し, 最初に選択した Assurance Level が, アプリケーションの特定のユーザ母集団及び脅威環境に与えうる影響を判断する. 最初の Assurance Level は調整され, 補償または補足のコントロールが特定され, すべての決定が文書化される. 成果は, 実装可能な Assurance Level を定義した Digital Identity Acceptance Statement ([Sec. 5.3.4](sec5_DIRM.md#IDacceptStmt) 参照) となる. 

<!-- 4.	**Continuously Evaluate & Improve**: In this step, information is collected on performance of the identity system across a diverse set of factors based on organization needs and evolving threat vectors. This information is used to determine if the selected assurance level and controls are meeting mission, business, and security needs and to monitor for unintended harms that may have emerged. The outcomes of this step are performance metrics, documented and transparent processes for evaluation and redress, and ongoing improvements to the identity system as needed. -->

4.	**継続的な評価と改善**: このステップでは, 組織のニーズと進化する脅威ベクトルに基づく, 多様な事実に基づく Identity システムのパフォーマンスに関する情報が収集される. この情報は, 選択した Assurance Level およびコントロールがミッション, ビジネス, およびセキュリティのニーズを満たしているかどうかを判断し, 生じている可能性のある意図しない被害を監視するために使用される. このステップの成果は, パフォーマンス指標, 評価および救済のための文書化された透明性のあるプロセス, および必要に応じた Identity システムの継続的な改善である. 

<!-- While presented as a “stepwise” approach, there can be many points in the process that require divergence from the sequential order, including the need for iterative cycles between initial task execution and revisiting tasks. For example, the introduction of new regulations or requirements while an assessment is ongoing may require organizations to revisit a step in the process. Additionally new functionality, changes in data usage, and changes to the threat environment may at any point require an organization to revisit steps in the digital identity risk management process. -->

"段階的" アプローチとして提示されているが, 最初のタスクの実行とタスクの再検討の間の反復サイクルの必要性など, プロセスには順次順序からの分岐を必要とする多くのポイントが存在し得る. 例えば, 評価を進めている最中に新しい規制や要件が導入された場合, 組織はプロセスのステップを再検討する必要が生じることがある. さらに, 新しい機能, データ使用の変更, および脅威環境の変更により, 組織はいつでも Digital Identity Risk Management プロセスのステップを再検討する必要が生じる可能性がある. 

<!-- Organizations **SHOULD** adapt and modify this overall approach to meet organizational processes, governance, and integration with enterprise risk management practices. At a minimum, organizations **SHALL** ensure that each step is executed and the normative mandates and outcomes of each step are completed and documented regardless of operational approach and enabling tools. -->

組織は, 組織のプロセス, ガバナンス, 及び企業 Risk Management のプラクティスとの統合に合わせて, この全体的なアプローチを適応及び修正すべき(**SHOULD**)である. 最低限, 組織は, 運用方法や実現手段にかかわらず, 各ステップを確実に実行し, 各ステップの規範的な義務及び成果を完了し, 文書化しなければならない（**SHALL**）. 

## Conduct Initial Impact Assessment {#intlAssess}

<!-- The purpose of the initial impact analysis is to identify the potential adverse impacts of failures in identity proofing, authentication, and federation specific to an RP application or service, yielding an initial set of assurance levels. Assessing these areas separately allows organizations maximum flexibility in developing or acquiring a digital identity service that best enables them to successfully deliver on mission objectives. -->

初期影響分析の目的は, RP アプリケーションまたはサービスに固有の Identity Proofing, Authentication, および Federation における障害の潜在的な悪影響を特定し, 最初の Assurance Level のセットをもたらすことである. これらの分野を個別に評価することにより, 組織は, ミッション目標を成功させるために最も有効な Digital Identity サービスを開発または獲得する上で, 最大限の柔軟性を得ることができる. 

<!-- The impact assessment includes: -->

影響調査の内容は以下の通り:

<!-- - Identifying impacted entities,
- Identifying a set of impact categories for which harms will be assessed,
- Identifying potential harms for each of the impact categories,
- Identifying the levels of impact those potential harms would inflict should failures occur, and
- Assessing the impact of each type of failure (proofing, authentication, and federation) and the resulting impact level to all affected entities. -->

- 影響を受ける主体の特定,
- 被害を評価する対象となる一連の影響カテゴリーの特定,
- 影響カテゴリーのそれぞれについて, 潜在的な被害を特定,
- 障害が発生した場合に, それらの潜在的な被害が与える影響のレベルの特定, ならびに
- 各タイプの障害（ Proofing, Authentication, Federation ）の影響の評価と, 影響を受けるすべての主体への影響レベルの評価. 

<!-- The output of this assessment is a defined impact level &mdash; High, Moderate, or Low &mdash; for each possible type of failure. This serves as the primary input to the initial assurance level selection. -->

この Assessment のアウトプットは, 起こりうる障害の種類ごとに定義された影響度（高, 中, 低）である. これは, 最初の Assurance Level を選択するための主要なインプットとなる.

### Identify Impacted Entities {#impctEnt}

<!-- When assessing impacts, an organization needs to determine the entities that will be impacted by the application or transaction under consideration. As mentioned earlier in this guideline, it is imperative to consider the impact on different entities resulting from a failure of the digital identity system. Of particular importance is ensuring that the potential impacts to individuals are considered alongside those of the enterprise. -->

影響を評価するとき, 組織は検討中のアプリケーションまたは Transaction によって影響を受ける主体を決定する必要がある. このガイドラインで前述したように, Digital Identity システムの障害によって生じる異なる主体への影響を考慮することが不可欠である. 特に重要なのは, 個人に対する潜在的な影響を, 企業の影響と並んで考慮することである. 

<!-- Accordingly, impact assessments **SHALL** include individuals using the system or application in addition to the organization itself. Additionally, organizations **SHOULD** identify other entities, such as mission partners, communities, and those identified in [[SP800-30]](sec8_references.md#ref-SP800-30), that need to be specifically included based on mission and business needs. At a minimum, agencies **SHALL** document all entities to which impacts will be assessed when conducting their impact analysis. -->

したがって, 影響評価には, 組織自身に加えて, システムまたはアプリケーションを使用する個人を含めなくてはいけない(**SHALL**). さらに組織は, ミッションパートナー, コミュニティ, [[[SP800-30]](sec8_references.md#ref-SP800-30)で特定された主体など, ミッションとビジネスの必要性に基づいて特に含める必要があるその他の主体を特定するべきである(**SHOULD**). 少なくとも, 機関は影響度分析を実施する際に, 影響が評価されるすべての主体を文書化しなければならない(**SHALL**). 

<!-- The outcome of this activity is a list of entities subject to the application or transaction under consideration for whom impacts will be assessed. -->

この活動の成果は, 影響を評価する検討中の申請または取引の対象となる主体のリストである. 

### Identify Impact Categories and Potential Harms {#impactCatHarms}

<!-- Initial assurance levels for digital transactions **SHALL** be determined by assessing the potential impact of, at a minimum, each of the following categories: -->

Digital Transaction の初期 Assurance Level は, 少なくとも以下の各カテゴリーの潜在的な影響を評価することにより決定されなければいけない(**SHALL**). 

<!--
  - Damage to mission delivery
  - Damage to trust or reputation
  - Loss of sensitive information
  - Damage to or loss of economic stability
  - Loss of life or damage to safety, health, or  environmental stability
  - Noncompliance with laws, regulations, and/or contractual obligations
-->

  - Damage to mission delivery / ミッション遂行に対する損害
  - Damage to trust or reputation / 信用や評判に対する損害
  - Loss of sensitive information / 機密情報の損失
  - Damage to or loss of economic stability / 経済的安定の損害又は損失
  - Loss of life or damage to safety, health, or  environmental stability / 生命の損失, 安全・健康・環境的安定に対する損害
  - Noncompliance with laws, regulations, and/or contractual obligations / 法律, 規制, 契約上の義務のすべて, または一部の不履行

<!-- Organizations **SHOULD** include additional impact categories as appropriate based on their mission. Each impact category **SHALL** be documented and consistently applied across different applications assessed by the organization. -->

組織は, そのミッションに基づき適切な範囲で追加の影響カテゴリーを含めるべきである(**SHOULD**). 各影響区分は, 文書化し, 組織が評価するさまざまなアプリケーションに一貫して適用しなければならない(**SHALL**). 

<!-- Harms are any adverse effects that would be experienced by an entity. They provide a means to more effectively understand the impact categories and how they may apply to specific entities associated with that application. Agencies **SHOULD** consider specific harms for each of the defined impact categories to better inform their impact analysis. Identification of harms for each category **SHALL** be done for each of the entities identified during "entity identification" process. -->

被害とは, ある主体が経験するであろうあらゆる有害な影響のことである. 被害は, 影響分類をより効果的に理解するための手段であり, 影響分類がその用途に関連する特定の主体にどのように適用され得るかを示すものである. 機関は, 影響度分析をより適切に行うため, 定義された影響度分類のそれぞれについて, 具体的な被害を検討すべきである(**SHOULD**). 各区分に対する損害の特定は, 「主体の特定」プロセスで特定された各主体に対して行われなければいけない(**SHALL**). 

<!-- Examples of harms associated with each category include, but are not limited to: -->

各カテゴリーに関連する被害の例としては, 以下のものが挙げられるが, これらに限定されるものではない.

<!-- Damage to mission delivery: -->

Damage to mission delivery / ミッション遂行に対する損害

<!--
  - Harms to individuals may include the inability to access government services or benefits for which they are eligible.
  - Harms to the organization may include an inability to perform current mission/business functions in a sufficiently timely manner, with sufficient confidence and/or correctness, within planned resource constraints, or an inability, or limited ability, to perform mission/business functions in the future.
-->

  - 個人に対する被害には, 本来受けられるはずの行政サービスや 福利厚生が受けられなくなることが挙げられる. 
  - 組織に対する被害には, 現在のミッション／ビジネス機能を, 十分な信頼性及び／又は正確性をもって, 計画されたリソースの制約の範囲内で, 十分にタイムリーに実行できないこと, 又は将来的にミッション／ビジネス機能を実行できないこと, 若しくは能力が限定されることが挙げられる. 

<!-- Damage to trust or reputation: -->

Damage to trust or reputation / 信用や評判に対する損害

<!--
  - Harms to individuals may include impersonation or damage to image or reputation.
  - Harms to the organization may include damage to trust relationships, image, or reputation including future, potential trust relationships.
-->

  - 個人に対する被害には, なりすましやイメージ・評判の悪化などが挙げられる. 
  - 組織に対する被害には, 信頼関係, イメージ, または評判（将来的, 潜在的な信頼関係を含む）の低下が挙げられる. 

<!-- Loss of sensitive information: -->

Loss of sensitive information / 機密情報の損失

<!--
  - Harms to individuals includes loss of PII or other sensitive information, which may result in secondary harms such as loss of economic stability, loss of life, physical or psychological injury, impersonation, identity theft, or persistent inconvenience.
  - Harms to the organization may include loss or degradation of intellectual property or other information assets such as classified materials or controlled unclassified information (CUI).
-->

  - 個人に対する被害には, PII やその他の機密情報の損失が含まれ, その結果, 経済的安定の損失, 生命の損失, 身体的または心理的傷害, なりすまし, Identityの盗難, または持続的な不都合などの二次的被害が挙げられる.
  - 組織に対する被害には, 知的財産や, 機密資料や管理された非機密情報（Controlled Unclassified Information / CUI）などの情報資産の損失や劣化が挙げられる.

<!-- Damage to or loss of economic stability: -->

Damage to or loss of economic stability / 経済的安定の損害又は損失

<!--
  - Harms to individuals may include debts incurred or assets lost as a result of fraud or other harm, damage to or loss of credit, actual or potential employment, or sources of income, and/or other financial loss.
  - Harms to the organization may include costs incurred related to fraud or other criminal activity, loss of assets, devaluation, or loss of business.
-->

  - 個人に対する被害には, 詐欺やその他の被害により発生した債務や資産の喪失, 信用, 実際のまたは潜在的な雇用, 収入源の損傷や喪失, および/またはその他の経済的損失が挙げられる. 
  - 組織に対する被害には, 詐欺やその他の犯罪行為に関連して発生した費用, 資産の損失や価値の低下, 事業損失などが挙げられる. 

<!-- Loss of life or damage to safety, health, or environmental stability: -->

Loss of life or damage to safety, health, or  environmental stability / 生命の損失, 安全・健康・環境的安定に対する損害

<!--
  - Harms to individuals may include death, damage to or loss of physical, mental, or emotional well-being, damage to the environment, or loss of accessible, affordable housing.
  - Harms to the organization may include damage to or loss of the organization's workforce or the impact of unsafe conditions rendering the organization unable to operate or operating at reduced capacity.
-->

  - 個人に対する被害には, 死亡, 身体的・精神的・情緒的な健康への損害または損失, 環境への損害, またはアクセス可能で安価な住宅の損失が挙げられる. 
  - 組織に対する被害には, 組織の労働力に対する損害や損失, 安全でない状況による組織の運営不能や能力低下などの影響が挙げられる. 

<!-- Noncompliance with laws, regulations, and/or contractual obligations: -->

Noncompliance with laws, regulations, and/or contractual obligations / 法律, 規制, 契約上の義務のすべて, または一部の不履行

<!--
  - Harms to individuals may include damage to or loss of economic stability, safety, privacy, civil liberties, equity, and/or usability due to violations of local, state, and federal laws, regulations, and/or contractual obligations.
  - Harms to the organization may include financial costs, sanctions, liability, etc, due to noncompliance with applicable laws, regulations, contractual requirements, or other requirements in other binding agreements.
-->

  - 個人に対する被害には, 地域・州・連邦の法律, 規制, 契約上の義務のすべてまたは一部の違反による, 経済的安定, 安全, プライバシー, 市民の自由, Equity, Usability のすべてまたは一部への損害や損失が挙げられる. 
  - 組織に対する被害には, 適用される法律, 規制, 契約上の要件, または他の拘束力のある契約における他の要件の不遵守に起因する金銭的コスト, 制裁, 責任などが挙げられる. 

<!-- The outcome of this activity will be a list of impact categories and harms which will be used to assess impacts to identified entities. -->

この活動の成果は, 特定された主体への影響を評価するために使用される影響カテゴリーと被害のリストとなる. 

### Identify Potential Impact Levels {#impLvls}

<!-- Initial assurance levels for digital transactions are determined by assessing the potential impact a failure would have on each of the categories from [Sec. 5.1.2](sec5_DIRM.md#impactCatHarms) using one of the following potential impact values: -->

Digital Transaction の Assurance Level は, [Sec. 5.1.2](sec5_DIRM.md#impactCatHarms) の各カテゴリーで障害が発生した場合の影響を, 以下の潜在的影響値のいずれかを用いて評価することで決定される. 

<!-- 1. Low potential impact: could be expected to have a limited adverse effect
2. Moderate potential impact: could be expected to have a serious adverse effect
3. High potential impact: could be expected to have a severe or catastrophic adverse effect -->

1. 潜在的影響 Low: 悪影響が限定的であると予想される場合
2. 潜在的影響 Moderate: 重大な悪影響を及ぼすと予想される場合
3. 潜在的影響 High: 深刻または壊滅的な悪影響を及ぼすと予想される場合

<!-- > Note: If a failure in the identity system causes no measurable consequences for a category, there is no impact. -->

> 注: Identity システムの障害がカテゴリに測定可能な結果をもたらさない場合は影響はない. 

<!-- Each assurance level, IAL, AAL, and FAL (if accepting or asserting a federated identity) **SHALL** be evaluated separately. Ideally, any evaluation will include different viewpoints such as harm to individuals, the organization, other organizations, and the nation as applicable to successful delivery of the organization's mission. Examples of potential impacts in each of the categories include: -->

各 Assurance Level, IAL, AAL, および FAL（Federated Identityを受け入れる, または Asserting する場合）は個別に評価しなくてはいけない(**SHALL**). 理想的には, どのような評価にも, 個人, 組織, 他の組織, および国に対する被害など, 組織のミッションを成功裏に遂行するために適用可能なさまざまな視点が含まれるようにする. 各カテゴリーにおける潜在的な影響の例としては, 以下が挙げられる. 

**Damage to mission delivery:**

<!-- - **Low**: at worst, slight outcome disparities exist between individuals that participate in federally funded programs and those that are eligible but unable to participate, or a limited adverse effect on organizational operations or assets, or public interests. Examples of limited adverse effects are: mission capability degradation to the extent and duration that the organization is able to perform its primary functions with noticeably reduced effectiveness, or minor damage to organizational assets or public interests. -->

- **Low**: 最悪の場合で, 連邦政府が資金提供するプログラムに参加する個人と, 参加資格はあるが参加できない個人との間にわずかな結果の格差が存在すること, または組織の運営や資産, あるいは公共の利益に限定的な悪影響がある場合. 限定的な悪影響の例としては, 組織がその主要機能の有効性を顕著に低下させても遂行できる範囲と期間のミッション能力の低下, または組織の資産や公共の利益に対する軽微な損害が挙げられる. 

<!-- - **Moderate**: at worst, outcome disparities are evident between individuals that participate in federally funded programs and those that are eligible but unable to participate, or a serious adverse effect on organizational operations or assets, or public interests. Examples of serious adverse effects are: significant mission capability degradation to the extent and duration that the organization is able to perform its primary functions with significantly reduced effectiveness; or significant damage to organizational assets or public interests. -->

- **Moderate**: 最悪の場合で, 連邦政府が資金提供するプログラムに参加する個人と, 参加資格はあるが参加できない個人との間に結果の格差が明らかになる, または, 組織の運営や資産, あるいは公共の利益に深刻な悪影響が及ぶ場合. 深刻な悪影響の例としては, 組織がその主要機能を著しく低下した状態で遂行できる範囲と期間の重大な任務能力の低下, または組織の資産や公共の利益に対する重大な損害が挙げられる. 

<!-- - **High**: outcome disparities endure across communities, indicating a systemic pattern of exclusion, avoidance, or other barriers to participation in federally funded programs, or a severe or catastrophic adverse effect on organizational operations or assets, or public interests. Examples of severe or catastrophic effects are: severe mission capability degradation or loss to the extent and duration that the organization is unable to perform one or more of its primary functions; or major damage to organizational assets or public interests. -->

- **High**: 地域社会全体で成果の格差が続いており, 連邦政府が資金提供するプログラムへの参加に対する排除, 回避, その他の障壁の体系的パターンを示している場合, または組織の運営や資産, あるいは公共の利益に深刻または壊滅的な悪影響を及ぼしている場合. 深刻または壊滅的な影響の例としては, 組織が1つ以上の主要機能を果たせないほど深刻な任務能力の低下または喪失, あるいは組織の資産または公共の利益に対する大きな損害が挙げられる. 

**Damage to trust and reputation:**

<!-- - **Low**: at worst, limited, short-term inconvenience, distress, or embarrassment to any party. -->

- **Low**: 最悪の場合で, いかなる主体に対しても, 限られた短期間の不便, 苦痛, 困惑を与える場合.

<!-- - **Moderate**: at worst, serious short-term or limited long-term inconvenience, distress, or damage to the standing or reputation of any party. -->

- **Moderate**: 最悪の場合で, 短期的または限定的な重大な不便, 苦痛, または主体の地位や評判に対する損害が発生する場合.

<!-- - **High**: severe or serious long-term inconvenience, distress, or damage to the standing or reputation of any party. This is ordinarily reserved for situations with particularly severe effects or which potentially affect many individuals. -->

- **High**: 主体の地位や評判に深刻なまたは重大な長期的不便, 苦痛, または損害が発生する場合. これは通常, 特に深刻な影響を及ぼす状況, または多くの個人に影響を及ぼす可能性のある状況にのみ適用される. 

**Loss of sensitive information:**

<!-- - **Low**: at worst, a limited release of personal, U.S. government sensitive, or commercially sensitive information to unauthorized parties resulting in a loss of confidentiality with a low impact as defined in [[FIPS199]](sec8_references.md#ref-FIPS199). -->

- **Low**: 最悪の場合で, [[FIPS199]](sec8_references.md#ref-FIPS199) で定義されているように, Personal Information, 米国政府の機密情報, 商業上の機密情報が権限のない者に限定的に開示され, 影響が少なく機密性が損なわれる場合.

<!-- - **Moderate**: at worst, a release of personal, U.S. government sensitive, or commercially sensitive information to unauthorized parties resulting in loss of confidentiality with a moderate impact as defined in [[FIPS199]](sec8_references.md#ref-FIPS199). -->

- **Moderate**: 最悪の場合で, [[FIPS199]](sec8_references.md#ref-FIPS199) で定義されているように, Personal Information, 米国政府の機密情報, 商業上の機密情報が不正な者に漏洩し, 機密性が失われ中程度の影響を与える場合.

<!-- - **High**: a release of personal, U.S. government sensitive, or commercially sensitive information to unauthorized parties resulting in loss of confidentiality with a high impact as defined in [[FIPS199]](sec8_references.md#ref-FIPS199). -->

- **High**: Personal Information, 米国政府の機密情報, 商業上の機密情報が不正に流出し, [[FIPS199]](sec8_references.md#ref-FIPS199) に定義されているように, 高い影響を与える機密性の喪失をもたらす場合.

**Damage to or loss of economic stability:**

<!-- - **Low**: at worst, an insignificant or inconsequential financial loss to any party.
- **Moderate**: at worst, a serious financial loss to any party.
- **High**: severe or catastrophic financial loss to any party. -->

- **Low**: 最悪の場合で, いかなる主体にとっても, 軽微な, あるいは重要でない金銭的損失となる場合
- **Moderate**: 最悪の場合で, いかなる主体にとっても深刻な経済的損失となる場合
- **High**: いかなる主体に対しても, 深刻または破滅的な金銭的損失となる場合

**Loss of life or damage to safety, health, or environmental stability:**

<!-- - **Low**: at worst, minor injury or acute health issue that resolves itself and does not require medical, including mental health, treatment; limited risk of environmental impact in locality where program operations take place.
- **Moderate**: at worst, moderate risk of minor injury or limited risk of injury requiring medical, including mental health, treatment; or the compounding impact of multiple low impact events; moderate risk of environmental impact in locality where program operations take place.
- **High**: a risk of serious injury, trauma, or death; or the compounding impact of multiple moderate impact events; high risk of environmental impact in locality where program operations take place. -->

- **Low**: 最悪の場合で, 自然治癒し, 精神衛生を含む医学的治療を必要としない軽傷または急性の健康問題, プログラム運用が行われる地域での環境影響の限定的なリスクの場合
- **Moderate**: 最悪の場合で, 軽傷の中程度のリスク, または精神衛生を含む医療処置を必要とする傷害の限定的なリスク, または複数の低影響事象の複合的影響, プログラム運用が行われる地域での環境影響の中程度のリスクの場合
- **High**: 重傷, 外傷, 死亡のリスク, または複数の中程度の影響の複合的影響, プログラム運用が行われる地域での環境影響が高リスクの場合

**Noncompliance with laws, regulations, and/or contractual obligations:**

<!-- - **Low**: at worst, a risk of civil or criminal violations of a nature that would not ordinarily be subject to enforcement efforts, or at worst, an insignificant or inconsequential organization liability.
- **Moderate**: at worst, a risk of civil or criminal violations that may be subject to enforcement efforts, or a serious organization liability.
- **High**: a risk of civil or criminal violations that are of special importance to enforcement programs, or severe or catastrophic organization liability. -->

- **Low**: 最悪の場合で, 通常は執行努力の対象とならない性質の民事上または刑事上の違反のリスク, あるいは最悪の場合で, 軽微なまたは重大でない組織上の責任が生じる場合.
- **Moderate**: 最悪の場合で, 強制捜査の対象となる民事・刑事上の違反のリスク, あるいは深刻な組織責任を負うことになる場合.
- **High**: 執行プログラムにとって特に重要な民事上または刑事上の違反, あるいは深刻なまたは壊滅的な組織の責任となるリスクがある場合.

### Impact Analysis {#impAnalysis}

<!-- The impact analysis helps determine the extent to which risk must be mitigated by the identity proofing, authentication, and federation processes. These determinations drive the relevant choices of applicable technologies and mitigation strategies, rather than the desire for any given technology driving risk determinations. -->

影響分析により, Identity Proofing, Authentication, および Federation プロセスによってどの程度までリスクを軽減しなければならないかが決定される. こういった決定は, リスク明確化に役立つ技術への欲求を引き起こすものではなく, 適用可能な技術とリスク軽減策の選択を推進するものである.

<!-- To determine the appropriate level of assurance of the user's asserted identity, organizations **SHALL** assess the potential risks and identify measures to minimize their impact. Organizations **SHALL** assess the risk of identity proofing, authentication, and federation failures separately to determine the required assurance level for each transaction. This process **SHALL** include consideration of potentially varying impacts of harms to different entities impacted by the digital identity system, as described in [Sec. 5.1.1](sec5_DIRM.md#impctEnt). Business processes, policies, and technologies may help reduce risk. Entities **SHOULD** consider the impact of specific modes of failures related to identity proofing, authentication, and federation this includes, but may not be limited to: -->

ユーザーの Asserted Identity の適切な Assurance Level を決定するため, 各組織は潜在リスクを評価し, その影響を最小限に抑える手段を特定する必要がある (**SHALL**). 組織は, 各 Transaction に必要な Assurance Level を決定するために, Identity Proofing, Authentication, および Federation の障害のリスクを個別に評価する. このプロセスには, [Sec. 5.1.1](sec5_DIRM.md#impctEnt) に記載されているように, Digital Identity システムの影響を受ける異なる主体に対する潜在的に異なる被害の影響を考慮することが含まなくてはいけない(**SHALL**). ビジネス・プロセス, ポリシー, および技術は, リスクの軽減に役立つ場合がある. 主体は, Identity Proofing, Authentication, および Federation に関連する特定の障害モードの影響を考慮するべきである(**SHOULD**)（ただし, これらに限定されない）. 

**Identity Proofing:**

<!-- - The impact of providing a service to the wrong subject (e.g., an attacker successfully proofs as someone else).
- The impact of not providing service to an eligible subject due to barriers, including biases, faced by the subject throughout the process of identity proofing.
- The impact of excessive information collection and retention to support identity proofing processes. -->

- サービスを異なる Subject に提供してしまうことによる影響. (例: Attacker が他人になりすませてしまう)
- Identity Proofing の過程で Subject が受ける偏見を含む障壁のために, 適格な Subject にサービスが提供されないことによる影響. 
- Identity Proofing プロセスをサポートするための過剰な情報収集と保持の影響. 

**Authentication:**

<!-- - The impact of authenticating the wrong subject (e.g., an attacker who compromises or steals an authenticator).
- The impact of failing to authenticate the correct subject due to barriers, including biases, faced by the subject in presenting their authenticator. -->

- 誤った Subject を Authenticating した場合の影響（例: Attacker が Authenticator を不正に利用する, または盗むなど）. 
- Subject が Authenticator を提示する際に直面する偏見などの障壁により, 正しい Subject の Authenticate に失敗した場合の影響. 

**Federation:**

<!-- - The impact of the wrong subject successfully accessing an application, system, or data (e.g., compromising or replaying an assertion).
- The impact of releasing subscriber attributes to the wrong application or system. -->

- 誤った Subject がアプリケーション, システム, またはデータへのアクセスに成功した場合の影響（例: Assertionの侵害や Replay など）. 
- Subscriber Attribute を誤ったアプリケーションやシステムに開示した場合の影響. 

<!-- Using a worksheet similar to [Table 1](sec5_DIRM.md#table-1) can assist organizations with compiling the information gathered in order to complete the analysis. This kind of analysis would be done for each type of potential failure for identity proofing, authentication, and federation to determine the overall risks to entities interacting with the digital identity system. -->

[Table 1](sec5_DIRM.md#table-1) のようなワークシートを使用すると, 分析を完了するために収集した情報をまとめる際に組織を支援することができる. この種の分析は Digital Identity システムとインタラクションする主体に対する全体的なリスクを判断するために, Identity Proofing, Authentication, および Federation に対する潜在的な障害の種類ごとに行うことになる. 

[Table 1 Impact Categories](sec5_DIRM.md#table-1){:name="table-1"}
{:latex-ignore="true"}

<!-- | Impact Categories | Harm to Individuals | Harm to the Organization | (Other harm categories) | Combined Impact Level |
| :--- | :----: | :----: | :----: | :----: |
| Damage to mission delivery | L / M / H | L / M / H | L / M / H |   |
| Damage to trust or reputation | L / M / H | L / M / H | L / M / H |   |
| Loss of sensitive information | L / M / H | L / M / H | L / M / H |   |
| Damage to or loss of economic stability | L / M / H | L / M / H | L / M / H |   |
| Loss of life or damage to safety, health, or environmental stability | L / M / H | L / M / H | L / M / H |   |
| Noncompliance with laws, regulations, and/or contractual obligations | L / M / H | L / M / H | L / M / H |   |
{:latex-table="1" latex-caption="Impact Categories" latex-columns="p@0.20\textwidth,p@0.15\textwidth,p@0.15\textwidth,p@0.15\textwidth,p@0.15\textwidth"} -->

| 影響カテゴリー | 個人への被害 | 組織への被害 | (その他の被害カテゴリー) | 複合的な影響レベル |
| :--- | :----: | :----: | :----: | :----: |
| Damage to mission delivery | L / M / H | L / M / H | L / M / H |   |
| Damage to trust or reputation | L / M / H | L / M / H | L / M / H |   |
| Loss of sensitive information | L / M / H | L / M / H | L / M / H |   |
| Damage to or loss of economic stability | L / M / H | L / M / H | L / M / H |   |
| Loss of life or damage to safety, health, or environmental stability | L / M / H | L / M / H | L / M / H |   |
| Noncompliance with laws, regulations, and/or contractual obligations | L / M / H | L / M / H | L / M / H |   |
{:latex-table="1" latex-caption="Impact Categories" latex-columns="p@0.20\textwidth,p@0.15\textwidth,p@0.15\textwidth,p@0.15\textwidth,p@0.15\textwidth"}

<!-- The output of this step is a defined impact level for failures of identity proofing, authentication, and federation which serve as the primary input to the initial assurance level selection. -->

このステップの成果は, Identity Proofing, Authentication, および Federation の失敗に対する影響レベルを定義したもので, 最初の Assurance Level 選択の主要な入力として機能するものである. 

## Select Initial Assurance Levels
<!-- The impact analysis serves as a primary input to the process of selecting initial assurance levels for identity proofing, authentication and federation. The assurance levels may differ across these areas based on the analysis of the potential impact of failures in each area. The purpose of these initial assurance levels is to identify baseline digital identity controls and processes, reflected in the requirements and guidelines in the companion volumes of [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP-800-63A"}, [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP-800-63B"}, and [[SP800-63C]](../_sp800-63c/sec1_purpose.md#purpose){:latex-href="#ref-SP-800-63C"}, which will be assessed and tailored based on mission need, cybersecurity risk, and other potential impacts to the organization and users of the digital identity systems. -->

影響分析は, Identity Proofing, Authentication, および Federation の初期 Assurance Level を選択するプロセスの主要な入力として機能する. Assurance Level は各エリアでの障害の潜在的な影響の分析に基づいて, これらのエリア間で異なる場合がある. これらの初期 Assurance Level の目的は, [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP-800-63A"}, [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP-800-63B"}, および [[SP800-63C]](../_sp800-63c/sec1_purpose.md#purpose){:latex-href="#ref-SP-800-63C"} の付属巻の要件およびガイドラインに反映される, 基本的な Digital Identity 制御およびプロセスを識別することであり, これらはミッションの必要性, サイバーセキュリティリスク, および組織と　Digital Identity システムのユーザに対するその他の潜在的な影響に基づいて評価および調整される. 

### Assurance Levels

<!-- An organization RP **SHALL** select, based on cybersecurity risk and mission needs, the following individual initial assurance levels: -->

組織 RP は, サイバーセキュリティリスクとミッションの必要性に基づいて, 以下の個々の初期 Assurance Level を選択しなければならない(**SHALL**). 

<!-- * **IAL**: The robustness of the identity proofing process to confidently determine the identity of an individual. IAL is selected to mitigate potential identity proofing failures.
* **AAL**: The robustness of the authentication process itself, and the binding between an authenticator and a specific individual's identifier. AAL is selected to mitigate potential authentication failures.
* **FAL**: The robustness of the federation process used to communicate authentication and attribute information (if applicable) to an RP from an IdP. FAL is optional as not all digital systems will leverage federated identity architectures. FAL is selected to mitigate potential federation failures. -->

* **IAL**: 個人の Identity を確信を持って決定するための Identity Proofing プロセスの頑強性. IAL は潜在的 Identity Proofing の失敗を軽減することを目的に選択される.
* **AAL**: Authentication プロセス自体, および Authenticator と特定個人の識別子の紐付けの頑強性. AAL は Authentication 失敗を軽減することを目的に選択される.
* **FAL**: IdP から RP に Authentication および Attribute 情報（該当する場合）を伝達するために使用される Federation プロセスの頑強性. すべての Digital システムが Federated Identity アーキテクチャーを採用する訳ではないため, FAL はオプションである. FAL は Federation の失敗を軽減することを目的に選択される.

### xAL Descriptions

<!-- A summary of each of the identity, authenticator, and federation assurance levels is provided below. -->

Identity, Authenticator, Federation Assurance Level の概要はそれぞれ以下にまとめる.

<!-- When described generically or bundled, these guidelines will refer to IAL, AAL, and FAL as **_xAL_**. -->

総称的ないしは一括で扱う場合, 本ガイドラン群では IAL, AAL, FAL を **_xAL_** と呼ぶこととする.

#### Identity Assurance Level

<!-- 
**IAL1**:
IAL1 requires validation of identifying attributes against authoritative or credible sources and use of basic processes to verify the claimed identity of the applicant. 
-->

**IAL1**:
IAL1 は, Authoritative または信用できる Source に対して識別に用いられる Attribute の Validation, および Applicant の Claimed Identity を検証するための基本的なプロセスの使用を必要とする. 

<!--
**IAL2**:
IAL2 requires identifying attributes to be supported by strong evidence and validated against authoritative or credible sources and use of processes to verify the claimed identity of the applicant. 
-->

**IAL2**:
IAL2 は, 識別に用いられる Attribute が強力な証拠によって裏付けられ, Authoritative または信用できる Source によって検証され, Applicant の Claimed Identity を検証するプロセスの使用を必要とする. 

<!--
**IAL3**:
IAL3 requires identifying attributes to be verified by an authorized CSP representative through examination of physical documentation using an interactive process with a CSP representative.
-->

**IAL3**:
IAL3 は, 認定された CSP 担当者が, CSP 担当者との対話型プロセスを使用した物理的な文書の検査を通じて, 識別に用いられる Attribute を検証することを必要とする. 

#### Authentication Assurance Level

<!-- 
**AAL1**:
AAL1 provides some assurance that the claimant controls an authenticator registered to the subscriber. AAL1 requires single-factor authentication using a wide range of available authentication technologies. Successful authentication requires that the claimant prove possession and control of the authenticator through a secure authentication protocol.
-->

**AAL1**:
AAL1 では, Claimant が Subscriber に紐づく Authenticator を管理下に置いていることが, ある程度の確からしさで確認できる. AAL1 では Single-factor Authentication が必須となり, そこでは幅広い Authentication 技術が利用可能である. Authentication を成功させるには, Claimant がセキュアな Authentication Protocol を通じて Authenticator を保持・管理していることを証明する必要がある.

<!-- 
**AAL2**:
AAL2 provides high confidence that the claimant controls authenticator registered to the subscriber. Proof of possession and control of two different authentication factors is required through a secure authentication protocol. Approved cryptographic techniques are required at AAL2 and above.
-->

**AAL2**:
AAL2 では, Claimant が Subscriber に紐づく Authenticator を管理下に置いているということが, 高い確度で保証される. セキュアな Authentication Protocol によって, 2つの異なる Authentication Factor を保持・管理していることを証明する必要がある. AAL2 以上では, Approved Cryptographic テクノロジーも必要となる.

<!-- 
**AAL3**:
AAL3 provides very high confidence that the claimant controls authenticator registered to the subscriber. Authentication at AAL3 is based on proof of possession of a key through a cryptographic authentication protocol capable of resisting phishing attacks.
-->

**AAL3**:
AAL3 では, Claimant が Subscriber のアカウントに紐づく Authenticator を管理下に置いているということが, 非常に高い確度で保証される. AAL3 の Authentication は, Phishing 攻撃にも耐えられる Cryptographic Authentication Protocol を用いて, Key の所有を証明することにより行われる.

#### Federation Assurance Level

<!-- 
**FAL1**:
FAL1 allows for the subscriber to log into the RP using an assertion from the IdP that can be verified by the RP as coming from the IdP and targeted for a specific RP. The assertion is protected from modification or construction by an attacker. The trust agreement and registration between the IdP and RP can happen dynamically.
-->

**FAL1**:
FAL1 は, Subscriber が IdP からの Assertion を使用して RP にログインすることを可能にし, RP はそれが IdP からのものであり, 特定の RP を対象としていることを検証することができる. Assertion は, Attacker による変更や作成から保護されている. IdP と RP の間の信頼関係の合意 (Trust Agreement) および登録 (Registration) は, 動的に行うことができる. 

<!-- 
**FAL2**:
FAL2 adds the requirement that the assertion be robust against injection at the RP. One means of this is to have the assertion presented directly to the RP from the IdP instead of passing through an intermediary like a browser. The trust agreement between the IdP and RP cannot happen dynamically, but dynamic registration of the specific IdP and RP can occur at runtime.
-->

**FAL2**:
FAL2 では, Assertion が RP でのインジェクションに対して頑強であるという要件が追加される. 一つの手段としては, ブラウザのような仲介者を通さずに, IdP から RP に直接 Assertion を提示することが挙げられる. IdP と RP の間の信頼関係の合意 (Trust Agreement) を動的に行うことはできないが, 特定の IdP と RP の動的な登録 (Dynamic Registration) は実行時に行うことができる. 

<!-- 
**FAL3**:
FAL3 adds the requirement that the subscriber authenticate directly to the RP using a bound authenticator along with presenting the authentication assertion. The presence of this additional authenticator provides a very high assurance to the RP that the party accessing the RP is the party identified in the assertion. The trust agreement and registration cannot be dynamic.
-->

**FAL3**:
FAL3は, Authentication Assertion の提示とともに, Subscriber にバインドされた Authenticator を使用して RP に直接 Authenticate させるという要件を追加している. この追加 Authenticator の存在により, RPにアクセスする主体が Assertion で識別された主体であることが, RPに対して非常に強く保証される. 信頼関係の合意 (Trust Agreement) および登録 (Registration) は, 動的に行うことはできない. 

### Initial Assurance Level Selection

<!-- The identification and assessment of the potential impacts of failures in identity proofing, authentication, and federation processes informs the organization's digital identity risk management process and the initial selection of assurance levels for those areas. These initial selections are primarily based on cybersecurity risk, but will be tailored, based on mission needs and other potential impacts to the organization, users, and mission partners. -->

Identity Proofing, Authentication, および Federation プロセスにおける障害の潜在的影響の特定と評価は, 組織の Digital Identity Risk Management プロセスおよびこれらの分野の Assurance Level の初期選択に役立つ. これらの初期選択は主にサイバーセキュリティリスクに基づくが, ミッションのニーズおよび組織, ユーザ,  ミッションパートナーに対するその他の潜在的影響に基づいて調整される. 

<!-- Organizations **SHALL** develop and document a process and governance model for selecting initial assurance levels based on the potential impact of digital identity failures. This section provides guidance on the major elements to include in that process. -->

組織は, Digital Identity 障害の潜在的な影響に基づいて初期 Assurance Level を選択するためのプロセスおよびガバナンスモデルを構築し, 文書化しなければならない(**SHALL**). このセクションでは, そのプロセスに含めるべき主な要素に関するガイダンスを提供する. 

#### Selecting Initial IAL {#IAL_CYOA}
<!-- The IAL reflects the level of assurance that an applicant holds the claimed real-life identity.  Organizations **SHALL** use a risk-based approach to select the most appropriate identity proofing requirements for their RP application. The impact analysis described in [Sec. 5.3.1](sec5_DIRM.md#impLvls) informs the selection of the initial IAL selection.  This initial selection **SHALL** be tailored, as described in [Sec. 5.3](sec5_DIRM.md#tailor), based on mission needs, risk tolerance, and potential impacts to privacy, equity, and usability, before making a final IAL determination. -->

IAL は Applicant が Claimed real-life Identity を保持しているという Level of Assurance を表す.  組織は, リスクベースのアプローチを使用して, RP アプリケーションに最も適切な Identity Proofing 要件を選択するべきである(**SHALL**). [Sec. 5.3.1](sec5_DIRM.md#impLvls)に記載されている影響分析が, 最初の IAL 選択の情報源となる.  この初期選定は, 最終的な IAL の決定を行う前に, [Sec. 5.3](sec5_DIRM.md#tailor) に記載されているように, ミッションのニーズ, リスク耐性, Privacy, Equity, Usability への潜在的な影響に基づいて調整されなければならない(**SHALL**). 

<!-- The IAL selection does not mean the RP application owner will need to perform the proofing themselves since identity proofing is the function of the CSP. -->

Identity Proofing は CSP の機能であるため, IALの選択では RP アプリケーションのオーナーが自ら Proofing を行う必要があることを意味しない. 

<!-- Not all RP applications will require identity proofing. If the RP application does not require any personal information to execute any digital transactions, the system can operate without identity proofing users of the RP application. If personal information is needed, the RP needs to determine if validated and verified attributes are required or if self-asserted attributes are acceptable. If there are insignificant potential harms from accepting self-asserted attributes, the system may also be able to operate without identity proofing users. In such cases, the identity proofing processes described in [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"} are not applicable to the system. -->

すべての RP アプリケーションで Identity Proofing が必要になるわけではない. RP アプリケーションが Digital Transaction の実行に Personal Information を必要としない場合, システムは RP アプリケーションの利用者の Identity Proofing を行わずに動作することができる. Personal Information が必要な場合, RP は検証された Attribute が必要か, Self-asserted Attribute が許容されるかを判断する必要がある. Self-asserted Attribute を受け入れることによる潜在的な被害が軽微であれば, システムは利用者の Identity Proofing を行わずに運用することも可能である. このような場合, [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"} に記述された Identity Proofing プロセスは, システムに適用されない. 

<!-- If an organization determines that identity proofing is necessary, the initial IAL **SHALL** be assessed based on the potential impacts of identity proofing failures.  As described in [Sec. 5.1](sec5_DIRM.md#intlAssess), potential impacts **SHALL** be considered from the perspective of the organization, individuals, other organizations, and the nation, for harms incurred through the use or operation of the RP application. While the organization may not be negatively impacted, the user could be significantly harmed, as could individuals whose privacy or other rights have been violated by the business practices of a service provider. Organizations **SHOULD** consider the worst-case when identifying the overall impact level of the RP application, but may use risk management processes to tailor their initial selection when there are differing impacts. -->

組織が Identity Proofing が必要であると判断した場合, 最初の IAL は Identity Proofing の失敗の潜在的な影響に基づいて評価しなければならない(**SHALL**). [Sec. 5.1](sec5_DIRM.md#intlAssess) に記載されているように, RP アプリケーションの使用または操作によって発生する被害について, 組織, 個人, 他の組織, および国の観点から潜在的影響を考慮しなければならない(**SHALL**). 組織は悪影響を受けないかもしれないが, ユーザは大きな損害を受ける可能性があり, サービスプロバイダの商習慣によってプライバシーや他の権利を侵害された個人も同様である. 組織は, RP アプリケーションの全体的な影響度を特定する際に, 最悪のケースを考慮すべきであるが, 影響度が異なる場合は, Risk Management Process を使用して最初の選択を調整すべきである(**SHOULD**). 

<!-- When assessing the overall impact level of the RP application, the organization **SHOULD** consider impacts to mission delivery separately from other impact categories. Potential failures in the identity proofing process that could lead to harms in mission delivery should be assessed by the organization to determine if the associated impacts would be mitigated or exacerbated by the implementation of more rigorous identity proofing processes. As such, the organization **MAY** exclude the mission delivery category when initially identifying the overall impact level of the RP application, as these impacts will need to be considered in the tailoring process. -->

RP アプリケーションの全体的な影響レベルを評価する場合, 組織はミッション遂行への影響を他の影響カテゴリーとは別に検討するべきである(**SHOULD**). ミッション遂行で被害につながる可能性のある Identity Proofing プロセスの潜在的な失敗は, より厳密な Identity Proofing　プロセスの実装によって関連する影響が緩和または悪化するかどうかを判断するために, 組織で評価する必要がある. そのため, 組織は, RP アプリケーションの全体的な影響レベルを最初に特定する際に, ミッション遂行のカテゴリを除外してもよい(**MAY**).

<!-- The overall impact level assessed by the organization leads to a preliminary selection of the IAL from which further tailoring may be done: -->

組織が評価した全体的な影響度から, IALを予備的に選択し, そこからさらに調整を行うことができる. 

<!-- - Low impact: IAL1
- Moderate impact: IAL2
- High impact: IAL3 -->

- 影響度 Low: IAL1
- 影響度 Moderate: IAL2
- 影響度 High: IAL3

<!-- The preliminary selection assumes that higher potential impacts of failures in the identity proofing process should be mitigated by higher assurance processes. While this is often the case, organizations should consider the specific failures, impact categories, and impacted entities identified as part of the impact analysis to determine if additional tailoring is warranted. For example, if a failure to enroll a legitimate applicant could lead to excessive harm, organizations should assess whether lower-assurance identity proofing processes would be appropriate. -->

予備的な選択は Identity Proofing プロセスにおける失敗のより大きな潜在的影響は, より高い保証プロセスによって軽減されるはずであると想定している. このようなケースはよくあるが, 組織は影響分析の一部として特定された特定の障害, 影響カテゴリー, および影響を受ける主体を考慮し, 追加の調整が正当化されるかどうかを判断する必要がある. たとえば, 正当な Applicant の登録に失敗すると過度の被害につながる可能性がある場合,  組織はより低い保証の Identity Proofing プロセスが適切であるかどうかを評価する必要がある. 

<!-- The result of this process, including any additional tailoring, is the initial assessment of the IAL, which will be assessed against additional potential impacts as described in [Sec. 5.3](sec5_DIRM.md#tailor). -->

このプロセスの成果は, 追加の調整も含めて, IALの初期評価となり, [Sec. 5.3](sec5_DIRM.md#tailor) で説明されているように, 追加の潜在影響に対して評価されることになる. 

#### Selecting Initial AAL {#AAL_CYOA}
<!-- The AAL reflects the level of assurance from the authentication process that the claimant is who they claim to be. Organizations **SHALL** use a risk-based approach to select the most appropriate authentication requirements for their RP application. The impact analysis described in [Sec. 5.1.3](sec5_DIRM.md#impLvls) informs the selection of the initial AAL selection.  This initial selection **SHALL** be tailored, as described in [Sec. 5.3](sec5_DIRM.md#tailor), based on mission needs, risk tolerance, and potential impacts to privacy, equity, and usability, before making a final AAL determination. -->

AAL は, Claimant が本人であるという Authentication プロセスによる Level of Assurance を表す. 組織は, リスクベースのアプローチを使用して, RP アプリケーションに最も適切な Authentication 要件を選択しなくては行けない(**SHALL**). [Sec. 5.1.3](sec5_DIRM.md#impLvls) で説明されている影響分析が, 最初の AAL 選択の判断材料となる.  この最初の選択は, 最終的な AAL の決定を行う前に, [Sec. 5.3](sec5_DIRM.md#tailor) に記載されているように, ミッションのニーズ, リスク耐性, Privacy, Equity, Usability への潜在的な影響に基づいて調整しなくてはいけない(**SHALL**).

<!-- The AAL selection does not mean the RP application owner will need to issue authenticators themselves. -->

AALを選択することは, RP アプリケーションのオーナーが自ら Authenticator を発行する必要があることを意味するものではない. 

<!-- The initial AAL **SHALL** be assessed based on the potential impacts of authentication failures. As described in [Sec. 5.1](sec5_DIRM.md#intlAssess), potential impacts **SHALL** be considered from the perspective of the organization, individuals, other organizations, and the nation, for harms incurred through the use or operation of the RP application, as the level of harm from a failure could vary significantly across these entities. Organizations **SHOULD** consider the worst-case when identifying the overall impact level of the RP application, but may use risk management processes to tailor their initial selection when there are differing impacts. -->

初期 AAL は, Authentication 失敗の潜在的な影響に基づいて評価されなければならない(**SHALL**). [Sec. 5.1](sec5_DIRM.md#intlAssess) に記載されているように, RP アプリケーションの使用または運用に よって発生する被害については, 障害による被害レベルが主体間で大きく異なる可能性があるため, 組織, 個人, 他の組織, 国の観点から潜在的影響を考慮しなければならない(**SHALL**). 組織は RP アプリケーションの全体的な影響レベルを特定する際に, 最悪のケースを考慮すべきであるが, 影響が異なる場合には Risk Management プロセスを使用して最初の選択を調整すべきである(**SHOULD**).

<!-- When assessing the overall impact level of the RP application, the organization **SHOULD** consider impacts to mission delivery separately from other impact categories. Potential failures in the authentication process that could lead to harms in mission delivery should be assessed by the organization to determine if the associated impacts would be mitigated or exacerbated by the implementation of more rigorous authentication controls. As such, the organization **MAY** exclude the mission delivery category when initially identifying the overall impact level of the RP application, as these impacts will need to be considered in the tailoring process. -->

RP アプリケーションの全体的な影響レベルを評価する場合, 組織は, ミッション遂行への影響を他の影響カテゴリとは別に検討するべきである(**SHOULD**). Authentication プロセスにおける潜在的な失敗がミッション遂行に害を及ぼす可能性がある場合, 組織は, より厳格な Authentication 管理の実施により, 関連する影響が緩和または悪化するかどうかを判断するために評価する必要がある. このため, 組織は, RP アプリケーションの全体的な影響レベルを最初に特定する際に, ミッション遂行カテゴリーを除外してもよい(**MAY**). 

<!-- The overall impact level assessed by the organization leads to a preliminary selection of the AAL from which further tailoring may be done: -->

組織が評価した全体的な影響度から, AALを予備的に選択し, そこからさらに調整を行うことができる. 

<!-- - Low impact: AAL1
- Moderate impact: AAL2
- High impact: AAL3 -->

- 影響度 Low: AAL1
- 影響度 Moderate: AAL2
- 影響度 High: AAL3

<!-- The preliminary selection assumes that higher potential impacts of failures in the authentication process should be mitigated by higher assurance processes. While this is often the case, organizations should consider the specific failures, impact categories, and impacted entities identified as part of the impact analysis to determine if additional tailoring is warranted. Further, organizations should consider legal, regulatory, or policy requirements that govern digital services. For example, the terms of [[EO13681]](sec8_references.md#ref-EO13681) requiring "that all organizations making personal data accessible to citizens through digital applications require the use of multiple factors of authentication," which would drive the selection of AAL2 or AAL3. -->

予備的な選択では, Authentication プロセスの失敗による潜在的な影響が, より高い保証のプロセスによって軽減されるはずであると想定している. このようなケースはよくあるが, 組織は, 影響度分析の一部として特定された具体的な障害, 影響カテゴリー, 影響を受ける主体について検討し, 追加的な調整が必要であるかどうかを判断する必要がある. さらに, 組織は Digital サービスを管理する法的, 規制的, または政策的な要件を考慮する必要がある. たとえば, 「デジタルアプリケーションを通じて市民が個人データにアクセスできるようにするすべての組織は, 複数の Authentication 要素を使用することを義務付ける」という [[EO13681]](sec8_references.md#ref-EO13681) の条件は, AAL2 または AAL3 の選択を推進することになる. 

<!-- The result of this process, including any additional tailoring, is the initial assessment of the AAL, which will be as assessed against additional potential impacts as described in [Sec. 5.3](sec5_DIRM.md#tailor). -->

このプロセスの成果は, 追加的な調整も含めて, AALの初期評価となり,  [Sec. 5.3](sec5_DIRM.md#tailor)で説明されているように, 追加の潜在影響に対して評価されることになる. 

#### Selecting Initial FAL {#FAL_CYOA}
<!-- The FAL reflects the level of assurance in identity assertions that convey the results of authentication processes and relevant identity information to RP systems. Organizations **SHALL** use a risk-based approach to select the most appropriate federation requirements for their RP application. The impact analysis described in [Sec. 5.3.1](sec5_DIRM.md#impLvls) informs the selection of the initial FAL selection.  This initial selection **SHALL** be tailored, as described in [Sec. 5.3](sec5_DIRM.md#tailor), based on mission needs, risk tolerance, and potential impacts to privacy, equity, and usability, before making a final FAL determination. -->

FAL は, Authentication プロセスの結果および関連する Identity 情報を RP システムに伝える Identity Assertion の Level of Assurance を表す. 組織は, リスクベースのアプローチを使用して, RP アプリケーションに最も適した Federation 要件を選択しなければならない(**SHALL**). [Sec. 5.3.1](sec5_DIRM.md#impLvls) に記載されている影響分析が, 最初の FAL 選択の判断材料となる. この最初の選択は, 最終的な FAL の決定を行う前に, [Sec. 5.3](sec5_DIRM.md#tailor) に記載されているように, ミッションのニーズ, リスク耐性, Privacy, Equity, Usability への潜在的影響に基づいて調整されなければならない(**SHALL**). 

<!-- The initial FAL **SHALL** be assessed based on the potential impacts of failures in the presentation or acceptance of assertions in federated identity architectures. Examples of compromise include use of assertion replay to impersonate a valid user or leakage of assertion information through the browser. As described in [Sec. 5.1](sec5_DIRM.md#intlAssess), potential impacts **SHALL** be considered from the perspective of the organization, individuals, other organizations, and the nation, for harms incurred through the use or operation of the RP application, as the level of harm from a failure could vary significantly across these entities. Organizations **SHOULD** consider the worst-case when identifying the overall impact level of the RP application, but may use risk management processes to tailor their initial selection when there are differing impacts. -->

初期の FAL は Federated Identity アーキテクチャにおける Assertion の提示または受け入れにおける失敗の潜在的な影響に基づいて評価されなければならない(**SHALL**). 侵害の例としては, Assertion Replay による有効なユーザへのなりすましや, ブラウザを介した Assertion 情報の漏洩がある. [Sec. 5.1](sec5_DIRM.md#intlAssess) に記載されているように, RP アプリケーションの使用または操作によって発生する被害について, 組織, 個人, 他の組織, 国の観点から潜在的な影響を検討しなくてはいけない(**SHALL**). これは, 障害による被害レベルがこれらの主体間で大幅に異なる可能性があるためである. 組織は, RPアプリケーションの全体的な影響レベルを特定する際に, 最悪のケースを考慮すべきであるが, 影響が異なる場合には, Risk Management プロセスを使用して最初の選択を調整することができる. 

<!-- When assessing the overall impact level of the RP application, the organization **SHOULD** consider impacts to mission delivery separately from other impact categories. Potential failures in federated architectures that could lead to harms in mission delivery **MAY** be assessed by the organization to determine if the associated impacts would be mitigated or exacerbated by the implementation of more rigorous controls by identity providers. As such, the organization may exclude the mission delivery impact category when initially identifying the overall impact level of the RP application, as these impacts will need to be considered in the tailoring process. -->

RP アプリケーションの全体的な影響度を評価する場合, 組織は, ミッション遂行への影響を他の影響カテゴリーとは別に検討すべきである(**SHOULD**). ミッションの遂行に害を及ぼす可能性のある Federated アーキテクチャの潜在的な障害は, 組織が評価し, ID プロバイダによるより厳格な管理の実施によって関連する影響が緩和または悪化するかどうかを判断してもよい(**MAY**). このため, 組織は, RP アプリケーションの全体的な影響レベルを最初に特定する際に, ミッション遂行の影響カテゴリーを除外することができる. これらの影響は, 調整プロセスで考慮する必要があるためである. 

<!-- The overall impact level assessed by the organization leads to a preliminary selection of the FAL from which further tailoring may be done: -->

組織が評価した全体的な影響度から, FALを予備的に選択し, そこからさらに調整を行うことができる. 

<!-- - Low impact: FAL1
- Moderate impact: FAL2
- High impact: FAL3 -->

- 影響度 Low: FAL1
- 影響度 Moderate: FAL2
- 影響度 High: FAL3

<!-- The preliminary selection assumes that higher potential impacts of failures in federated identity architectures should be mitigated by higher assurance processes. While this is often the case, organizations should consider the specific failures, impact categories, and impacted entities identified as part of the impact analysis to determine if additional tailoring is warranted. -->

予備的な選定では, Federated Identity アーキテクチャにおける障害の潜在的な影響は, より高い保証プロセスによって軽減されるはずであると想定している. このようなケースはよくあるが, 組織は, 影響分析の一部として特定された特定の障害, 影響カテゴリー, および影響を受ける主体を考慮して, 追加の調整が正当化されるかどうかを判断する必要がある. 

<!-- The result of this process, including any additional tailoring, is the initial assessment of the FAL, which will be as assessed against additional potential impacts as described in [Sec. 5.3](sec5_DIRM.md#tailor). -->

このプロセスの成果は, 追加的な調整も含めて, FALの初期評価となり, [Sec. 5.3](sec5_DIRM.md#tailor) で説明するように, 追加の潜在影響に対して評価されることになる. 

## Tailor and Document Assurance Levels {#tailor}

<!-- Tailoring provides a process to modify an initially assessed assurance level or implement compensating controls based on ongoing detailed impact and risk assessments. Organizations **SHOULD** implement the assessed assurance level as defined in these guidelines. However, these guidelines provide flexibility to allow for organizations to meet specific mission needs and address unique risk appetites and considerations. Therefore, organizations **SHALL** establish and document an xAL tailoring process. At a minimum this process: -->

調整は, 最初に評価した Assurance Level を修正し, または継続的な詳細な影響と Risk Assessment に基づき, 代替の管理策を実施するプロセスを提供する. 組織は, このガイドラインで定義された評価済み Assurance Level を実施するべきである(**SHOULD**). しかし, 本ガイドラインは, 組織が特定のミッションのニーズを満たし, 独自のリスク選好及び考慮事項に対処できるよう, 柔軟性を提供するものである. したがって, 組織は, xALの調整プロセスを確立し, 文書化しなければならない(**SHALL**). 最小限のこのプロセスは以下の通り:

<!-- 1. **SHALL** include a structured governance approach to allow for decision-making and conflict resolution.
2. **SHALL** document all decisions in the tailoring process, including the assessed xALs, modified xALs, and compensating controls in the Digital Identity Acceptance Statement (see [Sec. 5.3.4](sec5_DIRM.md#IDacceptStmt)).
3. **SHALL** justify and document all risk-based decisions or modifications to the initially assessed xALs in the Digital Identity Acceptance Statement (see [Sec. 5.3.4](sec5_DIRM.md#IDacceptStmt)).
4. **SHOULD** establish a cross-functional capability to support subject matter analysis of xAL selection impacts in the tailoring process.
5. **SHOULD** be a continuous process that incorporates real world operational data to evaluate the impacts of selected xAL controls. -->

1. **SHALL** 意思決定と対立の解消を可能にするために, 構造化されたガバナンスのアプローチを含める
2. **SHALL** 評価された xAL, 修正された xAL, および Digital Identity Acceptance Statement ([Sec. 5.3.4](sec5_DIRM.md#IDacceptStmt) 参照）の補償管理を含む, 調整プロセスのすべての決定を文書化する
3. **SHALL** Digital Identity Acceptance Statement（[Sec. 5.3.4](sec5_DIRM.md#IDacceptStmt) 参照）において, 当初評価した xAL に対するすべてのリスクベースの決定または修正の正当性を証明し文書化する. 
4. **SHOULD** 調整プロセスにおける xAL 選択の影響に関する主題分析をサポートするために, 部門横断的な能力を確立する
5. **SHOULD** 選択された xAL コントロールの影響を評価するために, 実際の運用データを取り入れた継続的なプロセスであること

<!-- The tailoring process promotes a structured means to balance risks and impacts in the furtherance of protecting systems, data, and services in a manner that enables mission success while supporting equity, privacy, and usability for individuals. -->

調整プロセスは, システム, データ, サービスを保護するために, リスクと影響のバランスを取るための構造的な手段を推進するもので, ミッションを成功させるとともに, Equity, Privacy, Usability をサポートする.

### Assess Privacy, Equity, Usability and Threats

<!-- When selecting and tailoring assurance levels for specific applications, it is critical that insights and inputs to the process extend beyond an initial, static impact assessment. When transitioning from an initial assurance level to the final xAL selection and implementation, organizations **SHALL** conduct detailed assessments of the controls defined at the assurance level to determine potential impacts in their operational environment. At a minimum, organizations **SHALL** assess impacts related to the following areas: -->

特定のアプリケーション向けに Assurance Level を選択及び調整する場合, プロセスに対するインサイト及びインプットは, 最初の静的な影響評価を超えて行われることが重要である. 最初の Assurance Level から最終的な xAL の選択及び実施に移行する際, 組織は Assurance Level で定義されたコントロールについて詳細なアセスメントを実施し, 運用環境における潜在的な影響を判断しなければならない(**SHALL**). 少なくとも, 組織は以下の領域に関する影響を評価しなければならない(**SHALL**). 

<!-- - **Privacy** – to determine unintended consequences to the privacy of individuals that will be subject to the controls at an assessed xAL and of individuals affected by organizational or third-party practices related to the establishment, management, or federation of a digital identity.
- **Equity** – to determine whether implementation of controls may create or maintain inequities across demographics or user groups.
- **Usability** – to determine whether implementation of the selected controls will result in challenges to end-user experience.
- **Threat** – to determine whether the defined assurance level will address specific threats based on environment, threat actors, and known tactics, techniques, and procedures (TTPs). -->

- **Privacy** – 評価された xAL での管理の対象となる個人, および Digital Identity の確立, 管理, または Federation に関連する組織または第三者の慣行の影響を受ける個人の Privacy に対する意図しない結果生じるかどうかを判断すること
- **Equity** – 統制の実施により, 人々の属性やユーザーグループ間で不公平が生じたり, その状態が継続したりする可能性がないかどうかを判断すること
- **Usability** – 選択したコントロールの実施により, エンドユーザー・エクスペリエンスに課題が生じるかどうかを判断すること
- **Threat** – 環境, 脅威要因, 既知の戦術, 技術, 手順（TTPs）に基づき, 定義された Assurance Level  が特定の脅威に対応できるかどうかを判断すること

<!-- Additionally, organizations **SHOULD** conduct additional business specific assessments as appropriate to fully represent mission and domain specific considerations not captured here. These assessments **SHALL** be extended to any compensating or supplemental controls as defined in [Sec. 5.3.2](sec5_DIRM.md#IDCompCntls) and [Sec. 5.3.3](sec5_DIRM.md#IDSupCntrls). -->

さらに, 組織は, ここに記載されていないミッションやドメイン特有の考慮事項を完全に把握するために, 必要に応じて追加のビジネス固有のアセスメントを実施するべきである(**SHOULD**). これらの評価は, [Sec. 5.3.2](sec5_DIRM.md#IDCompCntls) 及び [Sec. 5.3.3](sec5_DIRM.md#IDSupCntrls) に定義されているように, 補償または補足の管理まで拡張しなくてはいけない(**SHALL**). 

### Identify Compensating Controls {#IDCompCntls}

<!-- A compensating control is a management, operational, or technical control employed by an organization in lieu of a recommended control in the defined xALs. They are intended, to the greatest degree possible, to address the same risks as the baseline control is intended to address. -->

代替策とは, 定義されたxALの推奨されているものの代わりに組織が採用する管理, 運用, 又は技術的な対策である. これらは, 可能な限り, 基準策が対処しようとするリスクと同じリスクに対処することを意図している. 

<!-- Organizations **SHOULD** implement their identity services per the requirements in these guidelines for their tailored assurance level. However, where organizations are unable to implement a specific control associated with their baseline or tailored assurance level, they **MAY** select to implement a compensating control. This control **MAY** be a modification to a digital identity process as defined in these guidelines, but **MAY** also be applied elsewhere in an application, transaction, or service lifecycle. For example: -->

組織は, 調整された Assurance Level に対して, このガイドラインの要件に従って Identity サービスを実装するべきである(**SHOULD**). ただし, 組織がベースラインまたは調整済み Assurance Level に関連する特定の制御を実装できない場合は, 代替策を実装することを選択してもよい(**MAY**). この対策は, このガイドラインで定義された Digital Identity プロセスの修正であってもよいが, アプリケーション, Transaction, またはサービスのライフサイクルの他の場所に適用してもよい. たとえば, 次のようなものである:

<!-- -	A federal agency could choose to use a federal background investigation and checks, as referenced by  _Personal Identity Verification_ [[FIPS201]](sec8_references.md#ref-FIPS201), to compensate for the identity evidence validation with authoritative sources requirement under these guidelines.
-	An organization could choose to implement stricter auditing and transactional review processes on a payment application where verification processes using weaker forms of identity evidence were accepted due to availability of evidence in the end-user population. -->

-	連邦機関は, このガイドラインに基づく Authoritative Sources による Identity Evidence の検証要件を補うために,  _Personal Identity Verification_ [[FIPS201]](sec8_references.md#ref-FIPS201) で参照される連邦バックグラウンド調査およびチェックを使用することを選ぶことができる. 
-	組織は, エンドユーザ母集団にとって利用可能な Evidence の制約により, より弱い形式の Identity Evidence を使用した検証プロセスを許容している支払アプリケーションについて, より厳しい監査および Transaction 審査プロセスを実施することを選択できる. 

<!-- Where compensating controls are implemented, organizations **SHALL** demonstrate comparability of a chosen alternative or document residual risk incurred by deviating from normative requirements. Organizations **SHALL** implement procedures to document both the justification for any departure from normative requirements and detail the compensating controls employed. The inclusion of compensating controls does not imply that an organization must tailor to a lower xAL. The process of tailoring allows for agencies and service providers to make risk-based decisions in how they implement their xALs and provides a mechanism for documenting and communicating decisions through the Digital Identity Acceptance Statement described in [Sec. 5.3.4](sec5_DIRM.md#IDSupCntrls). -->

代替策を実施する場合, 組織は選択した代替案の比較可能性を証明するか, または Normative 要件から逸脱することによって生じる残留リスクを文書化しなければならない(**SHALL**). 組織は Normative 要件からの逸脱の正当な理由と, 採用した代替策の詳細を文書化する手順を実施しなければならない(**SHALL**). 代替となる管理策を含めることは, 組織がより低い xAL に合わせなければならないことを意味するものではない. 調整プロセスにより, 機関およびサービスプロバイダは, xAL の実装方法についてリスクに基づく決定を下すことができ, [Sec. 5.3.4](sec5_DIRM.md#IDSupCntrls) に記載されている Digital Identity Acceptance Statement を通じて決定を文書化し伝達するためのメカニズムが提供される. 

### Identify Supplemental Controls {#IDSupCntrls}

<!-- Supplemental controls are those that may be added, in addition to those specified in the organizations tailored assurance level, in order to address specific threats or attacks. Organizations **SHOULD** identify and implement supplemental controls where they identify threats that may not be addressed in baseline controls. For example: -->

補足的な対策とは, 特定の脅威または攻撃に対処するために, 組織が調整した Assurance Level で指定されたものに加えて追加することができるものである. 組織は, 基本的な管理策では対処できない脅威を特定した場合, 補足的な管理策を特定し, 実施すべきである(**SHOULD**). たとえば, 次のようなものである:

<!-- - An organization could choose to verify an end user against additional pieces of identity evidence, beyond what is required by the assurance level, due to a high prevalence of fraudulent attempts to complete the proofing process.
- An organization could choose to implement risk-scoring analytics, coupled with re-proofing mechanisms, to confirm a user’s identity when their access attempts exhibit certain risk factors. -->

- Proofingプロセスを完了するための不正な試行が多発しているため, 組織は Assurance Level で要求される以上の追加の Identity Evidence に対してエンドユーザを検証することを選択することができる. 
- アクセス試行が特定のリスク要因を示す場合, ユーザの Identity を確認するために, 組織はリスクスコア分析を実装して re-proofing 機構と組み合わせることを選択することができる. 

<!-- Where organizations implement supplemental controls, these **SHALL** be assessed for impacts based on the same factors used to tailor the organization’s assurance level.
Supplemental controls **SHALL** be documented. -->

組織が補足的な対策を導入する場合, 組織の Assurance Level を調整するために使用したのと同じ要素に基づき, これらの影響について評価しなくてはいけない(**SHALL**).
補足的な対策は文書化しなければならない. 

### Document Results - The Digital Identity Acceptance Statement {#IDacceptStmt}

<!-- The Digital Identity Acceptance Statement documents the results of the digital identity risk management process. This includes the Impact Assessment, Initial Assurance Level Selection, and Tailoring process. -->

Digital Identity Acceptance Statementは, Digital Identity Risk Management プロセスの結果を文書化したものである. これには, Impact Assessment, 初期 Assurance Level の選択, および調整プロセスが含まれる. 

<!-- The statement **SHALL** include, at a minimum: -->

Statement には, 最低限, 以下を含めること:

<!-- 1.	Initial Impact Assessment Results
2.	Initially assessed xAL,
3.	Tailored xAL and rationale, if tailored xAL differs from initially assessed xAL,
4.	All compensating controls and their comparability or residual risk associated with compensating controls
5.	All supplemental controls -->

1.	初期影響調査の結果
2.	初期の xAL 評価,
3.	調整された xAL と当初評価された xAL が異なる場合, 調整されたxALとその根拠, 
4.	すべての代替策とその比較可能性, または代替策に関連する残存リスク
5.	すべての補足的な対策

<!-- Federal agencies **SHOULD** include this information in the system authorization package described in [[SP800-37]](sec8_references.md#ref-SP800-37). -->

連邦政府機関は, この情報を [[SP800-37]](sec8_references.md#ref-SP800-37) に記載されているシステム Authorization パッケージに含めるべきである(**SHOULD**).

## Continuously Evaluate and Improve

<!-- Threat actors adapt, user expectations and needs shift, and missions evolve. As such, risk assessments and identity solutions are not to be set and forgotten. To maintain pace with the constantly shifting environment in which they operate, organizations **SHOULD** implement a continuous evaluation and improvement program that leverages input from people interacting with the identity system. These programs **SHOULD** consider feedback from application performance metrics, threat intelligence, fraud analytics, assessments of equity impacts, privacy impact analysis, and user inputs. -->

脅威をもたらす主体は適応し, ユーザーの期待とニーズは変化し, ミッションは進化する. このように Risk Assessment と Identity ソリューションは, 定められたあとに忘れ去られるものではない. 常に変化する環境に対応するために, 組織は Identity システムとインタラクションする人々からのインプットを活用する継続的な評価および改善プログラムを実施するべきである(**SHOULD**). これらのプログラムは, アプリケーション・パフォーマンス測定基準, 脅威インテリジェンス, 不正分析, Equityへの影響の評価, Privacy 影響分析, およびユーザの入力からのフィードバックを考慮すべきである(**SHOULD**).

## Cyber, Fraud, and Identity Program Integrity

<!-- Typically, identity solutions are the front door for a critical business or service function. Accordingly, they should not operate in a vacuum. Close coordination of identity functions with cybersecurity teams, threat intelligence teams, and program integrity teams can enable a more complete protection of business capabilities, while constantly improving identity solution capabilities. For example, payment fraud data collected by program integrity teams could provide indicators of compromised subscriber accounts and potential weaknesses in identity proofing implementations. Similarly, threat intelligence teams may receive indication of new TTPs that may impact identity proofing, authentication, and federation processes. Organizations **SHOULD** establish consistent mechanisms for the exchange of information between critical security and fraud stakeholders. -->

通常, Identity ソリューションは, 重要なビジネスまたはサービス機能のフロントドアである. したがって, 孤立した状態で運用するべきではない. Identity 機能をサイバーセキュリティ・チーム, 脅威インテリジェンス・チーム, およびプログラム・インテグリティ・チームと緊密に連携させることにより, ビジネス機能をより完全に保護し Identity ソリューション機能を常に向上させることができる. たとえば, プログラム・インテグリティ・チームが収集した不正支払のデータは, 漏洩した Subscriber Account および Identity Proofing の実装における潜在的な弱点の指標を提供することができる. 同様に, 脅威インテリジェンス・チームは, Identity Proofing, Authentication, および Federationプロセスに影響を与える可能性のある新しい TTP の兆候を受け取ることができる. 組織は, 重要なセキュリティおよび不正行為の関係者間で情報を交換するための一貫したメカニズムを確立するべきである(**SHOULD**). 

<!-- Where supporting service providers, such as CSPs, are external, this may be complicated, but **SHOULD** be considered in contractual and legal mechanisms. All data collected, transmitted, or shared **SHALL** be minimized and subject to a detailed privacy and legal
assessment. -->

CSP などの支援サービス・プロバイダーが外部にある場合, 複雑になる可能性があるが, 上記のような項目は契約上および法的な仕組みの中で考慮されるべきである(**SHOULD**). 収集, 送信, または共有するすべてのデータは, 最小化し, 詳細な Privacy および法的な評価を受けなければならない(**SHALL**). 