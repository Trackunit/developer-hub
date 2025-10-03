---
title: How to submit an App SDK
category:
  uri: Apps & Extensions
parent:
  uri: publish-app
---

Submitting an App SDK will allow you to offer the app to customers to download and use.

This guide assumes you've completed the [getting started](./getting-started) guide.

1. Open a Terminal or Command window and enter the build command (`nx run [name-of-your-app]:build`) to build your App SDK.

```
npx nx run [name-of-your-app]:build
```

2. Verify the Name and Version number in the package.json in the `dist/apps/[name-of-your-app]`. When the App SDK is submitted, the name and version fields combine to create a unique identifier for the app.

```
"name": "[name-of-your-app]"
"version": "1.0.0",
```

3. Enter the submit command (`nx run [name-of-your-app]:submitApp`) to submit your app for approval.

```
npx nx run [name-of-your-app]:submitApp
```

4. Accept the [developer terms and conditions](https://trackunit.com/terms-conditions-marketplace/)) by typing `accept` when prompted.

5. A browser will open, asking you to authenticate your ID. Use your Trackunit manager credentials to authenticate your ID. It will inform you your device is activated.

   By device it refers to the command line interface.

6. Once the submit is complete it will show

```
🚀 Uploaded the app package version 1.0.0.
```

> 📘 Remember
>
> Remember to bump the version number inside `apps/[name-of-your-app]/package.json` before you build and submit!
>
> It is not possible to submit the same version multiple times.

> 📘 Nice to know
>
> If running this as part of a CI pipeline you can also accept the developer terms and conditions by setting the environment variable `TU_DEV_TERMS_AND_CONDITIONS=accept`.
> 
> The access token can be supplied using the `TU_TOKEN` environment variable.
> 
