---
title: Change Log
category: 61fcd8e1a448f5004215317c
parentDocSlug: iris-app-sdk-reference
---

> 🚧 Beta
>
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

# Breaking Changes

## @trackunit/iris-app v0.0.367

In this version we have renamed publishApp to submitApp to avoid confusion about when an app was actually made public. This change means that for existing apps you should open up the `project.json` file and change:

```json
  "publishApp": {
    "executor": "@trackunit/iris-app:publish",
```

To now refer to the submit executor:

```json
  "submitApp": {
    "executor": "@trackunit/iris-app:submit",
```

## @trackunit/ui-icons v0.0.76

In this version a new format was introduced for icons, which require an update of jest configurations in extensions that use this library.

> Ekstensions created with `@trackunit/iris-app@0.0.366` should already have the required configuration.

Add the following entries to the `moduleNameMapper` array of `jest.config.ts` in all relevant libraries.

```
    '@trackunit/ui-icons/icons-sprite-outline.svg': 'jest-transform-stub',
    '@trackunit/ui-icons/icons-sprite-solid.svg': 'jest-transform-stub',
```

The end result should look like the following.

```
export default {
  displayName: 'extension',
  preset: '../../jest.preset.js',
  transform: {
    '^(?!.*\\.(js|jsx|ts|tsx|css|json)$)': '@nx/react/plugins/jest',
    '^.+\\.[tj]sx?$': ['babel-jest', { presets: ['@nx/react/babel'] }],
  },
  moduleFileExtensions: ['ts', 'tsx', 'js', 'jsx'],
  coverageDirectory: '../../coverage/libs/extension',
  moduleNameMapper: {
    '@trackunit/css-core': 'jest-transform-stub',
    '@trackunit/ui-icons/icons-sprite-outline.svg': 'jest-transform-stub',
    '@trackunit/ui-icons/icons-sprite-solid.svg': 'jest-transform-stub',
  },
};
```
