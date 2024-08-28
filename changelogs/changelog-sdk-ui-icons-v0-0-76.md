---
title: trackunit/ui-icons v0.0.76 - new format for icons
type: improved
---

[Breaking change] In this version of our App SDK a new format was introduced for icons, which require an update of jest configurations in extensions that use this library.

> Extensions created with `@trackunit/iris-app@0.0.366` should already have the required configuration.

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
