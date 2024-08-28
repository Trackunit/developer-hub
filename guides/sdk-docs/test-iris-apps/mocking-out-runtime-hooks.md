---
title: Mocking out runtime hooks
category: 61fcd8e1a448f5004215317c
parentDocSlug: test-iris-apps
---




If you need to mock out runtimes you can do it like this, lets say you are using our hook `useAssetRuntime()` in your Iris App extension.
Then you can mock it out like this:

```typescript
import { screen } from '@testing-library/react';
import { trackunitProviders } from '@trackunit/react-core-contexts-test';
import { App } from './app';

describe('App', () => {
  beforeEach(() => {
    jest.restoreAllMocks(); // this ensures that we are not using any mocks from other tests
  });

  it('Should render', async () => {
    const getAssetInfo = jest.spyOn(AssetRuntime, "getAssetInfo").mockResolvedValue({ assetId: "assetId" });

    await trackunitProviders().render(<App />);

    expect(getAssetInfo).toHaveBeenCalled();
  });
});
```