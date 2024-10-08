---
title: trackunit/iris-app-api v0.0.172 - removed `default-src` from CSP header
type: improved
---

[Breaking change] We are removing the `default-src` from the `cspHeader` property in the IrisX App manifest.

We are doing this since we have seen issues with more specific CSP rules and conflicts with `default-src`.

So in case you have to call an external API and defined:

```json
{
  "cspHeader": {
    "default-src": ["https://api.mycompany.com"]
  }
}
```

Then it should be changed to the more specific `connect-src` for API calls:

```json
{
  "cspHeader": {
    "connect-src": ["https://api.mycompany.com"]
  }
}
```
