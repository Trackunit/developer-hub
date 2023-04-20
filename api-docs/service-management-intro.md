---
title: Service Management Introduction
category: 624ebf4c9f55f70565968067
---
Our Service Management API provides a list of APIs enabling service providers and machine owners in maintaining the service cycle of assets.

![](https://cdn.statically.io/gh/Trackunit/developer-hub/tree/SM-1631/api-docs/service-management-intro-wheel-of-service.jpg "Wheel of service.jpg")

The document is intended for developers, who wants to integrate systems, write client libraries or other interactions on an API-level.

> 📘 Available with the Service Management app
>
> This API is available for customers that has acquired a license for the Service Management capability.

## Interface

The API expose an OpenAPI JSON REST interface that you can call directly using your OAuth 2.0 access token. See [Access IRIS APIs](../reference/access-token) for further details on how to obtain an access token.

## Concepts

Service Management is built on the following concepts

- An **asset** is a trackable piece of equipment e.g. a machine or an accessory.
- A **service plan** is a collection of **planned services**, which defines the criteria for service intervals e.g. based on operating hours.
    - A **service plan** is assignable to an **asset**.
    - A **service plan** is owned by the creating account.
    - A **service plan** is assignable by the **service plan** owner and if assigned, visible to the **asset owner**.
    - A **service plan** can be shared with other accounts by using a **service network**.
    - A **service plan** can be published for a specific brand and model, making the service plan available to the **asset owner** when matching brand and model of an owned **asset**.
- A **service provider** is capable of carrying out **asset** services. The **service provider** is an account and defined by the account's id. A **service provider** is assignable to an **asset** in conjunction with a **service plan**.
- The **service network** forms a network of **service plans** assignable to assets, and **service providers** capable of carrying out services on the **assets**.
    - The **service network**'s owner can add and remove both the **service providers** and **service plans** within the network, and thereby granting the **service provider** access to servicing **assets** under an assigned **service plan**.
- An **overlay** can be applied to a **service plan** within a **service network** by a **service provider** to override the **service plan**'s warning thresholds. Only **assets** having both the **service plan** and the **service provider** will be affect by the overlay.

Workflow operations

- **Service plan assignment** forms a link between a **service plan**, a **service provider** and an **asset**. The **service plan** dictates when services should be performed for the **asset**. The **service provider** is responsible for performing services on the **asset**. Multiple **service plans** can be assigned to an **asset**.
- The **service plan** is activated for an **asset** when both **service plan** and **service provider** have been assigned.
- Pending (overdue or upcoming) services are resolved or cleared by a **service registration**, which marks pending services as performed or skipped at the time of registration. The **service registration** marks individual services performed. A **service registration** can also be used to register a service performed outside the schedule service window.

Constraints

- Visibility of an assigned service plan is always limited to the asset visibility and is defined as
    - **Service plans** are visible to **asset owner** and **service plan owner**.
    - **Service plans** within a **service network** are visible to the **network owner** and **service providers** within the network.
    - A **service provider** is removed from a **service plan assignment** if the service provider's **asset** visibility is revoked and not restored with 4 hours.
- There can only be one **service provider** assigned to an asset per **service plan assignment**.
- An account can create any number of **service networks**. The creating account of the **service network** will be the network owner.
- An account can only assign itself as **service provider**.
- A public **service plan** can be assigned and provided for by the **asset owner** if the public **service plan** is not assigned and provided for by an other **service provider**.

[block:image]
{
"images": [
{
"image": [
"https://cdn.statically.io/gh/Trackunit/developer-hub/tree/SM-1631/api-docs/service-management-intro-service-mgmt-domain.png",
"service mgmt domain.png",
1424
],
"align": "center",
"caption": "Relationship between concepts"
}
]
}
[/block]

## Basic steps

Try it out using the following basic steps

## 1. Enable Service Management

Contact us to acquire a license for the Service Management capability. Your service network will be created during enablement. You can decide which of your accounts should be part of your network. The service network owner must be hierarchically above your service providing accounts as shown in the figure below. After enablement all service providers will have access to the Service Management app within Manager.

![](https://cdn.statically.io/gh/Trackunit/developer-hub/tree/SM-1631/service-management-intro-service-provider-network-illustration.jpg "Service Provider Network Illustration.jpg")

## 2. Add a service plan

Visit the Manager application to create a service plan.

Locate the Service Management app and navigate to Configuration and then "Manage Service Plans" tab.

Create a new service plan by clicking "Create service plan" in the top right corner of the "Manage Service Plans" tab.

Fill in the name of your service plan and add one or more services by clicking "Add service" located in the bottom right corner of the tile. Afterwards create it by clicking "Create".

## 3. Assign service plan & service provider

Now it's time to use the Service Management API.

For this step you will need an API token. If you don't have one then follow the our [Access IRIS APIs](../reference/access-token) guide to obtain one.

Locate your newly created service plan by getting available service plans from **/plans**

```curl
curl --location --request GET 'https://iris.trackunit.com/api/service-management/v2/plans' \
--header 'Authorization: Bearer <<YOUR_TOKEN>>'
```



Verify the response body contains the service plan you just created in the Manager application.

```json
{
    "servicePlans": [
        {
            "id": "3f3543f7-9c58-4d6c-8c67-ce48349bc46d",
            "metadata": {
                "createdAt": "2021-08-25T19:55:34.879147Z",
                "updatedAt": "2021-08-25T19:55:34.879147Z"
            },
            "plannedServices": [
                {
                    "id": "97e7ac2d-59e7-4559-909b-56ff68eba616",
                    "serviceCriteria": {
                        "distanceCriteria": null,
                        "timeIntervalCriteria": null,
                        "cumulativeOperatingHoursCriteria": {
                            "id": "ca618f3a-08f2-4694-aa55-4106afb2333b",
                            "notifyHoursBefore": 50,
                            "serviceHours": 500
                        }
                    },
                    "recurrent": true,
                    "offset": false
                }
            ],
            "name": "My first service plan",
            "isPublic": false
        }
  ]
}
```



Assign the service plan to one of your assets. Capture the id of the service plan you want to assign from the response listing your service plans - in the example above the id is **3f3543f7-9c58-4d6c-8c67-ce48349bc46d**. Also locate the id of the asset you want to assign your service plan to.

You can locate the id of your asset by getting a list of your machines from the [Asset API](../reference/getassets).

```curl
curl --request GET \
     --url https://iris.trackunit.com/api/asset/v1beta1/assets \
     --header 'accept: */*' \
     --header 'authorization: Bearer <<YOUR_TOKEN>>
```



```json
{
  "totalPages": 1,
  "totalElements": 2,
  "number": 0,
  "size": 20,
  "numberOfElements": 2,
  "content": [
    {
      "id": "00000000-0000-0000-0000-000001427023",
      "assetType": "MACHINE",
      "type": "AWP/Scissor lift",
      "name": "Asset #1",
      "externalReference": "",
      "model": "My model",
      "brand": "My brand",
      "serialNumber": "1234abc",
      "productionYear": 2021,
      "ownerAccountId": "7045120f-5ee7-4613-9977-7e2d8b01ce8c",
      "createdAt": null,
      "permissions": {
        "edit": false
      },
      "telematicsDevices": [
        {
          "id": "199214"
        }
      ]
    },
    {
      "id": "00000000-0000-0000-0000-000001427026",
      "assetType": "MACHINE",
      "type": "AWP/Boom lift",
      "name": "Asset #4",
      "externalReference": "",
      "model": "My model",
      "brand": "My brand",
      "serialNumber": "4567abc",
      "productionYear": 2018,
      "ownerAccountId": "01a0dcc2-4365-4cd6-9450-ea271133c047",
      "createdAt": null,
      "permissions": {
        "edit": false
      },
      "telematicsDevices": [
        {
          "id": "199211"
        }
      ]
    }
  ]
}
```



Assign the service plan to your asset.

```curl
curl --location --request PUT 'https://iris.trackunit.com/public/api/service-management/v2/plans/assignments' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <<YOUR_TOKEN>>' \
--data-raw '{
  "add": [
    {
    	"assetId": "00000000-0000-0000-0000-000001427023",
      "servicePlanId": "3f3543f7-9c58-4d6c-8c67-ce48349bc46d",
      "provideFor": true
    }
  ]
}'
```



Response code 200 means the service plan has been assigned to the asset and your account is the service provider.

**The service plan is now active for the asset.**

## 4. Resolve pending services

You are able to retrieve a list of asset by service status using **/plans/assignments/service-status/:serviceStatus/assets**. Depending on what service criteria you have added to your plan, your asset's service status will either be in service status PLANNED, UPCOMING or OVERDUE. In this example it is in OVERDUE.

```curl
curl --location --request GET 'https://iris.trackunit.com/api/service-management/v2/plans/assignments/service-status/OVERDUE/assets' \
--header 'Authorization: Bearer <<YOUR_TOKEN>>'
```



Response

```json
{
    "assetIds": [
        "00000000-0000-0000-0000-000001427023"
    ]
}
```



After the overdue services has been performed, you can resolve the overdue service by creating a service registration.

To perform the registration you will need call **/plans/assignments/service-registrations** with the id of the asset and id of the planned service perform, which can be located in the get service plan response. In this example the asset id is **00000000-0000-0000-0000-000001427023** and planned service id is **97e7ac2d-59e7-4559-909b-56ff68eba616**.

```curl
curl --location --request POST 'https://iris.trackunit.com/api/service-management/v2/plans/assignments/service-registrations' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <<YOUR_TOKEN>>' \
--data-raw '{
  "assetIds": [
    "00000000-0000-0000-0000-000001427023"
  ]
}
{
  "assetId": "00000000-0000-0000-0000-000001427023",
  "performedAt": "2021-09-20T06:09:09.621736Z",
  "servicesPerformed": [
    {
      "plannedServiceId": "97e7ac2d-59e7-4559-909b-56ff68eba616"
    }
  ]
}'
```



You have now successfully completed a service cycle. If your service plan has further planned services then the next service is now planned and the asset is in service status PLANNED.
