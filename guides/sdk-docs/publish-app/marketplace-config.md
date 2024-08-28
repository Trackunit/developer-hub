---
title: Controlling marketplace behavior
category: 61fcd8e1a448f5004215317c
parentDocSlug: publish-app
---

The app is presented in the Iris Marketplace – from where apps can be deployed as extensions to the Manager.

The marketplace will be the gateway for new services to the industry provided by customers themselves, partners and 3rd party software developers – as well as Trackunit.

# Installation policies

To control the behavior of your app inside the marketplace you have to specify an installation policy inside the IrisX App manifest using the `installation.pricingPlanPolicy` attribute.

It is possible to specify a policy regardless of the customer plan:

```json
installation: {
  pricingPlanPolicy: { ALL_PLANS: "ON_DEMAND" },
  ...
}
```

Or make it dependent on the pricing plan of the customer installing the app by providing a map between pricing plan and policy:

```json
installation: {
  pricingPlanPolicy: { 
    LEAP: "PREINSTALLED" 
    LIFT: "PREINSTALLED_REQUIRES_APPROVAL" 
  },
  ...
}
```

There are five distinct installation policies, with their behaviour described in the table below:

| InstallationPolicy             | Requires approval from sales ops | Initially installed (once approved if applicable) | Uninstallable | Visible on Marketplace | Description <br/>                                                              |
|--------------------------------|----------------------------|---------------------------------------------------|---------------|---------------|--------------------------------------------------------------------------------|
| PERMANENT                      | no  | yes | no  | no  | Apps developed by Trackunit, needed by all customers                           |
| PREINSTALLED                   | no  | yes | yes | no  | Apps developed by Trackunit or Partners that are part of the base subscription |
| ON_DEMAND                      | no  | no  | yes | yes | Apps developed by Trackunit or Partners that are free to install               |
| PREINSTALLED_REQUIRES_APPROVAL | yes | yes | yes | yes | Apps developed by Trackunit that require extra pricing agreement               |
| ON_DEMAND_REQUIRES_APPROVAL    | yes | no  | yes | yes | Apps developed by Partners that require extra pricing agreement                |

<!--

[//]: # (new image should go here)

The image below demonstrates the installation flow for apps using each of the installation policies:

![](https://files.readme.io/e11630c-image.png)

-->

Most generally available apps should use a policy that requires explicit approval. Trackunit sales ops will make sure the customer has the right agreement before making the app available to the customer. This supports setting up rules for individually sold apps. Requirements such as pricing schemes should be agreed on with Trackunit before submitting the app for review.

Customer specific apps developed for one or few customers should include a list of customer account IDs in the `installation.accountIds` attribute and use the `PREINSTALLED` policy.  
These apps will automatically be visible to the customers in the list.

Apps that are tied to a specific pricing plan should set the `installation.pricingPlanPolicy` attribute and map the relevant plans to either the `ON_DEMAND` or `PREINSTALLED` policies. Everyone with this pricing plan should get the app in the marketplace.

The `PERMANENT` installation policy should only be used with prior agreement with Trackunit, since they will be enabled for all customers and customers cannot uninstall the app. The app will not be visible in the marketplace. The only way to limit which customers get the app is using the `installation.accountIds` and/or `installation.pricingPlanPolicy` attributes.

# Marketplace content

## Overview

The marketplace overview will include the `name` and the `description` attributes from the app manifest. The description should be a short text without any formatting.
To show a logo you should put a image inside the `assets` folder in your IrisX App and specify the name of the image in the `logoPath` attribute.

## Detailed view

The detailed app view includes a longer description and a number of images and/or videos.

To add a longer description you should create a markdown file inside the `assets` folder and set the `fullDescriptionPath` attribute to the name of the file.

Any screenshots can also be added to the `assets` folder. They should all be listed in the `assets` array inside the manifest with their type set to `IMAGE`.

Videos of the app can also be added by uploading the video to Youtube or Vimeo and then adding a link to the video in the `assets` array inside the manifest. The video link should follow one of these formats for the Marketplace to pick it up as a video link:
- `https://www.youtube.com/watch?v=XXXXXXXX`
- `https://vimeo.com/XXXXXXXX`

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

Example of marketplace content inside IrisX App manifest:

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
    tags: []
}
```

We recommend studying the iris-app-manifest.ts file before building your app, as it will give you an understanding of the constraints within which your app can be built.
