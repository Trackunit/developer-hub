---
title: Installing IrisX App Runtime in an IrisX App Extension
category:
  uri: Apps & Extensions
parent:
  uri: runtime-libs
---

To use Trackunit APIs and integrating with the manager to get information on current asset, site, custom fields or navigate - you need to install the IrisX App core hooks. The IrisX App core hooks is the interface to the manager from your react IrisX App extension.

- Open a Terminal or Command window to install IrisX App core hooks.

```
npm install @trackunit/react-core-hooks
```



Then you can import the core hooks in your extensions  `app.tsx`:

```typescript
import { useAssetRuntime, useHasAccessTo, useNavigateInHost } from "@trackunit/react-core-hooks";
```

In this example we can navigate to asset home if you have the assetID.

```typescript
import { Button } from '@trackunit/react-components';
import { useAssetRuntime, useHasAccessTo, useNavigateInHost } from "@trackunit/react-core-hooks";

export const App = () => {
  const { assetInfo } = useAssetRuntime();

  const { gotoAssetHome }= useNavigateInHost(); 
  const { hasAccess: hasAccessToMovementTab } = useHasAccessTo({ assetId: assetInfo?.assetId, page: "movement" });
  
  return (
    <div>
      <p>Can goto asset MovementTab: {hasAccessToMovementTab ? "YES" : "NO"}</p>
      <Button onClick={() => assetInfo?.assetId && gotoAssetHome(assetInfo.assetId, { page: "movement" })}>
        MOVE TO ASSET
      </Button>
    </div>
  );
};

```