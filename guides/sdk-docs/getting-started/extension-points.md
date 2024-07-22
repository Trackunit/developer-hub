---
title: Extension Point Types
category: 61fcd8e1a448f5004215317c
parentDocSlug: getting-started
---

> 🚧 Beta
>
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

An Iris App is a collection of a number of extensions.

[block:image]
{
  "images": [
    {
      "image": [
        "https://cdn.statically.io/gh/trackunit/developer-hub/master/iris%20app.png",
        null,
        "Asset home extension"
      ],
      "align": "center",
      "sizing": "50% "
    }
  ]
}
[/block]

The Iris App SDK provides these extension points in the manager.

# Asset Home Extension Point

This extension point allows you to add a new tab to the Assets Home screen within Trackunit Manager, as illustrated in the image below. The extension is controlled in the extension-manifest.ts file.

[block:image]
{
  "images": [
    {
      "image": [
        "https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/sdk-docs/extension_to_asset_home.png",
        null,
        "Asset home extension"
      ],
      "align": "center",
      "sizing": "50% "
    }
  ]
}
[/block]

## Menu Item

```ts
menuItem: {
  name: "Specification";
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

[block:image]
{
  "images": [
    {
      "image": [
        "https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/sdk-docs/extension_to_site.png",
        null,
        "Site home extension"
      ],
      "align": "center",
      "sizing": "50% "
    }
  ]
}
[/block]

# Fleet Wide Extension Point

This extension point allows you to add a new tab to the tiles list on the Main Menu within Trackunit Manager, as illustrated in the image below. The extension is controlled in the extension-manifest.ts file.

[block:image]
{
  "images": [
    {
      "image": [
        "https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/sdk-docs/extension_to_navbar.png",
        null,
        "Fleet wide extension"
      ],
      "align": "center",
      "sizing": "50% "
    }
  ]
}
[/block]

## Menu Item

```ts
menuItem: {
  name: 'Fleet Inventory',
  icon: 'AnalyticsPie1Bold',
}
```

The `icon` field allows you to select the icon used in the navigation bar. See the Icon component in our [UI Components](https://apps.iris.trackunit.com/storybook/) Library for an overview of supported icons.

### Visibility

Visibility is controlled using conditions. If Brand and Model fields are filled out they must match at least one asset in the fleet for the menu item to show.

```ts
conditions: {
  brand: "your-brand", // optional as single or array
  model: ["your model", "your model2"] // optional as single or array
}
```

# Report Extension Point

The Report Extension Point allows you to add a new report to the Reports screen within Trackunit Manager. The extension is controlled in the extension-manifest.ts file.

[block:image]
{
  "images": [
    {
      "image": [
        "https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/sdk-docs/extension_reports.png",
        null,
        "Report extension"
      ],
      "align": "center",
      "sizing": "50% "
    }
  ]
}
[/block]

# App Settings Extension Point

This extension point allows you to add a configuration user interface for your app in the App library. After a user installs an app he will be guided to the app library, so this is the perfect place to add an extension if your app requires configuration.

[block:image]
{
  "images": [
    {
      "image": [
        "https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/sdk-docs/extension_settings.png",
        null,
        "App settings extension"
      ],
      "align": "center",
      "sizing": "50% "
    }
  ]
}
[/block]

# Administration Extension Point

This extension point allows you to add a new tab in the administration user interface. It will only be visible to users in the Administrator role.

[block:image]
{
  "images": [
    {
      "image": [
        "https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/sdk-docs/extension_administration.png",
        null,
        "Administration extension"
      ],
      "align": "center",
      "sizing": "50% "
    }
  ]
}
[/block]

# Widget Extension Point

This extension point allows you to add a widget to Trackunit Manager.

## Header

The widget has an header which should be filled out such that users know what widget it is.

```ts
header: {
  name: "Mixer widget",
  icon: "ConcreteMixer",
},
```

## Widget size

It is possible to control the widget size by specifying grid options:

```ts
gridOptions: {
  minH: 2,
  minW: 1,
  maxH: 2,
  maxW: 4,
}
```

# Asset Events Actions Extension Point

This extension point allows you to add a user interface in the Events within Asset Home in Trackunit Manager. The extension is controlled in the extension-manifest.ts file.

## Menu Item

```ts
menuItem: {
  name: "Specification";
}
```

### Visibility

Visibility is controlled using conditions. The Event's Type must match the Type entered within the code.

```ts
conditions:{
  eventType: "event-type",
}
```
