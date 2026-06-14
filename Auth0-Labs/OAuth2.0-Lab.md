# OAuth 2.0 Client Credentials Flow Lab - Auth0

## Overview

This lab demonstrates an OAuth 2.0 Machine-to-Machine (M2M) authentication flow using the Client Credentials grant type.

The objective was to understand how backend applications obtain access tokens and securely access APIs without a user being involved in the authentication process.

Unlike OpenID Connect (OIDC), which focuses on user identity, OAuth 2.0 focuses on authorization and access to protected resources.

---

## Objectives

- Create and configure an API in Auth0
- Create a Machine-to-Machine application
- Authorize an application to access an API
- Request an OAuth 2.0 access token
- Decode and inspect an access token
- Analyze OAuth scopes and audience values
- Understand the Client Credentials grant type

---

## Lab Environment

### Authorization Server

Auth0

### Client Application

Internal Processing Engine

### Resource Server (API)

Corporate Invoice API

### Tools Used

- Auth0 Dashboard
- Hoppscotch
- JWT.io

---

## Architecture

Client Application → Auth0 → Access Token → Corporate Invoice API

The client application requests an access token from Auth0.

Auth0 validates the request and issues an access token.

The client uses the token to access the protected API.

---

## API Configuration

Created a new API in Auth0.

### API Name

Corporate Invoice API

### Identifier (Audience)

```text
https://api.mycompany.com/invoices
```

### Scope Created

```text
read:invoices
```

Purpose:

Allows applications to read invoice data from the API.

---

## Machine-to-Machine Application Configuration

Created a Machine-to-Machine application named:

**Internal Processing Engine**

Authorized the application to access:

**Corporate Invoice API**

Granted the following permission:

```text
read:invoices
```

This established which resources the application was allowed to access.

---

## Token Request

Configured a POST request in Hoppscotch.

### Endpoint

```text
https://YOUR_AUTH0_DOMAIN/oauth/token
```

### Content Type

```text
application/json
```

### Request Body

```json
{
  "client_id": "YOUR_CLIENT_ID",
  "client_secret": "YOUR_CLIENT_SECRET",
  "audience": "https://api.mycompany.com/invoices",
  "grant_type": "client_credentials"
}
```

The request was submitted successfully and Auth0 returned an access token.

---

## OAuth 2.0 Flow

1. The client application requests an access token from Auth0.
2. Auth0 validates the client credentials.
3. Auth0 verifies the requested audience and permissions.
4. Auth0 issues an access token.
5. The client application uses the token to access the API.
6. The API validates the token before granting access.

---

## Access Token Analysis

The access token was decoded using JWT.io.

### Claims Observed

#### aud

Audience claim.

Purpose:

Identifies the API that the token was issued for.

Example:

```text
https://api.mycompany.com/invoices
```

#### scope

Permission claim.

Purpose:

Defines what actions the client application is authorized to perform.

Example:

```text
read:invoices
```

#### iss

Issuer claim.

Purpose:

Identifies Auth0 as the authority that issued the token.

#### exp

Expiration timestamp.

Purpose:

Determines when the token expires.

#### iat

Issued-at timestamp.

Purpose:

Indicates when the token was created.

---

## Key Observation

Unlike the ID Token used in OpenID Connect, this access token contained:

- No email address
- No username
- No profile information
- No human identity data

The token only contained information required to authorize access to a protected resource.

This demonstrates the core purpose of OAuth 2.0:

**Authorization, not authentication.**

---

## Validation Performed

Verified that:

- Auth0 successfully issued an access token
- The audience matched the Invoice API
- The scope matched the assigned permission
- The token decoded successfully
- The token contained authorization data
- No user identity information was present

---

## Key Concepts Demonstrated

### OAuth 2.0

An authorization framework that allows applications to obtain access to protected resources.

### Client Credentials Grant

An OAuth flow used when an application needs access to a resource without a user being involved.

### Access Token

A credential used to authorize requests to a protected resource.

### Audience (aud)

Identifies the API that should accept the token.

### Scope

Defines the permissions granted to the client application.

### Machine-to-Machine Authentication

Communication between backend systems using application identities instead of human users.

---

## Comparison with OIDC

| OpenID Connect (OIDC) | OAuth 2.0 Client Credentials |
|----------------------|-----------------------------|
| Authentication | Authorization |
| User identity | Resource access |
| ID Token | Access Token |
| Contains user claims | Contains permissions |
| User login required | No user involved |

---

## Key Takeaways

This lab demonstrated a complete OAuth 2.0 Client Credentials flow using Auth0.

By creating an API, authorizing a Machine-to-Machine application, and requesting an access token, I was able to observe how backend systems securely obtain access to protected resources.

The exercise reinforced the distinction between authentication and authorization and showed how OAuth 2.0 enables secure service-to-service communication without requiring user interaction.

---

##Screenshots
<img width="1920" height="1032" alt="Screenshot 2026-06-14 000455" src="https://github.com/user-attachments/assets/4bd29279-8d17-48d2-b089-340f34537ee8" />
<img width="1920" height="1032" alt="Screenshot 2026-06-14 000513" src="https://github.com/user-attachments/assets/ab8f1d3b-5255-4430-8ba0-c533d27d96e1" />
<img width="1920" height="1032" alt="Screenshot 2026-06-14 000829" src="https://github.com/user-attachments/assets/430d9a64-1589-42de-8c1e-2637e1e3e045" />
<img width="1920" height="1032" alt="Screenshot 2026-06-14 000946 edit" src="https://github.com/user-attachments/assets/aff4167b-67e6-49ec-81b7-0ec2d40c394e" />
<img width="1920" height="1032" alt="Screenshot 2026-06-14 001006" src="https://github.com/user-attachments/assets/abd344b3-cf12-4e57-8f5a-3207a14776b7" />
