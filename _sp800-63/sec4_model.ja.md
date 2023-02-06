---
layout: default.ja
title: Digital Identity Model
navOrder: 4
navTitle: Model
permalink: /sp800-63/model/
anchor: sec4
section: 4
---

# Digital Identity Model {#sec4}

*This section is informative.*

## Overview {#s-4-1}

<!-- The SP 800-63 guidelines use digital identity models that reflect technologies and architectures currently available in the market. These models have a variety of entities and functions and vary in complexity. Simple models group functions, such as creating subscriber accounts and providing attributes, under a single entity. More complex models separate these functions among a larger number of entities. The entities and their associated functions found in digital identity models include: -->

SP 800-63 ガイドラインでは, 現在市場で入手可能な技術およびアーキテクチャを反映した Digital Identity モデルが使用されている. これらのモデルにはさまざまな主体および機能があり, 複雑さもさまざまである. 単純なモデルは, Subscriber Account の作成および Attribute の提供などの機能を 1 つの主体の下にグループ化する. より複雑なモデルでは, これらの機能をより多くの主体に分割している. Digital Identity モデルに見られる主体およびその関連機能には, 以下のものがある.

**Subject** (represented by one of three roles):

<!-- * Applicant &mdash; the subject to be identity proofed
* Subscriber &mdash; the subject that has successfully completed the identity proofing process or has successfully completed authentication
* Claimant &mdash; the subject to be authenticated -->

* Applicant &mdash; Identity Proofing される Subject
* Subscriber &mdash; Identity Proofing が完了した, または Authentication が完了した Subject
* Claimant &mdash; Authentication される Subject

<!-- **Credential Service Provider (CSP)**: A trusted entity whose functions include identity proofing applicants to the identity service and the registration of authenticators to subscriber accounts. A _subscriber account_ is the CSP's established record of the subscriber, the subscriber's attributes, and associated authenticators. A CSP may be an independent third party. -->

**Credential Service Provider (CSP)**: Identity サービスへの申請者の Identity Proofing ,および Subscriber Account への Authenticator の登録を含む機能を持つ, 信頼された主体. _Subscriber Account_ は, Subscriber, Subscriber の Attribute , および関連する Authenticator に関する CSP の確立された記録である. CSP は, 独立したサード・パーティである場合もある.

<!-- **Relying Party (RP)**: An entity that relies upon the information in the subscriber account, or an identity provider (IdP) assertion when using federation, typically to process a transaction or grant access to information or a system. -->

**Relying Party (RP)**: 通常, Transaction を処理し, 情報またはシステムへの Access を許可するために, Subscriber Account の情報, または Federation を使用する場合の Identity Provider (IdP) Assertion に依存する主体.

<!-- **Verifier**: An entity whose function is to verify the claimant's identity by verifying the claimant's possession and control of one or more authenticators using an authentication protocol. To do this, the verifier needs to confirm the binding of the authenticators with the subscriber account and check that the subscriber account is active. -->

**Verifier**: Authentication Protocol を使用して, Claimant が1 つまたは複数の Authenticator を所有および管理していることを検証することにより, Claimant の身元を確認する機能を有する主体. これを行うには, Verifier は Authenticator と Subscriber Account の紐づきを確認し, Subscriber Account がアクティブであることを確認する必要がある.

<!-- **Identity Provider (IdP)**: An entity in a federated model that performs both the CSP and Verifier functions. The IdP is responsible for authenticating the subscriber and issuing assertions to communicate with one or more RPs. -->

**Identity Provider (IdP)**: Federated モデルにおける, CSP と Verifier の両方の機能を実行する主体. IdP は, Subscriber の Authentication と, 1つまたは複数の RP と通信するための Assertion の発行を責務とする.

