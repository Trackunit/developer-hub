---
title: Extension Point Types
category: 61fcd8e1a448f5004215317c
parentDocSlug: iris-app-sdk-reference
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice.

# Asset Home Extension Point

This extension point allows you to add a new tab to the Assets Home screen within Trackunit Manager, as illustrated in the image below. The extension is controlled in the extension-manifest.ts file.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9a8920c-b40d70a-AssetHomeTile.svg",
        "b40d70a-AssetHomeTile.svg",
        ""
      ],
      "align": "center",
      "sizing": "50% "
    }
  ]
}
[/block]



- **Menu Item:**

```ts
menuItem: {
  name: 'Specification'
}
```



- **Visibility of Menu Item:**
  - Visibility is controlled using conditions. The Asset's Brand and Model fields must match the Brand and Model entered within the code.

```ts
conditions: {
  brand: "your-brand", // optional as single or array
  model: ["your model", "your model2"] // optional as single or array
}
```



# Fleet Wide Extension Point

This extension point allows you to add a new tab to the tiles list on the Main Menu within Trackunit Manager, as illustrated in the image below. The extension is controlled in the extension-manifest.ts file.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/58910f3-07990a8-FleetTile.svg",
        "07990a8-FleetTile.svg",
        ""
      ],
      "align": "center",
      "sizing": "50% "
    }
  ]
}
[/block]



- **Menu Item:**

```ts
menuItem: {
  name: 'Fleet Inventory',
  icon: 'AnalyticsPie1Bold',
}
```



# Report Extension Point

The Report Extension Point allows you to add a new Report Tile on the Reports screen within Trackunit Manager. The extension is controlled in the extension-manifest.ts file.

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

This extension point allows you to add an configuration user interface for your app in the App library.

# Admin settings extension point

This extension point allows you to add a new tab in the administration user interface.
