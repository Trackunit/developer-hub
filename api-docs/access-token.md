---
title: Access Token
category: 652e70de24294117a69a20f0
---
IRIS APIs use the [OAuth 2.0 protocol](https://tools.ietf.org/html/rfc6749) for authentication and authorization. IRIS APIs supports OAuth 2.0's Resource Owner Password Flow.

To begin, obtain OAuth 2.0 client credentials from the Manager application. Then your client application requests an access token from the IRIS Authorization Server, extracts a token from the response, and sends the token to the IRIS API that you want to access.

This page gives an overview of how to use OAuth 2.0's Resource Owner Password Flow. 

## Basic Steps

All applications follow a basic pattern when accessing IRIS API using OAuth 2.0. At a high level, you follow four steps:

## 1. Obtain OAuth 2.0 credentials from the Manager application.

Visit the Manager application to create an API User and obtain OAuth 2.0 credentials such as a username, password, client ID and client secret that are known to both Trackunit and your application.

> 🚧 Admin user privileges
> 
> API Users will act as the admin user. Only the admin user can access the "API Access"-page to create API Users and obtain credentials.

Find the "API Access" page in the upper right corner of the Manager application.

![](https://files.readme.io/af2792b-d4792b9-a8de0f7-Skrmbillede_2020-04-15_kl._12.33.13.png "d4792b9-a8de0f7-Skrmbillede_2020-04-15_kl._12.33.13.png")

Create a new API User by clicking "Create New API User". 

![](https://files.readme.io/a7dc2b4-397ca9d-72bbb1f-Skrmbillede_2020-04-14_kl._15.50.31.png "397ca9d-72bbb1f-Skrmbillede_2020-04-14_kl._15.50.31.png")

Capture the username and password of created user along with the "Client ID" and "Client Secret". Beware the password will only be visible this one time.

![](https://files.readme.io/4b969c6-f2791eb-a04e37e-Skrmbillede_2020-04-14_kl._16.39.47.png "f2791eb-a04e37e-Skrmbillede_2020-04-14_kl._16.39.47.png")

## 2. Obtain an access token from the IRIS Authorization Server.

Before your application can access private data using a IRIS API, it must obtain an access token that grants access to that API. A single access token can grant varying degrees of access to multiple APIs based on subscription package and add-ons.

Authenticate against the IRIS Authorization Server using the OAuth 2.0 credentials from step 1.

```curl
curl --location --request POST 'https://auth.trackunit.com/token' \
--header 'Authorization: Basic PDxjbGllbnRfaWQ+Pjo8PGNsaWVudF9zZWNyZXQ+Pg==' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'grant_type=password' \
--data-urlencode 'username=<<username>>' \
--data-urlencode 'password=<<password>>' \
--data-urlencode 'scope=api'
```

> 🚧 Authorization Header
> 
> Applications has to supply client_id and client_secret through basic authentication. Base64 encode <<client_id>>:<<client_secret>> and include it in the 'Authorization' header e.g. 'Authorization: Basic "<<base64 encoded client_id:client_secret>>"'

If the user grants at least one permission, the IRIS Authorization Server sends your application an access token. If the user does not grant the permission, the server returns an error.

A granted permission response from IRIS Authorization Server will be returned as:

```json Successful Response
{
    "token_type": "Bearer",
    "expires_in": 3600,
    "access_token": "<<access_token>>",
    "scope": "api"
}
```

## 3. Send the access token to an API.

After an application obtains an access token, it sends the token to a IRIS API in an HTTP Authorization request header.

## 4. Refresh the access token, if necessary.

Access tokens have limited lifetimes. If your application needs access to a IRIS API beyond the lifetime of a single access token, it can obtain a new token from the IRIS Authorization Server.
