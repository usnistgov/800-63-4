---
layout: default
title: Authenticator Event Management
navOrder: 5
navTitle: Events
permalink: /sp800-63b/events/
anchor: sec6
section: 4
---

# Authenticator Event Management {#sec6}

*This section is normative.*

Events can occur over the lifetime of a subscriber's authenticator and affect its use. These events include binding, maintenance, loss, theft, compromise, unauthorized duplication, expiration, and revocation. This section describes the actions to be taken in response to those events.

## Authenticator Binding {#binding}

*Authenticator binding* refers to establishing an association between a specific authenticator and a subscriber account to enable the authenticator to authenticate for that subscriber account, possibly in conjunction with other authenticators.

Authenticators **SHALL** be bound to subscriber accounts by either:

- Being issued by the CSP as part of enrollment or
- Using a subscriber-provided authenticator that is acceptable to the CSP.

The SP 800-63 suite of guidelines refers to the *binding* rather than the issuance of authenticators to accommodate both options.

Throughout the lifetime of a digital identity, CSPs **SHALL** maintain a record of all authenticators that are or have ever been bound to each subscriber account. The CSP **SHALL** determine the characteristics of the authenticator being bound (e.g., single-factor versus multi-factor, phishing-resistant or not) so that verifiers can assess compliance with the requirements at each AAL. This determination **MAY** be based on strong evidence (e.g., authenticator attestation), direct information from having issued the authenticator, or typical characteristics of authenticator implementations (e.g., whether a user verification bit is set).

