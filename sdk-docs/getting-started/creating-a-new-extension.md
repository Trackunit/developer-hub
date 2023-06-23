---
title: Creating a new extension
category: 61fcd8e1a448f5004215317c
parentDocSlug: getting-started
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

Once you have created the Iris App, you will need to create an extension and connect it to the app. An extension is either a hook in to a certain place in the Manager UI or a report.

### 1. Create your first extension

```bash
nx g @trackunit/iris-app:extend [name-of-your-extension]
```



### 2. Answer the following questions:

- **What subdir would you like to use for this app-extension?:** 
  - Trackunit recommends bundling extensions as related yet independent components of larger features. You can decide to leave this field empty, and then your extension's folder will be created in the root. But if you are working on bigger things, you have the option to put extensions in the same subfolder. It will not impact functionality, but it helps structuring your code.
- **What app should this app-extension extend?:**
  - Enter the app name used in step 3 in the **[Creating a new app](https://developers.trackunit.com/docs/creating-a-new-app)** section (e.g., my-first-app).  
    - 📌 This question will not appear if you only have a single app in your NX Workspace.

- **Which Iris App extension should be generated?:** 
  - **Fleet** Allows you to add a new tab to the main menu in Trackunit Manager.
  - **Asset Home** Allows you to add a new tab to the menu on the Asset Home screen in Trackunit Manager.
  - **Site Home** Allows you to add a new tab to the menu on the Site Home screen in Trackunit Manager.
  - **Report** Allows you to add a new report to the Reports screen in Trackunit Manager.
  - **Admin** Allows you to add a new tab in the adminstration page in Trackunit Manager.

    ![](https://cdn.statically.io/gh/trackunit/developer-hub/master/which%20iris%20app%20extension%20should%20be%20generated_.png)

```
✔ What name would you like to use for this app-extension? · [name-of-your-extension]
✔ What subdir would you like to use for this app-extension? · [feature-name]
✔ Which Iris App extension should be generated? · FLEET_EXTENSION

CREATE libs/[feature-name]/[name-of-your-extension]/extension-manifest.ts
UPDATE package.json
UPDATE nx.json
CREATE jest.config.ts
CREATE jest.preset.js
UPDATE .vscode/extensions.json
CREATE babel.config.json
CREATE libs/[subdir-of-your-extension]/[name-of-your-extension]/project.json
CREATE .eslintrc.json
CREATE libs/[subdir-of-your-extension]/[name-of-your-extension]/.eslintrc.json
CREATE libs/[subdir-of-your-extension]/[name-of-your-extension]/.babelrc
CREATE libs/[subdir-of-your-extension]/[name-of-your-extension]/README.md
CREATE libs/[subdir-of-your-extension]/[name-of-your-extension]/tsconfig.json
CREATE libs/[subdir-of-your-extension]/[name-of-your-extension]/tsconfig.lib.json
UPDATE tsconfig.base.json
CREATE libs/[subdir-of-your-extension]/[name-of-your-extension]/jest.config.ts
CREATE libs/[subdir-of-your-extension]/[name-of-your-extension]/tsconfig.spec.json
CREATE libs/[subdir-of-your-extension]/[name-of-your-extension]/src/app.spec.tsx
CREATE libs/[subdir-of-your-extension]/[name-of-your-extension]/src/app.tsx
CREATE libs/[subdir-of-your-extension]/[name-of-your-extension]/src/index.tsx
```



### 3. After answering all the questions, a new extension will be created under the libs folder. 

```
⊢ libs
	⊢ [subdir-of-your-extension]/[name-of-your-extension]
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
    ⊢ .gitkeep
```



### 4. The new extension is also added to the `iris-app-manifest.ts` file in your Iris App under apps.

```
  extensions: [[name-of-your-extension]Extension],
```



## Example of an Extension Manifest 
(in this example a Report extension)

```ts
import { ReportExtensionManifest } from '@trackunit/iris-app-api';

const extensionManifest: ReportExtensionManifest = {
  id: 'your-report-id-extension',
  type: 'REPORT_EXTENSION',
  main: '<path-to-report-in-jasper>',
  
};

export default extensionManifest;

```

Now that you have created an Iris App with 1 extension, you are ready to run the Iris App.
( you can add more extensions or new Iris Apps later )