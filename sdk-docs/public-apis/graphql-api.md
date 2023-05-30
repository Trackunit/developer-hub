---
title: Calling Trackunit GraphQL API
category: 61fcd8e1a448f5004215317c
parentDocSlug: public-apis
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

Trackunit exposes a [GraphQL API](/page/graphql-api) to create your query and we also expose an NX executor to make it easy to query our GraphQL API inside your Iris App extension.

In this example, we will use a Query for asset information.  

### 1. Open a Terminal or Command Window and enter: 

```
npm install @trackunit/react-graphql-tools
```



### 2. Add "graphql-hooks" to targets
Assuming you have already created an extension - go to the root of that project (like libs/[feature-name]/[name-of-your-extension]/ ) otherwise follow [this guide](creating-a-new-extension) and open the `project.json` and add to the targets node:

```ts
    "graphql-hooks": {
      "executor": "@trackunit/react-graphql-tools:createHooks"
    },
```



### 3. Create Graphql Query 
Now you are ready to create React hooks from your GraphQL queries, just copy your query or the below query to your src folder in the libs/[feature-name]/[name-of-your-extension]/src and name it demo.graphql

```Text Graphql
query GetFirstAsset {
  assets(first: 1) {
    edges {
      node {
        id
        model
        brand
      }
    }
  }
}
```



### 4. Generate React Hooks
Call this command:
```ts
nx run [feature-name]-[name-of-your-extension]:graphql-hooks
```



### 5. Use it in your React code 
Now that it has generated a folder with generated files in your src folder you can use it in your React code. The syntax is like use\<YOUR_QUERY>Query. In the above example GetFirstAsset will translate into useGetFirstAssetQuery

```ts
import { useGetFirstAssetQuery } from './generated/graphql-api';

const { data, loading, error } = useGetFirstAssetQuery({
  variables: {
    // Any variables your query requires
  },
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
import { useGetFirstAssetQuery } from './generated/graphql-api';


export const App = () => {
  const { data, loading, error } = useGetFirstAssetQuery({
    variables: {
      // Any variables your query requires
    },
    // skip: !assetInfo?.assetId,
    context: {
      headers: { // Your http-headers here
        //"TU-PREVIEW": "TIME-EXCAVATORS,JUNGLE-DIGGER", // enables speicifc properties that are in preview only
      },
    },
  });

  return (
    <div className="w-full h-full grid place-content-center">
    <Card className="w-full">
      {loading && <Spinner centering="centered" />}
      {error && <div>CRASHED: {error.message}</div>}
      {data && <Heading variant="primary">We can now use useGetFirstAssetQuery</Heading>}
      <Card>
        <Text>Brand: {data?.assets.edges[0].node.brand}</Text>
        <Text>Model: {data?.assets.edges[0].node.model}</Text>
      </Card>
    </Card>
  </div>
  );
};
```
<br>

> 📘 Nice to know
>
> The generated `graphql-hooks` employ the [Apollo library](https://www.apollographql.com/) to interact with the GraphqlAPI. In addition to the options demonstrated in the above example, such as `variables`, `skip`, and `context`, there exist various other options. You can find a comprehensive list of these options in the [Apollo Docs](https://www.apollographql.com/docs/react/api/react/hooks/#params-3).

<br>

> 📘 Nice to know 2!
>
> In the complete example mentioned above, we have commented out the HTTP header `TU-PREVIEW:<codeword(s)>`.
Certain GraphQL objects are currently in a preview state and may undergo changes without prior notice.
To indicate your acceptance of these terms, include the HTTP header `TU-PREVIEW:<codeword(s)>` in your query requests.
The specific codeword varies for each preview object and can be found by referring to the [GraphQL Explorer](https://developers.trackunit.com/page/graphql-explorer).
You can include one or more comma-separated codewords.