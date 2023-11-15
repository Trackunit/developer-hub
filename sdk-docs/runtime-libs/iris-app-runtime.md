---
title: Installing Iris App Runtime in an Iris App Extension 
category: 61fcd8e1a448f5004215317c
parentDocSlug: runtime-libs
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

To use Trackunit APIs and integrating with the manager to get information on current asset, site, custom fields or navigate - you need to install the Iris App core hooks. The Iris App core hooks is the interface to the manager from your react Iris App extension.

- Open a Terminal or Command window to install Iris App core hooks.

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