---
title: API Tokens v2
category: 652e70de24294117a69a20f0
---
**API Tokens V2** (Scoped Tokens), are OAuth 2.0 access tokens issued to an **account**. Scoped Tokens are obtained via a standard OAuth 2.0 **Client Credentials** flow and are constrained to the scopes you configure on each API Key.

### Why Scoped Tokens?

API Token v2 provide important security and flexibility improvements over previous access methods:

- **Least privilege**: You can create tokens limited only to the scopes required for a specific integration, without leaking full administrator-level access across multiple systems.
- **Separation of duties**: Each API Key can be tied to a specific purpose or service, reducing blast radius in case of compromise.
- **Manageability**: You can create, rotate, and revoke up to 10 keys per account, each with a unique name and description for traceability.

> 🚧 Availability
> API Tokens V2 are being **gradually rolled out**. You may not have access yet, or the system you want to integrate with might not support API Tokens V2 at this time.

This page explains how Scoped Tokens work and how to issue them.

## Overview

- **Who can use it:** Any **account** with access to the **API Keys** app.
- **API Keys per account:** Up to **10** active API Keys.
- **Each API Key has:** a **name**, **description**, and a set of **allowed scopes**.
- **Credentials you receive:** a **client_id** and **client_secret** for each API Key.
- **Token endpoint:** `https://auth.trackunit.com/token/v2`
- **Grant type:** `client_credentials`
- **Scopes:** You request one or more scopes (space-separated). The requested scopes must be a subset of the API Key’s allowed scopes.

> 📘 Scopes
>
> A token’s permissions are limited to the scopes you request **and** the API Key’s allowed scope list. Requesting a scope that isn’t allowed for the API Key will result in an error.

---

## Basic Steps

All applications follow a similar pattern when accessing IRIS APIs with Scoped Tokens:

1. **Create an API Key** in the API Keys application.
2. **Exchange** the API Key’s `client_id` and `client_secret` for an access token at `token/v2`.
3. **Call IRIS APIs** with the bearer token.
4. **Renew the token** when it expires (no refresh token support).

---

## 1. Create an API Key

Open the **API Keys** application and create a new API Key. Provide:

- **Name** – a friendly identifier
- **Description** – what the key is used for
- **Allowed Scopes** – the scopes this key is permitted to request

> 🚧 Limit
>
> Each account can create up to **10** API Keys.

When you create the key, you’ll receive:

- **Client ID** (`client_id`)
- **Client Secret** (`client_secret`)

> 📘 Client Secret
>
> Save the **client secret** securely. For security reasons it may only be shown **once**.

---

## 2. Obtain an Access Token

Use the **Client Credentials** flow to exchange your API Key credentials for an access token. The scopes you request must be **space-separated** and must be contained within the key’s allowed scopes.

```bash
curl --location 'https://auth.trackunit.com/token/v2' \
  --header 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'grant_type=client_credentials' \
  --data-urlencode 'client_id=CLIENT_ID' \
  --data-urlencode 'client_secret=CLIENT_SECRET' \
  --data-urlencode 'scope=AVAILABLE_SCOPES_SEPARATED_WITH_SPACE'
```

### Successful Response

```json
{
  "token_type": "Bearer",
  "expires_in": 1200,
  "access_token": "<<access_token>>",
  "scope": "requested scopes here"
}
```

> 🔐 Security Note
>
> Store tokens securely and transmit them only over HTTPS. Treat `client_secret` like a password—do not embed it in client-side code or mobile apps.

---

## 3. Call IRIS APIs with the Token

Include the access token in the `Authorization` header when calling IRIS APIs:

```
Authorization: Bearer <<access_token>>
```

---

## 4. Renewing Tokens

Scoped Tokens issued via the **Client Credentials** flow **do not support refresh tokens**.
When a token expires (see `expires_in` value in the response), your application must request a **new access token** from the Authorization Server using the same `client_id`, `client_secret`, and scope configuration.

### Renew Token Example

```bash
curl --location 'https://auth.trackunit.com/token/v2' \
  --header 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'grant_type=client_credentials' \
  --data-urlencode 'client_id=CLIENT_ID' \
  --data-urlencode 'client_secret=CLIENT_SECRET' \
  --data-urlencode 'scope=AVAILABLE_SCOPES_SEPARATED_WITH_SPACE'
```

This will return a **new access token** with the same scopes.

---

## Error Handling

Common error cases you may encounter:

- **Invalid client** – wrong `client_id` or `client_secret`.
- **Invalid scope** – requested scope is not allowed by the API Key.
- **Unsupported grant type** – `grant_type` must be `client_credentials`.

Example error:

```json
{
  "error": "invalid_scope",
  "error_description": "Requested scope is not allowed for this API Key."
}
```

---

## Best Practices

- **Least privilege:** Request only the scopes your workload needs.
- **Key hygiene:** Rotate API Keys periodically; revoke keys that are no longer needed.
- **Secret management:** Keep `client_secret` in a secure secret store; avoid logging it.
- **Short-lived access tokens:** Request new tokens automatically when they expire.
- **Audit:** Track which services use which API Key via the key’s name/description.

---

## Quick Reference

### Get Access Token

```bash
curl --location 'https://auth.trackunit.com/token/v2' \
  --header 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'grant_type=client_credentials' \
  --data-urlencode 'client_id=CLIENT_ID' \
  --data-urlencode 'client_secret=CLIENT_SECRET' \
  --data-urlencode 'scope=scope1 scope2'
```

### Renew Token

```bash
curl --location 'https://auth.trackunit.com/token/v2' \
  --header 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'grant_type=client_credentials' \
  --data-urlencode 'client_id=CLIENT_ID' \
  --data-urlencode 'client_secret=CLIENT_SECRET' \
  --data-urlencode 'scope=scope1 scope2'
```

That's it—your account can create up to five API Keys, each with clearly defined scopes, and use them to mint least-privileged Scoped Tokens for IRIS APIs. Since refresh tokens are **not available** for this flow, simply request a new token whenever one expires.
