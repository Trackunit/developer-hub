---
title: Calling external APIs from an Iris App
category: 61fcd8e1a448f5004215317c
---


In most cases to call an external API you can just use http client in your app's code and do the requests. But there are
two situations in which you will need to use Iris App SDK Proxy service:

1. When the external API does not implement CORS or does not allow Trackunit as an origin and the browser will not allow
   the call
2. To use secrets (like API key) without hardcoding them in your application

