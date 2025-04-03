---
title: Sites API - Introduction
category: 63fc7f4a12fbea0327599d65
---

The Sites API is designed to facilitate the seamless creation and management of sites at scale - construction sites, depots, workplaces or other areas. This REST API empowers developers to interact with site information, including users and contacts of a site, assets on or related to a site and a site's comprehensive history.

> 📘 IrisX customers can also access data connected to Sites via the GraphQL API
> 
> Via the Public GraphQL API, you can utilize query capabilities to fetch data connected to sites. Explore the GraphQL schema through our [GraphQL Explorer](https://apps.iris.trackunit.com/graphql-public-viewer/) following the 'sites' subgraph. Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview).

## Use Cases
- Get an up-to-the-minute picture of vital activity across all of your job sites eliminating the need for ongoing manual site-level administration, whether online or in-person.
- Sites seamlessly blend live machine data with site applications to optimize your business processes, giving you a complete picture to deliver your project and business outcomes.
- Optimise integration possibilities and e.g. connect ERP data to sites to be able to drill into specific depot sites and better plan depot stock and turn around times.

## Concepts & Interface

### [Create Site endpoint](https://developers.trackunit.com/reference/createsite)
Create a site within your account. Once the site is created, you will gain the ability to see on-site assets and their historical data.

**Define a Site:**
- Address: define a site by providing the location via street, ZIP code, city and country (Note: if you omit address, it will be filled in based Google maps lookup on the center of the polygon)
- Polygon: define a site by providing an array of GPS points, where each point consists of two or three coordinates (longitude, latitude, optionally altitude)

> 💡 Advise
> 
> Having difficulties defining polygons? Use the [Site suggestion endpoint](https://developers.trackunit.com/reference/getsitesuggestion) to get automatically detected sites based on your assets' locations. The suggested sites reflect locations where your assets are or have been previously. Use the 'suggestionId' to copy a polygon from a suggestion when creating a new site.

**Types of Sites**
- *Construction site:* A temporary site where structures, buildings, or roads are constructed, as well as where existing structures may be demolished, renovated, or expanded 
- *Depot:* A storage facility for assets while they are not in use. Use this type of site for asset depots, rental yards, and rental branches
- *Workplace:* A permanent site where assets are used daily, such as warehouses or factories
- *Area:* Covers any other type of sites and should be used only for creating basic alerts
- :construction: Note: The types 'Classic Point' and 'Classic Zone' are only used for migration away from Manager Classic and cannot be provided when creating new sites.

**Status of a Site**
Start and end date will affect the status of a site:
- If the start date is set in the future, then the status shows as PLANNED
- If the end date is in the part, then the status shows as FINISHED
- Else the status is ACTIVE
- Setting the status to ARCHIVED overwrites this logic

### 


## Extending the Data Model of Sites

Missing any fields needed to define your sites perfectly? Custom fields provide a way to define new fields in the Trackunit data model. Allowing to extend and customize Trackunit Manager. Currently we support **extending the data model of assets, accounts, groups, sites, customers and rental contracts with new fields**. Learn more in the [Custom Fields API -Introduction](https://developers.trackunit.com/reference/custom-field-intro#define-your-own-custom-fields).

the data model of assets, accounts, groups, sites, customers and rental contracts with new fields\*\*.

> 📘 Subscription requirement
> 
> IrisX is required to create and change custom field definitions. Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview)

## Constraints
- 
