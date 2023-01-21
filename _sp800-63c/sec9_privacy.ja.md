---
layout: default.ja
title: Privacy
navOrder: 9
navTitle: Privacy
permalink: /sp800-63c/privacy/
anchor: privacy
section: 9
---

# Privacy Considerations {#privacy}

*This section is informative.*

## Minimizing Tracking and Profiling

<!--
Federation offers numerous benefits to RPs and subscribers, but requires subscribers to have trust in the federation participants. [Sec. 5](sec5_federation.md#federation) and [Sec. 6.2.5](sec6_assertions.md#ppi) cover a number of technical requirements, the objective of which is to minimize privacy risks arising from increased capabilities to track and profile subscribers. For example, a subscriber using the same IdP to authenticate to multiple RPs allows the IdP to build a profile of subscriber transactions that would not have existed absent federation. The availability of such data makes it vulnerable to uses that may not be anticipated or desired by the subscriber and may inhibit subscriber adoption of federated services.
-->

Federation は RP と Subscriber に多くの恩恵をもたらすが, Subscriber による Federation 参加者への信頼を必要とする.
[Sec. 5](sec5_federation.md#federation) および [Sec. 6.2.5](sec6_assertions.md#ppi) は, Subscriber の追跡およびプロファイリング可能性の向上により増大するプライバシーリスクの最小化を目的とした, 多数の技術要件をカバーしている.
例えば同じ IdP を複数の RP に対する Authentication のために用いる Subscriber は, IdP によって Federation がなければ起こり得なかったであろう Subscriber Transaction のプロファイリングを行われる可能性がある.
このようなデータが利用可能になると, Subscriber が予期または希望しない利用のされかたが行われる恐れにつながり, Subscriber が Federated サービスの採用を躊躇うことにもつながりうる.

<!--
[Sec. 5.5](sec5_federation.md#privacy-reqs) requires IdPs to use measures to maintain the objectives of predictability (enabling reliable assumptions by individuals, owners, and operators about PII and its processing by an information system) and manageability (providing the capability for granular administration of PII, including alteration, deletion, and selective disclosure) commensurate with privacy risks that can arise from the processing of attributes for purposes other than identity proofing, authentication, authorization, or attribute assertions, related fraud mitigation, or to comply with law or legal process [[NISTIR8062](references.md#ref-NISTIR8062)].
-->

[Sec. 5.5](sec5_federation.md#privacy-reqs) では, IdP に Predictability (PII および情報システムによる PII の処理に関して, 個人, 所有者およびオペレーターによる確実な予測可能性) および Manageability (変更, 削除および選択的開示を含む PII の細やかな管理機能の提供) を維持するための手段を要求している.
この Predictability および Manageability は, Identity Proofing, Authentication, Authorization のほか, Attribute Assesion, 関連する不正防止ないしは法律や法的プロセスへの準拠以外の目的での Attribute の処理により生じるプライバシーリスクに相応するものである必要がある [[NISTIR8062](references.md#ref-NISTIR8062)].

<!--
IdPs may have various business purposes for processing attributes, including providing non-identity services to subscribers. However, processing attributes for different purposes from the original collection purpose can create privacy risks when individuals are not expecting or comfortable with the additional processing. IdPs can determine appropriate measures commensurate with the privacy risk arising from the additional processing. For example, absent applicable law, regulation or policy, it may not be necessary to get consent when processing attributes to provide non-identity services requested by subscribers, although notices may help subscribers maintain reliable assumptions about the processing (predictability). Other processing of attributes may carry different privacy risks that call for obtaining consent or allowing subscribers more control over the use or disclosure of specific attributes (manageability). Subscriber consent needs to be meaningful; therefore, when IdPs do use consent measures, they cannot make acceptance by the subscriber of additional uses a condition of providing the identity service.
-->

IdP は Attribute を処理する際に多様なビジネス上の目的を持ちうる.
これには Subscriber への Identity Service 以外のサービス提供を含む.
しかしながら, Attribute をその収集の本来の目的とは異なる目的で処理することは, 個人が追加処理に対して期待ないし満足していない場合にはプライバシーリスクにつながりうる.
例えば, 適用される法律, 規制ないしポリシーが存在しなければ, Identity Service 以外のサービスを提供する際に Subscriber の同意は不要かもしれないが, Subscriber が確実な予測を行えるようにする (Predictability) には, その処理に関する通知が役に立つこともある.
また別の Attribute の処理により異なるプライバシーリスクが生じる可能性もあり, Subscriber による同意や Subscriber による特定の Attribute の利用ないし開示に関するより詳細なコントロール (Manageability) が求めれることもある.
Subscriber の同意は意味のあるのでなければならず, IdP が同意による手段をとる場合は, Subscriber による追加利用に関する同意を Identity Servicee の提供条件にしてはならない.

<!--
Consult the SAOP if there are questions about whether the proposed processing falls outside the scope of the permitted processing or the appropriate privacy risk mitigation measures.
-->

検討中の処理が許可された処理や適切なプライバシーリスク軽減措置の範囲を超えるかどうかに疑念がある場合は SOAP に相談すること.

<!--
[Sec. 5.5](sec5_federation.md#privacy-reqs) also encourages the use of technical measures to provide disassociability (enabling the processing of PII or events without association to individuals or devices beyond the operational requirements of the system) and prevent subscriber activity tracking and profiling [[NISTIR8062]](references.md#ref-NISTIR8062). Technical measures, such as those outlined in [Sec. 5.1.3](sec5_federation.md#proxied) for proxied federation and [Sec. 6.2.5](sec6_assertions.md#ppi) for pairwise pseudonymous identifiers, can increase the effectiveness of policies by making it more difficult to track or profile subscribers beyond operational requirements.
-->

[Sec. 5.5](sec5_federation.md#privacy-reqs) では, Disassociability (システム運用上の要件を超えて個人またはデバイスに関連付けることなく, PII またはイベントの処理を可能にすること) を提供する技術的手段の採用も推奨しており, Subscriber のアクティビティがトラキングされたりプロファイリングされることを防止している [[NISTIR8062]](references.md#ref-NISTIR8062).
[Sec. 6.2.5](sec6_assertions.md#ppi) で述べた Proxied Federation や [Sec. 6.2.5](sec6_assertions.md#ppi) で述べた Pairwise Pseudonymous Identifier  [Sec. 5.1.3](sec5_federation.md#proxied) のような技術的手段は, Subscriber を運用上の要件を超えて Subscriber をトラッキングないしプロファイリングすることをより困難にし, ポリシー適用の効率化に寄与しうる.

## Notice and Consent {#notice}

To build subscriber trust in federation, subscribers need to be able to develop reliable assumptions about how their information is being processed. For instance, it can be helpful for subscribers to understand what information will be transmitted, which attributes for the transaction are required versus optional, and to have the ability to decide whether to transmit optional attributes to the RP. Accordingly, [Sec. 5.1](sec5_federation.md#trust-agreement) requires that positive confirmation be obtained from the authorized party before any attributes about the subscriber are transmitted to any RP. In determining when a set of RPs should share a common pairwise pseudonymous identifier as in [Sec. 6.2.5.2](sec6_assertions.md#ppi-gen), the IdP considers the subscriber's understanding of such a grouping of RPs and the role of notice in assisting such understanding. An effective notice will take into account user experience design standards and research, as well as an assessment of privacy risks that may arise from the information processing. There are various factors to be considered, including the reliability of the assumptions subscribers may have about the processing and the role of different entities involved in federation. However, a link to a complex, legalistic privacy policy or general terms and conditions that a substantial number of subscribers do not read or understand is never an effective notice.

[Sec. 5.1](sec5_federation.md#trust-agreement) does not specify which party should provide the notice. In some cases, a party in a federation may not have a direct connection to the subscriber in order to provide notice and obtain consent. Although multiple parties may elect to provide notice, it is permissible for parties to determine in advance, either contractually or through trust framework policies, which party will provide the notice and obtain confirmation, as long as the determination is being based upon factors that center on enabling the subscriber to pay attention to the notice and make an informed choice.

If an IdP is using an allowlist of RPs as described in [Sec. 5.3](sec5_federation.md#idp-runtime-decisions), any RPs on that list are not presented to the subscriber during an authentication transaction. Since the IdP does not provide notice to the subscriber at runtime, the IdP makes its list of allowlisted RPs available to the subscriber so that the subscriber can see which RPs on the allowlist have access to which of the subscriber's attributes in an authentication transaction. Since IdPs can not share a subscriber's authentication information or attributes with an allowlisted RP outside of an authentication transaction involving the subscriber (see [Sec. 5.5](sec5_federation.md#privacy-reqs)), the existence of an RP on a list of IdPs does not indicate that the subscriber's information will be shared. However, if the subscriber logs into any of the allowlisted RPs using the IdP, the attributes indicated will be shared as part of the authentication transaction.

If a subscriber's runtime decisions at the IdP were stored in the subscriber account by the IdP to facilitate future transactions, the IdP also needs to allow the subscriber to view and revoke any RPs that were previously approved during a runtime decision. This list includes information on which attributes were approved. Similarly, if a subscriber's runtime decisions at the RP are stored in some fashion, the RP also needs to allow the subscriber to view and revoke any IdPs that were approved during a runtime decision.

## Data Minimization {#minimization}

Federation enables the data exposed to an RP to be minimized, which can yield privacy protections for subscribers. Although an IdP may collect additional attributes beyond what the RP requires for its use case, only those attributes that were explicitly requested by the RP are to be transmitted by the IdP. In some instances, an RP does not require a full value of an attribute. For example, an RP may need to know whether the subscriber is over 13 years old, but has no need for the full date of birth. To minimize collection of potentially sensitive PII, the RP may request a derived attribute value (e.g., Question: Is the subscriber over 13 years old? Response: Y/N or Pass/Fail). This minimizes the RP's collection of potentially sensitive and unnecessary PII. Accordingly, [Sec. 7.3](sec7_presentation.md#protecting-information) requires the RP to, where feasible, request derived attribute values rather than full attribute values. To support this RP requirement IdPs are, in turn, required to support a derived attribute value.

## Agency-Specific Privacy Compliance  {#agency-privacy}

[Section 5.5](sec5_federation.md#privacy-reqs) identifies agency requirements to consult their SAOP to determine privacy compliance requirements. It is critical to involve the agency's SAOP in the earliest stages of digital authentication system development to assess and mitigate privacy risks and advise the agency on compliance obligations such as whether the federation triggers the Privacy Act of 1974 or the E-Government Act of 2002 requirement to conduct a PIA. For example, if the agency is serving as an IdP in a federation, it is likely that the Privacy Act requirements will be triggered and require coverage by either a new or existing Privacy Act system of records since credentials would be maintained at the IdP on behalf of any RP it federates with. If, however, the agency is an RP and using a third-party IdP, digital authentication may not trigger the requirements of the Privacy Act, depending on what data passed from the RP is maintained by the agency at the RP (in such instances the agency may have a broader programmatic SORN that covers such data).

The SAOP can similarly assist the agency in determining whether a PIA is required. These considerations should not be read as a requirement to develop a Privacy Act SORN or PIA for use of a federated credential alone. In many cases it will make the most sense to draft a PIA and SORN that encompasses the entire digital authentication process or includes the digital authentication process as part of a larger programmatic PIA that discusses the program or benefit the agency is establishing online access.

Due to the many components of digital authentication, it is important for the SAOP to have an awareness and understanding of each individual component. For example, other privacy artifacts may be applicable to an agency offering or using federated IdP or RP services, such as Data Use Agreements, Computer Matching Agreements, etc. The SAOP can assist the agency in determining what additional requirements apply. Moreover, a thorough understanding of the individual components of digital authentication will enable the SAOP to thoroughly assess and mitigate privacy risks either through compliance processes or by other means.


## Blinding in Proxied Federation {#blinding}

While some proxy structures — typically those that exist primarily to simplify integration — may not offer additional subscriber privacy protection, others offer varying levels of privacy to the subscriber through a range of blinding technologies. Privacy policies may dictate appropriate use of the subscriber attributes and authentication transaction data (e.g., identities of the ultimate IdP and RP) by the IdP, RP, and the federation proxy.

Technical means such as blinding can increase effectiveness of these policies by making the data more difficult to obtain. A proxy-based system has three parties, and the proxy can be used to hide information from one or more of the parties, including itself. In a double-blind proxy, the IdP and RP do not know each other's identities, and their relationship is only with the proxy. In a triple-blind proxy, the proxy additionally does not have insight into the data being passed through it. As the level of blinding increases, the technical and operational implementation complexity may increase. Since proxies need to map transactions to the appropriate parties on either side as well as manage the keys for all parties in the transaction, fully triple-blind proxies are very difficult to implement in practice.

Even with the use of blinding technologies, a blinded party may still infer protected subscriber information through released attribute data or metadata, such as by analysis of timestamps, attribute bundle sizes, or attribute signer information. The IdP could consider additional privacy-enhancing approaches to reduce the risk of revealing identifying information of the entities participating in the federation.

The following table illustrates a spectrum of blinding implementations used in proxied federation. This table is intended to be illustrative, and is neither comprehensive nor technology-specific.

[Table 4 Federation Proxies](sec9_privacy.md#table-4){:name="table-4"}
{:latex-ignore="true"}

|Proxy Type|RP knows IdP|IdP knows RP|Proxy can track subscriptions between RP and IdP|Proxy can see attributes of Subscriber|
|---|:---:|:---:|:---:|:---:|
|Non-Blinding Proxy with Attributes|Yes|Yes|Yes|Yes|
|Non-Blinding Proxy|Yes|Yes|Yes|N/A|
|Double Blind Proxy with Attributes|No|No|Yes|Yes|
|Double Blind Proxy|No|No|Yes|N/A|
|Triple Blind Proxy with or without Attributes|No|No|No|No|
{:latex-table="4" latex-caption="Proxy Characteristics" latex-columns="p@0.20\textwidth,p@0.17\textwidth,p@0.17\textwidth,p@0.25\textwidth,p@0.20\textwidth"}
