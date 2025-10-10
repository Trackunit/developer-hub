---
title: Loading Asset Information into an Asset Home Extension
category:
  uri: /branches/1.0/categories/guides/Apps & Extensions
parent:
  uri: runtime-libs
---

In an asset home extension there is a special asset runtime that allows you to query what asset is currently selected.

### 1. First import the runtime in your App.tsx of the asset home extension
```typescript
import { useAssetRuntime } from '@trackunit/react-core-hooks';
```

In this example we can get the assetId of the current selected asset - in a asset home extension.

```typescript
import { useAssetRuntime } from '@trackunit/react-core-hooks';

export const App = () => {
  const { assetInfo }= useAssetRuntime(); 
  
  return (
    <div>
      {assetInfo?.assetId}
    </div>
  );
};
```
