---
title: Iris App Tokens and API access
category: 61fcd8e1a448f5004215317c
parentDocSlug: public-apis
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

When launching your app the Trackunit Manager will provide a token for your app. For security purposes this token will not provide full access to all APIs but limited to the scopes specified in the app manifest.

Is it therefor required to specify the scopes required for your app to function correctly. Then specifying scopes the app may choose to mark a scope `optional: true`. This means that the user installing the app will able to deny that scope to the app.

So for example if the app requires access to show asset data, and may also change assets, but will function without. You can add something like this to your Iris App manifest:

```TypeScript
  scopes: [
    { scope: "asset.view", optional: false },
    { scope: "account.asset.manage", optional: true },
  ],
```

The currently supported scopes are listed here:

| Scope | Description |
|-------|-------------|
| `account.access-management.manage` | Can manage Access Management |
| `account.alert.manage` | Can manage alerts |
| `account.alert.view` | Can view alerts |
| `account.api-key.manage` | Can manage API keys |
| `account.asset.manage` | Can manage assets |
| `account.audit-log.view` | Can view audit logs |
| `account.billing.manage` | Can manage billing |
| `account.custom-fields.manage` | Can manage custom fields |
| `account.customer.manage` | Can manage customers |
| `account.delete` | Can delete account |
| `account.event.manage` | Can manage events |
| `account.event.report-issue` | Can report issue as event |
| `account.group.manage` | Can manage groups |
| `account.manage` | Can manage account |
| `account.marketplace.app.install` | Can install apps from marketplace |
| `account.service-management.network.manage` | Can manage networks in service management |
| `account.service-management.network.view` | Can view networks in service management |
| `account.service-management.service-plan.assignment.manage` | Can manage assignment of service plans in service management |
| `account.service-management.service-plan.assignment.report` | Can report assignment of service plans in service management |
| `account.service-management.service-plan.assignment.service-registration.register` | Can manage service registration on service plans in service management |
| `account.service-management.service-plan.assignment.service-registration.view` | Can view service registration on service plans in service management |
| `account.service-management.service-plan.assignment.view` | Can view service plan assignments in service management |
| `account.service-management.service-plan.manage` | Can manage service plans in service management |
| `account.service-management.service-plan.view` | Can view service plans in service management |
| `account.site.manage` | Can manage sites |
| `account.support-access.approval-flow` | Can approve support access requests |
| `account.user.manage` | Can manage users |
| `account.view` | Can view account |
| `asset.view` | Can view assets |

# Asynchronous API access

If you need access to make API calls on behalf of the user without having to wait for the user to launch your app inside manager. You will need to specify `tokenCallback` in the App manifest:

```TypeScript
  tokenCallback: {
    url: "https://myserver.com/appinstall",
  },
```

When a user installs an app we will call the specified URL with a client ID and Secret that can be used to retrieve an access token to make calls on behalf of the user. The message will look something like this:

```JSON
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

```sh
curl --location --request POST 'https://auth.trackunit.com/apptoken' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'grant_type=client_credentials' \
--data-urlencode 'client_id=0oa10o3h43eulvWtz358' \
--data-urlencode 'client_secret=wZtQppu1huik4cYBAhYXnZS29pSudTBne2SE6WEM5C5' \
--data-urlencode 'scope=asset.view account.view'
```

Remember to include the desired scopes and make sure they are all listed in the manifest.

This will give an result like this:

```JSON
{
    "token_type": "Bearer",
    "expires_in": 3600,
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIn0.dozjgNryP4J3jVmNHl0w5N_XgL0n3I9PlFUP0THsR8U",
    "scope": "asset.view account.view"
}
```

Note the `expires_in`, since it indicates when you need to obtain a new token.

To call the API include a `Authorization: Bearer <access_token>` header in the request.
