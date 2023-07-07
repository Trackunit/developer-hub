---
title: How to publish an Iris App SDK
category: 61fcd8e1a448f5004215317c
parentDocSlug: publish-app
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

Publishing an Iris App SDK will allow you to offer the app to customers to download and use. 



This guide assumes you've completed the [getting started](./getting-started) guide.

1. Open a Terminal or Command window and enter the build command (`nx run [name-of-your-app]:build`) to build your Iris App SDK.

```
nx run [name-of-your-app]:build
```

2. Verify the Name and Version number in the package.json in the `dist/apps/[name-of-your-app]`. When the Iris App SDK is published, the name and version fields combine to create a unique identifier for the app.

```
"name": "[name-of-your-app]"
"version": "1.0.0",
```



3. Enter the Publish command (`nx run [name-of-your-app]:publish`) to publish your app.

```
nx run [name-of-your-app]:publishApp
```



4. A browser will open, asking you to authenticate your ID. Use your Trackunit manager credentials to authenticate your ID. It will inform you your device is activated.
   
   By device it refers to the command line interface.

5. Once the publish is complete it will show

```
🚀 Uploaded the app package version 1.0.0.
```

> 📘 Nice to know
> 
> Remember to bump the version number inside `apps/[name-of-your-app]/package.json` before you build and publish!
>
> It is not possible to publish the same version multiple times.
>
____
## Troubleshooting tips
If anything fails during the publish flow, look for clues in the terminal:
![](https://cdn.statically.io/gh/trackunit/developer-hub/master/sdk-docs/publish-device-not-activated-termina.png)

If you get an error that you can't figure out yourself, like the one below, reach out to support.
![](https://cdn.statically.io/gh/trackunit/developer-hub/master/sdk-docs/publish-device-not-activated-web.png)