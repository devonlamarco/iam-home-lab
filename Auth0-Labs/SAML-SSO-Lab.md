# SAML 2.0 SSO Integration Lab

## Objective

Configure an end-to-end SAML 2.0 Single Sign-On (SSO) integration between an Identity Provider (IdP) and Service Provider (SP).

## Skills Practiced

- SAML federation
- Identity Provider configuration
- Service Provider configuration
- Metadata exchange
- SAML assertions
- Certificate-based trust
- SSO troubleshooting

## Environment

Identity Provider (IdP):
Auth0

Service Provider (SP):
samlsp.com

Tools:
- Auth0 Dashboard
- Browser
- SAML-tracer extension

---

# Architecture

User → Service Provider → Auth0 → SAML Assertion → Service Provider

Auth0 acts as the Identity Provider responsible for authentication.

samlsp.com acts as the Service Provider that trusts Auth0.

---

# Lab Overview

SAML requires a trust relationship between the Identity Provider and Service Provider.

The SP provides configuration information:
- Assertion Consumer Service (ACS) URL
- Entity ID (Audience)

The IdP provides:
- Metadata
- Login endpoint
- Signing certificate

---

# Configuration Steps

## 1. Configure Service Provider

Collected the required SP values:

- ACS URL
- Entity ID

These values identify where Auth0 should send the SAML response.

---

## 2. Configure Auth0 as Identity Provider

Created a SAML application in Auth0.

Configured:

- SAML callback URL (ACS URL)
- Application settings

Enabled SAML 2.0 Web App integration.

---

## 3. Metadata Exchange

Downloaded Auth0 Identity Provider metadata.

Metadata contained:

- IdP Entity ID
- SSO endpoint
- X.509 certificate

Imported metadata into the Service Provider.

This established trust between Auth0 and the application.

---

# Authentication Flow

1. User accesses the Service Provider.
2. SP redirects user to Auth0.
3. User authenticates with Auth0.
4. Auth0 creates a SAML Response.
5. Auth0 sends a signed SAML Assertion to the SP.
6. SP validates the assertion.
7. User receives access.

---

# SAML Assertion Review

Inspected the SAML response using SAML-tracer.

Verified:

- Assertion element
- Subject information
- User attributes
- Authentication status

The assertion acted as proof that Auth0 authenticated the user.

---

# Troubleshooting / Validation

No configuration errors occurred during this lab.

To validate the integration, I verified:

- Service Provider ACS URL matched Auth0 configuration
- Entity ID/Audience values matched between systems
- Metadata exchange completed successfully
- Auth0 issued a SAML response
- Service Provider accepted the SAML assertion
- User attributes were successfully returned

Common SAML issues to investigate in production:

## Invalid Audience

Cause:
Service Provider Entity ID does not match the value configured in the IdP.

Resolution:
Update the Entity ID configuration so both systems expect the same audience.

## Invalid ACS URL

Cause:
The SAML response is being sent to an incorrect endpoint.

Resolution:
Verify the Assertion Consumer Service URL.

## Certificate Validation Failure

Cause:
The Service Provider cannot verify the IdP signature.

Resolution:
Update the IdP signing certificate/metadata.

---

# Key Takeaways

SAML enables federation by allowing a Service Provider to trust an Identity Provider for authentication.

The Identity Provider authenticates the user and sends a signed assertion containing user claims.

The Service Provider validates the assertion and creates a session.

---

# Screenshots
<img width="1920" height="1032" alt="Screenshot 2026-06-12 143424" src="https://github.com/user-attachments/assets/d451432d-4498-4e3a-8fb5-e39354de5dd6" />
<img width="1920" height="1032" alt="Screenshot 2026-06-12 143450" src="https://github.com/user-attachments/assets/e93f4ad2-4061-48ac-acf3-32849c0f4fc6" />
<img width="1920" height="1032" alt="Screenshot 2026-06-12 143556" src="https://github.com/user-attachments/assets/ef4bb122-b3d1-49c0-8390-5956773b6dac" />
<img width="1920" height="1032" alt="Screenshot 2026-06-12 145710" src="https://github.com/user-attachments/assets/5953e682-4b8b-43cf-b627-04c869bf882f" />
<img width="1920" height="1032" alt="Screenshot 2026-06-12 150307" src="https://github.com/user-attachments/assets/a731591e-2a56-4b92-a7f6-e1d7e2ca5247" />
<img width="1920" height="1032" alt="Screenshot 2026-06-12 150516" src="https://github.com/user-attachments/assets/690440b1-070f-4df4-8274-f28635e1ff5c" />
<img width="1920" height="1032" alt="Screenshot 2026-06-12 151830" src="https://github.com/user-attachments/assets/87634baf-7e9a-4f9b-bf21-9a0b368caf1f" />


