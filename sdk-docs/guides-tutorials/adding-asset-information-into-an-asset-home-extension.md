---
title: Loading Asset Information into an Asset Home Extension
category: 61fcd8e1a448f5004215317c
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice.

In an asset home extension there is a special asset runtime that allows you to query what asset is currently selected.

1. First import the runtime:

```ts
import { AssetRuntime } from '@trackunit/iris-app-runtime-core';
```



2. You can then load asset info by calling the runtime:

```ts
const updatedAssetInfo = await AssetRuntime.getAssetInfo();
```
