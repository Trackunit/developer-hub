---
title: Project Structure
category: 61fcd8e1a448f5004215317c
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

# Project Structure
The Iris App SDK leverages the Nx build system to generate a mono-repo structure for app development. This structure allows developers to create and manage multiple apps and extensions within the same repository. By utilizing the mono-repo approach, developers can easily share code and resources between apps, reducing redundancy and enhancing maintainability. The shared codebase promotes consistency across applications and simplifies collaboration within teams. Therefore our suggested approach is to have *one* workspace setup and develop all your apps and extensions in it.

## Table of Contents
1. [Overview](#overview)
2. [Main Directories](#main-directories)
3. [Configuration Files In Depth](#configuration-files)

## Overview
### Difference between apps and extensions
It is important to distinguish between an app and an extension as it might be confusing in the beginning.
An "app" serves as a container, bundling one or more "extensions" to create an installable unit. The app handles configuration and metadata such as appearance in the marketplace, installation process, logo, screenshots and descriptive information.

On the other hand, an "extension" is where the main programming efforts are directed to, as it contains the essential application logic and user interface. One or more extensions do, in fact, make up the core functionality of the app.

In simpler terms, think of the app as the external "shell" that brings everything together, while the extensions lie at the very heart of the app, where the functional aspects reside. It's crucial to grasp this distinction early on, but rest assured that it will become clearer as you delve deeper into app development.

[comment]: <Should put an illustration that depicts the above in a simple manner>

## Main Directories
[comment]: <Visual representation of the structure (tree diagram or screenshot)>

### apps
The `apps` directory houses the main application projects within the mono-repo. Each app project resides in its own subdirectory. The apps can share code and resources from the `libs` directory, streamlining the development process and reducing code duplication. The following files are important to understand and are created after generating an app:
- `/[app_name]`
    - `/src`
        - `index.ts`: Leave it empty as it is an autogenerated file that is not used in our setup. 
    - `iris-app-manifest.ts`: This is a very important file that keeps all your configuration, such as marketplace configurations, activationMode, extensions, etc.
    - `package.json`: this package.json file's only role is to define the name and version of the application. This is where you bump your version number before pushing a new version of your app.
    - `project.json`: holds project-specific settings and build configurations and is used by the Nx CLI to understand how to build, test, and serve your application or library. this is where the different targets for the app live. The command "nx run <AppName>:serve" will execute the action described in the serve target in the project.json file, located in the <AppName> folder. Beyond what our guides tell you to do, you likely won't have to look too much into this file to begin with, unless you have a large monorepo and use generic libraries.  Reference the [Nx documentation](https://nx.dev/reference/project-configuration) for more information.
    - `webpack.config.ts`: configuration file used by Webpack, a popular open-source JavaScript module bundler. Under normal circumstances you won't touch this file a lot.

### libs
The libs folder should contain all the extensions, tools and helper-functions that you might want to share between apps. When you generate your first extension, you will have a folder structure looking roughly like this:
- `/[feature_name]`: This folder contains all extensions, which can be shared between apps. Developers can also create normal NX libraries (not extensions) for tools, helper functions, and other shared code such as React components to share between extensions. We suggest a convention where you bundle all extensions related to an overarching "feature" under a subcategory named after the feature. For example, suppose you want to create a weather-availability feature with an Asset Home Extension that indicates if an asset is safe to use in current weather conditions. To apply this feature at the Fleet level, create a Fleet Extension and apply the same weather-prediction logic to both extensions.
    - `/[extension_name]`:
        - `/src`: This folder should house all your code. It is reccomended you bring in your tools, helper functions etc. as dependencies instead of keeping them here.
            - `/generated`: This folder is automatically generated when you follow our graphql guide.
                - `graphql-api.tsx`: It houses auto-generated hooks (functions) that call the graphql api for you.
            - `/queries`: You should create this folder manually and put all your custom graphql queries in it. The hooks above are generated based on the queries you store in this folder
                - `[query_name].graphql`: This is one of your custom graphql queries.
            - `app.spec.tsx`: Unit tests for the App component.
            - `app.tsx`: The entry-point of your custom code logic. Start coding here!
            - `index.tsx`: The entry-point of your extension. It will initialize the App component above and you shouldn't do any changes here. Your point of interest is app.tsx.
        - `extension-manifest.ts`: A small configuration file for the extension that controls the type of the extension, the location of the source code and the name of the extension when it is rendered in the UI as a menu item. Depending on the type of extension, differetn configurations will be available. Check the JSDoc of the **IrisAppManifest** interface for specific explanations.



## Configuration Files
### iris-app-manifest.ts
Possibly the most important configuration file that you need to understand.
It configures the following crucial settings for your app:
-  `specVersion`: The version of the app manifest file. Should not be changed manually. 
- `moduleFederationName`: Name of your app including workspace name, automatically parsed from your app-specific package.json.
- `dependencies`: A full list of runtime dependencies for the app. Automatically parsed from the package.json in root. The list will be security scanned.
- `devDependencies`: Same as above but for dev-dependencies. These are also security scanned.
- `validDomains`: A list of any external domains that the app needs to communicate with. The list is audited in the approval step of the app and every external API call must be listed here to get through the verification process. Even if it goes through without being listed, your app will fail to call the endpoint.
- `validForAccountIds`: Put `ALL_ACCOUNTS` in if your app is available to all users. If you want to only make it available to certain users, provide a list of account ID's as strings.
- `marketplace`: Holds all the settings associated with your apps listing on the marketplace.
    - `name`: Well..the name of your app.
    - `description`: Write a small summary of your app here that describes what it does. Only supports plain text.
    - `fullDescriptionPath`: The path to a markdown file that explains your app in more detail. The file must be stored in the assets folder within the app directory to work. The path is relative to that directory. This means that for a file apps/my-app/assets/description.md, this parameter should be: description.md
    - `logoPath`: Path to an image in the assets folder of the app. The image will be shown in the marketplace. Example: typing "MyImage.png" here, will show the file "apps/my-app/assets/MyImage.png"
    - `assets`: Assets (images and videos) used for the marketplace.
    - `allowForPackage`: Defines with which subscription packages your app is compatible. Take great care when entering this, as your app might bug out (if it went through the approval phase in the first place) if what is stated here does not match reality.
    - `tags`: A list of relevant tags to make your app easier to find.
    - `categories`: A list of categories that your app falls under.
- `extensions`: This is an array containing all the extensions included in this app.
Extensions are automatically added when a new extension is generated.
The array contains an import of the extension manifest within the extension.
If an extension is required in multiple apps, the developer must manually add it to the arrays of those apps.

It is a good idea to inspect the Typescript interface called **IrisAppManifest** in the code to get a good idea on all the configurations you can set and what it means.

### nx.json
[nx.json](https://nx.dev/reference/nx-json#nx.json) is the main configuration file for the Nx workspace, containing project-specific settings, cache settings, and task runner configurations.
New apps, extensions, and libraries are automatically added here when NX generators are used.

### tsconfig.json
There's rarely any reason to change these. It is a configuration file used by the TypeScript compiler. It contains various settings and options
that determine how your TypeScript code should be transpiled into JavaScript, 
as well as how it should handle type checking and other features.
If you haven't worked with Typescript before, familiarize yourself with the [official documentation](https://www.typescriptlang.org/docs/) for it. 