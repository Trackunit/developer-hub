---
title: Maintaining Your Application
category: 61fcd8e1a448f5004215317c
parentDocSlug: iris-app-sdk-reference
---

> 🚧 Beta
> 
> Please note that this is a beta version and is subject to change without notice. The final version may include changes to pricing, terms, conditions, and availability.

### Security Patching
As a developer, it is essential to keep your application and its dependencies up-to-date, ensuring that there are no vulnerabilities. With each update, you should bump the version number and submit it for review. Our team will manually review and approve each patch, ensuring the safety and stability of the platform. We are continiously scanning apps on the platform for vulnurabilities and not upgrading your app can cause it to be disabled.

### Upgrading SDK Packages
We will periodically release updates for our SDK libraries. It is crucial to keep your applications using the latest versions to maintain compatibility as our platform evolves. You may receive a warning in the terminal when publishing your app if your SDK is outdated. While you can initially ignore this warning, outdated SDK versions may eventually result in your app not being approved or even removed from the platform.

### Updating Your Nx Workspace
The SDK relies on specific Nx and Node.js versions. Ensure that your application complies with the required versions at all times. Do *not* update your Nx workspace immediately when a new Nx version is released. Instead, only upgrade when our SDKs depend on a newer version. If in doubt, refer to the [prerequisites](hhttps://developers.trackunit.com/docs/prerequisites) page.
It will be updated whenever our packages depend on new Nx and Node versions. Warnings in your terminal will also notify you that your app is using the wrong versions.

[Migrating](https://nx.dev/packages/nx/documents/migrate) an existing Nx workspace to a new version may not be a straightforward process.
The migration may require manual intervention, such as deleting, moving, renaming, or creating certain files.
The migration process depends on the Nx team's implementation. Sometimes they provide a tool that automatically migrates older versions
to newer ones, while other times you may need to take additional steps.
Always follow the provided guidelines and best practices for a smooth migration experience.

For more information on how to migrate an Nx workspace see Nx's own guide: [Manual migration of existing code bases](https://nx.dev/recipes/adopting-nx/manual)
