---
title: Creating a workspace
category: 61fcd8e1a448f5004215317c
parentDocSlug: getting-started
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

To setup an empty NX workspace follow the steps below, if you do not already know NX feel free to checkout their website [NX.dev](https://nx.dev)

### 1. Run the command below to create an nx workspace for all your Iris Apps:

```
npx create-nx-workspace@16.5 --preset=react-monorepo
```

### 2. It should guide you to enter:

```
✔ Where would you like to create your workspace?    · <repository-name>
✔ Application name                                  · <sample-app-name>
✔ Which bundler would you like to use?              · webpack
✔ Default stylesheet format                         · css
✔ Enable distributed caching to make your CI faster · No
```

### 3. Go into your NX Workspace folder

```
cd <repository-name>
```

You now have a NX Workspace and are ready to create your first Iris app!

> Note that a couple of sample apps was created as part of setting up the workspace. These are safe to delete by running the commands
> ```
> nx generate @nx/workspace:remove <sample-app-name>-e2e
> nx generate @nx/workspace:remove <sample-app-name>
> ```
