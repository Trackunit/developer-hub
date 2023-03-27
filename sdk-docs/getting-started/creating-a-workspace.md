---
title: Creating a workspace
category: 61fcd8e1a448f5004215317c
parentDocSlug: getting-started
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice.

The workspace will contain all apps and extensions. To create a workspace, you can either base it on a workspace we have created or create a NX workspace from scratch.

# Create workspace from scratch

We follow [the NX guide to create a workspace.](https://nx.dev/getting-started/react-tutorial#create-a-new-workspace)

1. Run the command below to create an nx workspace for a react application:

```
npx create-nx-workspace@15.3.0 --preset=react-monorepo
```



2. It should prompt you to enter a repository name, application name, preferred choice of stylesheet format, and whether you want you enable distributed caching as shown below:

```
✔ Repository name									· <repository-name>
✔ Application name                    				· <app-name>
✔ Default stylesheet format           				· css
✔ Enable distributed caching to make your CI faster	· Yes
```



NX also creates an app in the above step which can be removed, since we will be creating an Iris app in the next stage. Go into the `apps` folder in the workspace directory and remove both the `<app name>` folder and `<app name-e2e>` folder. 

3. The remove them using the CLI, first change directory to the apps folder:

```
cd <repository-name>/apps/
```



Now remove the folders related to the app:

```
rm -rf <app-name> <app-name-e2e>
```



You now have an empty apps folder and are ready to create an Iris app!