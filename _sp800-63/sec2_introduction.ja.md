---
layout: default.ja
title: Introduction
navOrder: 2
navTitle: Introduction
permalink: /sp800-63/introduction/
anchor: intro
section: 2
---

# Introduction {#intro}

*This section is informative.*

<!-- As the line between the virtual world and physical world blurs, and as digital and internet-enabled technologies continue to proliferate and connect, it is imperative that developers and consumers alike understand this changing hybrid ecosystem - including its associated opportunities and risks. Engagement across this ecosystem is often determined by an individual's ability and willingness to establish a digital identity - the unique representation of a person engaged in an online transaction. -->

仮想世界と物理世界の境界線が曖昧になり, デジタルとインターネット技術の急速な拡大と繋がりが進む中, 開発者と消費者は同様に, この変化するハイブリッドエコシステムを, それに伴う機会とリスクも含めて理解することが不可欠となっている. このハイブリッドエコシステムとの関わりは, しばしば Digital Identity （オンライン取引に関わる人物を一意に表現すること）を確立する個人の能力と意思によって決定される.

<!-- A digital identity is always unique in the context of a digital service but does not always uniquely identify a person in all contexts. Further, while a digital identity may relay unique and specific meaning within the context of a digital service, the real-life identity of the individual behind the digital identity may not be known. For the purpose of this publication, a "person" refers to natural persons only (i.e., not all legal persons.) -->

Digital Identity は, デジタルサービスのコンテキストでは常に一意であるが, すべてのコンテキストで常に個人を一意に特定できるわけではない. さらに, Digital Identity はデジタルサービスのコンテキスト内では一意で明確な意味を持つが, Digital Identity の背後にある個人の現実の身元は知られていない場合がある. 本書では, 「人」は自然人のみを指す（すなわち, 法人を指していない）. 

<!-- Establishing a digital identity is intended to demonstrate trust between the holder of the digital identity and the person, organization, or system on the other side of the digital transaction. However, this process can present challenges. As in relationships and transactions in the physical world, there are multiple opportunities for mistakes, miscommunication, impersonation, and other attacks that fraudulently claim another person's digital identity. Additionally, given the broad range of individual needs, constraints, capacities, and preferences, digital services must be designed with equity and flexibility in mind to ensure broad and enduring participation. -->

Digital Identity の確立は, Digital Identity の保有者と, Digital Transaction の相手側にいる個人, 組織, または システムとの間に信頼を示すことを意図している. しかし, このプロセスには課題がある. 物理的な世界での関係や Transaction と同様に, ミスコミュニケーション, なりすまし, 他人の Digital Identity の詐称, およびその他の Attack の機会が多数存在する. 加えて, 個人のニーズ, 制約, 能力, 嗜好が多岐に渡ることを考えると, デジタルサービスは, 広く永続的に参加できるように, Equity と柔軟性を考慮して設計する必要がある. 

<!-- Risks associated with digital identity stretch beyond the potential impacts to enterprises and should be incorporated into enterprise decision-making. This publication endeavors to more robustly and explicitly account for risks to individuals, communities, and other organizations. Specifically, while using this guidance, organizations should consider how decisions related to digital identity that prioritize organizational cybersecurity objectives might affect or need to accommodate other objectives, such as those related to privacy, equity, usability, and other indicators of mission and business performance that center the experiences of the individuals interacting with programs and services. By taking a human-centered and continuously informed approach to mission delivery, organizations have an opportunity to incrementally build trust with the variety of populations they serve, improve customer satisfaction, identify issues more quickly, and provide individuals with effective and culturally appropriate redress options. -->

Digital Identity に関連するリスクは, 企業への潜在的な影響を超えて広がっており, 企業の意思決定に組み込まれる必要がある. 本書は, 個人, コミュニティ, および他の組織に対するリスクをより強固にかつ明示的に考慮するように努めている. 具体的には, 組織はこの指針を使用しながら, 組織のサイバーセキュリティの目標を優先する Digital Identity に関する決定が, Privacy, Equity, Usability, およびプログラムやサービスを利用する個人の経験を中心とするミッションとビジネスパフォーマンスのその他の指標に関連するものなどにどのように影響するか, または対応する必要があるかを検討する必要がある. ミッションの提供において, 人間中心で継続的に情報を提供するアプローチをとることにより, 組織は, サービスを提供するさまざまな人々との信頼を徐々に築き, 顧客満足度を高め, 問題をより迅速に特定し, 効果的で文化的に適切な是正策を個人に提供する機会を持つことができる. 

