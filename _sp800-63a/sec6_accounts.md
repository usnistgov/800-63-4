---
layout: default
title: Subscriber Accounts
navOrder: 6
navTitle: accounts
permalink: /sp800-63a/accounts/
anchor: accounts
section: 6
---

# Subscriber Accounts {#accounts}

_This section is normative._

## Subscriber Accounts

With the exception of identity proofing for the purposes of providing one-time access to an online service, or when an applicant declines enrollment into an account, the CSP **SHALL** enroll the applicant as a subscriber into its identity service and establish a unique _subscriber account_ for that subscriber following the successful identity proofing of an applicant. 

The CSP **SHALL** assign a unique identifier to each subscriber account. 

At a minimum the CSP **SHALL** include the following information in each subscriber account:

* Unique identifier established for the subscriber 
* A record of the identity proofing steps completed for the subscriber in accordance with [Sec. 5.1.1](sec5_ial.md#DocRecReqs)
* Maximum IAL successfully achieved for the identity proofing of the subscriber
* Subscriber consent provided for the processing, retention, or disclosure of any personal or sensitive information maintained in the subscriber account
* All authenticators currently bound to the subscriber account, whether registered at enrollment or subsequent to enrollment
* All attributes that were validated during the identity proofing process or in subsequent transactions to support RP access 

The CSP **SHALL** record information in the subscriber account that was collected during the identity proofing process or subsequently updated for each subscriber, including:

* Validated identity evidence 
* Validated attribute information 
* Attribute information that was collected for enrollment in the CSP identity service that was not validated for identity proofing purposes

The CSP **SHALL** perform a privacy risk assessment for the processing, retention, or disclosure of any personal information maintained in the subscriber account in accordance with [Sec. 5.1.2](sec5_ial.md#PrivacyReqs).

## Subscriber Account Access

In order to meet the requirement that accounts containing PII be protected by multi-factor authentication (MFA), the CSP **SHALL** provide a way for subscribers to access the information in their subscriber account through AAL2 or AAL3 authentication processes using authenticators registered to the subscriber account. 

The CSP **SHALL** provide the capability for subscribers to change or update the personal information contained in their subscriber account.

## Subscriber Account Lifecycle

### Subscriber Account Activity

The CSP **SHALL** establish and maintain a unique subscriber account for each active subscriber in the CSP identity system from the time of enrollment to the time of account closure, as described below.  Until the account is closed, the CSP **SHALL** provide for the use of the subscriber account, information contained in the account, and registered authenticators. 

### Subscriber Account Termination

The CSP **SHALL** terminate the subscriber account and discontinue its use when one of the following occur:

* The subscriber elects to terminate their subscriber account with the CSP.
* The CSP determines, following any due notice period and requirements established by the CSP, that the subscriber account has been compromised.
* The CSP determines, following any due notice period and requirements established by the CSP, that the subscriber has violated the policies or rules for participation in the CSP identity service. 
* The CSP determines, following any due notice period and requirements established by the CSP, that the subscriber account is inactive in accordance with the policies or rules established by the CSP.
* The CSP ceases identity system and services operations.

The CSP **SHALL** delete any personal or sensitive information from the subscriber account records following account termination in accordance with the record retention and disposal requirements.
