---
title: Calling Trackunit REST APIs
category:
  uri: /branches/1.0/categories/guides/Apps & Extensions
parentDocSlug: public-apis
---

> 📘 GraphQL
>
> The REST APIs are designed to only expose a single domain within the Trackunit data model.
> If you need data from different parts of the Trackunit data model consider using the [public GraphQL API](./graphql-api) instead of the individual REST APIs.

Trackunit exposes public REST APIs as NPM packages to make it easy to query our REST APIs inside an IrisX App.

In this example, we will use the Rest Machine API.  

1. Open a Terminal or Command Window and enter the npm install @trackunit/rest-machine command to Install the machine Rest API: 

```
npm install @trackunit/rest-machines
```



2. Enter the Import command (import { AssetRuntime, RestRuntime } from '@trackunit/iris-app-runtime-core';) to import `RestRuntime` from @trackunit/iris-app-runtime-core. 

```ts
import { AssetRuntime, RestRuntime } from '@trackunit/iris-app-runtime-core';
```



3. To obtain the data from the Machine API, you must convert the assetID to machineID using the following utility function.

```ts
const toID = (uuid: string): number => {
  return Number(uuid?.replace(/-/g, '')?.replace(/^0+/, ''));
};
```



5. Enter the following command to call the Machine API.  

```ts
const machineResult = await machinesApi.machines_getMachine(
  toID(updatedAssetInfo.assetId)
);
```



### Example: Full React Component (App.tsx)

Select the Open Recipe link below to see a Full React Component example.

```typescript
import React, { useEffect, useState } from 'react';
import {
  AssetInfo,
  AssetRuntime,
  RestRuntime,
} from '@trackunit/iris-app-runtime-core';
import { Machines } from '@trackunit/rest-machines';

const toID = (uuid: string): number => {
  return Number(uuid?.replace(/-/g, '')?.replace(/^0+/, ''));
};

const machinesApi = new Machines(RestRuntime);

export const App: React.FC = () => {
  const [assetInfo, setAssetInfo] = useState<AssetInfo>();
  const [brand, setBrand] = useState<string>();
  const [vin, setVin] = useState<string>();

  useEffect(() => {
    (async () => {
      const updatedAssetInfo = await AssetRuntime.getAssetInfo();
      setAssetInfo(updatedAssetInfo);

      const machineResult = await machinesApi.machines_getMachine(
        toID(updatedAssetInfo.assetId)
      );
      setBrand(machineResult.data?.brand);
      setVin(machineResult.data?.vin);
    })();
  }, []);

  return (
    <div className="text-3xl bg-none">
      <div>AssetInfo: {assetInfo?.assetId}</div>
      <div>brand: {brand} </div>
      <div>vin: {vin} </div>
    </div>
  );
};
```