---
title: Calling Trackunit GraphQL API
category: 61fcd8e1a448f5004215317c
parentDocSlug: guides-tutorials
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

Trackunit exposes a GraphQL API see [The GraphQL Playground](/page/graphql-api) to create your query and we also expose an NX executor to make it easy to query our GraphQL API inside your Iris App extension.

In this example, we will use a Query for asset information.  

### 1. Open a Terminal or Command Window and enter: 

```
npm install @trackunit/react-graphql-tools
```



### 2. Add "graphql-hooks" to targets
Assuming you have already created an extension for asset home - go to the root of that project (like libs/demo/[name-of-your-extension]/ ) otherwise follow [this guide](creating-an-iris-app-sdk-extension) and open the `project.json` and add to the targets node:

```ts
    "graphql-hooks": {
      "executor": "@trackunit/react-graphql-tools:createHooks"
    },
```



### 3. Create Graphql Query 
Now you are ready to create React hooks from your GraphQL queries, just copy your query or the below query to your src folder in the libs/demo/[name-of-your-extension]/src and name it demo.graphql

```Text Graphql
query GetDemoAsset($assetId: String!) {
  asset(id: $assetId) {
    id
    assetType
    name
    model
    type
    brand
    serialNumber
  }
}
```



### 4. Generate React Hooks
Call this command:
```ts
nx run demo-[name-of-your-extension]:graphql-hooks
```



### 5. Use it in your React code 
Now that it has generated a folder with generated files in your src folder you can use it in your React code. The syntax is like use\<YOUR_QUERY>Query. In the above example GetDemoAsset will translate into useGetDemoAssetQuery

```ts
import { useGetDemoAssetQuery } from './generated/graphql-api';

const assetId = "00000000-0000000-0000000-0000000"; // <<-- Use asset Runtime to get it

const { data, loading, error } = useGetDemoAssetQuery({
  variables: {
    assetId: assetId!,
  },
  skip: !assetId, // Allows you to skip if assetId is not defined yet
});
```



### 6. You are now ready to call GraphQL using hooks 
For more advanced info on the executor you can read up on how to generate code from [GraphQL codegen cli](https://the-guild.dev/graphql/codegen/docs/getting-started/installation)   

## Example: Full React Component (App.tsx)

```typescript
import {
  Card,
  Text,
  Spinner,
  Heading,
} from '@trackunit/react-components';
import { useGetDemoAssetQuery } from './generated/graphql-api';
import { useAssetRuntime } from '@trackunit/react-core-hooks';


export const App = () => {
  const { assetInfo } = useAssetRuntime();
  const { data, loading, error } = useGetDemoAssetQuery({
    variables: {
      assetId: assetInfo?.assetId!,
    },
    skip: !assetInfo?.assetId,
  });

  return (
    <div className="w-full h-full grid place-content-center">
    <Card className="w-full">
      {loading && <Spinner centering="centered" />}
      {error && <div>CRASHED: {error.message}</div>}
      {data && <Heading variant="primary">We can now use useGetDemoAssetQuery</Heading>}
      <Card>
        <Text>Brand: {data?.asset?.brand}</Text>
        <Text>Model: {data?.asset?.model}</Text>
      </Card>
    </Card>
  </div>
  );
};
```