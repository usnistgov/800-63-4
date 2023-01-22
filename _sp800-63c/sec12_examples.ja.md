---
layout: default.ja
title: Examples
navOrder: 12
navTitle: Examples
permalink: /sp800-63c/examples/
anchor: examples
section: 12
---

# Examples {#examples}

*This section is informative.*

<!--
Three types of assertion technologies are discussed below: SAML assertions, Kerberos tickets, and OpenID Connect tokens. This list is not inclusive of all possible assertion technologies, but does represent those commonly used in federated identity systems.
-->

以下では, SAML Assertion, Kerberos Ticket, OpenID Connect Token という3種類の Assertion 技術について述べる.
このリストは考えうる全ての Assertion 技術を含むものではないが, Federated Identity System において一般的に使用されているものを示している.

## Security Assertion Markup Language (SAML)

<!--
SAML is an XML-based framework for creating and exchanging authentication and attribute information between trusted entities over the internet. As of this writing, the latest specification for [SAML](references.md#ref-SAML) is SAML v2.0, issued 15 March 2005.
-->

SAML はインターネットを介して信頼された主体間で Authentication および Attribute 情報を生成・交換するための, XML ベースのフレームワークである.
本稿執筆段階での [SAML](references.md#ref-SAML) の最新仕様は2005年3月15日に発行された SAML 2.0 である.

<!--
The building blocks of SAML include:
-->

SAML の構成要素は以下の通りである.

<!--
- The Assertions XML schema, which defines the structure of the assertion.
- The SAML Protocols, which are used to request assertions and artifacts (the assertion references used in the indirect model described in [Sec. 7.1](sec7_presentation.md#back-channel)).
- The Bindings, which define the underlying communication protocols (such as HTTP or SOAP), and can be used to transport the SAML assertions.
-->

- Assertion XML Schema: Assertion の構造を定義する.
- SAML Protocol: Assertion および Artifact ([Sec. 7.1](sec7_presentation.md#back-channel) で述べた間接モデルで用いる Assertion Reference) を要求するために用いる.
- Binding: その下で用いるコミュニケーションプロトコル (HTTP や SOAP など) を定義し, SAML Assertion の転送に用いる.

<!--
The three components above define a SAML profile that corresponds to a particular use case such as "Web Browser SSO".
-->

上記3つの構成要素により SAML プロファイルが定義され, これらのプロファイルが "Web Browser SSO" などの特定のユースケースに対応する.

<!--
SAML Assertions are encoded in an XML schema and can carry up to three types of statements:
-->

SAML Assertion は XML Schema でエンコードされ, 最大3つの Statement を伝搬可能である.

<!--
-   *Authentication statements* include information about the assertion issuer, the authenticated subscriber, validity period, and other authentication information. For example, an Authentication Assertion would state the subscriber "John" was authenticated using a password at 10:32pm on 06-06-2004.
-->

- *Authentication Statement*: Asseriton Issuer, Authenticated Subscriber, 有効期間およびその他の Authentication に関する情報を含む. 例えば, ある Authentication Assertion は Subscriber "John" が 2024-06-06 10:32pm に Password を用いて Authenticate されたことを表現できる.

<!--
-   *Attribute statements* contain specific additional characteristics related to the subscriber. For example, subject "John" is associated with attribute "Role" with value "Manager".
-->

- *Attribute Statement*: Subscriber に関する追加の特徴を含む. 例えば, Subject "John" に "Manager" という "Role" Attribute が関連づけられているなど.

<!--
-   *Authorization statements* identify the resources the subscriber has permission to access. These resources may include specific devices, files, and information on specific web servers. For example, subject "John" for action "Read" on "Webserver1002" given evidence "Role".
-->

- *Authorization Statement*: Subscriber が Access する権限を持つリソースを識別する. こういったリソースには特定のデバイス, ファイル, 特定の Web サーバー上の情報などが含まれうる. 例えば, Subject "John" が "Role" を証拠として "Webserver1002" 上の "Read" というアクションに対して権限を持つなど.

<!--
Authorization statements are beyond the scope of this document and will not be discussed.
-->

Authorization Statement は本ドキュメントのスコープ外であり, ここでは議論しない.

## Kerberos Tickets  {#kerberos}

<!--
The Kerberos Network Authentication Service [[RFC4120]](references.md#ref-RFC4120) was designed to provide strong authentication for client/server applications using symmetric-key cryptography on a local, shared network. Extensions to Kerberos can support the use of public key cryptography for selected steps of the protocol. Kerberos also supports confidentiality and integrity protection of session data between the subscriber and the RP. Even though Kerberos uses assertions, it was designed for use on shared networks and, therefore, is not truly a federation protocol.
-->

Kerberos Network Authentication Service [[RFC4120]](references.md#ref-RFC4120) は, ローカルの共有 Network 上で, Symmetric Key Cryptography を用いて, Client/Server 形アプリケーションに対して強固な Authentication を提供するために設計されている.
拡張機能によって, Kerberos はプロトコル上の指定されたステップで Public Key Cryptography をサポートすることもできる.
Kerberos は Subscriber と RP の間の Session データに関して Confidentiality 保護および Integrity 保護をサポートすることもできる.
Kerberos は Assertion を利用するが, これは共有 Network 上での利用を想定して設計されたものであり, 真の Federation Protocol ではない.

<!--
Kerberos supports authentication of a subscriber over a network using one or more IdPs. The subscriber implicitly authenticates to the IdP by demonstrating the ability to decrypt a random session key encrypted for the subscriber by the IdP. (Some Kerberos variants also require the subscriber to explicitly authenticate to the IdP, but this is not universal.) In addition to the encrypted session key, the IdP also generates another encrypted object called a Kerberos ticket. The ticket contains the same session key, the identity of the subscriber to whom the session key was issued, and an expiration time after which the session key is no longer valid. The ticket is confidentiality and integrity protected by a pre-established key that is shared between the IdP and the RP during an explicit setup phase.
-->

Kerberos は1つ以上の IdP を用いた Network 経由の Subscriber Authentication をサポートする.
Subscriber は, IdP が Subscriber に対して暗号化したランダムな Session Key を復号できることを示すことで, 暗黙的に IdP に Authenticate される.
(一部の Kerberos 派生系は Subscriber が IdP に対して明示的に Authenticate することを要求するが, これは一般的ではない)
暗号化された Session Key に加え, IdP はその他の暗号化されたオブジェクトも生成する. これは Kerberos Ticket と呼ばれる.
この Ticket は同じ Session Key, Session Key を発行された Subscriber の Identity, Session Key の有効期限を含む.
この Ticket は, 明示的なセットアップフェーズ中に IdP-RP 間で共有される事前確立鍵により Confidentiality 保護および Integrity 保護を施される.

<!--
To authenticate using the session key, the subscriber sends the ticket to the RP along with encrypted data that proves that the subscriber possesses the session key embedded within the Kerberos ticket. Session keys are either used to generate new tickets or to encrypt and authenticate communications between the subscriber and the RP.
-->

Session Key を利用して Authenticate するには, Subscriber は Ticket を RP に送り, それに Subscriber が Kerberos Ticket 内に含まれた Session Key を保持することを証明する暗号化されたデータを添える.
Session Key は新しい Ticket の生成に用いられることもあれば, Subscriber と RP の間の通信を暗号化および Authenticate するために用いられることもある.

<!--
To begin the process, the subscriber sends an authentication request to the Authentication Server (AS). The AS encrypts a session key for the subscriber using the subscriber's long-term credential. The long-term credential may either be a secret key shared between the AS and the subscriber, or in the PKINIT variant of Kerberos, a public key certificate. Most variants of Kerberos based on a shared secret key between the subscriber and IdP derive this key from a user-generated password. As such, they are vulnerable to offline dictionary attacks by passive eavesdroppers, unless Flexible Authentication Secure Tunneling (FAST) \[[RFC6113](references.md#ref-RFC6113)\] or some other tunneling and armoring mechanism is used.
-->

このプロセスを開始するにあたり, Subscriber は Authentication リクエストを Authentication Server (AS) に送る.
AS は Subscriber の長時間有効な Credential を用いて Subscriber の Session Key を暗号化する.
この長期間有効な Credential は AS と Subscriber 間で共有された Secret Key であることもあれば, Kerberos の PKINIT 相当のものに含まれる Public Key Certificate であることもある.
Subscriber と IdP の間の Shared Secret Key に基づいている大抵の Kerberos 派生系は, ユーザーが生成した Password からこの Key を導出する.
そのため, Flexible Authentication Secure Tunneling (FAST) \[[RFC6113](references.md#ref-RFC6113)\] やその他のトンネリングおよび防御メカニズムが採用されていない限り, パッシブな盗聴者によるオフライン辞書攻撃に対して脆弱である.

<!--
In addition to delivering the session key to the subscriber, the AS also issues a ticket using a key it shares with the Ticket Granting Server (TGS). This ticket is referred to as a Ticket Granting Ticket (TGT), since the verifier uses the session key in the TGT to issue tickets rather than to explicitly authenticate the verifier. The TGS uses the session key in the TGT to encrypt a new session key for the subscriber and uses a key it shares with the RP to generate a ticket corresponding to the new session key. The subscriber decrypts the session key and uses the ticket and the new session key together to authenticate to the RP.
-->

Session Key の Subscriber への配送に加え, AS は Ticket Granting Server (TGS) と共有する鍵を使って Ticket を発行する.
この Ticket は Ticket Granting Ticket (TGT) と呼ばれる. これは, Verifier が TGT 内の Session Key を用いて Authenticate するかわりに Ticket を発行するからである.
TGS は TGT 内の Session Key を用いて新たな Session Key を Subscriber に対して暗号化し, RP と共有する鍵を用いて新たな Session Key に対応する Ticket を生成する.
Subscriber は Session Key を復号し, Ticket と新たな Session Key を使って RP に対して Authenticate を行う.

<!--
When Kerberos authentication is based on passwords, the protocol is known to be vulnerable to offline dictionary attacks by eavesdroppers who capture the initial user-to-KDC exchange. Longer password length and complexity provide some mitigation to this vulnerability, although sufficiently long passwords tend to be cumbersome for users. However, when Kerberos password-based authentication is used in a FAST (or similar) tunnel, a successful attacker-in-the-middle attack is additionally required in order to perform the dictionary attack.
-->

Kerberos Authentication が Password に基づいている場合, このプロトコルは最初のユーザーと KDC の交換を盗聴する盗聴者によるオフライン辞書 Attack に脆弱であることが知られている.
この脆弱性は長く複雑な Password により軽減されるが, 十分に長い Password はユーザーにとって扱いにくい傾向がある.
ただし, Password ベースの Kerberos Authentication が FAST (または類似の) トンネル内で用いられている場合, 自書攻撃を実行するには中間者攻撃を成功させることも必要になる.

## OpenID Connect

<!--
OpenID Connect \[[OIDC](references.md#ref-OIDC)\] is an internet-scale federated identity and authentication protocol built on top of the OAuth 2.0 authorization framework and the JSON Object Signing and Encryption (JOSE) cryptographic system.
-->

OpenID Connect は, OAuth 2.0 Authorization Framework および JSON Object Signing and Encryption (JOSE) Cryptographic System に基づいた, インターネットスケールの Federated Identity & Authentication Protocol である.

<!--
OpenID Connect builds on top of the OAuth 2.0 authorization protocol to enable the subscriber to authorize the RP to access the subscriber's identity and authentication information. The RP in both OpenID Connect and OAuth 2.0 is known as the client.
-->

OpenID Connect は OAuth 2.0 Authorization Protocol の上に構築され, Subscriber が RP に対して Subscriber Identity および Authentication 情報に Access することを Authorize 可能にする.
OpenID Connect および OAuth 2.0 における RP は Client とも呼ばれる.

<!--
In a successful OpenID Connect transaction, the IdP issues an ID Token, which is a signed assertion in JSON Web Token (JWT) format. The client parses the ID Token to learn about the subscriber and primary authentication event at the IdP. This token contains at minimum the following information about the subscriber and authentication event:
-->

OpenID Connect Transaction 成功時, IdP は ID Token を発行する. これは JSON Web Token (JWT) 形式の署名付き Assertion である.
Client は ID Token をパースし, Subscriber および IdP におけるプライマリな Authentication Event についての情報を得る.
このトークンは最低限以下のような Subscriber および Authentication Event に関する情報を含む.

<!--
 - `iss` - An HTTPS URL identifying the IdP that issued the assertion.
 - `sub` - An IdP-specific subject identifier representing the subscriber.
 - `aud` - An IdP-specific audience identifier, equal to the OAuth 2.0 client identifier of the client at the IdP.
 - `exp` - The timestamp at which the ID Token expires and after which **SHALL NOT** be accepted the client.
 - `iat` - The timestamp at which the ID Token was issued and before which **SHALL NOT** be accepted by the client.
-->

- `iss` - Assertion を発行した IdP を識別する HTTPS URL.
- `sub` - Subscriber を示す, IdP 固有の Subject Identifier.
- `aud` - IdP 固有の Audience Identifier. 当該 Client の IdP における OAuth 2.0 Client Identifier と等しい.
- `exp` - ID Token が期限切れになるタイムスタンプ. Client はこれ以降にこの ID Token を受け入れてはならない (**SHALL NOT**).
- `iat` - ID Token が発行されたタイムスタンプ. Client はこれ以前にこの ID Token を受け入れてはならない (**SHALL NOT**).

<!--
In addition to the ID Token, the IdP also issues the client an OAuth 2.0 access token which can be used to access the UserInfo Endpoint at the IdP. This endpoint returns a JSON object representing a set of attributes about the subscriber, including but not limited to their name, email address, physical address, phone number, and other profile information. While the information inside the ID Token is reflective of the authentication event, the information in the UserInfo Endpoint is generally more stable and could be more general purpose. Access to different attributes from the UserInfo Endpoint is governed by the use of a specially-defined set of OAuth scopes, `openid`, `profile`, `email`, `phone`, and `address`. An additional scope, `offline_access`, is used to govern the issuance of refresh tokens, which allow the RP to access the UserInfo Endpoint when the subscriber is not present. Access to the UserInfo Endpoint is structured as an API and may be available when the subscriber is not present. Therefore, access to the UserInfo Endpoint is not sufficient for proving a subscriber's presence and establishing an authenticated session at the RP.
-->

ID Token に加え, IdP は Client に OAuth 2.0 Access Token を発行することもできる. これは IdP の UserInfo Endpoint への Access に利用できる.
この Endpoint は Subscriber に関する Attribute セットを表現する JSON Object を返す.
返される Attribute には, 氏名, Email Address, 住所, 電話番号およびその他のプロフィール情報が含まれるが, それに限るものでもない.
ID Token に含まれる情報は Authentication Event を反映している一方, UserInfo Endpoint から返される情報は一般的にはより永続的でより一般的な目的で利用される.
UserInfo Endpoint から返される Attribute への Access は, Attribute 毎に特別に定義された `openid`, `profile`, `email`, `phone` および `address` といった OAuth Scope のセットにより決定される.
`offline_access` という追加の Scope もあり, これは Refresh Token の発行を制御するために用いられる.
RP は Subscriber が介在しない時でも Refresh Token を使って UserInfo Endpoint への Access を行うことができる.
UserInfo Endpoint への API として実現されており, Subscriber が介在しない場合でも利用できる可能性がある.
従って UserInfo Endpoint への Access を持つからといって, Subscriber の存在証明や RP における認証済 Session の確立には不十分である.