<!-- These guidelines lay out a model for federal programs and other organizations to assess and manage risks associated with digital identity systems, including the processes, policies, data, people, and technologies that support digital identity management. The model is supported by a series of processes: identity proofing, authentication, and federation. The identity proofing process establishes that a subject is a specific physical person. The digital authentication process determines the validity of one or more authenticators used to claim a digital identity and establishes confidence that a subject attempting to access a digital service: (1) is in control of the technologies being used for authentication, and (2) is the same subject that previously accessed the service. Finally, the federation process allows for identity information to be shared in support of authentication across systems. -->

これらのガイドラインは, 連邦プログラムおよびその他の組織が, Digital Identity 管理をサポートするプロセス, ポリシー, データ, 人, および技術を含む Digital Identity システムに関連するリスクを評価および管理するためのモデルを示している. このモデルは, Identity Proofing, Authentication, および Federation という一連のプロセスによってサポートされている. Identity Proofing は, Subject が特定の物理的人物であることを証明する. Digital Authentication プロセスは, Digital Identity を主張するために使用される 1 つまたは複数の Authenticator の有効性を判断し, デジタルサービスに Access しようとする Subject が, （1） Authentication に使用されている技術を管理しており, （2）以前にサービスにアクセスした Subject と同一であるという信頼を確立するものである. 最後に, Federation プロセスは, システム間で Authentication をサポートするために Identity 情報を共有することを可能にする. 

<!-- The composition, model, and availability of identity services has significantly changed since the first version of SP 800-63 was released, as have the considerations and challenges of deploying secure, private, and equitable services to diverse user communities. This revision addresses these challenges while facilitating the new models and architectures for identity services that have developed by clarifying requirements based on the function an entity may serve under the overall digital identity model. -->

Identity サービスの構成, モデル, および可用性は, SP 800-63 の初版が発表されて以来大幅に変化し, 安全, プライベート, および公平なサービスを多様なユーザコミュニティに展開する際の考慮事項や課題も変化してきている. この改訂は, 全体的な Digital Identity モデルの下でエンティティが果たすであろう機能に基づいて要件を明確にし発展した Identity サービスの新しいモデルおよびアーキテクチャを促進しながら, これらの課題に対処している. 

