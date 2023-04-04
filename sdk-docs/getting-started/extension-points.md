---
title: Extension Point Types
category: 61fcd8e1a448f5004215317c
parentDocSlug: iris-app-sdk-reference
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

An Iris App is a collection of a number of extensions. 

![](https://files.readme.io/a4ab2cf-image.png)

The Iris App SDK provides these extension points in the manager. 

# Asset Home Extension Point

This extension point allows you to add a new tab to the Assets Home screen within Trackunit Manager, as illustrated in the image below. The extension is controlled in the extension-manifest.ts file.

![Asset home extension](https://cdn.statically.io/gh/trackunit/developer-hub/master/sdk-docs/extension_to_asset_home.png)

## Menu Item

```ts
menuItem: {
  name: 'Specification'
}
```

### Visibility
Visibility is controlled using conditions. The Asset's Brand and Model fields must match the Brand and Model entered within the code.

```ts
conditions: {
  brand: "your-brand", // optional as single or array
  model: ["your model", "your model2"] // optional as single or array
}
```


# Site Home Extension Point

This extension point allows you to add a new tab to the Site Home screen within Trackunit Manager, as illustrated in the image below. The extension is controlled in the extension-manifest.ts file.

![Site home extension](https://cdn.statically.io/gh/Trackunit/developer-hub/master/sdk-docs/extension_to_site.png)


# Fleet Wide Extension Point

This extension point allows you to add a new tab to the tiles list on the Main Menu within Trackunit Manager, as illustrated in the image below. The extension is controlled in the extension-manifest.ts file.

![Fleet wide extension](https://cdn.statically.io/gh/Trackunit/developer-hub/master/sdk-docs/extension_to_navbar.png)



## Menu Item

```ts
menuItem: {
  name: 'Fleet Inventory',
  icon: 'AnalyticsPie1Bold',
}
```

The `icon` field allows you to select the icon used in the navigation bar. See the Icon component in our [UI Component Library](https://developers.trackunit.com/page/ui-components) for an overview of supported icons.

# Report Extension Point

The Report Extension Point allows you to add a new report to the Reports screen within Trackunit Manager. The extension is controlled in the extension-manifest.ts file.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7c40e14-7041c70-ReportTile.svg",
        "7041c70-ReportTile.svg",
        ""
      ],
      "align": "center",
      "sizing": "50% "
    }
  ]
}
[/block]


# App settings extension point

This extension point allows you to add a configuration user interface for your app in the App library. After a user installs an app he will be guided to the app library, so this is the perfect place to add an extension if your app requires configuration.

# Administration extension point

This extension point allows you to add a new tab in the administration user interface. It will only be visible to users in the Administrator role.
