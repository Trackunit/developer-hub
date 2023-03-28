---
title: Installing Iris App Runtime in an Iris App Extension 
category: 61fcd8e1a448f5004215317c
parentDocSlug: guides-tutorials
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice.

To use Trackunit APIs and integrating with the manager to get information on current asset you need to install the Iris App Runtime. The Iris App Runtime is the interface to the manager from your app.

- Open a Terminal or Command window and enter the Iris App Runtime command  to install Iris App Runtime.

```
npm i @trackunit/iris-app-runtime-core
```



Then you can import the runtime in your `app.tsx`:

```typescript
import * as runtime from '@trackunit/iris-app-runtime-core';
```



And for example ask the manager who the current user is:

```typescript
const userInfo = await runtime.CurrentUserRuntime.getCurrentUserContext();
```