<!-- Additionally, this publication provides instruction for credential service providers (CSPs), verifiers, and relying parties (RPs) and it describes the risk management processes that organizations should follow for implementing digital identity services and that supplement the *NIST Risk Management Framework* [[NISTRMF]](sec8_references.md#ref-NIST-RMF) and its component special publications. The publication expands upon the NIST RMF by outlining how equity and usability considerations should be incorporated into digital identity risk management processes and it highlights the importance of considering impacts, not only on the enterprise operations and assets, but also on individuals, other organizations, and, more broadly, society. Further, while digital authentication supports privacy protection by mitigating risks of unauthorized access to individuals' information, given that identity proofing, authentication, authorization, and federation often involve the processing of individuals' information, these functions can also create privacy risks. These guidelines, therefore, include privacy requirements and considerations to help mitigate potential associated privacy risks. -->

さらに, 本書は Credential Service Provider（CSP）, Verifier , および Relying Party (RP) に対する指針を提供し, Digital Identity サービスの実装のために組織が従うべき Risk Management プロセスを説明し, *NIST Risk Management Framework* [[NISTRMF]](sec8_references.md#ref-NIST-RMF) およびそれを構成する Special Publication 群を補完するものである. この出版物は, NIST RMF を拡張して, Equity と Usability への配慮を Digital Identity Risk Management プロセスに組み込む方法を概説し, 企業の運用と資産だけでなく, 個人, 他の組織, およびより広く社会への影響を考慮することの重要性を強調している. さらに, Digital Authentication は, 個人の情報への不正アクセスのリスクを軽減することで Privacy 保護をサポートするが, Identity Proofing, Authentication, Authorization, および Federation は, しばしば個人情報の処理を伴うため, これらの機能は Privacy リスクを引き起こす可能性もある. したがって, このガイドラインは, 関連する潜在的な Privacy リスクの軽減を支援するための Privacy 要件および考慮事項を含んでいる. 

<!-- Finally, while this publication provides organizations with technical requirements and recommendations for establishing, maintaining, and authenticating the digital identity of subjects in order to access digital systems over a network, additional support options outside the purview of information technology teams may need to be provided to address barriers and adverse impacts, foster equity, and successfully deliver on mission objectives. -->

最後に, 本書は, ネットワーク上のデジタル・システムにアクセスするために対象者の Digital Identity を確立, 維持, および Authenticate するための技術要件と推奨事項を組織に提供しているが, 障壁や悪影響に対処し, Equity を育み, ミッション目標を正常に達成するには, 情報技術チームの権限外のサポートオプションを追加する必要がある場合がある. 

## Scope & Applicability

<!-- Not all digital services require identity proofing or authentication; however, this guidance applies to all online transactions for which some level of digital identity is required, regardless of the constituency (e.g., citizens, business partners, and government entities). -->

すべてのデジタルサービスに Identity Proofing　または Authentication が必要なわけではないが, このガイダンスは利用者層（市民, ビジネス・パートナー, 政府機関など）に関係なく, 何らかのレベルの Digital Identity が必要なすべてのオンライン Transaction に適用される. 

<!-- These guidelines primarily focus on organizational services that interact with external users, such as citizens accessing public benefits or private sector partners accessing collaboration spaces. However, it also applies to federal systems accessed by employees and contractors. The *Personal Identity Verification (PIV) of Federal Employees and Contractors* standard [[FIPS201]](sec8_references.md#ref-FIPS201) and its corresponding set of special publications and organization-specific instructions, extend these guidelines for the federal enterprise, providing additional technical controls and processes for issuing and managing Personal Identity Verification (PIV) cards, binding additional authenticators as derived PIV credentials, and using federation architectures and protocols with PIV systems. -->

本ガイドラインは, 公共サービスにアクセスする市民やコラボレーションスペースにアクセスする民間セクターのパートナーなど, 外部ユーザーとやり取りする組織サービスを主に対象としている. しかし, 職員や契約社員がアクセスする連邦システムにも適用される. *Personal Identity Verification (PIV) of Federal Employees and Contractors* standard [[FIPS201]]（sec8_references.md#ref-FIPS201）および対応する一連の Special Publication と組織固有の説明書は, 連邦企業向けにこれらのガイドラインを拡張し, Personal Identity Verification（PIV）カードの発行と管理, 派生 PIV Credential としての追加 Authenticator のバインド, PIV システムでの Federation アーキテクチャおよびプロトコルの使用に関する追加の技術統制および手順を規定している. 

<!-- Transactions not covered by this guidance include those associated with national security systems as defined in 44 U.S.C. § 3542(b)(2). Private sector organizations and state, local, and tribal governments whose digital processes require varying levels of digital identity assurance may consider the use of these standards where appropriate. -->

本ガイダンスの対象とならない Transaction には, 44 U.S.C. § 3542(b)(2) に定義される国家安全保障システムに関連するものが含まれる. デジタルプロセスでさまざまなレベルの Digital Identity Assurance を必要とする民間部門組織, 州, 地方, および部族の政府は, 必要に応じてこれらの標準の使用を検討することができる. 

<!-- Additionally, these technical guidelines do not address the identity of subjects for physical access (e.g., to buildings), though some identities used for online transactions may also be used for physical access. Additionally, this revision of these guidelines does not explicitly address device identity, often referred to as machine-to-machine (such as router-to-router) authentication or interconnected devices, commonly referred to as the internet of things (IoT), although these guidelines are written to refer to generic subjects wherever possible to leave open the possibility for applicability to devices. Furthermore, these guidelines do not address authorization of access to Application Programming Interfaces (APIs) on behalf of subjects. -->

加えて, オンライン Transaction に使用される一部の Identity は（建物など）物理的 Access の際にも使用される場合があるが, これらの技術ガイドラインは物理的 Access に対する Subject の Identity は扱っていない. また, 今回の改訂では, 機器間（ルータ間など） Authentication や Internet of Things (IoT) と呼ばれる相互接続されたデバイスの Identity については明示的に触れていないが, デバイスへの適用可能性を残すため, 可能な限り一般的な Subject に言及するよう記述されている. さらに, Application Programming Interfaces (API) に対する Subject の代理については, 本ガイドラインでは触れていない. 


## How to Use this Suite of SPs

<!-- These guidelines support the mitigation of the negative impacts induced by a digital identity error by separating the individual elements of digital identity into discrete, component parts. For non-federated systems, agencies will select two components, referred to as *Identity Assurance Level (IAL)* and *Authentication Assurance Level (AAL)*. For federated systems, a third component, *Federation Assurance Level (FAL)*, is included. [Sec. 5, Digital Identity Risk Management](sec5_DIRM.md#sec5) provides details on the risk assessment process and how the results of the risk assessment, with additional context, inform organizational selection of IAL, AAL, and FAL combinations based on risk and mission. -->

本ガイドライン群は, Digital Identity を個別要素ごとに分割することで, Authentication の誤りがもたらすネガティブインパクトの軽減に寄与する. Non-federated なシステムでは, 各機関はそれらのうち *Identity Assurance Level (IAL)* と *Authenticator Assurance Level (AAL)* という2つの要素を用いるであろう. Federated なシステムでは, それに加えて3つ目の要素となる *Federation Assurance Level (FAL)* も用いることとなろう. [Sec. 5, Digital Identity Risk Management](sec5_DIRM.md#sec5) では, Risk Assessment プロセスの詳細と, Risk Assessment の結果が, リスクとミッションに基づいて IAL, AAL, FAL の組み合わせを組織的に選択するための追加のコンテキストをどのように提供するかについて説明する.

<!-- By conducting appropriate risk management for business, security, and privacy, side-by-side with mission needs, organizations will select IAL, AAL, and FAL as distinct options. Specifically, organizations are required to individually select levels corresponding to each function being performed. While many systems could have the same numerical level for each IAL, AAL, and FAL, this is not a requirement and organizations should not assume they will be the same in any given system or application. -->

ミッションのニーズと並行して, ビジネス, セキュリティ, プライバシーの適切な Risk Management を行うことで, 組織は IAL , AAL , FAL を個別のオプションとして選択することになる. 具体的には, 各機能に対応したレベルを個別に選択することが求められる. 多くのシステムでは, IAL, AAL, およびFALの各レベルが同じ数値になる可能性があるが, これは要件ではなく, 組織は任意のシステムまたはアプリケーションでこれらが同じであると仮定すべきではない. 

<!-- The components of identity assurance detailed in these guidelines are as follows: -->

本ガイドライン群において詳しく扱う Identity Assurance の構成要素は以下の通りである.

<!-- * **IAL** refers to the identity proofing process. -->
<!-- * **AAL** refers to the authentication process. -->
<!-- * **FAL** refers to the federation process, when the RP is connected through a federated protocol. -->

* **IAL** は, Identity Proofing プロセスについて述べる.
* **AAL** は, Authentication プロセスについて述べる.
* **FAL** は, RP が Federated Protocol で接続されている場合の Federation プロセスについて述べる. 

<!-- > Note: When described generically or bundled, these guidelines will refer to IAL, AAL, and FAL as ***xAL***. -->

> 注: 本ガイドラインでは, IAL , AAL , FAL を総称して, ***xAL*** と表記する場合がある.

<!-- SP 800-63 is organized as the following suite of volumes: -->

SP 800-63 は以下のような一連の Vol. から構成される:

<!-- SP 800-63 *Digital Identity Guidelines*: Provides the risk assessment methodology and an overview of general identity frameworks, using authenticators, credentials, and assertions together in a digital system, and a risk-based process of selecting assurance levels. _SP 800-63 contains both normative and informative material._ -->

SP 800-63 *Digital Identity Guidelines* :　SP 800-63 では, Risk Assesment の方法論, デジタルシステムにおける Authenticator, Credential, Assertion を利用した一般的な Identity Framework の概観, およびリスクベースプロセスに基づく各 Assurance Level の選択方法について述べる. _SP 800-63 には規範的な資料と情報的な資料の両方が含まれている._

<!-- [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"}: Provides requirements for enrollment and identity proofing of applicants, either remotely or in person, that wish to gain access to resources at each of the three identity assurance levels (IALs). It details the responsibilities of Credential Service Providers (CSPs) with respect to establishing and maintaining subscriber accounts and binding authenticators (either CSP-issued or subscriber-provided) to the subscriber account.
_SP 800-63A contains both normative and informative material._ -->

[[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"}: 3 つの Identity Assurance Level（IAL）ごとに, リソースへの Access を希望する Applicant の登録と Identity Proofing の要件を規定する. この文書では, Subscriber Account の確立および維持, ならびに Subscriber Account への Authenticator（CSP 発行または Subscriber 提供のいずれか）のバインドに関する Credential Service Providers (CSP) の責務について詳述している. 

_SP 800-63A contains both normative and informative material._

<!-- [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}: Provides recommendations on types of authentication processes, including choices of authenticators, that may be used at each of the three authentication assurance levels (AALs). It also provides recommendations on the lifecycle of authenticators, including invalidation in the event of loss or theft. 
_SP 800-63B contains both normative and informative material._-->

[[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}: 3つの Authentication Assurance Level（AAL）のそれぞれで使用できる Authentication プロセス（ Authenticator の選択など）の種類に関する推奨事項を規定する. また, 紛失または盗難時の無効化など, Authenticator のライフサイクルに関する推奨事項を記載している. 

_SP 800-63B contains both normative and informative material._

<!-- [[SP800-63C]](../_sp800-63c/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63C"}: Provides requirements on the use of federated identity architectures and assertions to convey the results of authentication processes and relevant identity information to an agency application. Further, this volume offers privacy-enhancing techniques to share information about a valid, authenticated subject, and describes methods that allow for strong multi-factor authentication (MFA) while the subject remains pseudonymous to the digital service. 
_SP 800-63C contains both normative and informative material._-->

[[SP800-63C]](../_sp800-63c/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63C"}: Authentication プロセスの結果および関連する Identity 情報を機関アプリケーションに伝達するための, Federated Identity Architecture および Assertion の使用に関する要件を規定している. さらに, この文書では, 有効な認証済 Subject に関する情報を共有するためのプライバシー強化技術を提供し, Subject がデジタルサービスに対して匿名のままで強力な　Multi-factor Authentication（MFA）を可能にする方法について説明している. 

_SP 800-63C contains both normative and informative material._

## Enterprise Risk Management Requirements and Considerations {#ERMreqs}

<!-- Effective enterprise risk management is multidisciplinary by default and involves the consideration of a diverse set of factors and equities. In a digital identity risk management context, these factors include, but are not limited to, information security, privacy, equity, and usability. It is important for risk management efforts to weigh these factors as they relate not only to enterprise assets and operations but also to individuals, other organizations, and society more broadly. -->

効果的な企業 Risk Management は, 基本的に多分野にまたがるものであり, 多様な要因および Equity の考慮が必要である. Digital Identity Risk Management のコンテキストでは, これらの要因には, 情報セキュリティ, Privacy, Equity, および Usability が含まれるが, これらに限定されるものではない. Risk Management の取り組みでは, 企業の資産および業務だけでなく, 個人, 他の組織, および社会により広く関係するこれらの要因を考慮することが重要である.

<!-- During the process of analyzing factors relevant to digital identity, organizations may determine that measures outside of those specified in this publication are appropriate in certain contexts, for instance where privacy or other legal requirements exist or where the output of a risk assessment leads the organization to determine that additional measures or other process safeguards are appropriate. Organizations, including federal agencies, may employ compensating or supplemental controls not specified in this publication. They may also consider partitioning the functionality of a digital service to allow less sensitive functions to be available at a lower level of assurance. -->

Digital Identity に関連する要素を分析する過程で, 組織は, たとえば Privacy または他の法的要件が存在する場合, または Risk Management の結果から組織が追加の対策または他のプロセスの安全策が適切であると判断する場合など, 特定の状況において本書に規定されていない対策が適切であると判断する場合があり得る. 連邦政府機関を含む組織は, 本書で規定されていない補正的または補足的な管理を採用することができる. また, より機密性の低い機能をより低い保証レベルで利用できるように, Digital Service の機能の分割を検討することもできる. 

<!-- The considerations detailed below support enterprise risk management efforts and encourage informed, inclusive, and human-centric service delivery. While this list of considerations is not exhaustive, it highlights a set of cross-cutting factors likely to impact decision-making associated with digital identity management. -->

以下に詳述する考慮事項は, 企業の Risk Management 努力を支援し, 情報に基づいた包括的で人間中心 のサービス提供を促進する. この考慮事項のリストはすべてを網羅しているわけではないが, Digital Identity 管理に関連する意思決定に影響を与える可能性がある一連の横断的な要因を取り上げている. 

### Security

<!-- It is increasingly important for enterprise organizations to assess and manage digital identity security risks, such as unauthorized access, availability issues, impersonation, and other types of fraudulent claims, as well as institute strong identity governance practices. As organizations consult this guidance, they should consider potential impacts to the confidentiality, integrity, and availability of information and information systems that they manage and that their service providers and business partners manage on behalf of the individuals and communities that they serve. -->

企業組織にとって, 不正アクセス, 可用性の問題, なりすまし, および他の不正などの Digital Identity セキュリティリスクを評価および管理し, 強力な ID ガバナンスプラクティスを確立することはますます重要となっている. 組織は, このガイダンスを参照しながら, 自分たちが管理し, サービスプロバイダやビジネスパートナーがサービスを提供する個人やコミュニティのために管理する情報および情報システムの機密性, 完全性, および可用性に対する潜在的な影響を検討する必要がある. 

<!-- Federal agencies implementing these guidelines need to adhere to their statutory responsibilities, including those under the _Federal Information Security Modernization Act (FISMA) of 2014_ [[FISMA]](sec8_references.md#ref-FISMA) and related NIST standards and guidelines. NIST recommends that non-federal organizations implementing these guidelines follow equivalent standards to ensure the secure operation of their digital systems. -->

本ガイドラインを導入する連邦政府機関は, _Federal Information Security Modernization Act (FISMA) of 2014_ [[FISMA]](sec8_references.md#ref-FISMA) および関連のNIST標準とガイドラインに基づくものを含む法的責任を遵守する必要がある. NISTは, これらのガイドラインを実施する非連邦組織が, デジタルシステムの安全な運用を確保するために, 同等の規格に従うことを推奨する. 

<!-- FISMA requires federal agencies to implement appropriate controls to protect federal information and information systems from unauthorized access, use, disclosure, disruption, or modification. The NIST RMF [[NISTRMF]](sec8_references.md#ref-NIST-RMF) provides a process that integrates security, privacy, and cyber supply chain risk management activities into the system development life cycle. It is expected that federal agencies and organizations that provide services under these guidelines have already implemented the controls and processes required under FISMA and associated NIST risk management processes and publications. -->

FISMA は, 連邦政府の情報および情報システムを不正なアクセス, 使用, 開示, 破壊, または改ざんから保護するために適切な管理を実施することを連邦機関に求める. NIST RMF [[NISTRMF]](sec8_references.md#ref-NIST-RMF) は, セキュリティ, プライバシー, サイバーサプライチェーンのリスク管理活動をシステム開発のライフサイクルに統合するプロセスを提供する. このガイドラインに基づいてサービスを提供する連邦政府機関や組織は, FISMAや関連するNISTのリスク管理プロセスや出版物の下で要求されるコントロールやプロセスをすでに実施していることを期待している. 

<!-- The controls and requirements encompassed by the identity, authentication, and federation assurance levels under these guidelines augment, but do not replace or alter, the information and information system controls as determined under FISMA and the RMF. -->

これらのガイドラインに基づく Identity, Authentication, および Federation Assurance Level に包含される管理 および要件は, FISMA および RMF に基づいて決定される情報および情報システムの管理を補完するが, 置き換えたり変更することはない. 

### Privacy

<!-- When designing, engineering, and managing digital identity systems, it is imperative to consider the potential of that system to create privacy-related problems for individuals when processing PII &mdash; a problematic data action &mdash; and the potential impact of the problematic data action should it occur. Additionally, by focusing on the privacy engineering objectives of predictability, manageability, and disassociability, organizations can determine the types of capabilities a given system may need to be able to demonstrate how organizational privacy policies and system privacy requirements have been implemented. -->

Digital Identity システムを設計, エンジニアリング, および管理する場合, そのシステムが PII を処理 (Processing) するときに個人のプライバシー関連の問題を引き起こす可能性, 問題のあるデータ操作, および問題のあるデータ操作が発生した場合の潜在的な影響を考慮することが不可欠である. さらに, Predictability, Manageability, およびDisassociabilityというプライバシー工学の目標に注目することで, 組織は, 組織のプライバシーポリシーとシステムのプライバシー要件がどのように実装されているかを実証できるように, 特定のシステムに必要な機能の種類を決定することができる.

<!-- The *Privacy Act of 1974, 2010 Edition*, [[PrivacyAct]](sec8_references.md#ref-PrivacyAct) established a set of fair information practices for the collection, maintenance, use, and disclosure of information about individuals that is maintained by federal agencies in systems of records. -->

*Privacy Act of 1974, 2010 Edition*, [[PrivacyAct]](sec8_references.md#ref-PrivacyAct)は, 連邦機関が記録システムに保持する個人に関する情報の収集, 維持, 使用, 開示に関する一連の公正な情報プラクティスを定めたものである.

<!-- When designing and implementing digital identity management processes and systems, privacy risk assessments are required for PII processing under these guidelines. Such privacy risk assessments can be used to support Privacy Impact Assessments under *OMB Guidance for Implementing the Privacy Provisions of the E-Government Act of 2002* [[M-03-22]](sec8_references.md#ref-M-03-22) as well as to select controls from NIST Special Publication 800-53, *Security and Privacy Controls for Information Systems and Organizations* [[SP800-53]](sec8_references.md#ref-SP800-53). Further, each volume of 800-63 (63A, 63B, and 63C) contains a specific section providing detailed privacy requirements and considerations for the implementation of the processes, controls, and requirements presented in that volume. -->

Digital Identity 管理プロセスおよびシステムを設計・実装する場合, プライバシー Risk Assessment はこれらのガイドラインに基づく PII Processing に必要となる. そのようなプライバシー Risk Assessment は, *OMB Guidance for Implementing the Privacy Provisions of the E-Government Act of 2002* [[M-03-22]](sec8_references.md#ref-M-03-22) に基づくPrivacy Impact Assessments の支援に使用できるほか, NIST Special Publication 800-53, *Security and Privacy Controls for Information Systems and Organizations* [[SP800-53]](sec8_references.md#ref-SP800-53) からコントロールを選択するためにも使用することができる. さらに, 800-63 の各巻（63A, 63B, 63C）には, その巻で提示されたプロセス, 管理, 要件の実装に関する詳細なプライバシー要件と考慮事項を示す特定のセクションが含まれている. 

### Equity

<!-- As defined in Executive Order 13985, *Advancing Racial Equity and Support for Underserved Communities Through the Federal Government* [[EO13985]](sec8_references.md#ref-EO13985), equity refers to the consistent and systematic fair, just, and impartial treatment of all individuals, including individuals who belong to underserved communities that have been denied such treatment, such as Black, Latino, and Indigenous and Native American persons, Asian Americans and Pacific Islanders, and other persons of color; members of religious minorities; lesbian, gay, bisexual, transgender, and queer (LGBTQ+) persons; persons with disabilities; persons who live in rural areas; and persons otherwise adversely affected by persistent poverty or inequality. -->

Executive Order 13985, *Advancing Racial Equity and Support for Underserved Communities Through the Federal Government* [[EO13985]](sec8_references.md#ref-EO13985) に規定されているように, Equityとは, 黒人, ラテン系, 先住民, ネイティブアメリカン, アジア系アメリカ人, 太平洋諸島民, その他の有色人種, 宗教的少数派の人々, レズビアン, ゲイ, バイセクシャル, トランスジェンダー, クィア（LGBTQ+）の人々, 障害者, 地方に住む人々, その他根強い貧困や不平等から悪影響を受ける人々など, これまでそうした扱いを受けてこなかった, 恵まれないコミュニティに属する個人を含むすべての個人に対する一貫した体系的かつ公正で公平な扱いを意味する. 

<!-- A person's ability to engage in an online transaction, such as accessing a critical service like healthcare, is often dependent on their ability to successfully and safely present a digital identity. Given the broad disparities that exist in the U.S. society and globally, many people are either unable to successfully present a digital identity, or they face a higher degree of burden in navigating online services than their more privileged peers, leaving them locked out of critical services or broader participation in the online world. In a public service context, this poses a direct risk to successful mission delivery. In a broader societal context, challenges related to digital access can exacerbate existing inequities and continue systemic cycles of exclusion for historically marginalized and underserved groups. -->

ヘルスケアなどの重要なサービスを利用する場合, オンライン Transaction に参加できるかどうかは, 多くの場合, Digital Identityを正しく安全に提示できるかどうかに依存している. 米国社会および世界的に存在する広範な格差を考慮すると, 多くの人々が Digital Identity をうまく提示できないか, またはオンラインサービスを利用する際に, より恵まれた人々よりも高い負担に直面し, 重要なサービスやオンラインの世界への幅広い参加から締め出されることになる. 公共サービスにおいては, このような状況は, ミッションを成功させるための直接的なリスクとなる. より広い社会的背景では, デジタルアクセスに関する問題は, 既存の不公平を悪化させ, 歴史的に疎外され, 十分なサービスを受けていないグループに対する排除の体系的なサイクルを継続させる可能性がある. 

<!-- Readers of this guidance are encouraged to consider existing inequities faced by the populations they serve to identify opportunities to design or operate digital identity systems and processes in ways that best support their needs. Readers are also encouraged to consider any potential or actual impact to the experiences and outcomes of these populations, including disparities between populations, caused by the design or operation of digital identity systems. -->

このガイダンスの読者は, Digital Identity システムおよびプロセスを彼らのニーズを最もよく支援する方法で設計または運用する機会を特定するために, サービスを提供する集団が直面する既存の不公平を考慮することが推奨される. 読者はまた, Digital Identity システムの設計または運用によって, 集団間の格差を含め, これらの集団経験および結果に潜在的または実際の影響を与えることを考慮するよう推奨される. 

<!-- For federal agencies implementing these guidelines, EO 13985 directs federal agencies to identify underserved communities for the programs and services that they provide and to determine and address any systemic barriers to underserved communities to provide equitable access to those programs and services. In alignment with the direction set by EO 13985, federal agencies should determine potential barriers communities and individuals may face to enrollment in and access to online benefits and services. They should also  identify whether programmatic changes may be necessary to advance equity. -->

このガイドラインを実施する連邦政府機関に対し, EO 13985 は, 連邦政府機関が提供するプログラムおよびサービスについて, 十分なサービスを受けていないコミュニティを特定し, それらのプログラムおよびサービスへの公平なアクセスを提供するために, 十分なサービスを受けていないコミュニティに対する制度的障害を特定し対処するよう指示している. EO 13985 の方向性に沿って, 連邦機関は, コミュニティや個人がオンライン給付やサービスへの登録やアクセスに直面する可能性のある障壁を判断するべきである. また, Equity を高めるためにプログラムの変更が必要であるかどうかを確認する必要がある. 

### Usability

<!-- Usability refers to the extent to which a system, product, or service can be used by specified users to achieve specified goals with effectiveness, efficiency, and satisfaction in a specified context of use. -->

Usability とは, あるシステム, 製品, サービスを, 特定のユーザーが, 特定の使用状況において, 有効性, 効率性, 満足性をもって, 特定の目標を達成するために使用できる程度を指す. 

<!-- Similar to equity, usability requires an understanding of the people interacting with a digital identity system or process, as well as their unique goals and context of use. To provide an effective, efficient, and satisfactory experience, readers of this guidance should take a holistic approach to considering the interactions that each user will engage in throughout the process of enrolling in and authenticating to a service. Throughout the design and development lifecycle of a digital identity system or process, it is important to conduct usability evaluation with representative users performing realistic scenarios and tasks in appropriate context of use. -->

Equity と同様に, Usability には Digital Identity システムまたはプロセスに触れる人々, および彼ら固有の目標や使用状況の理解が必要である. 効果的, 効率的, かつ満足のいく体験を提供するために, このガイダンスの読者は, Enrollment および Authentication のプロセスを通じて各ユーザが行うインタラクションを考慮する全体的なアプローチを取る必要がある. Digital Identity システムまたはプロセスの設計および開発ライフサイクルを通じて, 適切な使用状況で現実的なシナリオおよびタスクを実行する代表的なユーザに対する Usability 評価を実施することが重要である. 

<!-- Digital identity management processes should be designed and implemented so it is easy for users to do the right thing, hard to do the wrong thing, and easy to recover when the wrong thing happens. -->

Digital Identity　管理プロセスは, ユーザーが正しいことを行うのは簡単で, 間違ったことを行うのは困難であり, 間違ったことが起こったときに回復するのが簡単であるように設計および実装されるべきである. 