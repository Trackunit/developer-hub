---
title: IrisX App Tokens and API access
category:
  uri: /branches/1.0/categories/guides/Apps & Extensions
parentDocSlug: public-apis
---

When launching your app the Trackunit Manager will provide a token for your app. For security purposes this token will
not provide full access to all APIs but limited to the scopes specified in the app manifest.

Is it therefor required to specify the scopes required for your app to function correctly. Then specifying scopes the
app may choose to mark a scope `optional: true`. This means that the user installing the app will able to deny that
scope to the app.

So for example if the app requires access to show asset data, and may also change assets, but will function without. You
can add something like this to your IrisX App manifest:

```json
  scopes: [
{scope: "asset.view", optional: false},
{scope: "account.asset.manage", optional: true},
],
```

The currently supported scopes are listed here:

| Scope                                                                              | Description                                                            |
|------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| `account.access-management.manage`                                                 | Can manage Access Management                                           |
| `account.alert.manage`                                                             | Can manage alerts                                                      |
| `account.alert.view`                                                               | Can view alerts                                                        |
| `account.api-key.manage`                                                           | Can manage API keys                                                    |
| `account.asset.manage`                                                             | Can manage assets                                                      |
| `account.audit-log.view`                                                           | Can view audit logs                                                    |
| `account.billing.manage`                                                           | Can manage billing                                                     |
| `account.custom-fields.manage`                                                     | Can manage custom fields                                               |
| `account.customer.manage`                                                          | Can manage customers                                                   |
| `account.delete`                                                                   | Can delete account                                                     |
| `account.event.manage`                                                             | Can manage events                                                      |
| `account.event.report-issue`                                                       | Can report issue as event                                              |
| `account.group.manage`                                                             | Can manage groups                                                      |
| `account.manage`                                                                   | Can manage account                                                     |
| `account.marketplace.app.install`                                                  | Can install apps from marketplace                                      |
| `account.service-management.network.manage`                                        | Can manage networks in service management                              |
| `account.service-management.network.view`                                          | Can view networks in service management                                |
| `account.service-management.service-plan.assignment.manage`                        | Can manage assignment of service plans in service management           |
| `account.service-management.service-plan.assignment.report`                        | Can report assignment of service plans in service management           |
| `account.service-management.service-plan.assignment.service-registration.register` | Can manage service registration on service plans in service management |
| `account.service-management.service-plan.assignment.service-registration.view`     | Can view service registration on service plans in service management   |
| `account.service-management.service-plan.assignment.view`                          | Can view service plan assignments in service management                |
| `account.service-management.service-plan.manage`                                   | Can manage service plans in service management                         |
| `account.service-management.service-plan.view`                                     | Can view service plans in service management                           |
| `account.site.manage`                                                              | Can manage sites                                                       |
| `account.support-access.approval-flow`                                             | Can approve support access requests                                    |
| `account.user.manage`                                                              | Can manage users                                                       |
| `account.view`                                                                     | Can view account                                                       |
| `account.iris.app.store-secret`                                                    | Can store secrets when configuring IrisX App                           |
| `asset.view`                                                                       | Can view assets                                                        |
| `api.iris.app.proxy.fetch`                                                         | Can make external HTTP requests using Proxy service                    |
