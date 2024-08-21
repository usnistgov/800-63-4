---
layout: default
title: Threats and Security Considerations
navOrder: 7
navTitle: Security
permalink: /sp800-63b/security/
anchor: sec8
section: 6
---

# Threats and Security Considerations {#sec8}

*This section is informative.*

## Authenticator Threats

An attacker who can gain control of an authenticator will often be able to masquerade as the authenticator's owner. Threats to authenticators can be categorized based on attacks on the types of authentication factors that comprise the authenticator:

* "Something you know" may be disclosed to an attacker. For example, the attacker may guess a password. If the authenticator is a shared secret, the attacker could access the CSP or verifier and obtain the secret value or perform a dictionary attack on a hash of that value. An attacker may observe the entry of a PIN or passcode, find a written record or journal entry of a PIN or passcode, or install malicious software (e.g., a keyboard logger) to capture the secret. Additionally, an attacker may determine the secret through offline attacks on a password database maintained by the verifier.

* "Something you have" may be lost, damaged, stolen from the owner, or cloned by an attacker. For example, an attacker who gains access to the owner's computer may copy a software authenticator. A hardware authenticator may be stolen, tampered with, or duplicated. Out-of-band secrets may be intercepted by an attacker and used to authenticate their own session. A subscriber may be socially engineered to provide access to secrets without intentional collusion.

* "Something you are" may be replicated. For example, an attacker may obtain a copy of the subscriber's fingerprint and construct a replica.

