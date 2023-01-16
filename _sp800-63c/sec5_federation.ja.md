---
layout: default.ja
title: Federation
navOrder: 5
navTitle: Federation
permalink: /sp800-63c/federation/
anchor: federation
section: 5
---

# Federation {#federation}

*This section is normative.*

<!--
In a federation protocol, a three-party relationship is formed between the subscriber, the IdP, and the RP, as shown in [Figure 1](sec5_federation.md#fig-1).
-->

Federation Protocol においては, [Figure 1](sec5_federation.ja.md#fig-1) に示されるように, Subscriber, IdP および RP の三者間の関係性が形成される.

[Figure 1. Federation Overview](sec5_federation.md#fig-1){:name="fig-1"}
{:latex-ignore="true"}

![Overview diagram of federated authentication systems showing parties involved and major steps in the process.]({{site.baseurl}}/{{page.collection}}/media/federation.png 'Federation Overview'){:style="width:628px;height:600px;;min-width: 628px;min-height: 600px;" latex-src="federation.png" latex-fig="1" latex-place="h"}

<!--
A federation relationship between an IdP and RP is established in a multi-stage process:
-->

IdP-RP 間の Federation の関係性は多段階のプロセスにより確立される.

<!--
1. First, the IdP and RP agree to enter into a trust agreement. This agreement can be bilateral between the parties, multilateral at the behest of an authority, or proxied through a trusted party. This step represents initial permission for the two systems in question to connect. Parameters of what can be requested and released are established in this step, though the details of which attributes are released to a given RP for a given subscriber can be deferred until a later stage.
-->

1. まず, IdP と RP が Trust Agreement の締結に合意する. これは二者間合意でも良いし, オーソリティの要請による多者間合意や信頼できる当事者を通じた委任によるものでもよい.
このステップは2つのシステムが接続するための最初の許可となる.
リクエストおよび開示できるパラメータはこのステップで確立される.
どの Attribute が所与の RP および Subscriber について開示されるかの詳細についての決定は, 以降のステージに遅延されることもある.

<!--
2. Next, the IdP and RP perform registration to establish their trust at a protocol level, allowing for information to be securely exchanged between the parties. While the first step entails a policy decision representing a permission to connect, this step entails establishment of credentials and identifiers representing the IdP and RP to allow communication through the federation protocol. This stage can occur before any subscriber tries to log in to the RP or as a response to a subscriber's attempt to use an IdP at an RP.
-->

2. 次に, IdP と RP はプロトコルレベルで信頼関係を確立するため Registration を行う. これにより当事者間で情報がセキュアに交換可能となる.
最初のステップでは接続許可を示すポリシー決定が行われるが, このステップでは IdP と RP を示す Credential および識別子の確立が行われる. これにより Federation Protocol を通じてコミュニケーションが可能となる.
このステージは Subscriber が RP にログインしようとする前に実施することもあるし, Subscriber が RP に対して IdP を利用するよう試行した結果として実施されることもある.

<!--
3. Next, the IdP and RP determine that they want to engage in a a to authenticate the subscriber. As part of this, they determine which attributes about the subscriber are to be passed from the IdP to the RP during this transaction. The decision made in this step builds on the trust agreement established in the first step and the identities of the RP and IdP established in the second step.
-->

3. 次に, IdP と RP は Subscriber を Authenticate するため Federation Transaction を実施することを決定する.
この一環として, IdP と RP は当該 Transaction において Subscriber に関するどの Attribute が IdP から RP に渡されるかを決定する.
このステップにおける決定は, 最初のステップで確立された Trust Agreement と, 2つめのステップで確立された RP および IdP の Identity に基づいて行われる.

<!--
4. Finally, the subscriber authenticates to the IdP and the result of that authentication event is asserted to the RP across the network. The RP processes this assertion from the IdP and establishes an authenticated session with the subscriber.
-->

4. 最後に, Subscriber は IdP に対して Authenticate し, その Authentication イベントの結果がネットワークを介して RP に Assertion として提示される.
RP は IdP から提示されたこの Assertion を処理し, Subscriber との間に認証済 Session を確立する.

<!--
In this transaction, the IdP acts as the verifier of the subscriber's authenticators, as described in [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}. The authentication event information is carried from the IdP to the RP through the use of an assertion, described in [Sec. 6](sec6_assertions.md#assertions). The IdP can also make statements about identity attributes of the subscriber as part of this assertion or through a secondary identity protocol protected by an authorized credential.
-->

この Transaction において, IdP は [[SP800-63B]](../_sp800-63b/sec1_purpose.ja.md#purpose){:latex-href="#ref-SP800-63B"} に述べるように Subscriber の Authenticator の Verifier として動作する.
Authentication イベントの情報は [Sec. 6](sec6_assertions.ja.md#assertions) に述べるように IdP から RP に Assertion を介して伝搬される.
IdP は, Assertion の一部として, ないしは Authorize された Credential で保護されたセカンダリな Identity プロトコルを通じて, Subscriber の Identity Attribute についてのステートメントを生成することができる.

## Trust Agreements {#trust-agreement}

<!--
IdPs that provide authentication services and RPs that consume those services are known as members of a federation. From an IdP's perspective, the federation consists of the RPs that it serves. From an RP's perspective, the federation consists of the IdPs that it uses. This section provides an overview of and requirements for common identity federation models currently in use. In each model, relationships are established between members of the federation. These relationships are  established in either a bilateral or multilateral fashion, as described in the following sections.
-->

Authentication サービスを提供する IdP とそのサービスを利用する RP は Federation のメンバーとなる.
IdP から見ると, Federation とは IdP がサービスを提供する相手である RP 群からなる.
RP から見ると, Federation とは RP が利用する IdP 群からなる.
本セクションでは, 現在利用されている Identity Federation モデルの概観について述べる.
各モデルで Federation メンバー間の関係性が構築される.
この関係性は後述のように二者間で確立されることもあるし多者間で確立されることもある.

<!--
Trust agreements **SHALL** establish the following parameters:
-->

Trust Agreement では, 以下のパラメータを確立することとする (**SHALL**).

<!--
- The set of attributes the IdP can make available to the RP
- The population of subscriber accounts the IdP can create assertions for
- The set of attributes the RP will request (a subset of the attributes made available)
- The purpose for each attribute requested by the RP
- The authorized party responsible for decisions regarding the release of subscriber attributes
- The means of informing subscribers about attribute release to the RP
- The xALs available from the IdP
- The xALs required by the RP
-->

- IdP が RP に対して開示できる Attribute のリスト
- IdP が Assertion を生成できる Subscriber Account の母集団
- RP がリクエストする Attribute のリスト (IdP が RP に対して開示できるリストのサブセット)
- RP がリクエストする各 Attribute についてその利用目的
- Subscriber Attribute の開示にかかる意思決定の責務を負う Authorized Party
- Subscriber が RP に開示される Attriburte について知る手段
- IdP が提供しうる xAL
- RP が必要とする xAL

<!--
Trust agreements are able to be established either statically or dynamically. In a static establishment, there is often a legal or contractual agreement binding the parties to a set of expected behaviors, rights, and requirements. The parameters of static trust agreements **SHALL** be available to all parties in the agreement, including the operator of the IdP, the operator of the RP, and affected subscribers.
-->

Trust Agreement は Static に確立されることもあれば Dynamic に確立されることもある.
Static Trust Agreement の確立においては, 双方に期待される挙動, 権利および要件について, 法的ないしは契約に基づいた合意がなされる.
Static Trust Agreement のパラメータは, 当該合意に参加する全当事者 (IdP や RP のオペレーターや影響する Subscriber を含む) に開示されなければならない (**SHALL**).

<!--
In dynamic trust establishment, in contrast, the trust agreement is implicitly defined when the RP and IdP first contact each other for the purposes of a subscriber's login. The expression of the parameters of a dynamic trust agreement is driven by the federation protocol in place, and are not usually tied to a contractual agreement between the federating parties. The parameters of a dynamic trust agreement **SHALL** be disclosed to the subscriber by the RP and the IdP during the federation transaction.
-->

Dynamic Trust Agreement 確立においては, Static な場合とは裏腹に, Trust Agreement は RP と IdP が Subscriber をログインさせる目的でやり取りをする初回に暗黙的に確立される.
Dynamic Trust Agreement のパラメータ表現は Federation Protocol によって定められ, 通常は Federation に参加する当事者間の契約等には紐づかない.
Dynamic Trust Agreement のパラメータは, Federation Transaction 中に IdP および RP から Subscriber に開示されなければならない.

<!--
The _authorized party_ in a trust agreement is the organization, person, or entity that is responsible for the specific release decisions covered by the trust agreement, including the release of subscriber attributes. For a static trust agreement, the authorized party **MAY** be the organization responsible for the IdP. In this case, consent to release attributes is decided for all subscribers and established by an allowlist as described in [Sec. 5.3.1](sec5_federation.md#idp-allowlist), allowing for the disclosure of attribute information without direct decisions and involvement by the subscriber. A static trust agreement **MAY** stipulate that an individual, such as the subscriber, is to be prompted at runtime for consent to disclose attributes as discussed in [Sec. 5.3.3](sec5_federation.md#idp-runtime-decision). Since dynamic trust agreements are established by subscriber actions, the authorized party in a dynamic trust agreement is always the subscriber. Disclosure of attributes in dynamic trust agreements **SHALL** be subject to a runtime decision from the subscriber and **SHALL NOT** be subject to an allowlist at the IdP.
-->

Trust Agreemeent における Authorized Party は, Subscriber Attribute の開示を含む Trust Agreement がカバーする特定の開示決定に責務を負う組織, 個人ないしはなんらかの主体である.
Static Trust Agreement では Authorized Party は IdP を管理する組織でありえる (**MAY**).
そのようなケースでは, Attribute 開示の同意は全ての Subscriber に対して決定され, [Sec. 5.3.1](sec5_federation.ja.md#idp-allowlist) に述べるように Allowlist 形式で確立された上で, Subscriber の直接の意思決定や関与を必要としない.
Static Trust Agreement では, [Sec. 5.3.3](sec5_federation.ja.md#idp-runtime-decision) に述べるように, Subscriber をはじめとする個人が Attribute 開示への同意を実行時に促されるように規定することもある (**MAY**).
Dynamic Trust Agreement は Subscriber のアクションを起点に確立されるため, Dynamic Trust Agreement における Authorized Party は常に Subscriber である.
Dynamic Trust Agreement における Attribute の開示は Subscriber による実行時の決定の対象とせねばならず (**SHALL**), IdP の Allowlist の対象としてはならない (**SHALL NOT**).

<!--
For example, a static trust agreement is established for an organization (the IdP) connecting to an enterprise service (the RP) to be made available to all subscribers at the organization on an allowlist. The authorized party for this trust agreement is the organization. When a subscriber logs in to the enterprise service, they are not prompted with any runtime decisions regarding the service since the static trust agreement establishes this a priori. In a different scenario, another service is made available to all subscribers at the same organization, but the static trust agreement stipulates that the subscriber is the authorized party. When logging in to the service for the first time, each subscriber is prompted for their consent to release their attributes to the RP. In another scenario, a dynamic trust agreement is established implicitly when a subscriber goes to access an RP that is otherwise unknown by their IdP. The RP informs the subscriber about the uses of all attributes being requested from the IdP, and the IdP prompts the subscriber for consent to release their attributes to the RP.
-->

例えば Static Trust Agreement は, エンタープライズサービス (RP) を Allowlist に基づき組織 (IdP) の全 Subscriber に提供するために確立されることもある.
この場合 Trust Agreement の Authorized Party は組織である.
Subscriber がエンタープライズサービスにログインする際は, 当該サービスに関してはなんら実行時決定は要求されない. これは Static Trust Agreement がそのように事前に確立されているからである.
別の例として, 同じ組織において別のサービスが全 Subscriber に提供されているが, 当該 Static Trust Agreement においては Subscriber が Authorized Party となっていることもある.
この場合, 当該サービスへの初回ログイン時には各 Subscriber が自身の Attribute を RP に開示する旨の同意を促される.
また別の例としては, Subscriber が IdP にとって未知な RP にアクセスした時点で Dynamic Trust Agreement が暗黙的に確立されることもある.
この場合, RP は Subscriber に対して IdP に対して当該 RP が要求する全 Attribute の利用について通知し, IdP はそれらの Attribute の開示について Subscriber に同意を促す.

<!--
Establishment of a trust agreement is required for all federation transactions, even those in which the IdP and RP have a shared security domain or shared legal ownership. In such cases, the establishment of the trust agreement is an internal process that can be completed quickly.
-->

Trust Agreement の確立は全ての Federation Transaction において必要となる.
IdP と RP が同一セキュリティドメインにあったり同じ法的所有権のもとにあってもそれは同様である.
そのような場合においては, Trust Agreement の確立は内部プロセスにより迅速に完了できるであろう.

<!--
During the course of a single federation transaction, it is important for the policies and expectations of the IdP and RP to be unambiguous for all parties involved. Therefore, there **SHOULD** be only one set of trust agreements in effect for a given transaction. This will usually be determined by the unique pair consisting of a single IdP and a single RP. However, these agreements could vary in other ways, such as an IdP and RP having different agreements for different populations of subscribers.
-->

単一の Federation Transaction の間, IdP と RP のポリシーおよび期待値が Transaction 参加者全員に対して明白であることが重要である.
従って, ある Transaction に対しては単一セットの Trust Agreement のみが有効とされるべきである (**SHOULD**).
これは通常単一の IdP および RP のペア毎に決定される.
しかしながら, Trust Agreement の有り様は多様であり, 単一の IdP および RP のペアが異なる Subscriber の集団毎に対して異なる Agreement を持つこともありえる.

<!--
The existence of a trust agreement between two parties does not preclude the existence of other agreements for each party in the agreement to have with other parties. That is to say, an IdP can have (and generally does have) independent agreements with multiple RPs simultaneously, and an RP can likewise have independent agreements with multiple IdPs simultaneously.
-->

2当事者間の Trust Agreement が存在したからといって, 当該 Agreement の各当事者が他の当事者と別の Agreement を持つことは排除されない.
つまり, IdP は同時に複数の RP に対してそれぞれ独立した Agreement を持つことができる (また, 一般的にはそうなっている).
また RP も同様に, 同時に複数の RP に対してそれぞれ独立した Agreement を持つことができる.

### Bilateral Trust Agreements {#bilateral}

<!--
In a bilateral trust agreement, each potential pairing of an IdP and RP form a trust relationship with each other. In this model, the IdP and RP each act as their own authority and establish the other party as capable of performing its role within the federation.
-->

二者間 (Bilateral) Trust Agreement においては, 組み合わせうる各 IdP-RP ペアが相互に信頼関係を構築する.
このモデルでは, IdP と RP がそれぞれ自ら Authority となり, 相手を Federation において役割を担えるものとして認める.

<!--
The IdP **SHALL** disclose its supported IAL, AAL, and FAL levels to the RP. The IdP **MAY** disclose a subset of its capabilities to a given RP depending on the needs of the application, for example only disclosing to a low-risk RP that accounts are proofed at IAL1 or better.
-->

IdP は自信がサポートする IAL, AAL および FAL を RP に開示せねばならない (**SHAL**).
IdP はアプリケーションのニーズに応じて RP に自身の機能のサブセットを開示してもよい (**MAY**).
例えば, 低リスクな RP にのみアカウントが IAL1 以上で確認されていることを開示するなど.

<!--
The RP **SHALL** disclose its list of required attributes to the IdP, including its purpose for use of each requested attribute. The RP **SHALL** communicate its required IAL, AAL, and FAL to the IdP, including whether no claim is required for IAL or AAL.
-->

RP は自信が必要とする Attribute をその利用目的を含めて IdP に開示せねばならない (**SHALL**).
RP は必要とする IAL, AAL および FAL を IdP に伝えねばならない (**SHALL**).
これにはいかなる IAL や AAL も必要としないということも含まれる.

<!--
The IdP **SHALL** transmit only those attributes that were explicitly requested by the RP. RPs **SHALL** include their requested attributes in their privacy risk assessment.
-->

IdP は RP が明示的にリクエストした Attribute のみを伝達すること (**SHALL**).
RP はリクエストした Attribute を Privacy Risk Assessment の対象とすること (**SHALL**).

### Multilateral Trust Agreements {#authorities}

<!--
In a multilateral trust agreement, the federated parties defer to a *federation authority* to assist in making federation trust decisions and to establish the working relationship between parties. In this model, the federation authority manages the membership of IdPs and RPs in the federation agreement. The federation authority conducts some level of vetting on each party in the federation to verify compliance with predetermined standards that define the trust agreement. The level of vetting is unique to the use cases and models employed within the federation. This vetting is depicted in the left side of [Figure 2](sec5_federation.md#fig-2).
-->

多者間 (Multilateral) Trust Agreement においては, Federation 当事者は Federation の信頼に関する決定を支援し当事者間での関係確立を行うため, *Federation Authority* に従う.
このモデルでは, Federation Authority は Federation Agreement に参加する IdP および RP を管理する.
Federation Authority は Federation に参加する各当事者に対して何らかの審査を行い, Trust Agreement を定義する事前に決定された標準に準拠しているか検証する.
審査のレベルは Federation のユースケースやそこで採用されるモデル毎に異なる.
[Figure 2](sec5_federation.ja.md#fig-2) の左サイドはこの審査を表現している.

<!--
Federation authorities approve IdPs to operate at certain IALs, AALs, and FALs. This information is used by relying parties, as shown in the right side of [Figure 2](sec5_federation.md#fig-2), to determine which identity providers meet their requirements.
-->

Federation Authority は IdP が所定の IAL, AAL および FAL で動作することを承認する.
この情報は, RP がどの IdP であれば自身の要件を満たすかを決定するために用いられる.
[Figure 2](sec5_federation.ja.md#fig-2) の右サイドがこれを表現している.

<!--
Federation authorities **SHALL** establish parameters regarding expected and acceptable IALs, AALs, and FALs in connection with the federated relationships they enable. Federation authorities **SHALL** individually vet each participant in the federation to determine whether they adhere to their expected standards.
-->

Federation Authority は, 自信が有効にする Federation 関係に対して, 期待される許容可能な IAL, AAL および FAL に関するパラメータを確立しなければならない (**SHALL**).
Federation Authority は Federation 参加者を個々に審査し, 彼らが期待される標準を遵守しているかどうか判断せねばならない (**SHALL**).

[Figure 2. Federation Authority](sec5_federation.md#fig-2){:name="fig-2"}
{:latex-ignore="true"}

![Diagram of a federation authority providing trust decisions for a federation network of IdPs and RPs.]({{site.baseurl}}/{{page.collection}}/media/authority.png 'Federation Authority'){:style="width:789px;height:490px;;min-width:789px;min-height:490px;" latex-src="authority.png" latex-fig="2" latex-place="h"}

<!--
Vetting of IdPs and RPs **SHALL** establish, as a minimum, that:
-->

IdP と RP の審査結果は最低限以下のようなものとなる.

<!--
* Assertions generated by IdPs adhere to the requirements in [Sec. 6](sec6_assertions.md#assertions).
* RPs adhere to requirements for handling subscriber attribute data, such as retention, aggregation, and disclosure to third parties.
* RP and IdP systems use approved profiles of federation protocols.
-->

* IdP が生成する Assertion は　[Sec. 6](sec6_assertions.ja.md#assertions) の要件に従っている.
* RP は Subscriber Attribute の保持, 集約および第三者への開示といった取り扱いに関する要件に従っている.
* RP と IdP のシステムは許可された Federation Protocol のプロファイルを利用している.

<!--
Federation authorities **MAY** assist the technical connection and configuration process between members, such as by publishing configuration data for IdPs or by issuing software statements for RPs.
-->

Federation Authority はメンバー間の技術的な接続および設定プロセスを支援してもよい (**MAY**).
IdP に対する設定データの発行や, RP に対する Software Statement の発行などが例として挙げられる.

<!--
Most federations managed through authorities have a simple membership model: parties are either in the federation or they are not. More sophisticated federations **MAY** have multiple membership tiers that federated parties can use to tell whether other parties in the federation have been more thoroughly vetted. IdPs **MAY** decide that certain subscriber attributes are only releasable to RPs in higher tiers and RPs **MAY** decide to accept certain information only from IdPs in higher tiers.
-->

Authority を介して管理されるほとんどの Federation は単純なメンバーシップモデルで構成され, 当事者は Federation に参加しているかいないかのどちらかである.
より高度な Federation では, 複数のメンバーシップ層が存在することもあり (**MAY**), Federation 当事者はその情報を用いて Federation 内の他当事者がより徹底した審査を通過しているか判断する.
IdP は特定の Subscriber Attribute をより高い層の RP にのみ開示するといった決定をすることもあり (**MAY**), RP は特定の情報をより高い層の IdP からのみ受け入れるといった決定をすることもある (**MAY**).

### Proxied Federation {#proxied}

<!--
In a proxied federation, all communication between the IdP and the RP is passed through an intermediary party in a way that prevents direct communication between the two parties. There are multiple methods to achieve this effect. Common configurations include:
-->

Proxied Federation においては, IdP-RP 間の全ての通信は中間者を介して行われ, 2者間の直接通信は防止される.
これを実現するにはいくつかの方法がある.
一般的な構成には以下のようものが含まれる.

<!--
* A third party that acts as a federation proxy (or *broker*)
* A network of nodes that distributes the communications and functions as a proxy between the endpoints
-->

* Federation Proxy (*Broker* とも呼ばれる) として動作する第三者
* 通信を振り分けエンドポイント間で Proxy として機能するノードからなるネットワーク

<!--
Where proxies are used, they function as an IdP on one side and an RP on the other. Therefore, all normative requirements that apply to IdPs and RPs **SHALL** apply to proxies in their respective roles.
-->

Proxy を利用する場合, 当該 Proxy はある一方には IdP, またある一方には RP として動作する.
従って IdP と RP に適用される全規範的要件が対応する役割を担う各 Proxy に適用されねばならない (**SHALL**).

[Figure 3. Federation Proxy](sec5_federation.ja.md#fig-3){:name="fig-3"}
{:latex-ignore="true"}

![Diagram of a federation proxy accepting assertions from an upstream IdP and providing assertions to a downstream RP.]({{site.baseurl}}/{{page.collection}}/media/broker.png 'Federation Proxy'){:style="width:600px;height:150px;;min-width:600px;min-height:150px;" latex-src="broker.png" latex-fig="3" latex-place="h"}

<!--
A proxied federation model can provide several benefits. Federation proxies can simplify technical integration between the RP and IdP by providing a common interface for integration. Additionally, to the extent a proxy effectively blinds the RP and IdP from each other, it can provide some business confidentiality for organizations that want to guard their subscriber lists from each other. Proxies can also mitigate some of the privacy risks described in [Sec. 5.5](sec5_federation.md#privacy-reqs) below.
-->

Proxyed Federation モデルにはいくつかの利点がある.
Federation Proxy は, インテグレーション用の共通インタフェースを提供することで, RP と IdP の間の技術的なインテグレーションを単純化することができる.
さらに, Proxy が効果的に RP と IdP を相互にブラインドすることで, 自身の Subscriber リストを相互に保護したい組織に対してある種のビジネス上の機密性をもたらす.
Proxy は [Sec. 5.5](sec5_federation.ja.md#privacy-reqs) で後述するプライバシーリスクを低減することもできる.

<!--
See [Sec. 9.5](sec9_privacy.md#blinding) for further information on blinding techniques, their uses, and limitations.
-->

ブラインドテクニックおよびその利用・限界に関する詳細情報は [Sec. 9.5](sec9_privacy.ja.md#blinding) を参照のこと.

<!--
Federations presented through a proxy **SHALL** be represented by the lowest FAL used during the proxied transaction. For example, if a proxy takes in an assertion from the IdP at FAL2 but presents a downstream assertion to the RP at FAL1, the entire transaction is considered FAL1. Likewise if a federation takes in an assertion at FAL1 but presents a downstream assertion to the RP at FAL3, the entire transaction is still considered FAL1. The proxy **SHALL** communicate this aspect to the RP either at runtime or through pre-configuration as part of the trust agreement.
-->

Proxy を介した Federation は, Proxy Transaction 内の最低の FAL とみなすものとする (**SHALL**).
例えば, Proxy が IdP から FAL2 で Assertion を受け取り, それを RP には FAL1 の Assertion に変換して提示する場合, 全体の Transaction は FAL1 となる.
同様に, ある Federation において Assertion が FAL1 で発行され, それが RP には FAL3 の Assertion に変換して提示される場合, 全体の Transaction は依然として FAL1 となる.
Proxy は, こういった側面を RP に伝えなければならない (**SHALL**). その伝達は実行時ないしは Trust Agreement の一部をなす事前設定を通じて行われる.

## Registration

<!--
Within federation protocols, protocol-specific information such as cryptographic keys, system identifiers, service endpoint URLs, and required access rights need to be established between the IdPs and RPs, allowing them to communicate securely with each other. Furthermore, subscriber-facing information such as system display names and home pages can be established to facilitate trust in and usability of the system. All of this information is used to digitally and programmatically establish trust between the IdP and RP within the scope of the federation protocol.
-->

Federation Protocol においては, Protocol 特有の情報が IdP と RP の間で確立され, 相互にセキュア通信が可能となる必要がある.
これらの情報としては, Cryptographic Key, システムの識別子, サービスエンドポイント URL, 必要な Access 権限などが挙げられる.
さらに, Subscriber が目にするシステムの表示名やホームページなどの情報も, システムの信頼とユーザビリティの向上のため確立されうる.
これらの全ての情報は, Federation Protocol のん範囲ないで IdP と RP がデジタルかつプログラム的に信頼を確立するために用いられる.

<!--
These exchanges of information happen in a pairwise fashion for each IdP and RP communicating within a federation transaction, regardless of the trust agreement underlying that transaction. The two phases of this process are commonly known as _discovery_ of the IdP by the RP and _registration_ of the RP at the IdP. These processes can happen in a manual, static fashion, where system administrators or developers enter the information into the target systems, or in an automated, dynamic fashion, where the systems themselves exchange information without direct human involvement.
-->

こういった情報は, Transaction の根底にある Trust Agreement に関係なく, Federation Transaction 内で通信を行う各 IdP-RP が対となる形でやり取りされる.
このプロセスは2つのフェーズからなり, 一般的には RP による IdP の _Discovery_ と IdP における RP の _Registration_ と呼ばれる.
このプロセスは, システム管理者や開発者が情報を大正システムに入力するといった形で手動 (Manual) かつ Static に行われることもあるし, 人間の直接的関与なしにシステム自身が情報を交換する形で自動的かつ Dynamic に行われることもある.

~~~
\clearpage
~~~
{:latex-literal="true"}

### Manual Registration {#manual-registration}

<!--
In the manual registration model, the operators of the IdP and RP manually provision configuration information about parties with which they expect to interoperate, prior to involvement of the subscriber.
-->

Manual Regisrtration モデルでは, Subscriber が関与する前に, IdP と RP のオペレータが手動で相互運用が期待される当事者に関する設定情報を Provisioning する.

[Figure 4. Manual Registration](sec5_federation.ja.md#fig-4){:name="fig-4"}
{:latex-ignore="true"}

![Diagram of the steps involved in a manual registration process between an RP and IdP.]({{site.baseurl}}/{{page.collection}}/media/manual.png 'Manual Registration'){:style="width:630px;height:400px;;min-width: 630px;min-height:400px;" latex-src="manual.png" latex-fig="4" latex-place="h"}

<!--
As shown in [Figure 4](sec5_federation.md#fig-4), manual registration involves three steps:
-->

[Figure 4](sec5_federation.ja.md#fig-4) にあるように, Manual Registration は3つのステップからなる.

<!--
1. The RP's system administrator shares the RP's attributes with the IdP's system administrator, who associates those attributes with the RP.

2. The IdP's system administrator shares the IdP's attributes with the RP's system administrator, who associates those attributes with the IdP.

3. The IdP and RP then communicate using a standard federation protocol.
-->

1. RP のシステム管理者が RP の Attribute を IdP のシステム管理者に共有し, IdP のシステム管理者はそれを RP に紐づける.

2. IdP のシステム管理者が IdP の Attributre を RP のシステム管理者に共有し, RP のシステム管理者はそれを IdP に紐づける.

3. IdP と RP は標準化された Federation Protocol を用いて通信する.

<!--
IdPs and RPs **MAY** act as their own authorities on who to federate with as in [Sec. 5.1.1](sec5_federation.md#bilateral) or **MAY** externalize those authority decisions to an external party as in [Sec. 5.1.2](sec5_federation.md#authorities).
-->

IdP と RP は [Sec. 5.1.1](sec5_federation.ja.md#bilateral) にあるように自ら Federation 相手に対する Authority となることもあれば (**MAY**), [Sec. 5.1.2](sec5_federation.ja.md#authorities) にあるように外部の当事者を Authority とすることもある (**MAY**).

<!--
Protocols requiring the transfer of keying information **SHALL** use a secure method during the registration process to exchange keying information needed to operate the federated relationship, including any shared secrets or public keys. Any symmetric keys used in this relationship **SHALL** be unique to a pair of federation participants.
-->

鍵情報の転送を必要とする Protocol では, Regisrtation プロセスにセキュアな手法を利用して Federation のために必要な鍵交換を行わねばならない (**SHALL**). これは Shared Secret の交換でも Public Key の交換でも同様である.
ここで用いられる Symmetric Key は Federation 参加者のペアごとにユニークでなければならない (**SHALL**).

<!--
Federation relationships **SHALL** establish parameters regarding expected and acceptable IALs and AALs in connection with the federated relationship.
-->

Federation 関係確立においては, 期待され許容可能な IAL, AAL に関するパラメータを確立しなければならない (**SHALL**).

### Dynamic Registration {#dynamic-registration}

<!--
In the dynamic registration model of federation, it is possible for relationships between members of the federation to be negotiated at the time of a transaction. This process allows IdPs and RPs to be connected together without manually establishing a connection between them using manual registration (See [Sec. 5.2.1](sec5_federation.md#manual-registration)). IdPs that support dynamic registration **SHALL** make their configuration information (such as dynamic registration endpoints) available in such a way as to minimize system administrator involvement.
-->

Federation の Dynamic Registration モデルでは, Transaction 実行時に Federation メンバー間の関係取り決めが行われることもある.
このプロセスのおかげで, IdP と RP は Manual Registration (See [Sec. 5.2.1](sec5_federation.ja.md#manual-registration)) により手動で関係を構築することなく相互接続することも可能である.
Dynamic Registration をサポートする IdP は自身の設定情報 (Dynamic Registration Endpoint 等) 可能な限りシステム管理者の関与を必要としない形で公開すること (**SHALL**).

[Figure 5. Dynamic Registration](sec5_federation.ja.md#fig-5){:name="fig-5"}
{:latex-ignore="true"}

![Diagram of the steps in a dynamic registration process between an IdP and an RP.]({{site.baseurl}}/{{page.collection}}/media/dynamic.png 'Dynamic Registration'){:style="width:630px;height:338px;;min-width: 630px;min-height:338px;" latex-src="dynamic.png" latex-fig="5" latex-place="h"}

<!--
As shown in [Figure 5](sec5_federation.md#fig-5), dynamic registration involves four steps:
-->

[Figure 5](sec5_federation.ja.md#fig-5) にあるように, Dynamic Registration は4つのステップからなる.

<!--
1. Discover. The RP goes to a well-known location at the IdP to find the IdP's metadata.

2. Validate. The RP and IdP determine each other's validity. This can be accomplished through keying information, metadata, software statements, or other means.

3. Register RP attributes. The RP sends its attributes to the IdP, and the IdP associates those attributes with the RP.

4. Federation Protocol. The IdP and RP then communicate using a standard federation protocol.
-->

1. Discover. RP は IdP メタデータを見つけるため IdP の well-known location にアクセスする.

2. Validate. RP と IdP はお互いの正当性を確認する. これには鍵情報, メタデータ, Software Statement もしくはその他の方法がある.

3. Register RP Attribute. RP は自身の Attribute を IdP に送信し, IdP はそれを RP に紐づける.

4. Federation Protocol. IdP と RP は標準化された Federation Protocol を用いて通信する.

<!--
Protocols requiring the transfer of keying information **SHALL** use a secure method during the registration process to establish such keying information needed to operate the federated relationship, including any shared secrets or public keys. Any symmetric keys used in this relationship **SHALL** be unique to a pair of federation participants.
-->

鍵情報の転送を必要とする Protocol では, Regisrtation プロセスにセキュアな手法を利用して Federation のために必要な鍵情報の確立を行わねばならない (**SHALL**). これは Shared Secret の交換でも Public Key の交換でも同様である.
ここで用いられる Symmetric Key は Federation 参加者のペアごとにユニークでなければならない (**SHALL**).

<!--
IdPs **SHOULD** issue pairwise pseudonymous subject identifiers to dynamically registered RPs, as discussed in [Sec. 6.2.5](sec6_assertions.md#ppi).
-->

IdP は, [Sec. 6.2.5](sec6_assertions.ja.md#ppi) にあるように, Dynamic Registration により登録された RP に対しては Pairwise Pseudonymous Subject Identifier を発行すべきである (**SHOULD**).

<!--
Where possible, dynamic registration **SHOULD** be augmented by *software statements* anchored in their trust agreement. Software statements are lists of attributes describing the RP software, cryptographically signed by an authority (either the IdP itself, a federation authority as in [Sec. 5.1.2](sec5_federation.md#authorities), or another trusted party). Software statements allow federated parties to cryptographically verify some attributes of an RP being dynamically registered without necessarily having all of the identifying information for that RP ahead of time. This cryptographically verifiable statement allows the connection to be established or elevated between the federating parties without relying solely on self-asserted attributes. (See [[RFC7591]](references.md#ref-RFC7591) Sec. 2.3 for more information on one protocol's implementation of software statements.)
-->

可能な限り, Dynamic Registration は Trust Agreement を基とする *Software Statement* により増強されるべきである (**SHOULD**).
Software Statement とは RP ソフトウェアについて記述する Attribute のリストであり, Authority (IdP 自身, [Sec. 5.1.2](sec5_federation.ja.md#authorities) で述べた Federation Authority ないしはその他の信頼できる当事者) により暗号論的に署名される.
Software Statement により, Federation の当事者は暗号論的に Dynamic Registration を行う RP の Attribute を検証でき,  事前に全ての当該 RP の識別情報を入手しておく必要はなくなる.
この暗号論的に検証可能な Statement により, Federation 当事者間の関係確立および構築において, 自己主張による Attribute にのみ依存せざるを得ない状況から脱することができる.
ある Protocol における Software Statement の実装に関しては (See [[RFC7591]](references.ja.md#ref-RFC7591) Sec. 2.3 を参照のこと.

## Authentication and Attribute Disclosure

<!--
Once the IdP and RP have entered into a trust agreement and have completed registration, the federation protocol can be used to pass subscriber attributes from the IdP to the RP. The decision of whether an authentication can occur or attributes may be passed **SHALL** be determined by the authorized party stipulated by the trust agreement, through use of an allowlist, a blocklist, or a runtime decision.
-->

IdP と RP が Trust Agreement を結び Registration を完了させると, Subscriber Attribute を IdP から RP に伝達するために Federation Protocol が利用可能となる.
Authentication を要求するか Attribute を伝達可能とするかは, Allowlist や Blocklist, 実行時決定などにより, Trust Agreement に規定された Authorized Party によって決定されるものとする (**SHALL**).

<!--
A subscriber's attributes **SHALL** be transmitted between IdP and RP only for identity federation transactions or support functions such as identification of compromised subscriber accounts as discussed in [Sec. 5.5](sec5_federation.md#privacy-reqs). A subscriber's attributes are not to be transmitted for any other purposes, even when parties are allowlisted.
-->

Subscriber Attribute は, Identity Federation Transaction や [Sec. 5.5](sec5_federation.ja.md#privacy-reqs) に後述する Subscriber Account 危殆化検知機能のサポートの目的でのみ, IdP と RP の間を伝達されるものとする (**SHALL**).
Allowlist に当事者が記載されているからといって, その他の目的で Subscriber Attribute を伝達してはならない.

<!--
A subscriber's attributes **SHALL NOT** be used by the RP for purposes other than those stipulated in the trust agreement.
-->

RP は Trust Agreement に規定される目的のほかには Subscriber Attribute を利用してはならない (**SHALL NOT**).

<!--
The subscriber **SHALL** be informed of the transmission of attributes to an RP. In the case where the authorized party is the organization, the organization **SHALL** make available to the subscriber the list of approved RPs and the associated sets of attributes sent to those RPs. In the case where the authorized party is the subscriber, the subscriber **SHALL** be prompted prior to release of attributes using a runtime decision at the IdP as described in [Sec. 5.3.3](sec5_federation.md#idp-runtime-decision).
-->

Subscriber は, RP への Attribute 送信について通知されるものとする (**SHALL**).
Authorized Party が組織の場合, 当該組織は Subscriber に許可された RP のリストと各 RP に送信される Attribute のセットを開示するべきである (**SHALL**).
Authorized Party が Subscriber 自身の場合, Subscriber は [Sec. 5.3.3](sec5_federation.ja.md#idp-runtime-decision) の通り IdP における実行時決定において, Attribute 開示前にそれを知らされるべきである (**SHALL**).

<!--
The IdP **SHALL** provide effective mechanisms for redress of subscriber complaints or problems (e.g., subscriber identifies an inaccurate attribute value). See [Sec. 10](sec10_usability.md#usability) on usability considerations for redress.
-->

IdP は Subscriber の苦情や問題 (Subscriber が誤った Attribute Value に気づいた, など) の是正のための効果的なメカニズムを提供すべきである (**SHALL**).
是正のためのユーザビリティ上の検討事項については [Sec. 10](sec10_usability.ja.md#usability) を参照のこと.

### IdP Allowlists of RPs {#idp-allowlist}

<!--
In a static trust agreement, IdPs **MAY** establish allowlists of RPs authorized to receive authentication and attributes from the IdP without a runtime decision from the subscriber. When placing an RP on its allowlist, the IdP **SHALL** ensure that the RP abides by all applicable provisions and requirements in the SP 800-63 guidelines. The IdP **SHALL** determine which identity attributes are passed to the allowlisted RP upon authentication. IdPs **SHALL** make allowlists available to subscribers as described in [Sec. 9.2](sec9_privacy.md#notice).
-->

Static Trust Agreement において, IdP は RP の Allowhist をもうけ, そこに含まれる RP については当該 IdP から Subscriber による実行時決定無しに Authentication および Attribute を受け取ることを認可されたものとすることができる (**MAY**).
RP を Allowlist に追加するには, IdP は RP が SP 800-63 ガイドライン群に規定される適切な規定及び要件に従うことを保証しなければならない (**SHALL**).
IdP は Authentication 時にどの Identity Attribute が Allowlist 内の RP に開示されるかを決定せねばならない (**SHALL**).
IdP は [Sec. 9.2](sec9_privacy.ja.md#notice) に後述の通り Allowlist を Subscriber に開示せねばならない (**SHALL**).

<!--
IdP allowlists **SHALL** uniquely identify RPs through the means of domain names, cryptographic keys, or other identifiers applicable to the federation protocol in use. Any entities that share an identifier **SHALL** be considered equivalent for the purposes of the allowlist. For example, a wildcard domain identifier of "*.example.com" would match the domains "www.example.com", "service.example.com", and "unknown.example.com" equally. All three of these sites would be treated as the same RP for disclosure decisions using the allowlist. Allowlists **SHOULD** be as specific as possible to avoid unintentional impersonation of an RP.
-->

IdP の Allowlist は, ドメイン名や Cryptographic Key, 利用している Federation Protocol が提供するその他の識別子などを用いて, 一意に RP を識別せねばならない (**SHALL**).
ある識別子が示す全ての主体は, Allowlist の目的のもとで同等とみなされるべきである (**SHALL**).
例えば "*.example.com" といったワイルドカードドメインは "www.example.com", "service.example.com" および "unknown.example.com" に等しくマッチする.
これら3つのサイトは Allowlist を用いた開示決定において全て同じ RP として扱われる.
Allowlist は予期せぬ RP のなりすましを防止するためできる限り RP を特定できるようにすべきである (**SHOULD**).


### IdP Blocklists of RPs

<!--
IdPs **MAY** establish blocklists of RPs not authorized to receive authentication assertions or attributes from the IdP, even if requested to do so by the subscriber. If an RP is on an IdP's blocklist, the IdP **SHALL NOT** produce an assertion targeting the RP in question under any circumstances.
-->

IdP は RP の Blocklist をもうけ, そこに含まれる RP については当該 IdP から Authentication Assertion や Attribute を受け取ることができないようにしても良い (**MAY**).
この場合, Subscriber が当該 RP を利用するようリクエストしたとしても拒否される.
RP が IdP の Blocklist に追加された場合, IdP はいかなる状況下でもその RP を対象とした Assertion を生成してはならない (**SHALL NOT**).

<!--
IdP blocklists **SHALL** uniquely identify RPs through the means of domain names, cryptographic keys, or other identifiers applicable to the federation protocol in use. Any entities that share an identifier **SHALL** be considered equivalent for the purposes of the blocklist. For example, a wildcard domain identifier of "*.example.com" would match the domains "www.example.com", "service.example.com", and "unknown.example.com" equally. All three of these sites would be treated as the same RP for decisions using the blocklist.
-->

IdP の Blocklist は, ドメイン名や Cryptographic Key, 利用している Federation Protocol が提供するその他の識別子などを用いて, 一意に RP を識別せねばならない (**SHALL**).
ある識別子が示す全ての主体は, Blocklist の目的のもとで同等とみなされるべきである (**SHALL**).
例えば "*.example.com" といったワイルドカードドメインは "www.example.com", "service.example.com" および "unknown.example.com" に等しくマッチする.
これら3つのサイトは Blocklist を用いた決定において全て同じ RP として扱われる.

### IdP Runtime Decisions {#idp-runtime-decision}

<!--
Every RP that is in a trust agreement with an IdP but not on an allowlist or a blocklist with that IdP **SHALL** be governed by a default policy in which runtime authorization decisions will be made by an authorized party identified by the trust agreement. In most circumstances, and for practical purposes, the authorized party is the subscriber; however, it is possible for an administrator or other party to be prompted on behalf of the subscriber. Note that in a dynamic trust agreement, only a runtime decision can be used to authorize the release of attributes.
-->

Trust Agreement 内の RP のうち IdP の Allowlist にも Blocklist にも記載のない RP は, デフォルトのポリシーに従い Trust Agreement により定められる Authorized Party による実行時の Authorization 決定に従うものとする (**SHALL**).
ほとんどの場合, 実用上, Authorized Party は Subscriber 自身である.
しかしながら管理者やその他の当事者が Subscriber に代わって許可を求められることもある.
Dynamic Trust Agreement においては, Attribute 開示の認可には実行時決定以外利用できないことに注意.

<!--
In this mode of operation, the authorized party is prompted by the IdP during the federation transaction for their consent to provide an authentication assertion and release specific attributes to the RP on behalf of the subscriber. The IdP **SHALL** provide the authorized party with explicit notice and prompt them for positive confirmation before any attributes about the subscriber are transmitted to the RP. At a minimum, the notice **SHOULD** be provided by the party in the position to provide the most effective notice and obtain confirmation, consistent with [Sec. 9.2](sec9_privacy.md#notice). The IdP **SHALL** disclose which attributes will be released to the RP if the transaction is approved. If the federation protocol in use allows for optional attribute disclosure at runtime, the authorized party **SHALL** be given the option to decide whether to transmit specific attributes to the RP without terminating the federation transaction entirely.
-->

実行時決定モードでは, Authorized Party は IdP から Authentication Assertion と特定の Attribute を Subscriber に代わって RP に開示する旨の同意を Federation Transaction 中に求められる.
IdP は, Subscriber に関する Attribute が RP に送信する前に, Authorized Party に明示的な通知を行い同意を求める必要がある (**SHALL**).
最低限, 通知は最も効果的に通知および同意取得を行える当事者から提供されるべきである (**SHOULD**).
これについては [Sec. 9.2](sec9_privacy.ja.md#notice) に後述する.
IdP は Transaction が許可された場合にどの Attribute が送信されるかを開示しなければならない (**SHALL**).
利用する Federation Protocol により実行時にオプショナルな Attribute の開示が可能な場合, Authorized Party には Federation Transaction 自体を終了させることなく特定の Attribute を送信するか否か決定できるオプションが与えられねばならない (**SHALL**).

<!--
To mitigate the risk of unauthorized exposure of sensitive information (e.g., shoulder surfing), the IdP **SHALL**, by default, mask sensitive information displayed to the authorized party. If the authorized party is the subscriber, the IdP **SHALL** provide mechanisms for the subscriber to temporarily unmask such information in order for the subscriber to view full values before transmission. For more details on masking, see [Sec. 10](sec10_usability.md#usability) on usability considerations.
-->

センシティブな情報の無認可での開示リスク (ショルダーサーフィン等) を低減するため, IdP はデフォルトでは Authorized Party に開示されるセンシティブ情報をマスクすべきである (**SHALL**).
Authorized Party が Subscriber 自身の場合, IdP は Subscriber が伝送前にその値を確認できるよう, 当該情報を一時的に閲覧可能とする仕組みを提供すべきである (**SHALL**).
マスキングに関しては, ユーザビリティの検討事項について [Sec. 10](sec10_usability.ja.md#usability) を参照のこと.

<!--
An IdP **MAY** employ mechanisms to remember and re-transmit the exact attribute bundle to the same RP, remembering the authorized party's decision. This mechanism is associated with the subscriber account as managed by the IdP. If such a mechanism is provided, the IdP **SHALL** allow the authorized party to revoke such remembered access at a future time.
-->

IdP は, Authorized Party の決定を記憶し, 同じ RP に対して同じ Attribute の組み合わせを再送できるようにしてもよい (**MAY**).
このメカニズムは IdP に管理される Subscriber Account に関連付けられる.
このようなメカニズムを提供する場合, IdP は Authorized Party が将来記憶された Access を無効化できるようにすること (**SHALL**).

### RP Allowlists of IdPs

<!--
RPs **MAY** establish allowlists of IdPs from which the RP will accept authentication and attributes without a runtime decision from the subscriber. When placing an IdP in its allowlist, the RP **SHALL** ensure that the IdP abides by the provisions and requirements in these guidelines.
-->

RP は IdP の Allowlist をもうけて, そこに含まれる IdP からは Subscriber の実行時決定無しに Authentication や Attribute を受け入れてもよい (**MAY**).
IdP を Allowlist に追加する場合, RP は IdP が本ガイドラインの規定及び要件に従うことを保証しなければならない (**SHALL**).

<!--
RP allowlists **SHALL** uniquely identify IdPs through the means of domain names, cryptographic keys, or other identifiers applicable to the federation protocol in use.
-->

RP の Allowlist は, ドメイン名や Cryptographic Key, 利用している Federation Protocol が提供するその他の識別子などを用いて, 一意に IdP を識別せねばならない (**SHALL**).

### RP Blocklists of IdPs

<!--
RPs **MAY** also establish blocklists of IdPs that the RP will not accept authentication or attributes from, even when requested by the subscriber. A blocklisted IdP can be otherwise in a valid trust agreement with the RP, for example if both are under the same federation authority.
-->

RP は IdP の Blocklist をもうけて, そこに含まれる IdP からは Subscriber の要求があったとしても Authentication や Attribute を受け入れないようにしてもよい (**MAY**).
Blocklist に追加された IdP は, Blocklist がない限り RP との間に有効な Trust Agreement を持つ可能性もある. 例えば両者が同じ Federation Authority のもとにある場合などが考えられる.

<!--
RP blocklists **SHALL** uniquely identify IdPs through the means of domain names, cryptographic keys, or other identifiers applicable to the federation protocol in use.
-->

RP の Blocklist は, ドメイン名や Cryptographic Key, 利用している Federation Protocol が提供するその他の識別子などを用いて, 一意に IdP を識別せねばならない (**SHALL**).

### RP Runtime Decisions {#rp-runtime-decision}

<!--
Every IdP that is in a trust agreement with an RP but not on an allowlist or a blocklist with that RP **SHALL** be governed by a default policy in which runtime authorization decisions will be made by the authorized party indicated in the trust agreement. In this mode, the authorized party is prompted by the RP to select or enter which IdP to contact for authentication on behalf of the subscriber. This process can be facilitated through use of a discovery mechanism allowing the subscriber to enter a human-facing identifier such as an email address. This process allows the RP to programmatically select the appropriate IdP for that identifier.
-->

RP と Trust Agreement を結びながら, Allowlist や Blocklist に記載されていないすべての IdP は, デフォルトのポリシーに従い, Trust Agreement により定められる Authorized Party による実行時の Authorization 決定に従うものとする (**SHALL**).
このモードでは, Authorized Party は RP から Subscriber に代わって Authentication に利用する IdP を選択/入力するよう促される.
このプロセスは, Subscriber が Email アドレスなどの人が目にする識別子を入力できるような Discovery メカニズムを採用することにより, より使いやすくすることができる.
このプロセスにより, RP は識別子が示す適切な IdP をプログラム的に IdP を選択できるようになる.

<!--
The RP **MAY** employ mechanisms to remember the authorized party's decision to use a given IdP. Since this mechanism is employed prior to authentication at the RP, the manner in which the RP provides this mechanism (e.g., a browser cookie outside the authenticated session) is separate from the RP subscriber account described in [Sec. 5.4](sec5_federation.md#rp-account). If such a mechanism is provided, the RP **SHALL** allow the authorized party to revoke such remembered options at a future time.
-->

RP は利用する IdP に関する Authorized Party の決定を記憶する仕組みを採用してもよい (**MAY**).
このメカニズムは RP における Authentication の前に用いられるため, RP がこのメカニズムを提供する方法 (認証済 Session 外のブラウザクッキー等) は [Sec. 5.4](sec5_federation.ja.md#rp-account) に述べる RP Subscriber Account とは紐づかない.
このようなメカニズムを提供する場合, RP は Authorized Party が将来記憶されたオプションを無効化できるようにすること (**SHALL**).

## RP Subscriber Accounts {#rp-account}

<!--
It is common for an RP to keep a record representing a subscriber local to the RP itself, known as the *RP subscriber account*. The RP subscriber account can contain things like access rights at the RP as well as a cache of identity attributes for the subscriber. An active RP subscriber account is bound to one or more federated identifiers from the RP's trusted IdPs. Successful authentication of one of these federated identifiers through a federation protocol allows the subscriber to access the information and functionality protected by the RP subscriber account.
-->

RP が Subscriber レコードを RP 自身のローカルに保存するのは一般的なことで, これは *RP Subscriber Account* と呼ばれる.
RP Subscriber Account には, RP において Subscriber が持つ Access 権限や, Subscriber の Identity Attribute のキャッシュなどが含まれる.
アクティブな RP Subscriber Account は, RP が信頼する IdP の1つ以上の Federated Identifier と紐づいている.
Federation Protocol を通じてそれらの Federated Identifier のいずれかの Authentication が成功すると, Subscriber は RP Subscriber Account により保護されている情報や機能への Access を得る.

<!--
An RP subscriber account is _provisioned_ when the RP has associated a set of attributes about the subscriber with a data record representing the subscriber account at the RP. The RP subscriber account **SHALL** be bound to at least one federated identifier, and a given federated identifier is bound to only one RP subscriber account at a given RP. The provisioning can happen prior to authentication or as a result of the federated authentication process, depending on the deployment patterns as discussed in [Sec. 5.4.1](sec5_federation.md#provisioning). Prior to being provisioned, the RP subscriber account does not exist and has no associated data record at the RP.
-->

RP Subscriber Account は RP が Subscriber に関する Attribute のセットを RP における Subscriber Account を示すレコードに関連づけることで _Provisioning_ される.
RP Subscriber Account は最低限一つの Federated Identifier に紐づけられるものとし (**SHALL**), 当該 Federated Identifier は当該 RP において唯一の RP Subscriber Accout に紐づけられるものとする.
Provisioning は Authentication の前に実行されることもあれば, Federated Authentication プロセスの結果として実行されることもある.
どのような Provisioning が行われるかは, [Sec. 5.4.1](sec5_federation.ja.md#provisioning) に述べるように実装パターンに依存する.
Provisioning が実行されるまでは, RP Subscriber Account は存在せず RP のいかなるデータレコードとも関連づけられていない.

<!--
An RP subscriber account is _terminated_ when the RP removes all access to the account at the RP. Termination **SHALL** include unbinding any federated identifiers and bound authenticators as well as removing attributes and information associated with the account except what is required for auditing and security purposes. An RP **MAY** terminate an RP subscriber account independently from the IdP for a variety of reasons, regardless of the current validity of the subscriber account from which it is derived.
-->

RP Subscriber Account は RP が RP における当該アカウントの全ての Access を削除した際に _Terminate_ される.
Termination は Federated Identifier や紐づけられた Authennticator の紐付け解除を含み, 監査やセキュリティ目的で必要とされない限り当該 Account に紐づく Attribute および情報の削除も含むものとする (**SHALL**).
RP は, さまざまな理由により, IdP とは独立して RP Subscriber Account を Terminate することができる (**MAY**).
これは Subscriber Account がその源泉において現在も正当であったとしても関係がない.

<!--
An authenticated session **SHALL** be created by the RP only when the RP has processed and verified a valid assertion from the IdP that is the issuer of the federated identifier associated with the RP subscriber account. If the assertion also requires presentation of a bound authenticator at FAL3, the bound authenticator **SHALL** also be presented and processed before the RP subscriber account is associated with an authenticated session, as discussed in [Sec. 6.1.2](sec6_assertions.md#boundauth). Before the federated assertion is processed and after termination of the authenticated session, the RP subscriber account is unauthenticated though it could still be provisioned.
-->

認証済 Session は, RP が RP Subscriber Account に関連づけられた Federated Identifier の発行元である IdP からの有効な Assertion を処理・検証して初めて生成されるものとする (**SHALL**).
Assertion が Bound Authenticator の提示を要求するものの場合, [Sec. 6.1.2](sec6_assertions.ja.md#boundauth) にあるように, RP Subscriber Account が認証済 Session に関連づけられる前に当該 Bound Authenticator が提示・処理されねばならない (**SHALL**).
Federated Assertion が処理される前, かつ認証済 Session が終了した後は, RP Subscriber Account は Unauthenticated となる.
ただし RP Subscriber Account は以前として Provisioning されうる.

### Provisioning Models {#provisioning}

<!--
The lifecycle of the provisioning process for an RP subscriber account varies depending on factors including the trust agreement discussed in [Sec. 5.1](sec5_federation.md#trust-agreement) and the deployment pattern of the IdP and RP. However, in all cases, the RP subscriber account **SHALL** be provisioned at the RP prior to the establishment of an authenticated session at the RP in one of the following ways:
-->

RP Subscriber Account の Provisioning プロセスのライフサイクルは [Sec. 5.1](sec5_federation.ja.md#trust-agreement) の Trust Agreement や IdP & RP の実装パターンなどの要因により多様である.
しかしながら, いかなるケースにおいても, RP Subscriber Account は認証済 Session の確立前に以下のいずれかの方法により RP に Provisioning されていなければならない (**SHALL**).

<!--
Just-In-Time Provisioning
: An RP subscriber account is created automatically the first time the RP receives an assertion with an unknown federated identifier from an IdP. Any identity attributes learned during the federation process, either within the assertion or through an identity API as discussed in [Sec. 6.3](sec6_assertions.md#s-identity-api), **MAY** be associated with the RP subscriber account. Accounts provisioned in this way are bound to the federated identifier in the assertion used to provision them.
This is the most common form of provisioning in federation systems, as it requires the least coordination between the RP and IdP. However, in such systems, the RP **SHALL** be responsible for managing any cached attributes it might have.
-->

Just-In-Time Provisioning
: RP Subscriber Account は RP が IdP から未知の Federated Identifier を含む Assertion を初めて受け取った際に自動的に生成される. Assertion に含まるか [Sec. 6.3](sec6_assertions.ja.md#s-identity-api) で述べる Identity API から取得するかのいずれかの方法で Federation Process 中に得られた Identity Attribute は, すべて RP Subscriber に関連づけることができる (**MAY**).
この方法で Provisioning された Account は, Provisioning に用いられた Assertion に含まれる Federated Identifier に紐づけられる.
これは Federation システムにおいて最も一般的な形であり, RP と IdP の間の協調動作が最も少なくて済む.
しかしながらこのようなシステムでは RP は自身が持ちうる全ての Attribute のキャッシュ管理に責任を持たねばならない (**SHALL**).

[Figure 6. Just-In-Time Provisioning](sec5_federation.md#fig-6){:name="fig-6"}
{:latex-ignore="true"}

![Diagram of the stages of a just-in-time provisioning of an RP subscriber account based on a subscriber account.]({{site.baseurl}}/{{page.collection}}/media/JIT-provisioning.png 'Just-In-Time Provisioning'){:latex-src="JIT-provisioning.pdf" latex-fig="6" latex-place="h"}

~~~
\clearpage
~~~
{:latex-literal="true"}

<!--
Pre-provisioning
: An RP subscriber account is created by the IdP pushing the attributes to the RP or the RP pulling attributes from the IdP. Pre-provisioning of accounts generally occurs in bulk through a provisioning API as discussed in [Sec. 5.4.3](sec5_federation.md#provisioning-api), as the provisioning occurs prior to the represented subscribers authenticating through a federated transaction. Pre-provisioned accounts **SHALL** be bound to a federated identifier at the time of provisioning. Any time a particular federated identifier is seen by the RP, the associated account can be logged in as a result.
This form of provisioning requires infrastructure and planning on the part of the IdP and RP, but these processes can be facilitated by automated protocols. The RP also collects attributes about users who have not interacted with the RP system yet, which can cause privacy issues. Additionally, the IdP and RP must keep the set of provisioned accounts synchronized over time as discussed in [Sec. 5.4.2](sec5_federation.md#attribute-sync).
-->

Pre-provisioning
: RP Subscriber Account は IdP が Attribute を RP に Push するか RP が IdP から Attribute を Pull ことで生成される.
Account の Pre-provisioning は, [Sec. 5.4.3](sec5_federation.ja.md#provisioning-api) にあるように一般的に Provisioning API を介して Bulk で行われる.
これは Provisioning が Federated Transaction を通じて Subscriber を Authenticate する前に発生するからである.
Pre-provisioning された Account は Provisioning 時に Federated Identifier と紐づけられるものとする (**SHALL**).
これにより, RP が特定の Federated Identifier を受け取ると, その結果として関連づけられた Account がログインできるようになる.
この形態の Provisioning は, IdP と RP にインフラストラクチャと計画を必要とするが, このプロセス自体は自動化されたプロトコルにより実現可能である.
RP は RP システムとインタラクションを行ったことのないユーザーの Attribute を収集するため, Privacy 上の問題も発生しうる.
さらに [Sec. 5.4.2](sec5_federation.ja.md#attribute-sync) で述べるように, IdP と RP は Provisioning された Account の集合を長期にわたって同期しなければならない.

[Figure 7. Pre-Provisioning](sec5_federation.md#fig-7){:name="fig-7"}
{:latex-ignore="true"}

![Diagram of the stages of a pre-provisioned RP subscriber account based on a subscriber account.]({{site.baseurl}}/{{page.collection}}/media/Pre-provisioning.png 'Pre-Provisioning'){:latex-src="Pre-provisioning.pdf" latex-fig="7" latex-place="h"}

~~~
\clearpage
~~~
{:latex-literal="true"}

<!--
Ephemeral
: An RP subscriber account is created when processing the assertion, but then the RP subscriber account is terminated when the authenticated session ends. This process is similar to a just-in-time provisioning, but the RP keeps no long-term record of the account when the session is complete, except what is required for audit and security purposes (such as access logs).
This form of provisioning is useful for RPs that fully externalize access rights to the IdP, allowing the RP to be more simplified with less internal state. However, this pattern is not common because even the simplest RPs tend to have a need to track state within the application or at least keep a record of actions associated with the federated identifier.
-->

Ephemeral
: RP Subscriber Account は Assertion を処理する際に生成されるが, 認証済 Session が終了する際に Terminate される.
このプロセスは Just-in-time Provisioning と似ているが, RP は Session が終了したらそれ以上 Account のレコードを保持しない. ただし監査やセキュリティ目的で必要とされる場合は別である (アクセスログ等).
この形態の Provisioning は IdP に Access 権限を完全に外部依存する RP にとっては使いやすい.
RP は内部的なステート管理を低減させ, よりシンプルになる.
しかしながらこのパターンは一般的ではない.
最もシンプルな RP ですら, アプリケーション内でのステート追跡は必要としがちであり, 少なくとも Federated Identifier に関連したアクションのレコードは保持するからである.

[Figure 8. Ephemeral Provisioning](sec5_federation.md#fig-8){:name="fig-8"}
{:latex-ignore="true"}

![Diagram of the stages of an ephemeral RP subscriber account based on a subscriber account.]({{site.baseurl}}/{{page.collection}}/media/Ephemeral-provisioning.png 'Ephemeral Provisioning'){:latex-src="Ephemeral-provisioning.pdf" latex-fig="8" latex-place="h"}

<!--
Other
: Other RP subscriber account provisioning models are possible but the details of such models are outside the scope of these guidelines. The details of any alternative provisioning model **SHALL** be included in the privacy risk assessments of the IdP and RP.
-->

Other
: その他の RP Subscriber Account Provisioning モデルも可能であるが, その詳細は本ガイドライン群のスコープ外とする.
いかなる代替の Provisioning モデルにおいても, IdP および RP において Privacy Risk Assessment を行うことが必要となる (**SHALL**).

<!--
All organizations **SHALL** document their provisioning model as part of their trust agreement.
-->

全組織は自身の Provisioning モデルを Trust Agreement の一部としてドキュメント化するべきである (**SHALL**).

### Attribute Synchronization {#attribute-sync}

<!--
In a federated process, the IdP and RP each have their own stores of identity attributes associated with the subscriber account. The IdP has a direct view of the subscriber account, but the RP subscriber account is derived from a subset of attributes from the subscriber account that are presented during the federation transaction. Therefore, it is possible for the IdP's and RP's attribute stores to diverge from with each other over time.
-->

Federation プロセスにおいて, IdP と RP は各々 Subscriber Account に関連づけられた Identity Attribute を保持する.
IdP は Subscriber Account を直接閲覧できるのに対し, RP Subscriber Account は Federation Transaction 時に提示された Subscriber Account の Attribute のサブセットから導出される.
したがって時間の経過に伴い IdP と RP がそれぞれ保持する Attribute が乖離する可能性がある.

<!--
From the RP's perspective, the IdP is the authoritative source for any attributes that the IdP asserts as being associated with the subscriber account at the IdP. However, the RP **MAY** additionally collect, and optionally verify, other attributes to associate with the RP subscriber account. Sometimes, these attributes can even override what's asserted by the IdP. For example, if an IdP asserts a full display name for the subscriber, the RP can allow the subscriber to provide an alternative preferred name for use at the RP.
-->

RP から見ると, IdP は IdP が当該 IdP において Subscriber Account と関連づけられていると主張する全ての Attribute の Authoritative Source である.
しかしながら, RP は追加で RP Subscriber Accout に関連づけられるその他の Attribute を収集, および時には検証することもできる (**MAY**).
ときにはこれらの Attribute は IdP が主張したものを上書くことすらありえる.
例えば IdP が Subscriber の完全なる Display Name を主張したとして, RP が Subscriber に RP において代替となる好きな名前を指定できるようにすることなどが考えられる.

<!--
The IdP **SHOULD** signal downstream RPs when the attributes of a subscriber account available to the RP have been updated. This can be accomplished using shared signaling as described in [Sec. 5.7](sec5_federation.md#shared-signals), through a provisioning API as described in [Sec. 5.4.3](sec5_federation.md#provisioning-api), or by providing a signal in the assertion (e.g., a timestamp indicating when relevant attributes were last updated, allowing the RP to determine that its cache is out of date).
-->

IdP は RP に提供した Subscriber Account の Attribute に更新があった場合, RP にシグナルを送るべきである (**SHOULD**).
これは, [Sec. 5.7](sec5_federation.ja.md#shared-signals) の Shared Signaling や [Sec. 5.4.3](sec5_federation.ja.md#provisioning-api) の Provisioning API を利用したり, Assertion にシグナルを含めて提供する (関連する Attribute の最終更新日時を含めたり, RP に自身のキャッシュが期限切れだと判断する手段を提供したり) などの方法で実現可能である.

<!--
The IdP **SHOULD** signal downstream RPs when a subscriber account is terminated, or when the subscriber account's access to an RP is revoked. This can be accomplished using shared signaling as described in [Sec. 5.7](sec5_federation.md#shared-signals) or through a provisioning API as described in [Sec. 5.4.3](sec5_federation.md#provisioning-api). Upon receiving such a signal, the RP **SHALL** terminate the RP subscriber account and remove all personal information associated with the RP subscriber account, except what is required for audit and security purposes.
-->

IdP は Subscriber Account が Terminate されたり Subscriber Account が持つ RP への Access が無効化された場合, RP にシグナルを送るべきである (**SHOULD**).
これは, [Sec. 5.7](sec5_federation.ja.md#shared-signals) の Shared Signaling や [Sec. 5.4.3](sec5_federation.ja.md#provisioning-api) の Provisioning API などの方法で実現可能である.
このシグナルを受け取った場合, RP は RP Subscriber Account を Terminate させ, RP Subscriber Account に関連する全ての personal information を削除せねばならない (**SHALL**).
ただし監査やセキュリティ目的で必要とされる場合を除く.

### Provisioning APIs {#provisioning-api}

<!--
As part of some proactive forms of provisioning, the RP can be given access to subscriber attributes through a general-purpose attribute API known as a _provisioning API_. This type of API allows an IdP to push attributes for a range of subscriber accounts, and sometimes allows an RP to query the attributes of these subscriber accounts directly. Since access to the API is granted outside the context of a federated transaction, access to the provisioning API for a given subscriber does not indicate to the RP that a given subscriber has been authenticated. See [Sec. 6, Assertions](sec6_assertions.md#assertions) for more information on how the federated authentication process is accomplished using assertions.
-->

プロアクティブな Provisioning の一環として, RP は _Provisioning API_ と呼ばれる汎用 Attribute API を介して Subscriber Attribute への Access を与えられることもある.
この種の API により, IdP は一定範囲の Subscriber Account の Attribute を Push できるようになり, ときには RP がこれら Subscriber Account の Attribute に直接クエリできるようにもなる.
この API への Access は Federation Transaction のコンテキスト外で許可されるため, Provisioning API を介して Subscriber  に Access できるからといって Subscriber が Authenticate されたとは言えない.
Federated Authentication プロセスが Assertion を用いてどのように実現されるかは [Sec. 6, Assertions](sec6_assertions.ja.md#assertions) を参照のこと.

<!--
The attributes in the provisioning API available to a given RP **SHALL** be limited to only those necessary for the RP to perform its functions. As part of establishing the trust agreement, the IdP **SHALL** document when an RP is given access to a provisioning API including at least the following:
-->

Provisioning API によって RP に提供される Attribute は, RP がその機能の実現に必要なものに限定されなければならない (**SHALL**).
Trust Agreement 確立の一環として, IdP は RP がいつ Provisioning API への Access を与えらえるかドキュメント化せねばならない (**SHALL**).
これには最低限以下のような項目を含む.

<!--
- the purpose for the access using the provisioning model;
- the set of attributes made available to the RP;
- whether the API functions as a push to the RP, a pull from the RP, or both; and
- the population of subscribers whose attributes are made available to the RP.
-->

- その Provisioning モデルを利用した Access の目的
- RP に開示される Attribute セット
- API が RP への Push を行うのか, RP からの Pull によるのか, 両方なのか
- RP に Attribute が開示される Subscriber の母集団

<!--
The IdP **SHALL** require authentication from the RP for any pull-based access to a provisioning API. The RP **SHALL** require authentication from the IdP for any push-based access to a provisioning API.
-->

IdP は Pull ベースの Provisioning API への Access 全てについて RP に Authentication を要求せねばならない (**SHALL**).
RP は Push ベースの Provisioning API への Access 全てについて IdP に Authentication を要求せねばならない (**SHALL**).

<!--
A provisioning API **SHALL NOT** be made available under a dynamic or implicit trust agreement. The IdP **SHALL NOT** make a provisioning API available to any RP outside of an established trust agreement. The IdP **SHALL** provide access to a provisioning API only as part of a federated identity relationship with an RP to facilitate federated transactions with that RP and related functions such as signaling revocation of the subscriber account. The IdP **SHALL** revoke an RP's access to the provisioning API once access is no longer required by the RP for its functioning purposes or when the trust agreement is terminated.
-->

Dynamic ないし Implicit な Trust Agreement のもとでは Provisioning API は利用してはならない (**SHALL NOT**).
IdP は Trust Agreement を確立していない RP に Provisioning API を提供してはならない (**SHALL NOT**).
IdP は RP との Federated Identity 関係の一環でのみ Provisioning API への Access を提供し, 当該 RP との Federated Transaction や Subscriber Account 無効化の Signaling を含む関連する機能に役立てるものとする (**SHALL**).
IdP は RP がもはやその機能を実現するのに必要としなくなった場合や Trust Agreement が Terminate した場合は, RP の Provisioning API への Access を無効化せねばならない (**SHALL**).

Any provisioning API provided to the RP **SHALL** be under the control and jurisdiction of the IdP. External attribute providers **MAY** be used as information sources by the IdP to provide attributes through this provisioning API, but the IdP is responsible for the content and accuracy of the information provided by the referenced attribute providers.

When a provisioning API is in use, the IdP **SHALL** signal to the RP when a subscriber account has been terminated. When receiving such a signal, the RP **SHALL** terminate the associated RP subscriber account.

### Attribute Collection {#rp-attribute-collection}

The RP **MAY** collect and maintain additional attributes from the subscriber beyond those provided by the IdP. These attributes are governed separately from any federation agreement since they are collected directly by the RP. All attributes associated with an RP subscriber account, regardless of their source, **SHALL** be removed when the RP subscriber account is terminated.

The RP **SHALL** disclose to the subscriber the purpose for collection of any additional attributes. These attributes **SHALL** be used solely for the stated purposes of the RP's functionality and **SHALL NOT** have any secondary use, including communication of said attributes to other parties.

An RP **SHALL** disclose any additional attributes collected, and their use, as part of its System of Records Notice (SORN). The RP **SHALL** provide an effective means of redress for the subscriber to update and remove these additionally-collected attributes from the RP subscriber account. See [Sec. 10](sec10_usability.md#usability) on usability considerations for redress.

### Time-based Removal of RP Subscriber Accounts {#stale-account}

Over time, an RP could accumulate RP subscriber accounts that are no longer accessible from the IdP. This poses a risk to the RP for holding personal information in the RP subscriber accounts, especially when a just-in-time provisioning model is in use and no shared signaling is available from the IdP to signal subscriber account termination as discussed in [Sec. 5.7](sec5_federation.md#shared-signals). In such circumstances, the RP **SHOULD** employ a time-based mechanism to identify RP subscriber accounts for termination that have not been accessed after a period of time, for example, 120 days since last access.

When processing such an inactive account, the RP **SHALL** provide sufficient notice to the subscriber, if possible, about the pending termination of the account and provide the subscriber with an option to re-activate the account prior to its scheduled termination. Upon termination, the RP **SHALL** remove all personal information associated with the RP subscriber account, except what is required for audit and security purposes.

## Privacy Requirements {#privacy-reqs}

The ultimate goal of a subscriber is to interact with and use the RP. Federation involves the transfer of personal attributes from a third party that is not otherwise involved in a transaction &mdash; the IdP. Federation also potentially gives the IdP broad visibility into subscriber activities and status. Accordingly, there are specific privacy requirements associated with federation.

Communication between the RP and the IdP could reveal to the IdP where the subscriber is conducting a transaction. Communication with multiple RPs allows the IdP to build a profile of subscriber transactions that would not have existed without federation. This aggregation could enable new opportunities for subscriber tracking and use of profile information that do not always align with subscribers' privacy interests.

If an IdP discloses information on subscriber activities at an RP to any party, or processes the subscriber's attributes for any purpose other than identity proofing, authentication, or attribute assertions (collectively "identity service"), related fraud mitigation, to comply with law or legal process, or, in the case of a specific user request, to transmit the information, the IdP **SHALL** implement measures to maintain predictability and manageability commensurate with the privacy risk arising from the additional processing. Measures **MAY** include providing clear notice, obtaining subscriber consent, or enabling selective use or disclosure of attributes. When an IdP uses consent measures, the IdP **SHALL NOT** make consent for the additional processing a condition of the identity service.

If the same subscriber account is asserted to multiple RPs, and those RPs communicate with each other, the colluding RPs could track a subscriber's activity across multiple applications and security domains. The IdP **SHOULD** employ technical measures, such as the use of pairwise pseudonymous identifiers described in [Sec. 6.2.5](sec6_assertions.md#ppi) or privacy-enhancing cryptographic protocols, to provide disassociability and discourage subscriber activity tracking and profiling between RPs.

An IdP **MAY** disclose information on subscriber activities to RPs for security purposes, such as communication of suspicious activity or a compromised subscriber account as described in [Sec. 5.7](sec5_federation.md#shared-signals), if stated within the trust agreement. An RP **MAY** disclose information on subscriber activities to IdPs for security purposes, such as communication of suspicious activity or a compromised RP subscriber account, if stated within the trust agreement.

An IdP **SHOULD** signal subscriber account termination to RPs that have been provisioned with federated identifiers bound to that subscriber account using shared signaling as discussed in [Sec. 5.7](sec5_federation.md#shared-signals). RPs that receive such a signal from the IdP **SHALL** terminate the RP subscriber account and remove all personal information associated with the RP subscriber account, except what is required for audit and security purposes.

The following requirements apply specifically to federal agencies:

1. The agency **SHALL** consult with their Senior Agency Official for Privacy (SAOP) to conduct an analysis determining whether the requirements of the Privacy Act are triggered by the agency that is acting as an IdP, by the agency that is acting as an RP, or both (see [Sec. 9.4](sec9_privacy.md#agency-privacy)).

2. The agency **SHALL** publish or identify coverage by a System of Records Notice (SORN) as applicable.

3. The agency **SHALL** consult with their SAOP to conduct an analysis determining whether the requirements of the E-Government Act are triggered by the agency that is acting as an IdP, the agency that is acting as an RP, or both.

4. The agency **SHALL** publish or identify coverage by a Privacy Impact Assessment (PIA) as applicable.

If the RP subscriber account lifecycle process gives the RP access to attributes through a provisioning API as discussed in [Sec. 5.4.3](sec5_federation.md#provisioning-api), additional privacy measures **SHALL** be implemented given the wide nature of information access. Specifically, it is possible for the attributes of a subscriber to be provided to an RP without the subscriber ever interacting with the RP in question. As a consequence, when a provisioning API is used, the IdP **SHALL** minimize the attributes made available to the RP. To prevent the transmission of attributes for users that will never use an RP, the IdP **SHALL** limit the population of subscriber accounts available via the provisioning API to the population of subscribers authorized to use the RP by the trust agreement.

##  Reauthentication and Session Requirements in Federated Environments {#federation-session}

In a federated environment, the RP manages its sessions separately from any sessions at the IdP. The assertion is related to both sessions but its validity period is ultimately independent of them. In order for the IdP to create an assertion for the subscriber, the subscriber needs to establish an authenticated session with the IdP. To create an authenticated session at the RP, the RP needs to process a valid assertion from the IdP.

Due to the distributed nature of a federated system, the subscriber's sessions with the IdP and with the RP terminate independently of each other. The RP **SHALL NOT** assume that the subscriber has an active session at the IdP past the issuance time of the assertion. The IdP **SHALL NOT** assume that termination of the subscriber's session at the IdP will propagate to any sessions that subscriber would have at downstream RPs. The RP and IdP **MAY** communicate session termination requests to other parties in the federation network, if supported by the federation protocol.

At the time of a federated login request, the subscriber **MAY** have a pre-existing session at the IdP which **MAY** be used to generate an assertion to the RP. The IdP **SHALL** communicate any information it has regarding the time of the subscriber's latest authentication event at the IdP, and the RP **MAY** use this information in making authorization and access decisions. Depending on the capabilities of the federation protocol in use, the IdP **SHOULD** allow the RP to request that the subscriber repeat authentication at the IdP as part of a federation request.

An RP requiring authentication through a federation protocol **SHALL** specify the maximum acceptable authentication age to the IdP, either through the federation protocol (if possible) or through the parameters of the trust agreement. The authentication age represents the time since the last authentication event in the subscriber's session at the IdP, and the IdP **SHALL** reauthenticate the subscriber if they have not been authenticated within that time period. The IdP **SHALL** communicate the authentication event time to the RP to allow the RP to decide if the assertion is sufficient for authentication at the RP and to determine the time for the next reauthentication event.

If an RP is granted access to an identity API along with the assertion, the lifetime of the access to the identity API is independent from the lifetime of the assertion itself. Since access to the identity API is often combined with access to additional APIs, it is common for this access to be valid long after the assertion has expired and possibly after the session with the RP has ended, allowing the RP to access APIs on the subscriber's behalf while the subscriber is no longer present. As a consequence, the RP's ability to successfully fetch additional attributes through an identity API **SHALL NOT** be used to establish a session at the RP. Likewise, inability to access an identity API **SHOULD NOT** be used to end the session at the RP.

See [[SP800-63B]](../_sp800-63b/sec7_session.md#sec7){:latex-href="#ref-SP800-63B"}, Sec. 7 for more information about session management requirements for both IdPs and RPs.

## Shared Signaling {#shared-signals}

In some environments, it is useful for the IdP and RP to send information to each other outside of the federation transaction. These signals can communicate important changes in state between parties that would not be otherwise known. The use of any shared signaling **SHALL** be documented in the trust agreement between the IdP and RP. Signaling from the IdP to the RP **SHALL** require a static trust agreement. Signaling from the RP to the IdP **MAY** be used in a static or dynamic trust agreement.

Any use of shared signaling **SHALL** be documented and made available to the authorized party stipulated by the trust agreement. This documentation **SHALL** include the events under which a signal is sent, the information included in such a signal (including any attribute information), and any additional parameters sent with the signal. The use of shared signaling **SHALL** be subject to privacy review under the trust agreement.

The IdP **MAY** send a signal regarding the following changes to the subscriber account:

- The account has been terminated.
- The account is suspected of being compromised.
- Attributes of the account, including identifiers other than the federated identifier (such as email address or certificate CN), have changed.
- The possible range of IAL, AAL, or FAL for the account has changed.

The RP **MAY** send a signal regarding the following changes to the RP subscriber account:

- The account has been terminated.
- The account is suspected of being compromised.
- An RP-managed bound authenticator is added.
- An RP-managed bound authenticator is removed.

Additional signals from both the IdP and RP **MAY** be allowed subject to privacy and security review as part of the trust agreement.
