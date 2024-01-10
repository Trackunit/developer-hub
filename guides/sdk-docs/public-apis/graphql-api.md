---
title: Calling Trackunit GraphQL API
category: 61fcd8e1a448f5004215317c
parentDocSlug: public-apis
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

Trackunit exposes a [GraphQL API](/reference/graphql-api-introduction) to create your query and we also expose an NX executor to make it easy to query our GraphQL API inside your Iris App extension.

# Query walkthrough

In this example, we will use a Query for asset information.  

## 1. Open a Terminal or Command Window and enter: 

```
npm install @trackunit/react-graphql-tools
```



## 2. Add "graphql-hooks" to targets
Assuming you have already created an extension - go to the root of that project (like `libs/[feature-name]/[name-of-your-extension]/`) otherwise follow [this guide](creating-a-new-extension) and open the `project.json` and add to the targets node:

```typescript
    "graphql-hooks": {
      "executor": "@trackunit/react-graphql-tools:createHooks"
    },
```

## 3. Add "codegen.ts" to lib
Now go to the root of that project (like `libs/[feature-name]/[name-of-your-extension]/`) and create a file called `codegen.ts` and add this code to it:

```typescript
import { type CodegenConfig } from "@graphql-codegen/cli";
import { getGraphqlCodegenConfig } from "@trackunit/iris-app-build-utilities";

const config: CodegenConfig = {
  ...getGraphqlCodegenConfig(__dirname),
};
export default config;
```


## 4. Create Graphql Query 
Now you are ready to create React hooks from your GraphQL queries, just copy your query or the below query to your src folder in the `libs/[feature-name]/[name-of-your-extension]/src` and name it `demo.graphql`.

```graphql
query GetAssetsByProductionYear($first: Int, $productionYears: [String!]) {
  assets(first: $first, filters: {productionYears: $productionYears}) {
    payload {
      productionYear
      model
      brand
    }
  }
}
```

## 5. Generate React Hooks
Call this command:
```sh
nx run [feature-name]-[name-of-your-extension]:graphql-hooks
```

## 6. Use it in your React code 
Now that it has generated a folder with generated files in your src folder you can use it in your React code. The syntax takes the form `<YOUR_QUERY>Document`.
In the above example `GetAssetsByProductionYear` will translate into `GetAssetsByProductionYearDocument`

```typescript
import { useQuery } from "@apollo/client";
import { GetAssetsByProductionYearDocument } from './generated/graphql-api/graphql';

const { data, loading, error } = useQuery(GetAssetsByProductionYearDocument, {
  variables: {
    // Any variables your query requires
  },
});
```



## 7. You are now ready to call GraphQL using hooks 
For more advanced info on the executor you can read up on how to generate code from [GraphQL codegen cli](https://the-guild.dev/graphql/codegen/docs/getting-started/installation)   

More information about the `useQuery` hook is available in [the Apollo React Client docs](https://www.apollographql.com/docs/react/data/queries).


# Mutations

The process for mutation is similar. 

## 1. Add mutation to .graphql file 

You should start with adding a mutation to the `demo.graphql` created above.

```graphql
mutation MyMutation($eventId: String!) {
  eventDismiss(eventId: $eventId) {
    success
  }
}
```

## 2. Generate React Hooks
Call this command:
```sh
nx run [feature-name]-[name-of-your-extension]:graphql-hooks
```

## 3. Use it in your React code 
Now that it has updated the generated files in your src folder you can use it in your React code. The syntax takes the form `<YOUR_MUTATION>Document`.
In the above example `MyMutation` will translate into `MyMutationDocument`

```typescript
import { useMutation } from "@apollo/client";
import { GetAssetsByProductionYearDocument } from './generated/graphql-api/graphql';

const [myMutation, { data, loading, error }] = useMutation(MyMutationDocument);

// Use mutation function to call the mutation
myMutation({
  variables: {
    eventId: "foo"
  }
});

// Use data, loading and error same way as for the query
```

More information about the `useMutation` hook is available in [the Apollo React Client docs](https://www.apollographql.com/docs/react/data/mutations).

# Preview features

Some part of the public graph are tagged with a `@preview` directive to indicate they are still under development and may change.

To call a preview query you will need to include `TU-PREVIEW` header like this:

```typescript
const { data, loading, error } = useQuery(GetAssetsByProductionYearDocument, {
  variables: {
    // Any variables your query requires
  },
  context: { 
    headers: {
      "TU-PREVIEW": "<FEATURE-CODE-NAME>" // Look up the feature code name in the schema docs.
    }
  },
});
```

You may look up the feature code name in the [GraphQL Explorer](https://apps.iris.trackunit.com/graphql-public-viewer/).

> 🚧 Do not use preview features in production. 
> 
> Preview feature may change without notice. So do not include them in critical code.

# Example: Full React Component (App.tsx)

```typescript
import { useQuery } from "@apollo/client";
import {
  Card,
  Text,
  Spinner,
  Heading,
} from '@trackunit/react-components';
import { GetAssetsByProductionYearDocument } from './generated/graphql-api/graphql';


export const App = () => {
 const { data, loading, error } = useQuery(GetAssetsByProductionYearDocument, {
    variables: {
     first: 5, // Take first 5 results
     productionYears: ["2017", "2023"] // Filter by these production years
    },
    // skip: <some_assetId>,
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
        {data && 
          <div>
            <Heading variant="primary">We can now use useGetAssetsByProductionYearQuery</Heading>
            {data?.assets?.payload?.map((asset, index) => (
              <Card key={index}>
                <Text>Brand: {asset.brand}</Text>
                <Text>Model: {asset.model}</Text>
                <Text>Year: {asset.productionYear}</Text>
              </Card>
            ))}
          </div>
        }
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
The specific codeword varies for each preview object and can be found by referring to the [GraphQL Explorer](https://apps.iris.trackunit.com/graphql-public-viewer/).
You can include one or more comma-separated codewords.