<!-- The entities and interactions that comprise the non-federated digital identity model are illustrated in [Figure 1](sec4_model.md#fig-1). The federated digital identity model is illustrated in [Figure 2](sec4_model.md#fig-2). -->

Non-federated Digital Identity モデルを構成する主体および相互作用を, [Figure 1](sec4_model.md#fig-1) に示す. Federated Digital Identity モデルは [Figure 2](sec4_model.md#fig-2) に示す.

[Figure 1. Non-federated Digital Identity Model Example](sec4_model.md#fig-1){:name="fig-1"}
{:latex-ignore="true"}

![High-level diagram of a non-federated digital identity model showing the entities and interactions between entities of the entire digital identity process, in which the verifier function is done by the RP.]({{site.baseurl}}/{{page.collection}}/media/Non-Federated.png 'Non-Federated Digital Identity Model Example'){:latex-src="Non-Federated.png" latex-fig="1" latex-place="h"}

<!-- [Figure 1](sec4_model.md#fig-1) shows an example of a common sequence of interactions in the non-federated model. Other sequences could also achieve the same functional requirements. The usual sequence of interactions for identity proofing and enrollment activities is as follows: -->

[Figure 1](sec4_model.md#fig-1) はNon-federated モデルでよく見られる相互作用のシーケンスの一例である. 他のシーケンスでも, 同じ機能要件を達成することができる. Identity Proofing よび Enrollment のための通常の相互作用のシーケンスは次のとおりである.

<!-- - Step 1: An applicant applies to a CSP through an enrollment process. The CSP identity proofs that applicant. -->

- Step 1: Applicantは, Enrollment プロセスを通じて CSP に申請する. CSP は, そのApplicantの身元を証明 (Identity Proof) する.

<!-- - Step 2: Upon successful proofing, the applicant is enrolled in the identity service as a subscriber. -->

- Step 2: Proofing に成功すると, Applicant は Identity サービスに Subscriber として Enrollment される.

<!--
     *	A subscriber account and corresponding authenticators are established between the CSP and the subscriber. The CSP maintains the subscriber account, its status, and the enrollment data. The subscriber maintains their authenticators.
-->

     * Subscriber Account および対応する Authenticator は, CSP と Subscriber の間で確立される. CSP は Subscriber Account, そのステータス, および Enrollment データを維持する. Subscriber は自分の Authenticator を保持する.

 <!-- The usual sequence of interactions involved in using one or more authenticators to perform digital authentication in the non-federated model is as follows: -->

Non-federated モデルにおいて, 1つまたは複数の Authenticator を使用して Digital Authentication を実行する際の, 通常の一連のやりとりは以下のとおりである.

<!-- - Step 3: The RP requests authentication from the claimant. -->

- Step 3: RP が Claimant に Authentication を要求する.

<!-- - Step 4: The claimant proves possession and control of the authenticators to the verifier through an authentication process. -->

- Step 4: Claimantは, Authentication プロセスを通じて, Authenticator の所有と管理を Verifier に証明する.

<!--
    -	The verifier interacts with the CSP to verify the binding of the claimant's identity to their authenticators in the subscriber account and to optionally obtain additional subscriber attributes.
    -  The CSP or verifier functions of the service provider provide information about the subscriber. The RP requests the attributes it requires from the CSP. The RP, optionally, uses this information to make authorization decisions.
-->

    - Verifier は CSP とやり取りして, Claimant の身元と Subscriber Account の Authenticator の結びつきを検証し, オプションで追加の Subscriber Attribute を取得する.
    - サービスプロバイダの CSP または Verifier の機能は, Subscriberに関する情報を提供する. RP は, 必要とする Attribute を CSP に要求する. RPは, オプションとして, この情報を使用して Authorization の決定を行う.

<!-- - Step 5: An authenticated session is established between the subscriber and the RP. -->

- Step 5: Subscriber と RP の間に Authenticated Session が確立される.

[Figure 2. Federated Digital Identity Model Example](sec4_model.md#fig-63Sec4-Figure2){:name="fig-2"}
{:latex-ignore="true"}

![High-level diagram of a federated digital identity model showing the entities and interactions between entities of the entire digital identity process, in which the CSP and verifier functions are done by the IdP.]({{site.baseurl}}/{{page.collection}}/media/Federated.png 'Federated Digital Identity Model Example'){:latex-src="Federated.png" latex-fig="2" latex-place="h"}

<!-- [Figure 2](sec4_model.md#fig-2) shows an example of those same common interactions in a federated model. -->

[Figure 2](sec4_model.md#fig-2) は, Federated モデルにおける同じ共通インタラクションの例である.

<!-- - Step 1: An applicant applies to an IdP through an enrollment process. Using its CSP function, the IdP identity proofs the applicant. -->

- Step 1: Applicantは, Enrollment プロセスを通じてIdPに申請する. IdPは, CSP機能を用いて, Applicant の Identity Proofing を行う.

<!-- - Step 2: Upon successful proofing, the applicant is enrolled in the identity service as a subscriber. -->

- Step 2: Proofing に成功すると, Applicant は Identity サービスに Subscriber として Enrollment される.

<!--
    -	A subscriber account and corresponding authenticators are established between the IdP and the subscriber. The IdP maintains the subscriber account, its status, and the enrollment data collected for the lifetime of the subscriber account (at a minimum). The subscriber maintains their authenticators.
-->

    -	Subscriber Account と対応する Authenticator は, IdP と Subscriber の間で確立される. IdP は, Subscriber Account とその状態, および収集した Enrollment データを Subscriber Account の存続期間中（最低限）保持する. Subscriber は Authenticator を保持する.

<!-- The usual sequence of interactions involved in using one or more authenticators in the federated model to perform digital authentication is as follows: -->

Federated モデルで1つ以上の Authenticator を使用してデジタル Authentication を行う際の通常の一連のやり取りは, 以下のとおり:

<!-- - Step 3: The RP requests authentication from the claimant. The IdP provides an assertion and optionally additional attributes to the RP through a federation protocol. -->

- Step 3: RP は Claimant に Authentication を要求する. IdP は Federation Protocol を通じて, RP に Assertion と, オプションで追加 Attribute を提供する.

<!-- - Step 4: The claimant proves possession and control of the authenticators to the verifier function of the IdP through an authentication process. -->

- Step 4: Claimant は Authentication プロセスを通じて, IdPの Verifier 機能に対して Authenticator の所有と管理を証明する.

<!--
    -	Within the IdP, the verifier and CSP functions interact to verify the binding of the claimant's authenticators with those bound to the claimed subscriber account and optionally to obtain additional subscriber attributes.
-->

    -	IdP 内では, Verifier と CSP の機能が相互に作用し, Claimant の Authenticator と Claimed Subscriber Account にバインドされている Authenticator のバインドを検証し, オプションとして追加の Subscriber Attribute を取得する.

<!-- - Step 5: All communication, including assertions, between the RP and the IdP happens through federation protocols. -->

- Step 5: RP と IdP の間の Assertion を含むすべての通信は, Federation プロトコルを通じて行われる.

<!-- - Step 6: The IdP provides the RP with the authentication status of the subscriber and relevant attributes and an authenticated session is established between the subscriber and the RP. -->

- Step 6: IdP は RP に Subscriber の Authentication の状況と, 関連する Attribute を提供し, Subscriber と RP の間で Authenticated Session が確立される.

<!-- For both models, the verifier does not always need to communicate in real time with the CSP to complete the authentication activity (e.g., some uses of digital certificates). Therefore, the line between the verifier and the CSP represents a logical link between the two entities. In some implementations, the verifier, RP, and CSP functions may be distributed and separated. However, if these functions reside on the same platform, the interactions between the functions are signals between applications or application modules running on the same system rather than using network protocols. -->

どちらのモデルでも, Verifier は Authentication アクティビティ（たとえば, デジタル証明書の一部の使用など）を完了するために, 常に CSP とリアルタイムで通信する必要はない. したがって, Verifier と CSP の間の繋がりは, 2つのエンティティ間の論理的な繋がりを表している. 一部の実装では, Verifier, RP, およびCSPの機能は分散され, 分離されている場合がある. しかし, これらの機能が同じプラットフォーム上に存在する場合, 機能間のインタラクションは, ネットワークプロトコルを使用するのではなく, 同じシステム上で動作するアプリケーションまたはアプリケーションモジュール間のシグナルとなる.

<!-- In all cases, the RP should request the attributes it requires from a CSP or IdP before authenticating the claimant. -->

いずれの場合も, RPは Claimant を Authentication する前に, CSP または IdP に必要な Attribute を要求する必要がある.

<!-- The following sections provide more detailed digital identity models for identity proofing, authentication, and federation. -->

以下のセクションでは, Identity Proofing, Authentication, および Federation に関するより詳細な Digital Identity モデルについて説明する.

## Enrollment and Identity Proofing

<!-- The previous section introduced the entities and interactions in the conceptual digital identity model. This section provides additional details regarding the participants' relationships and responsibilities with respect to identity proofing and enrollment processes. -->

前のセクションでは, 概念的な Digital Identity モデルにおけるエンティティとインタラクションについて紹介した. このセクションでは, Identity Proofing および Enrollment プロセスに関する参加者の関係および責任についての追加的な詳細を説明する.

<!-- [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"}, *Enrollment and Identity Proofing* provides general information and normative requirements for the identity proofing and enrollment processes as well as requirements specific to identity assurance levels (IALs). In addition to a "no identity proofing" level, IAL0, this document defines three IALs that indicate the relative strength of an identity proofing process. -->

[[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"}, *Enrollment and Identity Proofing* は, Identity Proofing および Enrollment プロセスに関する一般情報および標準的な要件と, Identity Assurance Level（IAL）に固有の要件を提供する. "No Identity Proofing" レベルである IAL0 に加えて, この文書では Identity Proofing プロセスの相対的な強さを示す 3 つの IAL を定義している.

<!-- An individual, referred to as an *applicant* at this stage, opts to enroll with a CSP. If the applicant is successfully proofed, the individual is then enrolled in the identity service as a *subscriber* of that CSP. -->

このステージで Applicant と呼ばれる個人は, CSP に Enroll することを選択する. Applicant の Proof に成功すると, その個人はその CSP の *Subscriber* として Identity サービスに登録される.

<!-- The CSP then establishes a subscriber account to uniquely identify each subscriber and record any authenticators registered (bound) to that subscriber account. The CSP may: -->

次に, CSP は, 各 Subscriber を一意に識別する Subscriber Account を確立し, その Subscriber Account に登録（バインド）されたすべての Authenticator を記録する. CSP は, 以下を行うことができる.

<!--
  - issue one or more authenticators to the subscriber at the time of enrollment,
  - bind authenticators provided by the subscriber, and/or
  - bind authenticators to the subscriber account at a later time as needed.
-->

  - Enrollment 時に, 1つ以上の Authenticator を Subscriber に発行する.
  - Subscriber より提供された Authenticator をバインドする, および／または
  - 必要に応じて, 後日, Subscriber Account に Authenticator をバインドする.

<!-- CSPs generally maintain subscriber accounts according to a documented lifecycle, which defines specific events, activities, and changes that affect the status of a subscriber account.  CSPs generally limit the lifetime of a subscriber account and any associated authenticators in order to ensure some level of accuracy and currency of attributes associated with a subscriber.  When there is a status change or when the authenticators near expiration and any renewal requirements are met, they may be renewed and/or re-issued.  Alternately, the authenticators may be invalidated and destroyed according to the CSPs written policy and procedures. -->

CSP は一般に, 文書化されたライフサイクルに従って Subscriber Account を維持する. このライフサイクルでは, Subscriber Account の状態に影響する特定のイベント, 活動, および変更が定義される. CSP は一般に, Subscriber に関連する Attribute の正確性と最新性をある程度保証するために, Subscriber Account および関連する Authenticator の有効期間を定める. ステータスに変更があった場合, または Authenticator の有効期限が近づいた場合, および更新要件が満たされた場合, Authenticator は更新および/または再発行されることがある. あるいは, CSP の文書化されたポリシーおよび手続きに従って, Authenticator が無効化され, 破棄されることもある.

<!-- Subscribers have a duty to maintain control of their authenticators and comply with CSP policies in order to remain in good standing with the CSP. -->

Subscriber は, CSP との良好な関係を維持するために Authenticator の管理を維持し, CSP ポリシーを遵守する義務がある.

<!-- In order to request issuance of a new authenticator, typically the subscriber authenticates to the CSP using their existing, unexpired authenticators. If the subscriber fails to request authenticator re-issuance prior to their expiration or revocation, they may be required to repeat the identity proofing (either complete or abbreviated) and enrollment processes in order to obtain a new authenticator. -->

新しい Authenticator の発行を要求するために, 通常 Subscriber は, 既存の有効期限内の Authenticator を使用して CSP に対して Authentication を行う. Subscriber が有効期限切れまたは失効前に Authenticator の再発行を要求しなかった場合, 新しい Authenticator を取得するために, Identity Proofing（完全または省略）および Enrollment プロセスを再度行うことが要求される場合がある.

<!-- [Figure 3](sec4_model.md#fig-3) shows a sample of interactions for identity proofing and enrollment. -->

[Figure 3](sec4_model.md#fig-3) に, Identity Proofing と Enrollment のためのインタラクションの例を示す.

[Figure 3. Sample Identity Proofing and Enrollment Digital Identity Model](sec4_model.md#fig-3){:name="fig-3"}
{:latex-ignore="true"}

![Sequence diagram of identity proofing and enrollment showing parties involved and major steps in the process.]({{site.baseurl}}/{{page.collection}}/media/ID_Proofing.png 'Sample Identity Proofing and Enrollment Digital Identity Model'){:latex-src="ID_Proofing.png" latex-fig="3" latex-place="h"}

~~~
\clearpage
~~~
{:latex-literal="true"}

## Authentication and Lifecycle Management

<!-- Normative requirements can be found in [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}, *Authentication and Lifecycle Management*. -->

標準的な要件は, [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}, *Authentication and Lifecycle Management* を参照のこと.

### Authenticators

<!-- The classic paradigm for authentication systems identifies three factors as the cornerstones of authentication: -->

Authentication システムの古典的パラダイムでは, 3つの要素を Authentication の要とする.

<!-- * Something you know (e.g., a password)
* Something you have (e.g., an ID badge or a cryptographic key)
* Something you are (e.g., a fingerprint or other biometric characteristic data) -->

* Something you know (例: Password)
* Something you have (例: IDカード, Cryptographic Key)
* Something you are (例: 指紋またはその他の Biometric 特有のデータ)

<!-- Single-factor authentication requires only one of the above factors, most often "something you know". Multiple instances of the same factor still constitute single-factor authentication. For example, a user generated PIN and a password do not constitute two factors as they are both "something you know." Multi-factor authentication (MFA) refers to the use of more than one distinct factor. For the purposes of these guidelines, using two factors is adequate to meet the highest security requirements. Other types of information, such as location data or device identity, may also be used by a verifier to evaluate the risk in a claimed identity but they are not considered authentication factors. -->

Single-factor Authentication は, 上記の要素のうち1つだけを必要とし, 多くの場合 "something you know" を必要とする. 同じ要素が複数ある場合でも, Single-factor Authentication となる. 例えば, ユーザーが作成した PIN とPassword は, どちらも "something you know" であるため, 2つの要素とはみなされない. Multi-factor authentication (MFA) とは, 1つ以上の異なる要素を使用することを指す. 本ガイドライン群の目的においては, 最高のセキュリティー要件を満たすには, 2つの要素を利用するのが適切である.　RP や Verifier は Claimed Identity に対するリスク評価のために, 位置データや Device Identity など, 上記以外のタイプの情報を利用することもありうるが, それらは Authentication Factor とは見なされない.

<!-- In digital authentication, the claimant possesses and controls one or more authenticators. The authenticators will have been bound with the subscriber account. The authenticators contain secrets the claimant can use to prove they are a legitimate subscriber. The claimant authenticates to a system or application over a network by demonstrating they have possession and control of the authenticator. Once authenticated, the claimant is referred to as a subscriber. -->

Digital Authentication では, Claimant は1つまたは複数の Authenticator を保持, 管理する. Authenticator は Subscriber Account にバインドされている. Authenticator には, Claimant が正当な Subscriber であることを証明するために使用できる Secret が含まれている. Claimantは, Authenticator を所有し管理していることを証明することにより, ネットワーク上のシステムまたはアプリケーションに対して Authenticate を行う. Authenticate されると, Claimantは Subscriber と呼ばれる.

<!-- The secrets contained in an authenticator are based on either key pairs (asymmetric cryptographic keys) or shared secrets (including symmetric cryptographic keys and memorized secrets). Asymmetric key pairs are comprised of a public key and a related private key. The private key is stored on the authenticator and is only available for use by the claimant who possesses and controls the authenticators. A verifier that has the subscriber's public key, for example through a public key certificate, can use an authentication protocol to verify the claimant has possession and control of the associated private key contained in the authenticators and, therefore, is a subscriber. -->

Authenticator に含まれる Secret は, Key Pair（Asymmetric Cryptographic Key）または Shared Secret（ Symmetric Cryptographic Keys, Memorized Secret を含む）のいずれかに基づいている. Asymmetric Key Pair は, Public Key と関連する Private Key で構成される. Private Key は Authenticator 内に保存され, Authenticator を所有し管理する Claimant のみが使用できる. Public Key Certificate などを通じて Subscriber の Public Key を持つ Verifier は, Authentication プロトコルを使用して Claimant が Authenticator に含まれる関連する Private Key を所有し管理していること, すなわち Subscriber であることを Verify する.

<!-- As mentioned above, shared secrets stored on an authenticator may be either symmetric keys or memorized secrets (e.g., passwords and PINs). While both keys and memorized secrets can be used in similar protocols, one important difference between the two is how they relate to the claimant. Symmetric keys are generally chosen at random and are complex and long enough to thwart network-based guessing attacks, and stored in hardware or software that the subscriber controls. Memorized secrets typically have fewer characters and less complexity than cryptographic keys to facilitate memorization and ease of entry. The result is that memorized secrets have increased vulnerabilities that require additional defenses to mitigate. -->

上述したように, Authenticator に格納される Shared Secret は, Symmetric Key または Memorized Secret (例えば, パスワードやPIN)のいずれかである可能性がある. Symmetric Key も Memorized Secret も同様のプロトコルで使用することができるが, 両者の重要な違いの1つは, それらが Claimant にどのように関係するかということである. Symmetric key は一般にランダムに選択され, ネットワークベースの Guessing Attack を阻止するのに十分な複雑さと長さを持ち, Subscriber が管理するハードウェアまたはソフトウェアに格納される. Memorized Secret は, 一般に, 暗記と入力を容易にするために, Cryptographic Key よりも文字数が少なく, 複雑でない. その結果, Memorized Secret は脆弱性が増加し, それを軽減するために追加の防御を必要とする.

<!-- There is another type of memorized secret used as an activation factor for a multi-factor authenticator. These are referred to as activation secrets. An activation secret is used to decrypt a stored key used for authentication or is compared against a locally held stored verifier to provide access to the authentication key. In either of these cases, the activation secret remains within the authenticator and its associated user endpoint. An example of an activation secret would be the PIN used to activate a PIV card. -->

Memorized Secret の Activation Factor として使用される Memorized Secret には, もう一つのタイプがある. これらは Activation Secret と呼ばれる. Activation Secret は Authentication に使用される保存された Key を復号するために使用されるか, または Authentication Key へのアクセスを提供するためにローカルに保存された Verifier と比較される. いずれの場合も, Activation Secret は, Authenticator とそれに関連するユーザーエンドポイント内に留まる. Activation Secretの例は, PIV カードを Activate するために使用される PIN である.

<!-- As used in these guidelines, authenticators always contain or comprise a secret; however, some authentication methods used for in-person interactions do not apply directly to digital authentication. For example, a physical driver's license is something you have and may be useful when authenticating to a human (e.g., a security guard) but it is not an authenticator for online services. -->

このガイドラインで使用されているように, Authenticator は常に Secret を含むか Secret を構成している. しかし, 対面での対話に使用される Authentication 方法の中には, Digital Authentication に直接適用されないものがある. たとえば, 物理的な運転免許証は, あなたが持っているもの(something you have)であり, 人間（例：警備員）に対して Authentication する場合には有用かもしれないが, オンライン・サービス用の Authenticator とはならない.

<!-- Some commonly used authentication methods do not contain or comprise secrets, and are therefore not acceptable for use under these guidelines. For example: -->

一般的に使用されている Authentication 方法の中には, Secret を含まない, あるいは Secret を構成しないものがあり, そのため本ガイドラインのもとでは使用できない. 例えば, 以下のようなものである.

<!-- -  Knowledge-based authentication, where the claimant is prompted to answer questions that are presumably known only by the claimant, does not constitute an acceptable secret for digital authentication.
-  A biometric also does not constitute a secret and can not be used as a single-factor authenticator. -->

-  Claimant だけが知っていると思われる質問に回答するよう Claimant に促す知識ベース認証 (Knowledge-Based Authentication) は, Digital Authentication の Secret として認められない.
-  また, Biometrics は Secret を構成しないため, Single-factor Authenticator として使用することはできない.

<!-- A digital authentication system may incorporate multiple factors in one of two ways: -->

Digital Authentication システムは, 以下の2つの方法のどちらかで複数の要素を内包する.

<!-- 1. The system may be implemented so that multiple factors are presented to the verifier, or
2. Some factors may be used to protect a secret that will be presented to the verifier. -->

1. 複数の要素が Verifier に提示される.
2. ある要素が Verifier に提示されるシークレットを保護するために利用される.

<!-- For example, item 1 can be satisfied by pairing a memorized secret (something you know) with an out-of-band device (something you have). Both authenticator outputs are presented to the verifier to authenticate the claimant. For item 2, the authenticator and authenticator secret could be a piece of hardware that contains a cryptographic key (something you have) that is controlled by the claimant where access is protected with a fingerprint (something you are). When used with the biometric factor, the cryptographic key produces an output that is used to authenticate the claimant. -->

例えば, 上記1は Memorized Secret (something you know) を Out-of-band Device (something you have) と組み合わせることで実現可能である. 両方の Authenticator Output が Verifier に提示され, Claimant の Authentication に使われる. 上記2は, Authenticator と Authenticator Secret は, Claimant が管理する Cryptographic Key（something you have） を含むハードウェアの一部で, Access が指紋（something you are）で保護されているものである. Biometric Factor と共に使用される場合, Cryptographic Key を使って Claimant を Authenticate するための Output が出力される.

<!-- As noted above, biometrics do not constitute acceptable secrets for digital authentication and, therefore, cannot be used for single-factor authentication. However, biometrics authentication can be used as an authentication factor for multi-factor authentication when used in combination with a possession-based authenticator. Biometric characteristics are unique, personal attributes that can be used to verify the identity of a person who is physically present at the point of verification. This includes, but is not limited to, facial features, fingerprints, iris patterns, and voiceprints. -->

上述のとおり, Biometricsは, Digital Authentication で利用可能なシークレットとはならないため, Single-factor Authentication に使用することはできない. しかし, Biometrics Authentication は, 所持ベースの Authenticator と組み合わせて使用する場合, Multi-factor Authentication の Authentication Factor として使用することができる. Biometric 特性は, Verification の時点で物理的に存在する人の Identity を確認するために使用できる, 固有の個人の Attribute である. これには, 顔の特徴, 指紋, 虹彩パターン, および声紋が含まれるが, これらに限定されない.

### Subscriber Accounts

<!-- As described in the preceding sections, a subscriber account binds one or more authenticators to the subscriber via an identifier as part of the registration process. A subscriber account is created, stored, and maintained by the CSP. The subscriber account records all identity attributes validated during the identity proofing process. -->

前節で説明したように, Subscriber Account は, 登録プロセスの一部として, Identifier を介して, 1つ以上の Authenticator を Subscriber にバインドする. Subscriber Account は, CSP によって作成, 保存, および維持される. Subscriber Account は, Identity Proofing プロセス中に検証されたすべての Identity Attribute を記録する.

### Authentication Process

<!-- The authentication process enables an RP to trust that a claimant is who they say they are. [Figure 4](sec4_model.md#fig-4) shows a sample authentication process. Other approaches are described in [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}, *Authentication and Lifecycle Management*. This sample authentication process shows interactions between the RP, a claimant, and a verifier/CSP. The verifier is a functional role and is frequently implemented in combination with the CSP, as shown in [Fig. 4](sec4_model.md#fig-4), the RP, or both. -->

Authentication プロセスにより, RPは Claimant による自分こそ本人であるという主張を信頼することができる. [Figure 4](sec4_model.md#fig-4)は Authentication プロセスの例を示している. その他のアプローチについては, [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}, *Authentication and Lifecycle Management* で説明されてる. このサンプル Authentication プロセスは, RP, Claimant,および Verifier / CSPの間のインタラクションを示す. Verifier は機能的な役割であり, [Fig. 4](sec4_model.md#fig-4) に示すように, CSP と組み合わせて実装されることが多いが, RP と組み合わせてもよい.

[Figure 4. Sample Authentication Process](sec4_model.md#fig-4){:name="fig-4"}
{:latex-ignore="true"}

![Sequence diagram of a sample authentication process showing parties involved and major steps in the process.]({{site.baseurl}}/{{page.collection}}/media/Sample_Authn_Process.png 'Sample Authentication Process'){:latex-src="Sample_Authn_Process.png" latex-fig="4" latex-place="h"}

<!-- A successful authentication process demonstrates that the claimant has possession and control of one or more valid authenticators that are bound to the subscriber's identity. In general, this is done using an authentication protocol involving an interaction between the verifier and the claimant. The exact nature of the interaction is extremely important in determining the overall security of the system. Well-designed protocols can protect the integrity and confidentiality of communication between the claimant and the verifier both during and after the authentication, and can help limit the damage that can be done by an attacker masquerading as a legitimate verifier. -->

Authentication プロセスの成功は, Claimant が Subscriber の Identity にバインドされている1つ以上の有効な Authenticator を所有し管理していることを証明する. 一般に, これは Verifier と Claimant の間のインタラクションを含む Authentication Protocol を使用して行われる. インタラクションの具体的な内容は, システム全体のセキュリティを決定する上で非常に重要である. よく設計されたプロトコルは, 認証中および認証後の請求者と検証者の間の通信の完全性と機密性を保護し, 正当な検証者を装った攻撃者が与える損害を制限するのに役立つ. よく設計されたプロトコルは, Authentication の最中および事後において, Claimant と Verifier の間のコミュニケーションの Integrity (完全性) および Confidentiality (機密性) を保護し, Attacker が正当な Verifier であるかのように偽装できてしまった場合の被害を限定的にする.

<!-- Additionally, mechanisms located at the verifier can mitigate online guessing attacks against lower entropy secrets &mdash; like passwords and PINs &mdash; by limiting the rate at which an attacker can make authentication attempts, or otherwise delaying incorrect attempts. Generally, this is done by keeping track of and limiting the number of unsuccessful attempts, since the premise of an online guessing attack is that most attempts will fail. -->

また, Verifier 側で Attacker による Authentication 試行レートを制限したり不正な試行を遅延させたりすることで, Password や PIN といったエントロピーの低いシークレットに対する Online Guessing Attack の影響を軽減できる. 一般的に Online Guessing Attack ではほとんどの試行が失敗するので, その対策は失敗試行数を制限するというような方式となる.

## Federation and Assertions {#Federation}

<!-- Normative requirements can be found in [[SP800-63C]](../_sp800-63c/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63C"}, *Federation and Assertions*. -->

標準的な要件は [[SP800-63C]](../_sp800-63c/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63C"}, *Federation and Assertions* を参照のこと.

<!-- In general usage, the term _federation_ can be applied to a number of different approaches involving the sharing of information between different trust domains. These approaches differ based on the kind of information that is being shared between the domains. Some common examples include: -->

一般的に _Federation_ という用語は, 異なる Trust ドメイン間の情報共有を含む多くの異なるアプローチに適用されることがある. これらのアプローチは, ドメイン間で共有される情報の種類によって異なる. 一般的な例としては, 以下のようなものがある.

<!-- - sharing identifiers (e.g., using a driver's license number or an email address),
- sharing authenticators (e.g., using a PKI authenticator for multiple applications),
- sharing identity assertions (e.g., a federation protocol like OpenID Connect or SAML),
- sharing account attributes (e.g., a provisioning protocol like SCIM), and
- sharing authorization decisions (e.g., a policy protocol like XACML). -->

- Identifier の共有 (例: 運転免許証やメールアドレスの利用),
- Authenticator の共有 (例: 複数のアプリケーションにおける PKI Authenticator の利用),
- Identity Assertion の共有 (例: OpenID Connect や SAML のような Federation Protocol),
- Account Attribute の共有 (例: SCIM のような Provisioning Protocol),
- Authorization Decisions の共有 (例: XACML のような Policy Protocol).

<!-- The SP 800-63 guidelines are agnostic to the identity proofing, authentication, and federation architectures an organization selects and they allow organizations to deploy a digital identity scheme according to their own requirements. However, there are scenarios that an organization may encounter that make federation potentially more efficient and effective than establishing identity services local to the organization or individual applications. The following lists detail scenarios where the organization may consider federation a viable option. These lists are provided for consideration and are not intended to be comprehensive. -->

SP 800-63 ガイドラインは, 組織が選択する Identity Proofing, Authentication, および Federation アーキテクチャには不可欠であり, 組織が独自の要件に従って Digital Identityスキームを展開することを可能にする. しかし, 組織が遭遇するシナリオには, 組織または個々のアプリケーションにローカルな Identity サービスを確立するよりも, Federation のほうが効率的かつ効果的である可能性があるものがある. 以下のリストは, 組織が Federation を有効なオプションと見なす可能性のあるシナリオの詳細を示している. これらのリストは検討のために提供されるものであり, 包括的であることは意図していない.

<!-- An organization should consider accepting federated identity assertions if any of the following apply: -->

組織は, 以下のいずれかに該当する場合, Federated Identity Assertion を受け入れることを検討すべきである.

<!-- 1. Potential users already have an authenticator at or above the required AAL.
2. Multiple types of authenticators are required to cover all possible user communities.
3. An organization does not have the necessary infrastructure to support management of subscriber accounts (e.g., account recovery, authenticator issuance, help desk).
4. There is a desire to allow primary authenticators to be added and upgraded over time without changing the RP's implementation.
5. There are different environments to be supported, as federation protocols are network-based and allow for implementation on a wide variety of platforms and languages.
6. Potential users come from multiple communities, each with its own existing identity infrastructure.
7. The ability to centrally manage account lifecycles, including account revocation and binding of new authenticators is important. -->

1. 想定される利用者が, 要求されたAAL以上の Authenticator をすでに持っている.
2. 想定されるすべてのユーザーコミュニティをカバーするためには複数のタイプの Authenticator が必要.
3. 組織に, Subscriber Account の管理をサポートするための必要なインフラがない（例：アカウントの回復, Authenticator の発行, ヘルプデスクなど）.
4. RP の実装を変更することなく, プライマリ Authenticator の追加やアップグレードが可能であることが望まれる.
5. Federation Protocol がネットワークベースであり, 様々なプラットフォームや言語での実装が可能であるため, サポートすべき環境が異なる.
6. 想定される利用者は複数のコミュニティから集まっており, それぞれが既存の Identity インフラを持っている.
7. アカウントの失効や新しい Authenticator のバインドなど, アカウントのライフサイクルを一元的に管理できることが重要である.

<!-- An organization should consider accepting federated identity attributes if any of the following apply: -->

組織は, 以下のいずれかに該当する場合, Federated Identity Attributes の受け入れを検討すべきである.

<!-- 1. Pseudonymity is required, necessary, feasible, or important to stakeholders accessing the service.
2. Access to the service requires a partial attribute list.
3. Access to the service requires at least one derived attribute value.
4. The organization is not the authoritative source or issuing source for required attributes.
5. Attributes are only required temporarily during use (such as to make an access decision), and the organization does not need to retain the data. -->

1. Pseudonymity が, サービスに Access する利害関係者に要求される, 必要である, 実行可能である, または重要である.
2. サービスへの Access には, 一部の Attribute リストが必要.
3. サービスに Access するためには, 少なくとも1つの Derived Attribute Value が必要.
4. 組織は, 要求された Attribute の Authoritative Source または Issuing Source ではない.
5. Attribute は使用時（Access 判断など）に一時的に必要となるだけで, 組織がデータを保持する必要はない.

### Federation Benefits

<!-- Federated architectures have many significant benefits, including, but not limited to: -->

Federated アーキテクチャには, 以下のような多くの重要な利点があるが, これらに限定されるものではない.

<!-- * Enhanced user experience: For example, an individual can be identity proofed once and reuse the subscriber account at multiple RPs.
* Cost reduction to both the user (reduction in authenticators) and the organization (reduction in information technology infrastructure).
* Minimizing data in applications as organizations do not need to collect, store, or dispose of personal information.
* Minimizing data exposed to applications, using pseudonymous identifiers and derived attribute values instead of copying account values to each application.
* Mission enablement: Organizations can focus on their mission without worrying about expending resources on identity management. -->

* ユーザーエクスペリエンスの向上. 例えば, ある個人が一度 Identity proofing すれば, 複数の RP でその Subscriber Account を再利用することができる.
* ユーザー（ Authenticator の削減）と組織（情報技術インフラの削減）双方にとってのコスト削減.
* 組織が Personal Information を収集, 保管, 廃棄する必要がないため, アプリケーションのデータを最小化できる.
* アカウントに保存されたそのものの値を各アプリケーションにコピーするのではなく, Pseudonymous Identifier や Derived Attribute Value を使用することで, アプリケーションに公開するデータを最小化できる.
* ミッションの実現: 組織は, Identity Management へのリソースの拡大を気にすることなく, ミッションに集中することができる.

<!-- The following sections discuss the components of a federated identity architecture should an organization elect this type of model. -->

以下のセクションでは, 組織がこのタイプのモデルを選択する場合の, Federated Identity アーキテクチャの構成要素について説明する.

### Federation Protocols and Assertions

<!-- Federation protocols allow for the conveyance of assertions, authentication attributes, and subscriber attributes across networked systems. In a federation scenario, as shown in [Figure 2](sec4_model.md#fig-2), the CSP provides a service known as an identity provider, or IdP. The IdP acts as a verifier for authenticators issued by the CSP. Using federation protocols, the IdP sends a message, called an assertion, about this authentication event to the RP. Assertions are verifiable statements from an IdP to an RP that represent an authentication event for a subscriber. The RP receives and uses the assertion provided by the IdP, but the RP does not verify authenticators directly. -->

Federation プロトコルでは, ネットワークシステム間で Assertion, Authentication Attribute, Subscriber Attribute を伝達することができる. Federation のシナリオでは, [Figure 2](sec4_model.md#fig-2) に示すように, CSP は Identity Provider または IdP と呼ばれるサービスを提供する. IdP は, CSP が発行する Authenticator の Verifier として機能する. Federation プロトコルを使用して, IdP は, この Authentication イベントに関する Assertion と呼ばれるメッセージを RP に送信する. Assertion は, Subscriberの Authentication イベントを表す, IdP から RP への検証可能な Statement である. RP は IdP から提供された Assertion を受信して使用するが, RP が Authenticator を直接 Verify することはない.

<!-- Federation is generally used when the RP and the IdP are not a single entity or are not under common administration, though this technology can be applied within a single security domain for a variety of reasons. The RP uses the information in the assertion to identify the subscriber and make authorization decisions about their access to resources controlled by the RP. -->

Federation は, 一般に RP と IdP が単一のエンティティでない場合, または共通の管理下にない場合に使用されるが, さまざまな理由から単一のセキュリティドメイン内でこの技術を適用することができる. RP は, Assertion 内の情報を使用して Subscriber を識別し, RP が管理するリソースへの Access に関する Authorization の決定を行う.

<!-- Examples of assertions include: -->

Assertion の例を以下に挙げる.

<!-- * Security Assertion Markup Language (SAML) assertions are specified using a mark-up language intended for describing security assertions. They can be used by a verifier to make a statement to an RP about the identity of a claimant. SAML assertions may optionally be digitally signed.
* OpenID Connect claims are specified using JavaScript Object Notation (JSON) for describing security, and optionally, user claims. JSON user information claims may optionally be digitally signed.
* Kerberos tickets allow a ticket-granting authority to issue session keys to two authenticated parties using symmetric or asymmetric key establishment schemes. -->

* Security Assertion Markup Language (SAML) Assertion はセキュリティー Assertion を記述するためのマークアップランゲージによって規定される. SAML Assertion は Verifier が RP に対して Claimant の Identity に関するステートメントを生成するために利用される. SAML Assertion にはデジタル署名が施されることもある.
* OpenID Connect Claim は, JavaScript Object Notation (JSON) を使ってセキュリティー Claim および任意でユーザー Claim を記述するために規定される. JSON User Information Claims にはデジタル署名が施されることもある.
* Kerberos Ticket は, Ticket-granting Authority が Symmetric または Asymmetric Key ベースの Key Establishment Schemes を利用し, 2つの Authenticated な主体 にSession Key を発行することを可能にする.

### Relying Parties

<!-- An RP relies on results of an authentication protocol to establish confidence in the identity or attributes of a subscriber for the purpose of conducting an online transaction. RPs may use a subscriber's federated identity (pseudonymous or non-pseudonymous), IAL, AAL, FAL, and other factors to make authorization decisions. -->

RP は, オンライン Transaction を行うために, Authentication Protocol の結果を頼りに Subscriber の Identity ないしは Attribute に関する確からしさを確立する. RP は, Subscriber の Federated Identity (Pseudonymous なこともあればそうでないこともある), IAL, AAL, FAL およびその他の要素をもとに, Authorization の決定を行う.

<!-- When using federation, the verifier is not a function of the RP. A federated RP receives an assertion from the IdP, which provides the verifier function, and the RP ensures that the assertion came from an IdP that is trusted by the RP. The RP also processes any additional information in the assertion, such as personal attributes or expiration times. The RP is the final arbiter concerning whether a specific assertion presented by a verifier meets the RP's established criteria for system access regardless of IAL, AAL, or FAL. -->

Federation を使用する場合, Verifierは RP の機能ではない. Federation を利用する RP は, Verifier 機能を提供する IdP から Assertion を受け取り, その Assertion が RP の信頼する IdP から来たことを確認する. RP は, Assertion に含まれる Personal Attribute や有効期限などの追加情報も処理する. RP は, Verifier から提示された特定の Assertion が, IAL, AAL, FAL にかかわらず, RP の確立したシステム Access の基準を満たしているかどうかを判断する最終裁定者となる.
