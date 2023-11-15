---
title: Trackunit React Providers
category: 61fcd8e1a448f5004215317c
parentDocSlug: iris-app-sdk-reference
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

**Trackunit React Providers  
:** The react component is exposed using @trackunit/react-core-contexts\` package.  
The TrackunitProviders is a wrapper for all the base react providers needed to use contexts available in Trackunit Manager, making it possible to use Hooks and complex components in your Iris App SDK. 

The provider also wraps the ThemeProvider, which is currently needed for our React components.

The following hooks from `react-core-hooks` can be used inside the provider:

- **useToken Hook:** This hook will retrieve an access token.
- **userCurrentUser Hook:** This hook will retrieve data on the current user.
- **useEnvironment Hook:** This hook will read the current environment.
- **useUserSubscription Hook:** This hook will retrieve the user's subscription package and features.
- **useHasAccessTo Hook:** This hook will check if the user has access to a specific page. 
- **useNavigateInHost Hook:** This hook will allow you to navigate to another page in the host.
- **useFilterBarContext Hook:** This hook will allow you to get the current filter bar context if filter is available on the page in the host.
- **useCustomFieldRuntimeForEntity Hook:** This hook will allow you to get the current custom field information.
- **useSiteRuntime Hook:** This hook will allow you to get the current site information if available on the page in the host.
- **useAssetRuntime Hook:** This hook will allow you to get the current asset information if available on the page in the host.
- **useToast Hook:** This hook will allow you to show a toast message in the host.