The CSP **SHALL** also maintain other state information required to meet the authenticator verification requirements. For example, the throttling of authentication attempts described in [Sec. 3.2.2](3_authenticators.md#throttle) requires the CSP or verifier to maintain state information on recent failed authentication attempts, except for activation factors verified at the authenticator.

The record created by the CSP **SHALL** contain the date and time of significant authenticator life cycle events (e.g., binding to the subscriber account, renewal, update, expiration). The record **SHOULD** include information about the source of the binding (e.g., IP address, device identifier) of any device associated with the event.

As part of the binding process, the CSP **MAY** require additional information about the new authenticator or its associated endpoint to determine whether it is suitable for the requested AAL.

### Binding at Enrollment

Binding at the time of enrollment is considered to be part of the enrollment process and is discussed in [[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"}.

### Post-Enrollment Binding {#post-enroll-bind}

#### Binding an Additional Authenticator {#bindexisting}

To minimize the need for account recovery, CSPs and verifiers **SHOULD** encourage subscribers to maintain at least two separate means of authentication. For example, a subscriber who usually uses an OTP authenticator as a physical authenticator **MAY** also be issued look-up secret authenticators or register a device for out-of-band authentication to be used if the physical authenticator is lost, stolen, or damaged. See [Sec. 4.2](4_events.md#recovery) for more information on replacing passwords.

Accordingly, CSPs **SHOULD** permit the binding of multiple authenticators to a subscriber account. When any new authenticator is bound to a subscriber account, the CSP **SHALL** ensure that the process requires authentication at either the maximum AAL currently available in the subscriber account or the maximum AAL at which the new authenticator will be used, whichever is lower. For example, binding an authenticator that is suitable for use at AAL2 requires authentication at AAL2 unless the subscriber account currently has only AAL1 authentication capability. When an authenticator is added, the CSP **SHALL** notify the subscriber via a mechanism independent of the transaction binding the new authenticator, as described in [Sec. 4.6](4_events.md#notification).

#### External Authenticator Binding

*External authenticator binding* refers to binding an authenticator to a subscriber account when it is not connected to or embedded in the authenticated endpoint. This process is typically used when adding authenticators that are embedded in a new endpoint or when connectivity limitations prevent the newly bound authenticator from being connected to an authenticated endpoint.

The binding process **SHALL** proceed in one of the following ways:

* An endpoint that has authenticated to the CSP requests a binding code from the CSP. The binding code is input into the endpoint associated with the new authenticator and sent to the CSP.

* The endpoint associated with the new authenticator obtains a binding code from the CSP. The binding code is input to an authenticated endpoint and sent to the CSP.

~~~
\clearpage
~~~
{:latex-literal="true"}

In addition to the requirements in [Sec. 4.1.2.1](4_events.md#bindexisting) and [Sec. 4.2](4_events.md#recovery), the following requirements **SHALL** apply when binding an external authenticator:

* An authenticated protected channel **SHALL** be established by the endpoint associated with the new authenticator and the CSP.

* The subscriber **MAY** be prompted to enter an identifier by which the CSP knows them on the endpoint associated with the new authenticator.

* The CSP **SHALL** generate a *binding code* using an approved random bit generator as described in [Sec. 3.2.12](3_authenticators.md#randomness) and send it to either the new authenticator endpoint or the authenticated endpoint approving the binding. The binding code **SHALL** be at least 40 bits in length if used with an identifier entered in the previous step. Otherwise, a binding code of at least 112 bits in length **SHALL** be required.

* The subscriber **SHALL** transfer the binding code to the other endpoint. This transfer **SHALL** either be manual or via a local out-of-band method (e.g., QR code). The binding code **SHALL NOT** be communicated over any insecure channel (e.g., email).

* The binding code **SHALL** be usable only once and **SHALL** be valid for a maximum of 10 minutes.

* Following the binding of the new authenticator (or issuance of a certificate, in the case of PKI-based authenticators), the CSP **SHOULD** encourage the subscriber to authenticate with the new authenticator to confirm that the process has been completed successfully.

* The CSP **SHALL** provide clear instructions on what the subscriber should do in the event of an authenticator binding mishap (e.g., making a button available to be pressed or a contact address to be used to allow a misbound authenticator to be quickly invalidated), as appropriate. This **MAY** be provided in the authenticated session in addition to the binding notification described in [Sec. 4.6](4_events.md#notification).

The binding of an external authenticator may introduce risks due to the potential for the subscriber to be tricked into using a binding code by an attacker or supplying a binding code to an attacker. In some cases, representations (e.g., QR codes) obtained from a trusted source (e.g., an authenticated session, especially when that authentication is phishing-resistant) are considered to be more robust against such attacks because they typically contain the URL of the CSP in addition to the binding code. As a result, there is less potential for the subscriber to be fooled into entering a binding code at a phishing site.

### Binding to a Subscriber-Provided Authenticator {#bind-subscriber-authenticator}

A subscriber may already possess authenticators that are suitable for authentication at a particular AAL. For example, they may have a multi-factor authenticator from a social network provider, considered AAL2 without identity proofing, and would like to use that authenticator at an RP that requires IAL2. This would necessitate identity proofing at IAL2, perhaps by a different CSP, and binding authenticators at enrollment with that CSP.

CSPs **SHOULD**, where practical, accommodate subscriber-provided authenticators to relieve the burden on the subscriber of managing many authenticators. The binding of these authenticators **SHALL** be done as described in [Sec. 4.1.2](4_events.md#post-enroll-bind). If the authenticator strength is not self-evident (e.g., between single-factor and multi-factor authenticators of a given type), the CSP **SHALL** assume that the weaker authenticator has been used unless it can establish that the stronger authenticator is being used (e.g., by verification with the issuer or manufacturer of the authenticator).

### Renewal

The subscriber **SHOULD** bind a new or updated authenticator before an existing authenticator's expiration. The process for this **SHOULD** conform closely to the binding process for an additional authenticator described in [Sec. 4.1.2](4_events.md#post-enroll-bind). The CSP **MAY** periodically take other actions (e.g., confirming contact addresses), either as a part of the renewal process or separately. Following the successful use of the replacement authenticator, the CSP **SHOULD** invalidate the expiring authenticator.

## Account Recovery {#recovery}

*Account recovery* is when a subscriber recovers from losing control of the authenticators necessary to authenticate at a desired AAL. This may be accomplished by repeating portions of the identity proofing process or by presenting one or more recovery codes, perhaps in conjunction with using an authenticator that is still available to the subscriber bound to their subscriber account. Once this is completed, the subscriber can bind one or more new authenticators to their subscriber account. An account recovery event always causes one or more notifications to be sent to the subscriber to aid in detecting the fraudulent use of account recovery.

Account recovery differs from authentication in several ways. Since account recovery is rarely expected to be invoked, it is generally less convenient than authentication and &mdash; depending on the situation and recovery methods offered by the CSP &mdash; may involve extended waiting times.

~~~
\clearpage
~~~
{:latex-literal="true"}

### Account Recovery Methods

Four general classes of account recovery methods are recognized. CSPs **SHALL** support one or more of the following:

* Saved recovery codes
* Issued recovery codes
* Use of recovery contacts
* Repeated identity proofing

In addition to these methods, the CSP **MAY** support an application-specific method (e.g., interaction with a CSP agent) to recover a subscriber account. The use of alternative methods **SHALL** be based on a risk analysis and documented by the CSP.

#### Saved Recovery Codes {#savedrecovery}

At enrollment, a CSP that supports this recovery option **SHOULD** issue a recovery code to the subscriber. The recovery code **SHALL** include at least 64 bits from an approved random bit generator. The saved recovery code may be presented as numeric or alphanumeric (e.g., Base64) for manual entry or as a machine-readable optical label (e.g., QR code) that contains the recovery code. At any point following enrollment, the subscriber **MAY** request a replacement recovery code. The issuance of a replacement recovery code **SHALL** result in an account recovery notification, as described in [Sec. 4.6](#notification).

Saved recovery codes are intended to be maintained offline (e.g., printed or written down) and stored securely by the subscriber for future use. The verification of saved recovery codes **SHALL** be subject to the throttling requirements in [Sec. 3.2.2](3_authenticators.md#throttle). Saved recovery codes **SHALL** be stored in the subscriber account in hashed form using an approved one-way function, as described in [Sec. 3.1.1.2](3_authenticators.md#passwordver). Following the use of a saved recovery code, the CSP **SHALL** invalidate that recovery code and **SHALL** issue a new saved recovery code to the subscriber.

#### Issued Recovery Codes

CSPs that support this option allow the subscriber to maintain one or more recovery addresses (e.g., postal, email, text message, or voice). When recovery is required, a recovery code will be sent to a claimant-chosen address. The issued recovery code **SHALL** include at least six decimal digits (or equivalent) from an approved random bit generator, as described in [Sec. 3.2.12](3_authenticators.md#randomness)). The issued recovery code may be presented as a numeric or alphanumeric (e.g., Base64) for manual entry, a secure (e.g., https) link with a representation of the confirmation code, or a machine-readable optical label (e.g., QR code) that contains the recovery code.

~~~
\clearpage
~~~
{:latex-literal="true"}

Issued recovery codes **SHALL** be valid for at most:

* 21 days when sent to a postal address within the contiguous United States,
* 30 days when sent to a postal address outside the contiguous United States,
* 10 minutes when sent via text messaging or voice, or
* 24 hours when sent to an email address.

The verification of issued recovery codes **SHALL** be subject to the throttling requirements in [Sec. 3.2.2](3_authenticators.md#throttle).

When establishing recovery addresses, the CSP **SHALL** send a confirmation code with the same characteristics as a recovery code to the newly established recovery address. The recovery address **SHALL** be established only after the subscriber successfully confirms it. CSPs **SHALL** allow the subscriber to establish at least two recovery addresses.

#### Recovery Contacts

CSPs that support the use of recovery contacts **SHALL** allow the subscriber to specify one or more addresses of trusted associates to receive issued recovery codes. The requirements for recovery contacts are very similar to those for issued recovery codes with the following exceptions:

* The validity time for recovery codes sent to recovery contacts **MAY** be extended by 24 hours (i.e., valid for no more than 24 hours and 10 minutes if sent via text messaging) to provide additional time for the recovery contact to communicate the recovery code to the subscriber.
* Confirmation of the recovery code address **MAY** also be extended by 24 hours to allow the recovery contact to send the confirmation code to the subscriber for entry.

#### Repeated Identity Proofing

When the subscriber account has been identity proofed at a minimum of IAL1, CSPs **SHOULD** support account recovery by repeating a portion of the identity proofing process. The CSP **SHALL** repeat the necessary steps of identity proofing consistent with the level of initial identity proofing and **SHALL** confirm that the claimant's identity is consistent with the previously established account. If the CSP has retained a biometric sample from the user or a copy of the evidence used during the initial proofing and it is of sufficient quality and resolution, the CSP **MAY** repeat only the verification portion of the identity proofing process, as described in [[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"}. 

### Recovery Requirements by IAL/AAL

Different recovery methods apply depending on the IAL and the maximum AAL associated with the subscriber account.

#### Recovery at AAL1

Since identity proofing requires issuing authenticators that are sufficient for multi-factor authentication to allow the subscriber to access personal information about themselves, subscriber accounts at AAL1 are without identity proofing, and therefore, repeated identity proofing is not possible. The CSP **SHALL** require the successful use of a saved recovery code, issued recovery code, or recovery contact.

#### Recovery at AAL2

To recover an account that can authenticate at a maximum of AAL2, the CSP **SHALL** require the subscriber to complete one of the following:

* Two recovery codes obtained using different methods from the set (saved, issued, and recovery contacts)
* One recovery code from the set (saved, issued, and recovery contacts) plus authentication with a single-factor authenticator bound to the subscriber account
* Repeated identity proofing (provided that the subscriber account has been identity proofed)

#### Recovery at AAL3

If an account that can authenticate at AAL3 has been identity proofed at IAL1 or IAL2, the requirements are the same as those for recovery at AAL2.

If an account that can authenticate at AAL3 has been identity proofed at IAL3, the CSP **SHALL** successfully perform a successful biometric comparison against the biometric characteristic collected during the initial identity proofing session, in an onsite attended identity proofing session, as described in [[SP800-63A]](../_sp800-63a/1_introduction.md#introduction){:latex-href="#ref-SP800-63A"}. The CSP **MAY** also require the presentation of evidence used in the initial identity proofing process.

### Account Recovery Notification {#recoverynotification}

In all cases, account recovery **SHALL** cause a notification to be sent to the subscriber, as described in [Sec. 4.6](4_events.md#notification).

## Loss, Theft, Damage, and Compromise

Compromised authenticators include those that have been lost, stolen, or subject to unauthorized duplication or that have activation factors that are no longer in the subscriber's control. Generally, one must assume that a lost authenticator has been stolen or compromised by someone other than the legitimate holder of the authenticator. Damaged or malfunctioning authenticators are also considered compromised to guard against any possibility of the extraction of the authenticator's secret. One notable exception is a password that has been forgotten without other indications of having been compromised, such as having been obtained by an attacker.

The CSP **SHALL** suspend, invalidate, or destroy compromised authenticators from the subscriber's account promptly following compromise detection. Organizations **SHOULD** establish time limits for this process.

To facilitate the secure reporting of an authenticator's loss, theft, damage, or compromise, the CSP **SHOULD** provide the subscriber with a method of authenticating using a backup or alternate authenticator. This backup authenticator **SHALL** be a password or a physical authenticator. Either could be used, but only one authentication factor is required to make this report. Alternatively, the subscriber **MAY** establish an authenticated protected channel for the CSP to verify the information collected during identity proofing. The CSP **MAY** choose to verify a contact address (i.e., the email address, telephone number, or postal address) and suspend or invalidate authenticators that are reported to have been compromised.

CSPs **MAY** support the temporary suspension of authenticators that are suspected of possible compromise. If suspension is supported, it **SHOULD** be reversed if the subscriber successfully authenticates to the CSP using a valid (i.e., not suspended) authenticator and requests reactivation of the suspended authenticator. The CSP **MAY** set a time limit after which a suspended authenticator can no longer be reactivated.

## Expiration {#expiration}

CSPs **MAY** issue authenticators that expire. If and when an authenticator expires, it **SHALL NOT** be usable for authentication. When an authentication is attempted using an expired authenticator, the CSP **SHOULD** indicate to the subscriber that the authentication failure is due to expiration rather than some other cause.

The CSP **SHOULD** retrieve any authenticator that contains personal information or provide for its zeroization (erasure) or destruction promptly following expiration.

The replacement of expired authenticators **SHALL** conform to the binding process for an additional authenticator, as described in [Sec. 4.1.2](4_events.md#post-enroll-bind).

## Invalidation {#invalidation}

The invalidation of an authenticator (sometimes referred to as revocation or termination) is the removal of the binding between the authenticator and a subscriber account.

CSPs **SHALL** promptly invalidate authenticators when a subscriber account ceases to exist (e.g., subscriber's death, the discovery of a fraudulent subscriber) when requested by the subscriber, when the authenticator is compromised, or when the CSP determines that the subscriber no longer meets its eligibility requirements. The CSP **SHALL** make a risk-based determination of the authenticity of invalidation requests from the subscriber, noting that the consequences of not invalidating a compromised authenticator are usually more significant than the denial-of-service potential of invalidating one in error.

The CSP **SHOULD** retrieve any authenticator that contains personal information or provide for its zeroization (erasure) or destruction promptly following invalidation.

Further requirements on the invalidation of PIV authenticators are found in [[FIPS201]](references.md#ref-FIPS201).

## Account Notifications {#notification}

Certain subscriber account events, such as the binding of an authenticator and account recovery, require the subscriber to be independently notified. These notifications help the subscriber detect possible fraud associated with their subscriber account.

Events that require notification **SHALL** cause a notification to be sent to the notification addresses stored in the subscriber account. Notification addresses may be a:

* Postal address
* Email address
* Address (e.g., telephone number) to which a text message or voice message is to be sent

CSPs **SHALL** support at least two notification addresses per subscriber account, and at least one **SHALL** be validated during the identity proofing process. The CSP **SHOULD** allow subscribers with authentication at AAL2 or higher (or at AAL1 if that is the highest AAL available for the subscriber account) to update their notification addresses. The CSP **SHOULD** encourage the subscriber to maintain multiple notification addresses.

Notifications **SHALL** be sent to all notification addresses except postal addresses. However, notifications **SHALL** be sent to postal addresses if no other form of notification address is stored in the subscriber account or if the notification is for account recovery at AAL3.

The notification **SHALL** provide clear instructions, including contact information, in case the recipient repudiates the event associated with the notification.

