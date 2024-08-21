---
layout: default
title: Usability
navOrder: 9
navTitle: Usability
permalink: /sp800-63c/usability/
anchor: usability
section: 8
---

# Usability Considerations {#usability}

*This section is informative.*

> In order to align with the standard terminology of user-centered design and usability, the term "user" is used throughout this section to refer to the human party. In most cases, the user in question will be the subject (in the role of applicant, claimant, or subscriber) as described elsewhere in these guidelines.

_Ergonomic of Human-System Interaction — Part 11: Usability: Definitions and Concepts_ [[ISO/IEC9241-11]](references.md#ref-ISOIEC9241) defines usability as the "extent to which a system, product or service can be used by specified users to achieve specified goals with effectiveness, efficiency and satisfaction in a specified context of use." This definition focuses on users, goals, and context of use as key elements necessary for achieving effectiveness, efficiency and satisfaction. A holistic approach considering these key elements is necessary to achieve usability.

From the usability perspective, one of the major potential benefits of federated identity systems is to address the problem of user fatigue associated with managing multiple authenticators. While this has historically been a problem with usernames and passwords, the increasing need for users to manage many authenticators — whether physical or digital — presents a usability challenge.

As stated in [Sec. 8 of [SP800-63A]](../_sp800-63a/8_usability.md#sec9){:latex-href="#ref-SP800-63A"} and [Sec. 8 of [SP800-63B]](../_sp800-63b/8_usability.md#sec10){:latex-href="#ref-SP800-63B"}, overall user experience is critical to the success of digital identity systems. This is especially true for federated identity systems, as federation is a less familiar user interaction paradigm for many users. Users' prior authentication experiences may influence their expectations.

The overall user experience with federated identity systems should be as smooth and easy as possible. This can be accomplished by following usability standards (such as the ISO 25060 series of standards) and established best practices for user interaction design.

Guidelines and considerations are described from the users' perspective.

Section 508 of the Rehabilitation Act of 1973 [[Section508]](references.md#ref-Section508) was enacted to eliminate barriers in information technology and require federal agencies to make electronic and information technology accessible to people with disabilities. While these guidelines do not directly assert requirements from Section 508, identity service providers are expected to comply with Section 508 provisions. Beyond compliance with Section 508, Federal Agencies and their service providers are generally expected to design services and systems with the experiences of people with disabilities in mind to ensure that accessibility is prioritized throughout identity system lifecycles.

## General Usability Considerations

Federated identity systems should:

* Minimize user burden (e.g., frustration, learning curve)
  * Minimize the number of user actions required.
  * Allow users to quickly and easily select among multiple subscriber accounts with a single IdP. For example, approaches such as [Account Chooser](https://openid.net/wg/ac/) allow users to select from a list of subscriber accounts they have accessed in the recent past, rather than start the federation process by selecting their IdP from a list of potential IdPs.
  * Balance minimizing user burden with the need to provide sufficient information to enable users to make informed decisions.

* Minimize the use of unfamiliar technical jargon and details (e.g., users do not need to know the terms IdP and RP if the basic concepts are clearly explained).

* Strive for a consistent and integrated user experience across the IdP and RP.

* Help users establish an understanding of identity by providing resources to users such as graphics, illustrations, FAQs, tutorials and examples. Resources  should explain how users' information is treated and how transacting parties (e.g., RPs, IdPs, and brokers) relate to each other.

* Provide clear, honest, and meaningful communications to users (i.e., communications should be explicit and easy to understand).

* Provide users online services independent of location and device.

* Make trust relationships explicit to users to facilitate informed trust decisions. Trust relationships are often dynamic and context dependent. Users may be more likely to trust some IdPs and RPs with certain attributes or transactions more than others. For example, users may be more hesitant to use federated identity systems on websites that contain valuable personal information (such as financial or health). Depending on the perceived sensitivity of users' personal information, users may be less comfortable with commercial as IdPs since people often have concerns about advertising and data-usage of such companies. Conversely, some may have more confidence in the commercial IdPs than government IdPs based on their historical interactions with government services. Either way, it is critical to be clear to end-users on the entities involved in a federation transaction and, ideally, provide options that support the broadest set of stakeholder perceptions possible. 

* Follow the usability considerations specified in [[SP800-63A] Sec. 8](../_sp800-63a/8_usability.md#sec9){:latex-href="#ref-SP800-63A"} for any user-facing information.

* Clearly communicate how and where to acquire technical assistance. For example, provide users with information such as a link to an online self-service feature, chat sessions or a phone number for help desk support. Avoid redirecting users back and forth among transacting parties (e.g., RPs, IdPs, and brokers) to receive technical assistance.

* Perform integrative and continuous usability evaluations with representative users and realistic tasks in an appropriate context to ensure success of federated identity systems from the users' perspectives.


## Specific Usability Considerations

This section addresses the specific usability considerations that have been identified with federated identity systems. This section does not attempt to present exhaustive coverage of all usability factors related to federated identity systems. Rather, it is focused on the larger, more pervasive themes in the usability literature, primarily users' perspectives on identity, user adoption, trust, and perceptions of federated identity space. In some cases, implementation examples are provided. However, specific solutions are not prescribed. The implementations mentioned are examples to encourage innovative technological approaches to address specific usability needs. See standards for system design and coding, specifications, APIs, and current best practices (such as OpenID and OAuth) for additional examples. Implementations are sensitive to many factors that prevent a one-size-fits-all solution.

### User Perspectives on Online Identity

Even when users are familiar with federated identity systems, there are different approaches to federated identity (especially in terms of privacy and the sharing of information) that make it necessary to establish reliable expectations for how users' data are treated. Users and implementers have different concepts of identity. Users think of identity as logging in and gaining access to their own private space. Implementers think of identity in terms of authenticators and assertions, assurance levels, and the necessary set of identity attributes to provide a service. Given this disconnect between users' and implementers' concepts of identity, it is essential to help users form an accurate concept of identity as it applies to federated identity systems. A good model of identity provides users a foundation for understanding the benefits and risks of federated systems and encourage user adoption and trust of these systems.

To minimize the personal information collected and protect privacy, IdPs ought to provide users with pseudonymous options for providing data to RPs, where possible, and inform users of the benefits and drawbacks of pseudonymous identification.
Likewise, RPs ought to request pseudonymous options for users when pseudonymity is possible for the RP's policy. Both IdPs and RPs need to seek to minimize unnecessary data transmission and inform users of which information is transmitted and for what purpose.

Many properties of identity have implications for how users manage identities, both within and among federations. Just as users manage multiple identities based on context outside of cyberspace, users must learn to manage their identity in a federated environment. Therefore, it must be clear to users how identity and context are used. The following factors should be considered:

* Provide users the requisite context and scope in order to distinguish among different user roles. For example, whether the user is acting on their own behalf or on behalf of another, such as their employer.

* Provide users unique, meaningful, and descriptive identifiers to distinguish among entities such as IdPs, RPs, and accounts. Any such user-facing identifiers are likely to be in addition to identifiers used by the underlying protocols, which are not normally exposed to the user.

* Provide users with information on data ownership and those authorized to make changes. Identities, and the data associated with them, can sometimes be updated and changed by multiple actors. For example, some healthcare data is updated and owned by the patient, while some data is only updated by a hospital or doctor's practice.

* Provide users with the ability to easily verify, view, and update attributes. Identities and user roles are dynamic and not static; they change over time (e.g., age, health, and financial data). The ability to update attributes or make attribute release decisions may or may not be offered at the same time. Ensure the process for how users can change attributes is well known, documented, and easy to perform.

* Provide users means for updating data, even if the associated subscriber account or RP subscriber account no longer exists. Consider applicable audit, legal, or policy constraints for needs to track updated data.

* Provide users means to delete their identities completely, removing all information about themselves, including transaction history. Consider applicable audit, legal, or policy constraints that may preclude such action. In certain cases, full deactivation is more appropriate than deletion.

* Provide users with clear, easy-to-find, site/application data retention policy information.

* Provide users with appropriate anonymity and pseudonymity options, and the ability to switch among such identity options as desired, in accordance with an organization's data access policies.

* Provide a means for users to manage each IdP to RP connection, including complete separation as well as the removal of RP access to one or more attributes.

### User Perspectives of Trust and Benefits


Many factors can influence user adoption of federated identity systems. As with any technology, users may value some factors more than others. Users often weigh perceived benefits versus risks before making technology adoption decisions. It is critical that IdPs and RPs provide users with sufficient information to enable them to make informed decisions. The concepts of trust and tiers of trust — fundamental principles in federated identity systems — can drive user adoption. Finally, a positive user experience may also result in increased user demand for federation, triggering increased adoption by RPs.

This sub-section is focused primarily on user trust and user perceptions of benefits versus risks.

To encourage user adoption, IdPs and RPs need to establish and build trust with users and provide them with an understanding of the benefits and risks of adoption. The following factors should be considered:

* Allow users to control their information disclosure and provide explicit consent through the appropriate use of interactive user interfaces and notifications (see [Sec. 7.2](7_privacy.md#notice)). Considerations such as balancing the content, size, and frequency of notifications as well as tailoring notifications to specific communities are necessary to avoid thoughtless user click-through.

* For attribute sharing, consider the following:
  * Provide a means for users to verify those attributes and attribute values that will be shared. Follow good security practices (see [Sec. 3.10.2](3_federation.md#protecting-information) and [Sec. 6](6_security.md#security)).
  * Enable users to consent to a partial list of attributes, rather than an all-or-nothing approach. Allow users some degree of online access, even if the user does not consent to share all information.
  * Allow users to update their consent to their list of shared attributes.
  * Minimize unnecessary information presented to users. For example, do not display system generated attributes (such as pairwise pseudonymous identifiers) even if they are shared with the RP as part of the authentication response.
  * Minimize user steps and navigation. For example, build attribute consent into the protocols so they're not a feature external to the federation transaction. Examples can be found in standards such as OAuth or OpenID Connect.
  * Provide effective redress methods such that a user can recover from invalid attribute information claimed by the IdP or collected by the RP. See [Sec 3.6 of [SP800-63]](../_sp80063/3_DIRM.md#redress){:latex-href="#ref-SP800-63"} for more requirements on providing redress.
  * Minimize the number of times a user is required to consent to attribute sharing. Limiting the frequency of consent requests avoids user frustration from multiple requests to share the same attribute.

* Collect information for constrained usage only and minimize information disclosure (see [Sec. 7.3](7_privacy.md#minimization)). User trust is eroded by unnecessary and superfluous information collection and disclosure or user tracking without explicit user consent. For example, only request attributes from the user that are relevant to the current transaction, not for all possible transactions a user may or may not access at the RP.

* Clearly and honestly communicate potential benefits and risks of using federated identity to users. Benefits that users value include time savings, ease of use, reduced number of passwords to manage, and increased convenience.

User concern over risk can negatively influence willingness to adopt federated identity systems. Users may have trust concerns, privacy concerns, security concerns, and single-point-of-failure concerns. For example, users may be fearful of losing access to multiple RPs if a single IdP is unavailable, either temporarily or permanently. Additionally, users may be concerned or confused about learning a new authentication process. In order to foster the adoption of federated identity systems, the perceived benefits must outweigh the perceived risks.

### User Mental Models and Beliefs

Users' beliefs and perceptions predispose them to expect certain results and to behave in certain ways. Such beliefs, perceptions, and predispositions are referred to in the social sciences as mental models. For example, people have a mental model of dining out that guides their behavior and expectations at each establishment, such as fast food restaurants, cafeterias, and more formal restaurants. Thus, it is not necessary to be familiar with every establishment to understand how to interact appropriately at each one.

Assisting users in establishing good and complete mental models of federation allows users to generalize beyond a single specific implementation. If federated identity systems are not designed from users' perspectives, users may form incorrect or incomplete mental models that impact their willingness to adopt these systems. The following factors should be considered:

* Clearly explain the working relationship and information flow among the transacting parties (e.g., RPs, IdPs, and proxies) to avoid user misconceptions. Use the actual names of the entities in the explanation rather than using the generic terms IdPs and RPs.
  * Provide prominent visual cues and information so that users understand why seemingly unrelated entities have a working relationship. For example, users may be concerned with mixing online personal activities with government services due to a lack of understanding of the information flow in federated identity systems.
  * Provide prominent visual cues and information to users about redirection when an RP needs to redirect control from their site to an IdP. For example, display RP branding within the IdP user interface to inform users when they are logging in with their IdP for access to the destination RP.

* Provide users with clear and usable ways (e.g., visual assurance) to determine the authenticity of the transacting  parties (e.g., RPs, IdPs, and proxies). This will also help to alleviate user concern over leaving one domain for another, especially if the root domain changes (e.g., .gov to .com). For example, display the URL of the IdP so that the user can verify that they are not being phished by a malicious site.

* Provide users with clear information, including visual cues, regarding logins and logouts. Depending on the implementation, logging into an RP with a federated account can create long-running sessions for the user at both the IdP and RP. Users may not realize that ending their session with the RP will not necessarily end their session with the IdP; users will need to explicitly "log out" of the IdP. Users require clear information to remind them if explicit logouts are required to end their IdP sessions. Both the IdP and RP could also have automated logout features, based on time since authentication or an activity timeout. Users require clear information about when their session might end without any action on their part, in order to avoid frustration, lost work, or insecure workarounds like copying data out of a secure site in order to avoid an unexpected session timeout.
