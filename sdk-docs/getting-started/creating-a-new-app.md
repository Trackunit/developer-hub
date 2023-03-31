---
title: Creating a new Iris App
category: 61fcd8e1a448f5004215317c
parentDocSlug: getting-started
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

In this step, we will create a new app in the workspace. An app is the deployable unit that will contain all the extensions and configurations.


### 1. Install the Iris App SDK into your NX Workspace by executing:

```
npm install @trackunit/iris-app
```



### 2. Use the Iris App SDK to generate your first Iris App

```
nx generate @trackunit/iris-app:create [name-of-your-app]
```



### 3. A confirmation message will appear confirming that the command was successful.  

```
UPDATE package.json
UPDATE workspace.json
CREATE apps/[name-of-your-app]/package.json
CREATE apps/[name-of-your-app]/index.ts
CREATE apps/[name-of-your-app]/iris-app-manifest.ts
CREATE apps/[name-of-your-app]/tsconfig.app.json
CREATE apps/[name-of-your-app]/tsconfig.json
CREATE apps/[name-of-your-app]/webpack.config.ts
```



### 4. Your first Iris App will be In the apps folder. 

```
⊢ apps
   ⊢ [name-of-your-app]
      ⊢ src
      ⊢ package.json
      ⊢ iris-app-manifest.ts
      ⊢ tsconfig.app.json
      ⊢ tsconfig.json
      ⊢ webpack.config.ts
      ⊢ .gitkeep
```

Next you should extend your Iris App with an extension to actually add some content.
