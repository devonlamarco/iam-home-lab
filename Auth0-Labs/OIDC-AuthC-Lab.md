# OIDC Authentication Lab - Auth0

## Overview

This lab demonstrates a complete OpenID Connect (OIDC) authentication flow using Auth0 as the OpenID Provider (OP) and OIDC Debugger as the Relying Party (RP).

The objective was to understand how modern applications authenticate users using OIDC and how identity information is transmitted through JSON Web Tokens (JWTs).

---

## Objectives

- Configure an OIDC application in Auth0
- Establish trust between Auth0 and a relying party application
- Authenticate a user using OIDC
- Obtain and inspect an ID Token
- Analyze JWT claims
- Understand the role of scopes in OIDC

---

## Lab Environment

### OpenID Provider (OP)

Auth0

### Relying Party (RP)

OIDC Debugger (https://oidcdebugger.com)

### Tools Used

- Auth0 Dashboard
- OIDC Debugger
- JWT.io

---

## Configuration

### Auth0 Application Setup

Created a new Single Page Application named:

**OIDC Testing App**

Configured the following callback URL:

```text
https://oidcdebugger.com/debug
```

Saved the application settings and recorded the Client ID and Auth0 Domain for use by the relying party.

### OIDC Debugger Configuration

Configured the following values:

**Authorize URI**

```text
https://dev-coqdkvo5rjwmc0vb.us.auth0.com/authorize
```

**Redirect URI**

```text
https://oidcdebugger.com/debug
```

**Client ID**

```text
<Client ID from Auth0>
```

**Scopes**

```text
openid profile email
```

**Response Type**

```text
id_token
```

---

## Authentication Flow

1. User initiates authentication through OIDC Debugger.
2. OIDC Debugger redirects the user to Auth0.
3. User authenticates using Auth0.
4. Auth0 requests consent for the application to access profile information.
5. Auth0 issues an ID Token.
6. User is redirected back to OIDC Debugger.
7. OIDC Debugger displays the returned JWT.

---

## Token Analysis

The returned ID Token was copied into JWT.io and decoded for inspection.

### Claims Observed

#### sub

Unique identifier assigned to the authenticated user.

**Purpose:**

Provides a stable identity reference that applications can use instead of email addresses.

#### iss

Issuer claim.

**Purpose:**

Identifies Auth0 as the authority that issued the token.

#### aud

Audience claim.

**Purpose:**

Identifies the application for which the token was issued.

#### email

User email address.

Returned because the `email` scope was requested.

#### exp

Expiration timestamp.

**Purpose:**

Determines when the token becomes invalid.

#### iat

Issued At timestamp.

**Purpose:**

Indicates when the token was created.

---

## Scope Analysis

### openid

Required for OpenID Connect authentication.

Without this scope, an ID Token is not issued.

### profile

Requests basic user profile information.

Examples include:

- Name
- Nickname
- Profile attributes

### email

Requests access to the user's email information.

---

## Validation Performed

Verified that:

- Authentication completed successfully through Auth0
- OIDC Debugger received an ID Token
- JWT was successfully decoded
- User claims matched the authenticated account
- Issuer and audience values were correct
- Requested scopes returned the expected claims

---

## Key Concepts Demonstrated

### OpenID Connect (OIDC)

An identity layer built on top of OAuth 2.0 that enables authentication and user identity verification.

### JSON Web Token (JWT)

A compact token format used to securely transmit identity information between parties.

### Claims

Pieces of information contained within a token that describe the authenticated user and token properties.

### Scopes

Permissions requested by an application that determine which user information can be returned.

---

## Key Takeaways

This lab demonstrated how OIDC enables modern authentication using JWTs instead of XML assertions. By configuring Auth0 as the OpenID Provider and OIDC Debugger as the Relying Party, I was able to authenticate a user, obtain an ID Token, and inspect the claims used to represent user identity.

The exercise reinforced the relationship between OIDC, OAuth 2.0, scopes, and JWT-based authentication.

---

## Screenshots
<img width="1920" height="1032" alt="Screenshot 2026-06-13 234808" src="https://github.com/user-attachments/assets/1a8d2db3-5bd4-4f96-b828-257e9e4ec028" />
<img width="1920" height="1032" alt="Screenshot 2026-06-13 234921" src="https://github.com/user-attachments/assets/f6dbf1de-a7b9-45e3-a409-4f7410b06181" />
<img width="1920" height="1032" alt="Screenshot 2026-06-13 235105" src="https://github.com/user-attachments/assets/37597821-cd0b-4c0d-8df6-1bc49465435d" />
<img width="1920" height="1032" alt="Screenshot 2026-06-13 235148" src="https://github.com/user-attachments/assets/886191af-90b4-40f6-aac7-6e55d1302cb5" />
