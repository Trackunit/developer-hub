---
title: Location API - Introduction
category: 6453af734f393c01aee97223
---
Discover the power of our Location API, your key to effortlessly accessing and tracking real-time GPS coordinates for your entire fleet of connected assets. 
With two convenient endpoints at your disposal, you can choose to retrieve precise location snapshots for a specific asset or access a paginated list containing all your assets.
Perfect to sync latest asset location data to any other system.

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
