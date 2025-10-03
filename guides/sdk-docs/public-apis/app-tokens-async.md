---
title: Calling the API on behalf of the User
category:
  uri: Apps & Extensions
parent:
  uri: public-apis
---



We support calling our API on behalf of a user who have installed your IrisX App without having to rely on the user to launch your app inside Trackunit Manager.

If you need access to make API calls on behalf of the user you will need to specify `tokenCallback` in the App manifest along with the `scopes` (see [here](app-tokens) for more information on scopes):

```json
  "scopes": [ ... ],
  "tokenCallback": {
    "url": "https://myserver.com/appinstall",
  },
```

When a user installs an app we will call the specified URL with a client ID and Secret that can be used to retrieve an access token to make calls on behalf of the user. The message will look something like this:

```json
{
  "type": "INSTALLED",
  "irisAppId": "@organization/appname",
  "accountId": "6b5cb246-7945-4bb6-bec5-2a1413ffd1b3",
  "clientId": "0oa10o3h43eulvWtz358",
  "clientSecret": "wZtQppu1huik4cYBAhYXnZS29pSudTBne2SE6WEM5C5"
}
```

The `accountId` identifies which account installed the app and should be stored securely together with the client ID and secret.

To retrieve an access token for our API you should call `https://auth.trackunit.com/apptoken` like this:

```shell
curl --location --request POST 'https://auth.trackunit.com/apptoken' \
  --header 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'grant_type=client_credentials' \
  --data-urlencode 'client_id=0oa10o3h43eulvWtz358' \
  --data-urlencode 'client_secret=wZtQppu1huik4cYBAhYXnZS29pSudTBne2SE6WEM5C5' \
  --data-urlencode 'scope=asset.view account.asset.manage'
```

Remember to include the desired scopes and make sure they are all listed in the manifest.

This will give an result like this:

```json
{
    "token_type": "Bearer",
    "expires_in": 3600,
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIn0.dozjgNryP4J3jVmNHl0w5N_XgL0n3I9PlFUP0THsR8U",
    "scope": "asset.view account.asset.manage"
}
```

Note the `expires_in`, since it indicates when you need to obtain a new token.

To call the API include a `Authorization: Bearer <access_token>` header in the request.

## Validating application credentials

To make sure the client credentials you received are actually coming from Trackunit, we include a custom header with our request: `Trackunit-Identity`.
It contains a signed JWT token that you can validate using the public key available at `https://iris.trackunit.com/api/marketplace/jwks`.