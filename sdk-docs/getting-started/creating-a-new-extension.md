---
title: Creating a new extension
category: 61fcd8e1a448f5004215317c
parentDocSlug: getting-started
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice.

Once you have created the Iris App, you will need to create an extension and connect it to the app. An extension is either a hook in to a certain place in the UI or a report.

1. Create your first extension (replace my-first-extension with your extension name).

```
npx nx g @trackunit/iris-app:extend my-first-extension
```



2. The following questions will appear when you run the command that will aid in app creation:

- **What subdir would you like to use for this iris-app-extension?:** Trackunit recommends using the Feature (my-feature-1) directory to sort your extensions.
- **What app should this iris-app-extension extend?:**Enter the app name used in step 3 in the **[Creating an Iris App SDK](#)** section (e.g., my-first-app).  

> 📌 The 'What app should the Iris-app extension extend?' question will not appear if you have a single app in your workspace.

- **Which tile-extension should be generated?:**Select an Extension Point type.
  - **Asset Home** Allows you to add a new tab to the menu on the Asset Home screen in Trackunit Manager.
  - **Fleet** Allows you to add a new tab to the main menu in Trackunit Manager.
  - **Report** Allows you to add a new report to the Reports screen in Trackunit Manager.
  - **Admin:** Allows you to add a new tab in the adminstration page in Trackunit Manager.

![](https://files.readme.io/dfc4901-aa9ca46-Screenshot_2021-11-30_at_07.30.00.png "aa9ca46-Screenshot_2021-11-30_at_07.30.00.png")

3. After answering all the questions, a new extension will be created under the libs folder. 

```text
⊢ libs
	⊢ [my-feature]/[my-iris-app]
      ⊢ src
        ⊢ app.tsx
        ⊢ index.ts
      ⊢ .babelrc
      ⊢ .eslintrc.json
      ⊢ extension-manifest.ts
      ⊢ jest.config.js
      ⊢ project.json
      ⊢ README.md
      ⊢ tsconfig.json
      ⊢ tsconfig.lib.json
      ⊢ tsconfig.spec.json
```



4. The new extension is also added to the `iris-app-manifest.ts` file in your Iris App SDK.

```
  extensions: [myFirstExtension],
```



# Example of an Extension Manifest

```ts
import { ReportExtensionManifest } from '@trackunit/iris-app-api';

const extensionManifest: ReportExtensionManifest = {
  id: 'your-report-id-extension',
  type: 'REPORT_EXTENSION',
  main: '<path-to-report-in-jasper>',
  
};

export default extensionManifest;

```
