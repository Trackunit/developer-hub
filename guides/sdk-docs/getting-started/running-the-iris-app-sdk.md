---
title: Run your Iris App
category: 61fcd8e1a448f5004215317c
parentDocSlug: getting-started
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

### 1. Use the NX command to serve the Iris App for local testing.

```
nx run [name-of-your-app]:serve
```



### 2. A browser window will open with this url <https://dev.manager.trackunit.com/iris-sdk-portal/main#runLocal>.
You might need to login before it hits that page, use your developer credentials.

### 3. The screen for the developer-server called _**Iris App Developer Portal**_ will appear.

[block:image]
{
  "images": [
    {
      "image": [
        "https://cdn.statically.io/gh/Trackunit/developer-hub/master/sdk-docs/localmode.png",
        null,
        "App settings extension"
      ],
      "align": "center",
      "sizing": "50% "
    }
  ]
}
[/block]

### 4. From this screen, make sure to enable **Local dev mode**.
Local dev mode enables the manager (which is remotely hosted) to load the apps directly from your local development environment. It might take around 30 seconds to load the first time. 


---

> **Troubleshooting Tips**
>
> - If the app is stuck loading:
>   - Look at the console and ensure that it is not still "bundling". Wait for its completion.
>   - Try reloading the page.
>   - Try a different browser (Safari is not currently supported).
>   - Ensure that you aren't running multiple instances by accident and if so, shutdown the duplicate processes.