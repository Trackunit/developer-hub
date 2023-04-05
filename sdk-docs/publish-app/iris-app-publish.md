---
title: How to publish an Iris App SDK
category: 61fcd8e1a448f5004215317c
parentDocSlug: publish-app
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

Publishing an Iris App SDK will allow you to offer the app to customers to download and use. 

> 📘 Nice to know
> 
> Before publishing an Iris App SDK, Trackunit must first approve the app.

First, you will need to create an Iris App SDK and Extension.

1. Open a Terminal or Command window and enter the build command (nx run [name-of-your-app]:build) to build your Iris App SDK. Use your app name instead of [name-of-your-app] within the command line.

```
nx run [name-of-your-app]:build
```



2. Verify the Name and Version number in the package.json in the `dist/apps/[name-of-your-app].`When the Iris App SDK is published, the Name and Version fields combine to create a unique identifier for the app.

```
"name": "[name-of-your-app]"
"version": "1.0.0",
```



1. Enter the Publish command (nx run [name-of-your-app]:publish) to publish your app. Use your app name instead of [name-of-your-app] within the command line.

```
nx run [name-of-your-app]:publishApp
```



4. A browser will open, asking you to authenticate your ID. Use your Trackunit user ID (email@trackunit.com) to authenticate your ID.

> 📘 Nice to know
> 
> Currently, you can only publish an app using an internal Trackunit account (email@trackunit.com).
