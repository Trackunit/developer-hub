---
title: Mocking out graphql calls
category: 61fcd8e1a448f5004215317c
parentDocSlug: testing-iris-apps
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

If you need to mock out graphql calls you can do it like this, lets say you are using a graphql call like this:
```
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

Then you can mock it out like this:

```
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