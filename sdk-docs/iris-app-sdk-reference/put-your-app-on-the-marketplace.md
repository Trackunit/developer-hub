---
title: Put your app on the marketplace
category: 61fcd8e1a448f5004215317c
parentDocSlug: iris-app-sdk-reference
---

The app is presented in the Iris Marketplace – from where apps can be deployed as extensions to the Manager.

The marketplace will be the gateway for new services to the industry provided by customers themselves, partners and 3rd party software developers – as well as Trackunit.

# Activation modes

To control the behavior of your app inside the marketplace you can specify a so called activation mode inside the Iris App manifest using the `activationMode` attribute.

There are four different activation modes:

![](https://files.readme.io/e11630c-image.png)

Most generally available apps should use the controlled installation. Trackunit sales ops will make sure the customer has the right agreement before making the app available to the customer. This support setting up rules for individually sold apps. Requirements around pricing schemes etc. should be agreed with Trackunit before submitting the app for review.

Customer specific apps developed for one or a few customers should include a list of customer account IDs in the `validForAccountIds` attribute and use the default enabled activation mode.  
These apps will automatically be visible to the customers in the list.

Subscription package apps that are tied to a specific subscription package should set the `allowForPackage` attribute and can then choose to use either the always visible or default enabled activation mode. Everyone with this subscription package should get the app in the marketplace.

The force enabled activation mode should only be used with prior agreement with Trackunit. Apps with this activation mode will be enabled for all customers and customers cannot disable the app. The app will not be visible in the marketplace. The only way to limit which customers get the app is using the `validForAccountIds` and/or `allowForPackage` attributes. So there might be a forced app that's limited to a subscription package or a specific customer.

# Marketplace content

## Overview

The marketplace overview will include the `name` and the `description` attributes from the app manifest. The description should be a short text without any formatting.  
To show a logo you should put a image inside the `assets` folder in your Iris App and specify the name of the image in the `logoPath` attribute.

## Detailed view

The detailed app view includes a longer description and a number of images and/or videos.

To add a longer description you should create a markdown file inside the `assets` folder and set the `fullDescriptionPath` attribute to the name of the file.

Any screenshots can also be added to the `assets` folder. They should all be listed in the `assets` array inside the manifest with their type set to `IMAGE`.

Videos of the app can also be added by uploading the video to Youtube and then adding a link to the video in the `assets` array inside the manifest.

### Description markdown format

To format the longer description we support basic markdown syntax.

```markdown
# The largest heading
With **bold** and *italic* text.
## The second largest heading
A a [link](https://trackunit.com) to somewhere.
###### The smallest heading
And a list
- Iris
- App
```



To test the markdown syntax [this site](https://marked.js.org/demo/?text=%23%20The%20largest%20heading%0AWith%20**bold**%20and%20*italic*%20text.%0A%23%23%20The%20second%20largest%20heading%0AA%20a%20%5Blink%5D(https%3A%2F%2Ftrackunit.com)%20to%20somewhere.%0A%23%23%23%23%23%23%20The%20smallest%20heading%0AAnd%20a%20list%0A-%20Iris%0A-%20App&options=%7B%0A%20%22async%22%3A%20false%2C%0A%20%22baseUrl%22%3A%20null%2C%0A%20%22breaks%22%3A%20false%2C%0A%20%22extensions%22%3A%20null%2C%0A%20%22gfm%22%3A%20true%2C%0A%20%22headerIds%22%3A%20true%2C%0A%20%22headerPrefix%22%3A%20%22%22%2C%0A%20%22highlight%22%3A%20null%2C%0A%20%22langPrefix%22%3A%20%22language-%22%2C%0A%20%22mangle%22%3A%20true%2C%0A%20%22pedantic%22%3A%20false%2C%0A%20%22sanitize%22%3A%20false%2C%0A%20%22sanitizer%22%3A%20null%2C%0A%20%22silent%22%3A%20false%2C%0A%20%22smartLists%22%3A%20false%2C%0A%20%22smartypants%22%3A%20false%2C%0A%20%22tokenizer%22%3A%20null%2C%0A%20%22walkTokens%22%3A%20null%2C%0A%20%22xhtml%22%3A%20false%0A%7D&version=master) can be used.

## Example

Example of marketplace content inside Iris App manifest:

```typescript
marketplace: {
    name: "Trackunit Demo App",
    description: "This demo app is used for demoing stuff. It has one of each extension type.",
    fullDescriptionPath: "description.md",
    logoPath: "logo.webp",
    assets: [
      { type: "IMAGE", path: "custom_fields.png" },
      { type: "IMAGE", path: "feature_demo.png" },
      { type: "IMAGE", path: "gql_demo.png" },
      { type: "VIDEO", url: "https://www.youtube.com/watch?v=5rsJeFEr4IE" },
    ],
    allowForPackage: ["VIEW", "COLLECT", "INSIGHT"],
    tags: [],
},
```
