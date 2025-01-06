---
title: trackunit/iris-app@v0.0.NEXT - upgrade to rspack from webpack
type: improved
---

In this version of our Iris App SDK we have added support for Rspack as well as the existing Webpack.
> to read more on rspack, please visit the [rspack documentation](https://rspack.dev/).

> Iris apps created with `@trackunit/iris-app@0.0.NEXT` should already have the required rspack configuration.

### Rename and update the webpack config file

Rename the `webpack.config.ts` file to `rspack.config.ts` and update the file to use the rspack configuration.

For the new `rspack.config.ts` file, you shold change the following import:
```
import { Configuration } from "webpack";
```
Change to: 
```
import { Configuration } from "@rspack/core";
```
The end result should look like the following:
```
import { Configuration } from "@rspack/core";

export default (configuration: Configuration) => {
  return configuration;
};
```

### Change the following entries in `targets` map in the `project.json` file of your iris app.

For the `build` target, change the following:
```
    "executor": "@trackunit/iris-app:build",
```
Change to: 
```
    "executor": "@trackunit/iris-app-sdk-rspack:build",
```

for `serve` target, change the following:
```
    "executor": "@trackunit/iris-app:serve",
```
Change to: 
```
    "executor": "@trackunit/iris-app-sdk-rspack:serve",
```

Also change the `webpackConfig` option to point to the new `rspack.config.ts` file instead of the `webpack.config.ts` file, and rename it to `rspackConfig`.

The end result should look something like the following.

```
  ...
  "build": {
      "executor": "@trackunit/iris-app-sdk-rspack:build",
      "options": { 
        "outputPath": "dist/apps/your_app", 
        "rspackConfig": "apps/your_app/rspack.config.ts" 
      },
      "outputs": ["{options.outputPath}"]
    },
    "serve": {
      "executor": "@trackunit/iris-app-sdk-rspack:serve",
      "options": { 
        "rspackConfig": "apps/your_app/rspack.config.ts" 
      },
      "outputs": ["{options.outputPath}"]
    },
    ...
```
