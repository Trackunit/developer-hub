---
title: Mocking out graphql calls
category: 61fcd8e1a448f5004215317c
parentDocSlug: test-iris-apps
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

Consider the following query that retrieves the details of an asset with a given ID:

```javascript
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

Then you can mock and test it like this:

```typescript
import { screen } from "@testing-library/dom";
import { AssetRuntime } from "@trackunit/iris-app-runtime-core";
import { queryFor, trackunitProviders } from "@trackunit/react-core-contexts-test";
import { App } from "./app";
import {
  AssetType,
  GetDemoAssetDocument,
  GetDemoAssetQuery,
  GetDemoAssetQueryVariables,
} from "./generated/graphql-api";

describe("App", () => {
  beforeEach(() => {
    jest.restoreAllMocks();
  });

  it("should show the data fetched from graphql", async () => {
    const mock = queryFor<GetDemoAssetQuery, GetDemoAssetQueryVariables>(
      GetDemoAssetDocument,
      {
        assetId: "assetId",
      },
      {
        asset: {
          id: "assetId",
          name: "name",
          model: "MODEL",
          serialNumber: "serialNumber",
          type: "type",
          brand: "Coool Brand",
          assetType: AssetType.Equipment,
        },
      }
    );

    const getAssetInfo = jest.spyOn(AssetRuntime, "getAssetInfo").mockResolvedValue({ assetId: "assetId" });

    await trackunitProviders()
      .apollo([mock])
      .render(<App />);

    expect(screen.getByText("Coool Brand")).toBeInTheDocument();
    expect(getAssetInfo).toHaveBeenCalled();
  });
});
```

Let's break the test down.
1. Notice that we imported the following libraries:
    - [@testing-library/dom](https://www.npmjs.com/package/@testing-library/dom) provides utilities involved with querying the DOM for nodes in a way that's similar to how the user finds elements on the page. In this way, the library helps ensure your tests give you confidence that your application will work when a real user uses it.

    - [@trackunit/react-core-contexts-test](https://www.npmjs.com/package/@trackunit/react-core-contexts-test) helps you mock Trackunit objects.

2. Create a `mock` object that will contain the query, variables, and result:

    ```typescript
    const mock = queryFor<GetDemoAssetQuery, GetDemoAssetQueryVariables>(
      GetDemoAssetDocument,
      {
        assetId: "assetId",
      },
      {
        asset: {
          id: "assetId",
          name: "name",
          model: "MODEL",
          serialNumber: "serialNumber",
          type: "type",
          brand: "Coool Brand",
          assetType: AssetType.Equipment,
        },
      }
    );
    ```

2. Spy on `AssetRuntime.getAssetInfo` method and resolve its value to mocked data:

    ```typescript
    const getAssetInfo = jest.spyOn(AssetRuntime, "getAssetInfo").mockResolvedValue({ assetId: "assetId" });
    ```

3. Render the `App` component and pass the `mock` object:

    ```typescript
    await trackunitProviders()
      .apollo([mock])
      .render(<App />);
    ```

4. Ensure that the mocked data is properly displayed:

    ```typescript
    expect(screen.getByText("Coool Brand")).toBeInTheDocument();
    ```

5. Ensure that the `getAssetInfo` function was called:

    ```typescript
    expect(getAssetInfo).toHaveBeenCalled();
    ```

In summary, the test ensures that:
- The GraphQL query is correctly built and can fetch the required data.
- The application correctly uses the response from the GraphQL query.
- The component correctly renders the fetched data.
- Any side effects, like calling `AssetRuntime.getAssetInfo`, happen as expected.