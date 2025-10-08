---
title: Run your IrisX App
category:
  uri: /branches/1.0/categories/guides/Apps & Extensions
parentDocSlug: getting-started
---

> 📘 This is intended for local testing on the developer machine.
>
> If you need to share your IrisX App with other parties, you will need to submit your app.

### 1. Use the NX command to serve the IrisX App for local testing.

```
npx nx run [name-of-your-app]:serve
```

... wait for the text to say ... compiled successfully in ...

### 2. Open a browser

Using this url: <https://new.manager.trackunit.com/iris-sdk-portal#runLocal>.

You might need to login before it hits that page, use your developer credentials.

### 3. The screen for the developer portal called _**IrisX App Developer Portal**_ will appear.

[block:image]
{
"images": [
{
"image": [
"https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/sdk-docs/localmode.png",
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

Local dev mode enables the manager (which is remotely hosted) to load the apps directly from your local development environment. It might take around 30 seconds to load the first time. This is also where you can turn off running in local dev mode.

> 📘 Troubleshooting Tips
>
> If the app is stuck loading:
>
> - Look at the console and ensure that it is not still "bundling". Wait for its completion.
> - Try reloading the page.
> - Try a different browser (Safari is not currently supported).
> - Ensure that you aren't running multiple instances by accident and if so, shutdown the duplicate processes.
