---
title: trackunit/filters-filter-bar v1.7.90 - Filter URL Synchronization
type: improved
---

## Filter URL Synchronization

Filter states are now automatically synchronized with URL parameters, allowing users to bookmark or share filtered views. When filters are applied, the URL updates to reflect the current filter state, and the filters are restored when navigating back to that URL.

### Breaking Change

**TanStack Router is now required** for Iris app extensions using the filter bar. 

Your app entry point must be wrapped with TanStack Router's `RouterProvider`. See the [iris-app-with-router-example](https://github.com/csk-trackunit/iris-app-with-router-example/blob/main/libs/context-test/src/index.tsx) for a complete implementation example showing how to set up the router in your Iris app extension.
