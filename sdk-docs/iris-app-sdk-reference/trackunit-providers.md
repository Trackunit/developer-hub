---
title: Trackunit React Providers
category: 61fcd8e1a448f5004215317c
parentDocSlug: iris-app-sdk-reference
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice.

**Trackunit React Providers  
:** The react component is exposed using @trackunit/react-core-contexts\` package.  
The TrackunitProviders is a wrapper for all the base react providers needed to use contexts available in Trackunit Manager, making it possible to use Hooks and complex components in your Iris App SDK. 

The provider also wraps the ThemeProvider, which is currently needed for our React components.

The following hooks from `react-core-hooks` can be used inside the provider:

- **userCurrentUser Hook:** This hook will retrieve data on the current user.
- **useEnvironment Hook:** This hook will read the current environment.
- **useUserSubscription Hook:** This hook will retrieve the user's subscription package and features.
- **useToken Hook:** This hook will retrieve an access token.
