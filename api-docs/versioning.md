---
title: Versioning
category: 6295ae369ba4b1001464c9e5
---
All Trackunit APIs are versioned using a URL versioning scheme

`<https://iris.trackunit.com/api/asset/v1/assets`>

When backwards-incompatible changes are made a new version of the API is released.  
For backwards compatible changes we do not update the API version.  
Breaking changes includes:

- Change in format of the response data
- Change in the request or response type
- Removing parts of the API

```json Example of breaking change
//In v1 VIN is an integer
{
	"id": "6977dc08-dc3c-476d-b424-7b0b81ade8bb",
	"name": "My Asset",
	"vin": 1234
}
//In v2 VIN is switched to a string, and thereby a breaking change to the interface
{
	"id": "6977dc08-dc3c-476d-b424-7b0b81ade8bb",
	"name": "My Asset",
	"vin": "1-2-3-4"
}
```

## Beta versions

When a Trackunit API is close to release, we will sometimes release a beta version of the API to allow early adopters access to our new capabilities and to help us validate our domain exposure.

We will use the beta versioning scheme when we are releasing an early version where changes to the  API might still occur.

APIs that are release in a beta version can be identified either by the versioning scheme below or by the  following banner

> 🚧 Beta

```text API version lifecycle example
# Pre-release
/api/v1beta1 -> non breaking changes will be published to this version
/api/v1beta2 -> a new version is released with every breaking change

# Release
/api/v1 -> released first version of API 

# Post-release changes
/api/v1 -> all non breaking changes
/api/v2 -> breaking changes
```



> 🚧 Beta APIs lifecycle
> 
> Trackunit will only have up to two beta versions running at the same time, for the same API. When new beta versions are released, the oldest version will be deprecated after **30 days**.
> 
> When APIs are released in a final version, beta versions are deleted from our cloud platform.  
> Consumers will have **30 days** to migrate from the beta version to the release version of the API.