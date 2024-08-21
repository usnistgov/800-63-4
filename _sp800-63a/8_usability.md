---
layout: default
title: Usability
navOrder: 9
navTitle: Usability
permalink: /sp800-63a/usability/
anchor: usability
section: 8
---

# Usability Considerations {#usability}
_This section is informative._

In order to align with the standard terminology of user-centered design and usability, the term "user" is used throughout this section to refer to the human party. In most cases, the user in question will be the subject (in the role of applicant, claimant, or subscriber) as described elsewhere in these guidelines.

This section is intended to raise implementers' awareness of the usability considerations associated with identity proofing and enrollment (for usability considerations for typical authenticator usage and intermittent events, see [Sec. 8 of [SP800-63B]](../_sp800-63b/8_usability.md#sec10){:latex-href="#ref-SP800-63B"}.

[[ISO/IEC9241-11]](references.md#ref-ISOIEC9241) defines usability as the "extent to which a system, product, or service can be used by specified users to achieve specified goals with effectiveness, efficiency and satisfaction in a specified context of use." This definition focuses on users, goals, and context of use as the necessary elements for achieving effectiveness, efficiency, and satisfaction. A holistic approach considering these key elements is necessary to achieve usability.

The overarching goal of usability for identity proofing and enrollment is to promote a smooth, positive enrollment process for users by minimizing user burden (e.g., time and frustration) and enrollment friction (e.g., the number of steps to complete and the amount of information to track). To achieve this goal, organizations have to first familiarize themselves with their users.

The identity proofing and enrollment process sets the stage for a user's interactions with a given CSP and the online services that the user will access; as negative first impressions can influence user perception of subsequent interactions, organizations need to promote a positive user experience throughout the process.

Usability cannot be achieved in a piecemeal manner. Performing a usability evaluation on the enrollment and identity proofing process is critical. It is important to conduct a usability evaluation with representative users, realistic goals and tasks, and appropriate contexts of use. The enrollment and identity proofing process should be designed and implemented so that it is easy for users to do the right thing, hard for them to do the wrong thing, and easy for them to recover when the wrong thing happens. [[ISO/IEC9241-11]](references.md#ref-ISOIEC9241), [[ISO16982]](references.md#ref-ISO16982), and [[ISO25060]](references.md#ref-ISO25060) provide guidance on how to evaluate the overall usability of an identity service and additional considerations for increasing usability.

From the user's perspective, the three main steps of identity proofing and enrollment are pre-enrollment preparation, the enrollment and proofing session, and post-enrollment actions. These steps may occur in a single session or there could be significant time elapsed between each one (e.g., days or weeks).

General and step-specific usability considerations are described in sub-sections below.

Guidelines and considerations are described from the users' perspective.


Section 508 of the Rehabilitation Act of 1973 [[Section508]](references.md#ref-Section508) was enacted to eliminate barriers in information technology and require federal agencies to make electronic and information technology accessible to people with disabilities. While these guidelines do not directly assert requirements from Section 508, identity service providers are expected to comply with Section 508 provisions. Beyond compliance with Section 508, Federal Agencies and their service providers are generally expected to design services and systems with the experiences of people with disabilities in mind to ensure that accessibility is prioritized throughout identity system lifecycles.


## General User Considerations During Identity Proofing and Enrollment

This sub-section provides usability considerations that are applicable across all steps of the enrollment process. Usability considerations specific to each step are detailed in [Sec. 8.2](8_usability.md##usability-pre), [Sec. 8.3](8_usability.md#usability-proofing), and [Sec. 8.4](8_usability.md#usability-post).

* To avoid user frustration, streamline the process required for enrollment to make each step as clear and easy as possible.

* Clearly communicate how and where to acquire technical assistance. For example, provide helpful information such as a link to an online self-service portal, chat sessions, and a phone number for help desk support. Ideally, sufficient information should be provided to enable users to answer their own enrollment preparation questions without outside intervention.

* Clearly explain what personal data is being collected and whether collecting the data is optional or not. Additionally, provide information indicating with whom the data will be shared, where it will be stored, and how it will be protected.

* Ensure that all information presented is usable.
  * Follow good information design practice for all user-facing materials (e.g., data collection notices and fillable forms).
  * Write materials in plain language and avoid technical jargon. If appropriate, tailor that language to the literacy level of the intended population. Use active voice and conversational style; logically sequence main points; use the same word consistently rather than synonyms to avoid confusion; and use bullets, numbers, and formatting where appropriate to aid readability.
  * Consider text legibility, such as font style, size, color, and contrast with the surrounding background. The highest contrast is black on white. Text legibility is important because users have different levels of visual acuity. Illegible text will contribute to user comprehension errors or user entry errors (e.g., when completing fillable forms). Use sans serif font styles for electronic materials and serif fonts for paper materials. When possible, avoid fonts that do not clearly distinguish between easily confusable characters (such as the letter "O" and the number "0"). This is especially important for confirmation codes. Use a minimum font size of 12 points, as long as the text fits the display.
* Perform a usability evaluation for each step with representative users. Establish realistic goals and tasks, and appropriate contexts of use for the usability evaluation.


## Pre-Enrollment Preparation {#usability-pre}

This section describes an effective approach to facilitate sufficient pre-enrollment preparation so users can avoid challenging, frustrating enrollment sessions. Ensuring that users are as prepared as possible for their enrollment sessions is critical to the overall success and usability of the identity proofing and enrollment process.

Such preparation is only possible if users receive the necessary information (e.g., the required documentation) in a usable format in an appropriate timeframe. This includes making users aware of exactly what identity evidence will be required. Users do not need to know anything about IALs or whether the identity evidence required is scored as "fair," "strong," or "superior," whereas organizations need to know what IAL is required for access to a particular system.

To ensure users are equipped to make informed decisions about whether to proceed with the enrollment process, and what will be needed for their session, provide users:

* Information about the entire process, such as what to expect in each step.   
  * Clear explanations of the expected timeframes to allow users to plan accordingly.

* Explanation of the need for — and benefits of — identity proofing to allow users to understand the value proposition.

* Identity evidence requirements for the intended IAL and a list of acceptable evidence documents, with information about how they will be validated. 

* If there is an enrollment fee and, if so, the amount and acceptable forms of payment. Offering a variety of acceptable forms of payment allows users to choose their preferred payment operation.

* Information on whether the user's enrollment session will be in-person or in-person over remote channels, and whether a user can choose. Only provide information relevant to the allowable session option(s).
  * Information on the location(s), whether a user can choose their preferred location, and necessary logistical information for in-person or in-person over remote channels session. Note that users may be reluctant to bring identity evidence to certain public places (a supermarket versus a bank), as it increases exposure to loss or theft.
  * Information on the technical requirements (e.g., requirements for internet access) for remote sessions.
  * An option to set an appointment for in-person or in-person over remote channels identity proofing sessions to minimize wait times. If walk-ins are allowed, make it clear to users that their wait times may be greater without an appointment.
    * Provide clear instructions for setting up an enrollment session appointment, reminders, and how to reschedule existing appointments.
    * Offer appointment reminders and allow users to specify their preferred appointment reminder method(s) (e.g., postal mail, voicemail, email, text message). Users need information such as the date, time, and location, and a description of the required identity evidence.
* Information on the allowed and required identity evidence and attributes, whether each piece is voluntary or mandatory, and the consequences for not providing the complete set of identity evidence. Users need to know the specific combinations of identity evidence, including requirements specific to a piece of identity evidence (e.g., a raised seal on a birth certificate). This is especially important due to potential difficulties procuring the necessary identity evidence.
  * Where possible, implement tools to make it easier to obtain the necessary identity evidence.
  * Inform users of any special requirements for minors or people with unique needs. For example, provide users with the information on whether applicant reference and/or trusted referee processes are available and the information necessary to use those processes (see [Sec. 3.1.13](3_ialgen.md#TRs-ARs)).
  * If forms are required:
     * Provide fillable forms before and at the enrollment session. Do not require users to have access to a printer.
     * Minimize the amount of information that users must enter on a form, as users are easily frustrated and more error-prone with longer forms. Where possible, pre-populate forms.

## Identity Proofing and Enrollment {#usability-proofing}

Usability considerations specific to identity proofing and enrollment include:

* At the start of the identity proofing session, remind users of the procedure. Do not expect them to remember the procedures described during the pre-enrollment preparation step. If the enrollment session does not immediately follow pre-enrollment preparation, it is especially important to clearly remind users of the typical timeframe to complete the proofing and enrollment phase.
* Depending on the identity proofing method (e.g., Remote or Onsite Unattended), provide a separate video window that provides a step-by-step tutorial of the identity proofing process. When these types of tutorials or examples are provided, service providers should provide a range of support options to cover a broad set of users. Alternatives to a video window include verbal or written instructions.
* Provide options for the user to reschedule the time or type of their identity proofing appointment, if needed.
* Provide a checklist with the allowed and required identity evidence to ensure that users have the requisite identity evidence to proceed with the enrollment session, including enrollment codes, if applicable. If users do not have the complete set of identity evidence, they must be informed regarding whether they can complete a partial identity proofing session or use exception processing through a trusted referee or, as appropriate, applicant references for identity proofing exception processing. This also would apply to international users where the types of identity evidence and access to data, services, and validation sources may not be easily or readily available to achieve IAL identity proofing requirements. Trusted referees and applicant references are intended to provide capabilities for alternative identity proofing workflows and risk-based decisions for such types of users needing exception processing.
* Notify users regarding what information will be destroyed, what, if any, information will be retained for future follow-up sessions, and what identity evidence they will need to bring to complete a future session. Ideally, users can choose whether they would like to complete a partial identity proofing session.
* Set user expectations regarding the outcome of the enrollment session, as prior identity verification experiences may drive their expectations (e.g., receiving a driver's license in person, receiving a passport in the mail).
* Clearly indicate if 1) users will receive an authenticator immediately at the end of a successful enrollment session; 2) if they will have to schedule a follow-up appointment to pick up an authenticator in person; or 3) or if users will receive the authenticator in the mail and, if so, when they can expect to receive it.

* During the enrollment session, there are several requirements to provide users with explicit notice at the time of identity proofing, such as what data will be collected and processed by the CSP. (See [Sec. 3.1](3_ialgen.md#genProofReqs) and [Sec. 7](7_privacy.md#privacy-section-header) for detailed requirements on notices). CSPs should be aware that seeking consent from users for the use of their attributes for purposes other than identity proofing, authentication, authorization, or attribute assertions, may make them uncomfortable. If users do not perceive how they benefit by the additional collection or uses, they may be unwilling or hesitant to provide consent or continue the process. It is recommended, then, that CSPs provide users with a thorough explanation of how they might benefit from the additional processing of their personal information, and steps the CSP takes to mitigate the risks associated with such processing. Additionally, CSPs should provide users with the ability to opt out of the additional processing. 

* If a confirmation code is issued:
    * Notify users in advance that they will receive a confirmation code, when to expect it, the length of time for which the code is valid, and how it will arrive (e.g., physical mail, SMS, landline telephone, or email).
    * When a confirmation code is delivered to a user, remind the users which service they are enrolling in and include instructions on how to use the code and the length of time for which the code is valid. This is especially important given the short validity timeframes specified in [Sec. 3.1.8](3_ialgen.md#ConfirmCodes).
    * If issuing a machine-readable optical label, such as a QR Code (see [Sec. 3.1.8](3_ialgen.md#ConfirmCodes)), provide users with information on how to obtain QR code scanning capabilities (e.g., acceptable QR code applications).
    * Inform users that they will be required to repeat the enrollment process if enrollment codes expire or are lost before use.
    * Provide users with alternative options, as not all users are able to access and use technology equitably. For example, users may not have the technology needed for this approach to be feasible.

* At the end of the enrollment session:
  * If enrollment is successful, send subscribers a notification of proofing confirming successful identity proofing and enrollment (see [Sec. 3.1.8](3_ialgen.md#ConfirmCodes)) and directions on next steps they need to take (e.g., when and where to pick up their authenticator, when it will arrive in the mail). 
  * If enrollment is partially complete (due to users not having the complete set of identity evidence, users choosing to stop the process, or session timeouts), communicate to users:  
  	* what information will be destroyed;
  	* what, if any, information will be retained for future follow-up sessions;
  	* how long the information will be retained; and
  	* what identity evidence they will need to bring to a future session.
  * If enrollment is not successful, provide users with clear instructions for alternative identity proofing and enrollment options, for example, in-person proofing for users who cannot complete remote proofing.
* If users receive the authenticator during the enrollment session, provide users with instructions on the use and maintenance of the authenticator. For example, information could include instructions for use (especially if there are different requirements for first-time use or initialization), information on authenticator expiration, how to protect the authenticator, and what to do if the authenticator is lost or stolen.

* For both in-person and remote identity proofing, additional usability considerations apply:
  * At the start of the enrollment session, operators or attendants need to explain their role to users (e.g., whether operators or attendants will walk users through the enrollment session or observe silently and only interact as needed).
  * At the start of the enrollment session, inform users that they must not depart during the session, and that their actions must be visible throughout the session.
  * When biometrics are collected during the enrollment session, provide users with clear instructions on how to complete the collection process. The instructions are best given just prior to the process. Verbal instructions with guidance from a live operator are the most effective (e.g., instructing users where the biometric sensor is, when to start, how to interact with the sensor, and when the biometric collection is completed).

* Since remote identity proofing is conducted online, follow general web usability principles. For example:
  * Design the user interface to walk users through the enrollment process.
  * Reduce users' memory load.
  * Make the interface consistent.
  * Clearly label sequential steps.
  * Make the starting point clear.
  * Design to support multiple platforms and device sizes.
  * Make the navigation consistent, easy to find, and easy to follow.


## Post-Enrollment {#usability-post}
Post-enrollment refers to the step immediately following enrollment but prior to the first use of an authenticator (for usability considerations for typical authenticator usage and intermittent events, see [[SP800-63B]](../_sp800-63b/1_introduction.md#introduction){:latex-href="#ref-SP800-63B"}, Sec. 10. As described above, users have already been informed at the end of their enrollment session regarding the expected delivery (or pick-up) mechanism by which they will receive their authenticator.

Usability considerations for post-enrollment include:

* Minimize the amount of time that users wait for their authenticator to arrive. Shorter wait times will allow users to access information systems and services more quickly.

* Inform users whether they need to go to a physical location to pick up their authenticators. The previously identified usability considerations for appointments and reminders still apply.

* Along with the authenticator, give users information relevant to the use and maintenance of the authenticator; this may include instructions for use, especially if there are different requirements for first-time use or initialization, information on authenticator expiration, and what to do if the authenticator is lost or stolen.

* Provide information to users about how to protect themselves from common threats to their identity accounts and associated authenticators, such as social engineering and phishing attacks. 
