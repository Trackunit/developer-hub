---
title: Classic to Iris APIs Migration Guide
category: 6613a6c0a960880062004859
---

Trackunit's underlying platforms have undergone a transformation, incorporating new scale-out technologies and our state-of-the-art platform is called Iris. It encompasses countless enhancements, aims to sustain seamless performance and facilitates continued scalability for ongoing usage and new technology capabilities. With the introduction of the Trackunit Iris platform, we are phasing out support for our legacy platform and Classic API suite.

Learn how to harness the power of the Iris platform and migrate your business away from using legacy Classic APIs.

## Concept shift: From Units to Assets

(Explain the shift in thinking from assets to units)

## Asset administration

### Asset API
(TBD)

### Groups API
Working with groups helps you manage your fleet and segment it in a way that makes sense for your day-to-day operations. Groups act like simple workspaces that can be used to focus your fleet overview by narrowing to a subset of assets.

The [Classic Group API](https://dev.trackunit.com/docs/group) allowed you to create and manage collections of units. Because Iris is build around the concept of assets, the [Iris Group API](https://developers.trackunit.com/reference/getgroups) allows you now to create and manage collections of assets instead. Additionally the Iris Group API endpoints also allow you to manage which users should have access to groups.

(any migration tool here for groups?!)
+ what about Classic Category?!


### Sites API
With the Iris platform we have evolved the concept of **Classic Zones (map areas)** and **Classic Points (location points on a map)** and collapsed the two into our new Sites concept. Sites keep the same importance as zones for running reports and creating alerts. Leverage automatically detected sites or enter site boundaries as you see fit – including the option to apply labels depending on the site type.

With the introduction of Sites in Trackunit Manager, existing Zones in Manager Classic were automatically transferred to Sites and classified as Classic Zones. To harvest the full power of Sites, it is recommended to [manually convert a Zone into a Site type](https://helpcenter.trackunit.com/s/article/How-do-I-convert-a-Zone-to-a-Site?language=en_US) of your choice and get an up-to-the-minute picture of equipment status across job sites.

Going forward use the [Iris Sites API](https://developers.trackunit.com/reference/getsites) to create and manage your Sites at scale and also e.g. retrieve a comprehensive site history, encompassing either asset intervals within a list of sites or the sites visited by a list of assets.

## Organizational Management

### Customers API
The [Classic Clients](https://dev.trackunit.com/docs/client) & [Contacts](https://dev.trackunit.com/docs/contact) functionality now has an equivalent feature called Customers in Trackunit Iris. We recommend you start using Customers as soon as possible to get access to the latest functionalities and be on board with the foundation for exiting new features like [ERP integrations](https://portal.productboard.com/mbaayvr5tzubn5acbd8dvqa8/c/288-rental-erp-integrations) and [Branded Customer Portals](https://portal.productboard.com/mbaayvr5tzubn5acbd8dvqa8/c/290-branded-customer-portals).

> 🚧 Migration note
> If you have set up Clients in Manager Classic that are attached to Service Management and Alarms in Manager Classic, we recommend that you wait until those two features are completely migrated over to Trackunit Iris to avoid disrupting your business processes. If you are in doubt, contact your Trackunit representative. 

The [Iris Customer API](https://developers.trackunit.com/reference/customers-api-intro) empowers developers to interact with customer information, including details about customers, their associated contacts and asset assignments.


