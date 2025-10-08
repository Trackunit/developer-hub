---
title: Maintaining Your Application
category:
  uri: "/branches/1.0/categories/guides/Apps & Extensions"
parent:
  uri: iris-app-sdk-reference
---

### Security Patching

As a developer, it is essential to keep your application and its dependencies up-to-date, ensuring that there are no vulnerabilities. With each update, you should bump the version number and submit it for review. Our team will manually review and approve each update, ensuring the safety and stability of the platform. We are continiously scanning apps on the platform for vulnurabilities and not upgrading your app can cause it to be disabled.

### Upgrading SDK Packages

We will periodically release updates for our SDK libraries. It is crucial to keep your applications using the latest versions to maintain compatibility as our platform evolves. You may receive a warning in the terminal when submitting your app if your SDK is outdated. While you can initially ignore this warning, outdated SDK versions may eventually result in your app not being approved or even removed from the platform.

### Updating Your Nx Workspace

The SDK relies on specific Nx and Node.js versions. Ensure that your application complies with the required versions at all times. Do _not_ update your Nx workspace immediately when a new Nx version is released. Instead, only upgrade when our SDKs depend on a newer version. If in doubt, refer to the [prerequisites](https://developers.trackunit.com/docs/prerequisites) page.
It will be updated whenever our packages depend on new Nx and Node versions. Warnings in your terminal will also notify you that your app is using the wrong versions.

Migrating an existing Nx workspace to a new version is relatively simple as long as you follow our guidelines and their best-practices when working with Nx.

For more information on how to migrate an Nx workspace refer to the official [NX documentation](https://nx.dev/features/automate-updating-dependencies) and the [nx migrate](https://nx.dev/nx-api/nx/documents/migrate#examples) command.
