---
title: Machine APIs - Introduction
category: 675ac7f3f2aec2002c641eaf
---

> 🚧 Onboarding / offboarding of machines
> 
> The Asset API currently does not yet support onboarding or offboarding assets with the MACHINE asset type. We are planning to support this in the Asset API in the future. Until then the Machine domain APIs should be used in the meantime. Read more about the evolution of Trackunit's data model below.

## Concept shift: From Units to Machines to Assets

Trackunit's underlying platforms have undergone a transformation evolving from our legacy platform and Classic API suite to our new state-of-the-art platform Iris. Alongside this transformation, Trackunit's data model has undergone a significant paradigm shift. We have transitioned from a unit-centric approach, where telematics devices and machines overlapped and identification relied on potentially non-unique strings, to a more refined machine-centric model, initially separating telematics devices from machines.

![From Unit to Machine](https://cdn.statically.io/gh/trackunit/developer-hub/master/api-docs/ClassicUnit-to-IrisAsset.png)

In the latest evolution Iris now embraces an asset-centric perspective, where the system supports multiple telematics devices per asset and ISO feeds, enabling seamless integration and robust data management. Moreover, it facilitates support for Bluetooth tags and attachment / machine connections, streamlining operations and enhancing connectivity across the asset ecosystem. This shift marks a pivotal advancement, empowering Trackunit to better cater to the complex needs of modern asset management and telemetry.

![From Machine to Asset](https://cdn.statically.io/gh/trackunit/developer-hub/master/api-docs/ClassicUnit-to-IrisAsset.png)
