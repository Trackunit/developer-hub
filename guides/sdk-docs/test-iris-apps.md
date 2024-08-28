---
title: Testing IrisX App
category: 61fcd8e1a448f5004215317c
---


We highly recommend reading through this section before you start developing your IrisX App. It will give you a good understanding of the testing effort for App SDK and how to use it.

## Testing your IrisX App

### 1. Learn about standard testing in react using the [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/).


### 2. Install the IrisX App testing contexts into your NX Workspace by executing:

```
npm i @trackunit/react-core-contexts-test
```


### 3. Start writing tests for your IrisX App. 

```
import { screen } from '@testing-library/react';
import { trackunitProviders } from '@trackunit/react-core-contexts-test';
import { App } from './app';

describe('App', () => {
  it('Should render', async () => {
    await trackunitProviders().render(<App />);
    expect(screen.getByTestId('app')).toBeDefined();
  });
});

```

### The big difference
The difference between how we test IrisX Apps and how you would normally test a React App is that we need to wrap the App in a set of providers. This is because the App SDK is using React Contexts to provide data to the App. If you wrap your test of IrisX App in the `trackunitProviders()` you will get the same data as the App SDK would provide using 
```
<TrackunitProviders><YOURAPP/></TrackunitProviders>
```

This way we can maintain an easy testing experience for you as an IrisX App developer. We can expand the providers to include more data as we expand the App SDK, without breaking any tests for you. The `trackunitProviders()` will always provide the same data as the App SDK would, so you can be sure that your tests are always up to date. Its using a [builder pattern](https://en.wikipedia.org/wiki/Builder_pattern#:~:text=The%20builder%20pattern%20is%20a,Gang%20of%20Four%20design%20patterns.) so you can override the context in your tests like mock out an graphql call or override the user context.
