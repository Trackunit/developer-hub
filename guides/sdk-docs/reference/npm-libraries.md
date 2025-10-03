---
title: npm libraries
category:
  uri: Apps & Extensions
parent:
  uri: iris-app-sdk-reference
---

# npm Libraries

The npm libraries that make up the SDK can be categorized into three types: vanilla JS libraries, tailwind-based styling libraries, and React libraries.
You can browse all of our packages on [npmjs.com](https://www.npmjs.com/search?q=%40trackunit) too by searching for @trackunit.

## Vanilla JS Libraries

While we recommend building IrisX Apps with React, the following libraries enable you to use whatever framework you want (even plain Javascript).

| Library                                                                                                    | Usage                                                                                                                                                                                                                                                                |
| ---------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [@trackunit/iris-app](https://www.npmjs.com/package/@trackunit/iris-app)                                   | Core library for building IrisX Applications with any JS framework. It's a [Nx](https://nx.dev/) plugin that adds helpful generators used to setup your app.                                                                                                          |
| [@trackunit/iris-app-api](https://www.npmjs.com/package/@trackunit/iris-app-api)                           | Contains types for main parts of the App SDK, such as the manifest.                                                                                                                                                                                             |
| [@trackunit/iris-app-runtime-core](https://www.npmjs.com/package/@trackunit/iris-app-runtime-core)         | Contains the code for the runtimes that are exposed to IrisX Apps. These facilitate communication with the manager and other things like setting up the rest api. Some runtimes might be part of other packages, this is the CORE one, that will be in all IrisX Apps. |
| [@trackunit/iris-app-runtime-core-api](https://www.npmjs.com/package/@trackunit/iris-app-runtime-core-api) | Types for the @trackunit/iris-app-runtime-core package.                                                                                                                                                                                                              |
| [@trackunit/nx-utils](https://www.npmjs.com/package/@trackunit/nx-utils)                                   | Contains reusable test utils for [Nx](https://nx.dev/).                                                                                                                                                                                                              |
| [@trackunit/rest-iso-feeds](https://www.npmjs.com/package/@trackunit/rest-iso-feeds)                       | The purpose of this library is to contain an easy access to trackunits REST apis.                                                                                                                                                                                    |
| [@trackunit/iris-app-oem-api](https://www.npmjs.com/package/@trackunit/iris-app-oem-api)                   | Used to add custom brand images into the Trackunit Manager.                                                                                                                                                                                                          |
| [@trackunit/i18n-library-translation](https://www.npmjs.com/package/@trackunit/i18n-library-translation)   | Provides i18n translation support for IrisX Apps.                                                                                                                                                                                                                     |
| [@trackunit/iris-app-build-utilities](https://www.npmjs.com/package/@trackunit/iris-app-build-utilities)   | Contains utilities for building IrisX Apps.                                                                                                                                                                                                                           |
| [@trackunit/iris-app-webpack-plugin](https://www.npmjs.com/package/@trackunit/iris-app-webpack-plugin)     | A custom webpack plugin for IrisX Applications.                                                                                                                                                                                                                       |

# Tailwind-based Styling Libraries

The styling libraries save developers a ton of time and make it easy to streamline the look and feel of the UI. All of our stling components depend on the Tailwind framework, so check out their [official documentation](https://tailwindcss.com/) if you are not familiar with it.

| Library                                                                                                                            | Usage                                                                                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [@trackunit/css-core](https://www.npmjs.com/package/@trackunit/css-core)                                                           | Includes all the Trackunit css base setup and PostCSS & Tailwind configuration.                                                                                                        |
| [@trackunit/css-components](https://www.npmjs.com/package/@trackunit/css-components)                                               | Includes all the css classes for [Design System](https://design.iris.trackunit.com/).                                                                  |
| [@trackunit/css-component-tokens](https://www.npmjs.com/package/@trackunit/css-component-tokens)                                   | Exposes the Trackunit Component Tokens Plugin.                                                                                                                                         |
| [@trackunit/css-tailwind](https://www.npmjs.com/package/@trackunit/css-tailwind)                                                   | Exposes the Trackunit Tailwind configuration.                                                                                                                                          |
| [@trackunit/css-tailwind-custom-properties-plugin](https://www.npmjs.com/package/@trackunit/css-tailwind-custom-properties-plugin) | Exposes a plugin used to convert the variables property in a Tailwind configuration to css custom properties.                                                                          |
| [@trackunit/tailwind-styled-components](https://www.npmjs.com/package/@trackunit/tailwind-styled-components)                       | Is a wrapper for [tailwind-styled-components](https://www.npmjs.com/package/tailwind-styled-components) Exposing a small utility for nested inline intellisense and some typing fixes. |
| [@trackunit/ui-icons](https://www.npmjs.com/package/@trackunit/ui-icons)                                                           | Used by the Icon component in [@trackunit/react-components](https://www.npmjs.com/package/@trackunit/react-components)                                                                 |
| [@trackunit/ui-design-tokens](https://www.npmjs.com/package/@trackunit/ui-design-tokens)                                           | Exposes the design tokens used to generate the Tailwind Config, as well as a color utility used to get colors from the theme without using css variables.                              |

# React Libraries

The React libraries do all the plumbing for you in various scenarios. For example when you need to interact with the GraphQL API or you want to get a list of custom fields and display React components without needing to handle state variables yourself.
| Library | Usage |
| --- | --- |
| [@trackunit/react-core-hooks](https://www.npmjs.com/package/@trackunit/react-core-hooks) | Contains core React hooks used for getting data from our context providers inside IrisX Apps. |
| [@trackunit/react-graphql-tools](https://www.npmjs.com/package/@trackunit/react-graphql-tools) | Provides tools for auto-generating hooks to interface our GraphQL API through React code. |
| [@trackunit/react-core-contexts](https://www.npmjs.com/package/@trackunit/react-core-contexts) | Defines core context providers. It is a wrapper for all the base react providers needed to use contexts available in the trackunit manager. This makes it possible to use Hooks and complex components in your IrisX App. For example you can get data on the current user through the useCurrentUser hook.|
| [@trackunit/react-core-contexts-test](https://www.npmjs.com/package/@trackunit/react-core-contexts-test) | Contains testing utilities for [@trackunit/react-core-contexts](https://www.npmjs.com/package/@trackunit/react-core-contexts). |
| [@trackunit/react-core-contexts-api](https://www.npmjs.com/package/@trackunit/react-core-contexts-api) | Holds the types for the providers and contexts in [react-core-contexts](https://www.npmjs.com/package/@trackunit/react-core-contexts). |
| [@trackunit/custom-field-components](https://www.npmjs.com/package/@trackunit/custom-field-components) | Contains React components used to render UI for [Custom Fields](https://developers.trackunit.com/docs/save-data-from-your-app). |
| [@trackunit/react-chart-components](https://www.npmjs.com/package/@trackunit/react-chart-components) | Contains a library of chart components. |
| [@trackunit/react-filter-components](https://www.npmjs.com/package/@trackunit/react-filter-components) | Provides a library of filter components. |
| [@trackunit/react-form-components](https://www.npmjs.com/package/@trackunit/react-form-components) | Offers a library of form components. |
