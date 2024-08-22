---
title: Creating a new Iris App
category: 61fcd8e1a448f5004215317c
parentDocSlug: getting-started
---

> 🚧 Beta
>
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

In this step, we will create a new app in the workspace. An app is the deployable unit that will contain all the extensions and configurations.

### 1. Use the Iris App SDK to generate your first Iris App

```bash
npx nx generate @trackunit/iris-app:create [name-of-your-app]
```

> Note: If you did not use the `@trackunit/create-iris-app-workspace` CLI to generate your workspace, you must add the Iris App SDK first by executing:
>
> ```
> npm install @trackunit/iris-app
> ```

### 2. A confirmation message will appear confirming that the command was successful.

```
UPDATE package.json
CREATE apps/app/project.json
CREATE apps/app/assets/description.md
CREATE apps/app/iris-app-manifest.ts
CREATE apps/app/package.json
CREATE apps/app/src/index.ts
CREATE apps/app/tailwind.config.js
CREATE apps/app/tsconfig.app.json
CREATE apps/app/tsconfig.json
CREATE apps/app/webpack.config.ts
```

### 3. Your first Iris App will be In the apps folder.

```
⊢ apps
   ⊢ [name-of-your-app]/
      ⊢ assets/
      ⊢ src/
      ⊢ iris-app-manifest.ts
      ⊢ package.json
      ⊢ project.json
      ⊢ tailwind.config.js
      ⊢ tsconfig.app.json
      ⊢ tsconfig.json
      ⊢ webpack.config.ts
   ⊢ .gitkeep
```

Next you should extend your Iris App with an extension to actually add some content.
