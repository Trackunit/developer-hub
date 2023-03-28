---
title: Example: Extension Manifest
category: 61fcd8e1a448f5004215317c
parentDocSlug: examples
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

```ts
import { ReportExtensionManifest } from '@trackunit/iris-app-api';

const extensionManifest: ReportExtensionManifest = {
  id: 'your-report-id-extension',
  type: 'REPORT_EXTENSION',
  main: '<path-to-report-in-jasper>',
  
};

export default extensionManifest;

```
