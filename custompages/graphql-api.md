---
title: GraphQL API Documentation
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

## Introduction
To create integrations and retrieve data use the GraphQL API. The GraphQL API offers more flexible queries than the TrackUnit REST API and only retrieves the data needed.

If you haven't already, it is reccommended to go through our example on how to interact with the GraphQL API using the SDK: 
- [Calling Trackunit GraphQL API using the Iris App SDK](https://developers.trackunit.com/docs/graphql-api)

If you want to call the API without using the SDK, you have to fetch your authentication token first and familiarize yourself with the available data models:
- [Obtain a token outside an Iris App](https://developers.trackunit.com/reference/access-token)
- [GraphQL Explorer and Query builder](./graphql-explorer)

Click below to download the public schema if you need it:
- [Public schema](https://apps.iris.trackunit.com/graphql-public-viewer/schema.gql)


## Types and fields
The most important datatypes are `assets` and `sites` as most other datatypes are child properties on these main ones.
> 📘 Nice to know
>
> Some fields are in a preview state and may change without notice.<br>
> To indicate you accept these terms pass the HTTP header `TU-PREVIEW: <codeword>` with your query requests.<br>
> The codeword differs for each preview field and you can find it by looking in the GQL schema above.

### Assets
An Asset represents the machines and equipment that have our sensors attached to them.
| Field             | Type                        | Description                                               | Is Preview? |
|-------------------|-----------------------------|-----------------------------------------------------------|------------------|
| advancedSensors   | AdvancedSensors             | Raw sensor data that only people with "advanced" knowledge of it can understand it.                     | Yes              |
| assetId           | ID!                         | Asset Entity ID.                                          | No               |
| assetType         | AssetType!                  | The primary categorization of the asset.<br>Availble types: ATTACHMENT, EQUIPMENT, GATEWAY, MACHINE, TOOL, OTHER.             | No               |
| brand             | String                      | The brand of the asset.                                   | No               |
| createdAt         | DateTime                    | When the asset was created.                               | No               |
| customFields      | CustomFieldValueAndDefinition | The [custom fields](https://developers.trackunit.com/docs/save-data-from-your-app) for the asset.                        | Yes              |
| editable          | Boolean                     | Indicates whether the asset's specification can be edited.      | No               |
| event             | EventDomain                 |                                              | No               |
| events            | EventList                   |                                               | No               |
| externalReference | String                      |                      | No               |
| followed          | Boolean                     |                          | No               |
| id                | ID!                         | Globally unique ID for Asset.                             | No               |
| image             | imageInputImage             | The id and url of the asset image.                        | No               |
| insights          | Insights                    | The insights of the asset.                                | Yes              |
| locations         | Locations                   | The locations of the asset.                               | No               |
| model             | String                      | The model type of the asset.                              | No               |
| name              | String!                     | The customer assigned name of the Asset.                  | No               |
| ownerAccount      | Account                     | The owner account of the asset.                           | No               |
| productionYear    | Int                         | The production year of the asset.                         | No               |
| relations         | AssetRelations              | The asset's relations in reference to ownership and visibility. | No        |
| score             | Int                         | The percentage showing how much of the metadata information is filled up for the asset. | No |
| serialNumber      | String                      | The asset serial number (VIN/PIN).                        | No               |
| servicePlans      | ServicePlan               | The service plans information for the asset.              | No               |
| status            | AssetStates                 | Describes an assets so-called `activity` and `criticality` states. Which indicates in how good shape it is and whether the asset is idling, working, etc.                       | No               |
| telematicsDevices | TelematicsDevice         | The serial numbers of the telematics devices attached to the asset.         | No               |
| type              | String                      |                  | No               |

<br><br>

### Sites
| Field              | Type                                      | Description                                                                                               | Is Preview? |
| ------------------ | ----------------------------------------- | --------------------------------------------------------------------------------------------------------- | ----------- |
| area               | Float                                     | Area in square meters                                                                                     | No          |
| assets             | Asset                                     | Get all assets for this site that are currently on site                                                   | No          |
| center             | Coordinates!                              | The center of the polygon for the site                                                                    | No          |
| city               | String                                    | The city that this site is currently located in                                                           | No          |
| contactInformation | SiteContact                               | Contact information for the person responsible for this site                                              | No          |
| country            | String                                    | The country that this site is currently located in                                                        | No          |
| customFields       | CustomFieldValueAndDefinition             | The [custom fields](https://developers.trackunit.com/docs/save-data-from-your-app) for the site.          | Yes          |
| description        | String                                    | The site's description                                                                                    | No          |
| endDate            | DateTime                                  | The site's end date                                                                                       | No          |
| id                 | ID!                                       | Globally unique ID for Site                                                                               | No          |
| name               | String!                                   | Name of the site                                                                                          | No          |
| polygon            | Coordinates!!                             | The polygon for the site. List contains all the geo coordinates defining it                               | No          |
| siteId             | ID!                                       | Site Entity ID                                                                                            | No          |
| startDate          | DateTime!                                 | The site's start date                                                                                     | No          |
| status             | SiteStatus                                | The site's status                                                                                         | No          |
| streetAddress      | String                                    | The street address that this site is currently located in                                                 | No          |
| timeZoneId         | String                                    | The time zone that this site is currently located in. TZ format (ex: Europe/Copenhagen)                   | No          |
| type               | SiteType!                                 | The site's type                                                                                           | No          |
| users              | SiteUser                                  | The users for a site                                                                                        | No          |
| zipCode            | String                                    | The zip code that this site is currently located in                                                       | No          |