Subscribers sometimes collude with attackers, and virtually nothing can be done from an authentication perspective to prevent these attacks. With this caveat in mind, threats to the authenticators used for digital authentication are listed in [Table 2](6_security.md#table-2) along with some examples.

[Table 2. Authenticator threats](6_security.md#table-2){:name="table-2"}
{:latex-ignore="true"}

| Authenticator Threat/Attack  | Description  | Examples |
|------------------------------------|------------------|--------------|
| **Theft** | An attacker steals a physical authenticator. | A hardware cryptographic authenticator is stolen. |
| | | An OTP authenticator is stolen. |
| | | A look-up secret authenticator is stolen. |
| | | A cell phone is stolen. |
| **Duplication** | The subscriber's authenticator has been copied with or without their knowledge. | Passwords written on paper are disclosed.
| | | Passwords stored in an electronic file are copied. |
| | | A vulnerability in an insufficiently secure password manager is exploited. |
| | | A software PKI authenticator (i.e., private key) is copied. |
| | | A Look-up secret authenticator is copied. |
| | | A counterfeit biometric authenticator is manufactured. |
| | | Exportable cryptographic keys are obtained from a device or cloud-based sync fabric. |
| **Eavesdropping** | The attacker observes the authenticator secret or authenticator output as the subscriber is authenticating. | Passwords are obtained by watching keyboard entries. |
| | | Passwords or authenticator outputs are intercepted by keystroke logging software. |
| | | A PIN is captured from a PIN pad device. |
| | | A hashed password is obtained and used by an attacker for another authentication (i.e., *pass-the-hash attack*). |
| | The attacker intercepts an out-of-band secret by compromising the communication channel. | An out-of-band secret is transmitted via unencrypted Wi-Fi and received by the attacker. |
| **Offline Cracking** | The authenticator is exposed using analytical methods outside of the authentication mechanism. | A software PKI authenticator is subjected to a dictionary attack to identify the correct password to decrypt the private key. |
| **Side-Channel Attack** | The authenticator's secret is exposed using the physical characteristics of the authenticator. | A key is extracted by differential power analysis on a hardware cryptographic authenticator. |
| | | A cryptographic authenticator secret is extracted by analysis of the authenticator's response time over several attempts. |
| **Phishing or Pharming** | The authenticator output is captured by fooling the claimant into thinking that the attacker is a verifier or RP. | A claimant reveals a password to a website impersonating the verifier.
| | | A password is revealed by a bank subscriber in response to an email inquiry from a phisher pretending to represent the bank. |
| | | A password is revealed by the claimant at a bogus verifier website reached through DNS spoofing.
| **Social Engineering** | The attacker establishes a level of trust with a subscriber to convince them to reveal their authenticator secret or authenticator output. | A password is revealed by the subscriber to an officemate asking for the password on behalf of the subscriber's boss. |
| | | A password is revealed by a subscriber in a telephone inquiry from an attacker masquerading as a system administrator. |
| | | An attacker who has convinced the mobile operator to redirect the victim's mobile phone to them receives an out-of-band secret sent via SMS. |
| | | A subscriber erroneously approves a push-based authentication request coming from a repeated "fatigue" attack. |
| **Online Guessing** | The attacker connects to the verifier online and attempts to guess a valid authenticator output in the context of that verifier. | Online dictionary attacks are used to guess passwords. |
| | | Online guessing is used to guess authenticator outputs for an OTP authenticator that is registered to a legitimate subscriber. |
| **Endpoint Compromise** | Malicious code on the endpoint proxies allow remote access to a connected authenticator without the subscriber's consent. | A cryptographic authenticator connected to the endpoint is used to authenticate remote attackers. |
| | Malicious code on the endpoint causes authentication to other than the intended verifier. | Authentication is performed on behalf of an attacker rather than the subscriber.
| | | A malicious app on the endpoint reads an out-of-band secret sent via SMS, and the attacker uses the secret to authenticate.
| | Malicious code on the endpoint compromises a multi-factor software cryptographic authenticator. | Malicious code proxies authenticate or export authenticator keys from the endpoint.
| **Unauthorized Binding** | An attacker causes an authenticator under their control to be bound to a subscriber account. | An attacker intercepts an authenticator or provisioning key en route to the subscriber. |
| **Latent Keys** | A decommissioned device retains authentication keys | A device (e.g., laptop computer) is sold without recognition that device-based authentication keys are present and could be used by a new owner. |
| **Proliferation of Keys** | Transferring device-based authentication keys between devices increases the attack surface | A subscriber copies authentication keys to many devices, possibly some that are not under their direct control, and loses track of where the keys are stored |
| **Key Transfer Security** | Authentication keys are transferred between devices through an insufficiently secure cloud service | Access to a cloud service that stores authentication keys requires only single-factor authentication |
| | | Keys are made available to others through a URL sent via email |
| **Insider Threats** | An insider with access to the CSP (e.g., customer support representative) colludes with an attacker to give access to subscriber accounts. |
{:latex-table="2" latex-caption="Authenticator Threats" latex-longtable="true"  latex-columns="p@0.20\textwidth,p@0.35\textwidth,p@0.35\textwidth"}

## Threat Mitigation Strategies
[Table 3](6_security.md#table-3) summarizes related mechanisms that assist in mitigating the threats described in [Table 2](6_security.md#table-2).

[Table 3. Mitigating authenticator threats](6_security.md#table-3){:name="table-3"}
{:latex-ignore="true"}

| Authenticator Threat/Attack | Threat Mitigation Mechanisms | Normative Reference Sections |
|---------------------------------|----------------------------------|-------|
| **Theft** | Use multi-factor authenticators that must be activated through a password or biometric.| [2.2.1](2_aal.md#aal2types), [2.3.1](2_aal.md#aal3types) |
| | Use a combination of authenticators that includes a password or biometric. | [2.2.1](2_aal.md#aal2types), [2.3.1](2_aal.md#aal3types) |
| **Duplication** | Use authenticators from which it is difficult to extract and duplicate long-term authentication secrets. | [2.2.2](2_aal.md#aal2req), [2.3.2](2_aal.md#aal3req), [3.1.6.1](3_authenticators.md#sfca) |
| | Enforce AAL2 requirements for access to sync fabrics that contain exported authentication keys, and only allow them to be imported into trusted devices. | [3.1.7.1](3_authenticators.md#mfca)
| **Eavesdropping** | Ensure the endpoint's security before use, especially with respect to freedom from malware (e.g., such as key loggers). | [2.2.2](2_aal.md#aal2req) |
| | Avoid using unauthenticated and unencrypted communication channels to send out-of-band authenticator secrets. | [3.1.3.1](3_authenticators.md#ooba) |
| | Authenticate over authenticated protected channels (e.g., observe the lock icon in the browser window). | [2.1.2](2_aal.md#aal1req), [2.2.2](2_aal.md#aal2req), [2.3.2](2_aal.md#aal3req) |
| | Use authentication protocols that are resistant to replay attacks (e.g., *pass-the-hash*). | [3.2.7](3_authenticators.md#replay) |
| | Use authentication endpoints that employ trusted input and display capabilities. | [3.1.6.1](3_authenticators.md#sfca), [3.1.7.1](3_authenticators.md#mfca) |
| **Offline Cracking** | Use an authenticator with a high entropy authenticator secret. | [3.1.2.1](3_authenticators.md#lusa), [3.1.4.1](3_authenticators.md#sfotpa), [3.1.5.1](3_authenticators.md#mfotpa), [3.1.6.1](3_authenticators.md#sfca), [3.1.7.1](3_authenticators.md#mfca) |
| | Store centrally verified passwords in a salted, hashed form, including a keyed hash. | [3.1.1.1.2](3_authenticators.md#passwordver) |
| **Side-Channel Attack** | Use authenticator algorithms that maintain constant power consumption and timing regardless of secret values. | [2.3.2](2_aal.md#aal3req)
| **Phishing or Pharming** | Use authenticators that provide phishing resistance. | [3.2.5](3_authenticators.md#verifimpers) |
| **Social Engineering** | Avoid using authenticators that present a social engineering risk to third parties (e.g., customer service agents). | [4.1.2.1](4_events.md#bindexisting), [4.2](4_events.md#recovery) |
| **Online Guessing** | Use authenticators that generate high entropy output. | [3.1.2.1](3_authenticators.md#lusa), [3.1.6.1](3_authenticators.md#sfca), [3.1.7.1](3_authenticators.md#mfca) |
| | Use an authenticator that locks after repeated failed activation attempts. | [3.2.2](3_authenticators.md#throttle) |
| **Endpoint Compromise** | Use hardware authenticators that require physical action by the claimant. | [3.2.8](3_authenticators.md#intent) |
| | Maintain software-based keys in restricted-access storage. | [3.1.3.1](3_authenticators.md#ooba), [3.1.6.1](3_authenticators.md#sfca), [3.1.7.1](3_authenticators.md#mfca), [3.2.13](3_authenticators.md#export) |
| **Unauthorized Binding** | Provision authenticators and associated keys using authenticated protected channels or in person. | [4.1](4_events.md#binding) |
| **Latent Keys** | Ensure the secure disposal of equipment that contains device-based authentication keys | [4.4](4_events.md#expiration), [4.5](4_events#invalidation) |
| | In enterprise applications, limit the transfer of keys to organizationally managed or trusted devices | [B.2](B_syncable.md#cloning) |
| **Key Transfer Security** | Encourage or require subscribers to use cloud services that have been approved for key storage and transfer | [B.2](B_syncable.md#cloning) |
{:latex-table="3" latex-caption="Mitigating Authenticator Threats" latex-longtable="true"  latex-columns="p@0.20\textwidth,p@0.35\textwidth,p@0.35\textwidth"}

Several other strategies may be applied to mitigate the threats described in [Table 3](6_security.md#table-3):

* *Multiple factors* make successful attacks more difficult to accomplish. If an attacker must steal a cryptographic authenticator and guess a password, then the work to discover both factors may be too high.

* *Physical security mechanisms* may be employed to protect a stolen authenticator from duplication. Physical security mechanisms can provide tamper evidence, detection, and response.

* *Requiring long passwords* that do not appear in common dictionaries may force attackers to try every possible value.

* *System and network security controls* may be employed to prevent an attacker from gaining access to a system or installing malicious software.

* *Periodic training* may be performed to ensure that subscribers understand when and how to report a compromise or a suspicion of compromise and to recognize patterns of behavior that may signify that an attacker is attempting to compromise the authentication process.

* *Out-of-band techniques* may be employed to verify the proof of possession of registered devices (e.g., cell phones).

## Authenticator Recovery

The weak point in many authentication mechanisms is the process followed when a subscriber loses control of one or more authenticators and needs to replace them. In many cases, the options for authenticating the subscriber are limited, and economic concerns (e.g., the cost of maintaining call centers) motivate the use of inexpensive and often less secure backup authentication methods. To the extent that authenticator recovery is human-assisted, social engineering attacks are also risky.

To maintain the integrity of the authentication factors, it is essential that one authentication factor cannot be leveraged to obtain an authenticator of a different factor. For example, a password must not be usable to obtain a new list of look-up secrets.

## Session Attacks

Hijacking attacks on the session following an authentication event can have similar security impacts. The session management guidelines in [Sec. 5](5_session.md#sec7) are essential to maintaining session integrity against attacks (e.g., XSS). It is also important to sanitize all information to be displayed [[OWASP-XSS-prevention]](references.md#ref-OWASP-XSS-prevention) to ensure that it does not contain executable content. These guidelines recommend that session secrets be made inaccessible to mobile code to provide extra protection against the exfiltration of session secrets.

Another post-authentication threat is cross-site request forgery (CSRF), which takes advantage of users' tendency to have multiple sessions active simultaneously. It is essential to embed and verify a session identifier for web requests to prevent a valid URL or request from being unintentionally or maliciously activated.
