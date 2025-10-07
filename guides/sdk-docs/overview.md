---
title: App SDK
category: /branches/1.0/categories/guides/Apps & Extensions

---

> 📘 IrisX Subscription needed
>
> App SDK is only available to IrisX customers. Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview)

# What is App SDK?

App SDK (Software Development Kit) is a set of tools and guidelines that allow you to create IrisX Applications that integrates with the [Trackunit Manager](https://trackunit.com/trackunit-manager/)) User Interface.

App SDK allows you to:

- **Custom tailored experience:** IrisX Apps can show exactly the data relevant for you or automate workflows. For example, and IrisX App can show a digital twin of a specific machine model.

- **Share Data Across Tools:** IrisX Apps add context and give a fuller picture of a user's business, integrate 3rd party products into Trackunit Manager, or integrate Trackunit data with 3rd party products. An app can let Trackunit users engage with their customer records in your CRM, balance statements, or display fleet information.

App SDK also allows you to extend the Trackunit Manager User Interface by using multiple extension points.

With UI (User Interface) extensions, users can interact with your app inside Trackunit Manager or use Iris REST APIs to interact with Trackunit's ecosystem (e.g., using webhooks or reading and writing data).

[block:html]
{
  "html": "<div class=\"tile-grid\">\n  \n  <div class=\"extension-link\">\n    <a href=\"https://developers.trackunit.com/docs/getting-started\">\n      <div class=\"content\">\n        <div class=\"img-container\">\n\t        <img src=\"https://files.readme.io/35d1841-Iris_App.png\">\n        </div>\n        <h3><center>Create an app</center></h3>\n        <h4><center>Learn the basics of app development by building your first IrisX App.</center></h4>\n      </div>\n    </a>\n  </div>\n  \n  <div class=\"extension-link\">\n    <a class=\"yellow\" href=\"https://design.iris.trackunit.com/\">\n      <div class=\"content\">\n        <div class=\"img-container\">\n\t        <img src=\"https://files.readme.io/d972a3b-Components_-_with_shapes.png\">\n          </div>\n        <h3><center>Design your app</center></h3>\n        <h4><center>Get started with design tools, guidelines, and language.</center></h4>\n      </div>\n    </a>\n  </div>\n  \n    <div class=\"extension-link\">\n    <a class=\"blue\" href=\"https://developers.trackunit.com/docs/iris-app-publish\">\n      <div class=\"content\">\n        <div class=\"img-container\">\n\t        <img src=\"https://files.readme.io/49eb2a1-Publish_and_distribute.png\">\n        </div>\n        <h3><center>Publish and distribute</center></h3>\n        <h4><center>Upload your app to your team's use, or submit to Trackunit Marketplace.</center></h4>\n      </div>\n    </a>\n  </div>\n  \n</div>\n\n<style>\n  .tile-grid{\n    display: flex;\n    flex-direction: row;\n    width: 100%;\n    gap: 3rem;\n  }\n  \n  .content{\n    display: flex;\n    flex-direction: column;\n  }\n  \n  .img-container {\n    border-radius: 3rem;\n    width: 100%;\n    overflow: hidden;\n    aspect-ratio: 1/1;\n  }\n  \n .tile-grid .extension-link{\n   display: flex;\n   flex: 1;\n   overflow: hidden;\n  }\n  \n  .img-container img{\n    height: 100%;\n    width: auto;\n    max-width: unset !important;\n  }\n  \n .extension-link>a{\n    text-decoration: none !important;\n    width: 100%;\n  }\n  \n  .content h4{\n    margin-top: unset !important;\n    font-weight: 500;\n    color: #493736 !important;\n  }\n  \n  .content h3{\n    margin-bottom: 0.5rem !important;\n  }\n\n\n</style>"
}
[/block]