---
layout: default
title: Identity Evidence Examples
navOrder: 11
navTitle: Evidence
permalink: /sp800-63a/evidence/
anchor: EvidenceExamples
section: A
---

# Identity Evidence Examples by Strength {#EvidenceExamples}

*This appendix is informative.*

This appendix provides a non-exhaustive list of types of identity evidence, grouped by strength.

## Fair Evidence Examples

[Table 4. Fair Evidence Examples](A_evidence.md#table-A1){:name="table-A1"}
{:latex-ignore="true"}

| Evidence | Proofing | Validation |  Verification
|---------------|------------------------|------------------|------------------|
Financial Account | KYC/CIP requirements | Confirm signature on assertion is from intended origin. | *Demonstrated possession via an AAL2 authentication event and FAL 2 federated assertion. *User input of a micro deposit event of sufficient entropy. 
Phone Account | Established and documented account opening practices. | *Confirm presence of user account with MNO. *Confirm signature on assertion is from intended origin. | *Demonstrated possession through enrollment code. *Demonstrated possession via and AAL2 authentication event and FAL2 federated assertion. 
Student ID Card | Student registration and enrollment practices. | *Confirm signature on assertion is from intended origin; or  *Confirm physical security features and evaluate for tampering. | *Demonstrated possession via and AAL2 authentication event and FAL2 federated assertion. *Physical comparison to image on the ID. *Biometric Comparison to image on the ID. 
Corporate ID Card | Onboarding and background screening practices. | *Confirm signature on assertion is from intended origin; or *Confirm physical security features and evaluate for tampering. | *Demonstrated possession via and AAL2 authentication event and FAL2 federated assertion. *Physical comparison to image on the ID. *Biometric Comparison to image on the ID. 
Veteran Health ID card | VA identity verification, issuance and eligibility process | *Confirm signature on assertion is from intended origin; or *Confirm physical security features and evaluate for tampering | *Demonstrated possession via and AAL2 authentication event and FAL2 federated assertion. *Physical comparison to image on the ID. *Biometric Comparison to image on the ID.
Credit or Debit Card | KYC/CIP Account Opening Practices. | *Confirm physical security features, physical signature. | *Demonstrated ability to authenticate to the card using a PIN or other activation factor (if available). *Physical inspection of the card. Must be presented with other evidence containing a photo.
Snap Card | State defined eligibility and enrollment requirements. | Confirm physical security features, physical signature | *Visual inspection of the card. Must be presented with other evidence containing a photo (if there is no image on the card). 
Social Security Card | SSN application process. | *Confirm physical security features, inspect for tampering. | *Visual inspection of the card. Must be presented with other evidence containing a photo. 
{:latex-table="4" latex-caption="Fair Evidence Examples" latex-longtable="true" latex-columns="p@0.20\textwidth,p@0.20\textwidth,p@0.20\textwidth,p@0.30\textwidth"}

~~~
\clearpage
~~~
{:latex-literal="true"}

## Strong Evidence Examples

[Table 5. Strong Evidence Examples](A_evidence.md#table-A2){:name="table-A2"}
{:latex-ignore="true"}

| Evidence | Proofing | Validation |  Verification
|---------------|------------------------|------------------|------------------|
Driver's License or State ID | State issuance processes, REAL ID Act | Confirm physical security features through inspection. | *Physical comparison of image on ID. *Biometric Comparison of the image on the ID. *Biometric comparison to issuing source records. 
Permanent Resident Card (issued prior to May 11, 2010) | DHS issuance and eligibility process | *Confirm physical security features through inspection. | *Physical comparison of image on ID. *Biometric Comparison of the image on the ID. *Biometric comparison to issuing source records.
U.S. Uniformed Services Privilege and Identification Card | DoD issuance and eligibility processes | *Confirm physical security features through inspection. | *Visual comparison of image on ID. *Biometric Comparison of the image on the ID. *Biometric comparison to issuing source records. 
Native American Tribal Photo Identification Card | Local issuance and eligibility processes | *Confirm physical security features through inspection. | *Visual comparison of image on ID. *Biometric Comparison of the image on the ID. *Biometric comparison to issuing source records. 
Veteran Health ID Card (VHIC) | VA identity verification, issuance and eligibility process | *Confirm physical security features and evaluate for tampering | *Visual comparison to image on the ID. *Biometric Comparison to image on the ID.
{:latex-table="5" latex-caption="Strong Evidence Examples" latex-longtable="true" latex-columns="p@0.20\textwidth,p@0.20\textwidth,p@0.20\textwidth,p@0.30\textwidth"}

~~~
\clearpage
~~~
{:latex-literal="true"}

## Superior Evidence Examples

[Table 6. Superior Evidence Examples](A_evidence.md#table-A3){:name="table-A3"}
{:latex-ignore="true"}

| Evidence | Proofing | Validation |  Verification
|---------------|------------------------|------------------|------------------|
Personal Identity Verification (PIV) Card | FIPS 201-3 identity verification and issuance processes | Validation of stored PKI Certificate, CRL check if available | *Authentication consistent with multi-factor cryptographic authenticators per NIST SP 800-63B. *Biometric comparison to image stored on ID or biometric stored on ID. *Visual comparison of image on ID. 
Personal Identity Verification-Interoperable (PIV-I) Card | FIPS 201-3 identity verification and issuance processes | Validation of stored PKI Certificate, CRL check if available | *Authentication consistent with multi-factor cryptographic authenticators per NIST SP 800-63B. *Biometric comparison to image stored on ID or biometric stored on ID. *Visual comparison of image on ID. 
Common Access Card (CAC) | DoD identity verification and issuance process | Validation of stored PKI Certificate, CRL check if available | *Authentication consistent with multi-factor cryptographic authenticators per NIST SP 800-63B. *Biometric comparison to image stored on ID or biometric stored on ID. *Visual comparison of image on ID.
US Passport | State Department passport issuance process | Validation of stored PKI certificate, CRL check if available.  | *Visual comparison of image on ID on stored in ID. *Biometric comparison to image on ID or stored in ID. *Biometric comparison to issuing source records. 
International e-Passports Passports | ICAO compliant and/or State Department approved | Validation of stored PKI certificate, CRL check if available. | *Visual comparison of image on ID on stored in ID. *Biometric comparison to image on ID or stored in ID. *Biometric comparison to issuing source records. 
Mobile Driver's License (MDL) | State Issuance processes, AAMVA guidance, and Real ID Act | Validation of Mobile Security Object, revocation check if available | *Authentication consistent with multi-factor cryptographic authenticators per NIST SP 800-63B.
Digital Permanent Resident Card (Verifiable Credential) | DHS issuance and eligibility process | Validation of stored verifiable credential, revocation check if available | *Authentication consistent with multi-factor cryptographic authenticators per NIST SP 800-63B.
European Digital Identity Wallet (EUDI Wallet) Personal Identification (PID) Element | EC defined identity verification and issuance process; qualified issuer certified | Validation of stored verifiable credential or Mobile Security Object, revocation check if available | *Authentication consistent with multi-factor cryptographic authenticators per NIST SP 800-63B.
{:latex-table="6" latex-caption="Superior Evidence Examples" latex-longtable="true" latex-columns="p@0.20\textwidth,p@0.20\textwidth,p@0.20\textwidth,p@0.30\textwidth"}
