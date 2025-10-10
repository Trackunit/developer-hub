---
title: Location API - Introduction
category:
  uri: /branches/1.0/categories/reference/Locations
---
Discover the power of our Location API, your key to effortlessly accessing and tracking real-time GPS coordinates for your entire fleet of connected assets.
With two convenient endpoints at your disposal, you can choose to retrieve precise location snapshots for a specific asset or access a paginated list containing all your assets.
Perfect to sync latest asset location data to any other system.

> 📘 IrisX customers can also access location data for an Asset via the GraphQL API
>
> Via the Public GraphQL API, you can utilize query capabilities to fetch 'location' data together with other asset data in one API call. Explore the GraphQL schema through our [GraphQL Explorer](https://apps.iris.trackunit.com/graphql-public-viewer/). Follow the 'asset' entry point and select 'locations'. Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview).

This API delivers location data in the [GeoJson](https://geojson.org/) format and the Geometry type is chosen to always be `point`, which serves the coordinates.
The `coordinates` array consists of two or three coordinates, in fixed order: longitude, latitude, optionally altitude:
- First: longitude value in range -180.0 to 180.0
- Second: latitude value in range -90.0 to 90.0
- Third: elevation in meters above mean sea level (not available for assets with Bluetooth tags)

Additionally location properties provide meta data including:
- `accuracy`: Accuracy of the GPS location in radial meters
- `heading`: Heading of the asset (not available for assets with Bluetooth tags)
- `locationAddress`: Consists of street, zip code, city and country
- `speed`: Speed of the asset, km/h (not available for assets with Bluetooth tags)
- `updatedAt`: Date and time when the location was registered

If you are interested in fetching historical location data for a certain asset, then check out the [location time-series endpoint of our Export ISO 15143-3 / AEMP 2.0](https://developers.trackunit.com/reference/getlocationtimeseries).

### Rate Limiting
To get more information about rate limiting see [Rate & Size Limiting](https://developers.trackunit.com/reference/rate-limit).
* [Get locations](https://developers.trackunit.com/reference/getlocations) - one request per second for specific page and user
* [Get location](https://developers.trackunit.com/reference/getlocation) - one request per second for specific asset id and user
