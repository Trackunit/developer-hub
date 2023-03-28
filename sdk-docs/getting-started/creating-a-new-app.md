---
title: Creating a new app
category: 61fcd8e1a448f5004215317c
parentDocSlug: getting-started
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version. Pricing, terms, conditions and availability may change in the final version.

In this step, we will create a new app in the workspace. An app is the deployable unit that will contain all the extensions and configurations.

1. Open a Terminal or Command Window and make sure you are in the workspace folder. If not, go into your workspace folder.

```
cd <path-to-workspace>
```



2. Install the SDK into your workspace by executing:

```
npm install @trackunit/iris-app
```



3. Use the Trackunit Iris App SDK plugin to generate your first Iris App by entering this command (you can use your app name instead of my-first-app within the command line).

```
nx generate @trackunit/iris-app:create [name-of-your-app]
```



4. A confirmation message will appear confirming that the command was successful.  

```
UPDATE package.json
UPDATE workspace.json
CREATE apps/[name-of-your-app]/package.json
CREATE apps/[name-of-your-app]/index.ts
CREATE apps/[name-of-your-app]/tile-manifest.ts
CREATE apps/[name-of-your-app]/tsconfig.app.json
CREATE apps/[name-of-your-app]/tsconfig.json
CREATE apps/[name-of-your-app]/webpack.config.ts
```



5. Your first Iris App will be In the apps folder. 

```
⊢ apps
	⊢ [name-of-your-app]
      ⊢ src
      ⊢ package.json
      ⊢ tile-manifest.ts
      ⊢ tsconfig.app.json
      ⊢ tsconfig.json
      ⊢ webpack.config.ts
   	⊢ .gitkeep
```
