---
title: Using Iris App SDK Proxy
category:
  uri: Apps & Extensions
parent:
  uri: external-apis
---

In most cases to call an external API you can just use http client in your app's code and do the requests. But there are
two situations in which you will need to use Iris App SDK Proxy service:

1. When the external API does not implement CORS or does not allow Trackunit as an origin and the browser will not allow
   the call
2. To use secrets (like API key) without hardcoding them in your application

## Manifest requirements

To use the Iris App SDK Proxy you need to add `api.iris.app.proxy.fetch` scope (to make calls using Proxy) and
optionally `account.iris.app.store-secret` scope (to store secrets) to your APPs manifest. Additionally, you need to
specify the domains that your app is allowed to call in the cspHeader `"connect-src"`. So your manifest could look like
this:

```ts
const irisAppManifest: IrisAppManifest = {
    // ommiting other config
    cspHeader: {
        "connect-src": ["https://dbc-1234-567.cloud.databricks.com"],
    },
    scopes: [
        {scope: "api.iris.app.proxy.fetch", optional: false},
        {scope: "account.iris.app.store-secret", optional: false},
    ],
};
```

Then you need to **Publish** your application and have it **Approved** at least once (it can be empty, only the manifest
is important at this stage) so that all required infrastructure is created for it and your app is assigned an AppId and
can get the AppToken. Follow this [publication guide](https://developers.trackunit.com/docs/publish-app) for details.
From this point you can develop your application locally. If you change the manifest then you need
to **Publish** and get **Approval** once again to unlock the local development mode with the Proxy functionality
working.

## Usage

The Iris App SDK Proxy has 2 GraphQL mutations that you can use - `irisAppProxyStoreSecrets` and `irisAppProxyFetch`.
> To get the latest information about the GraphQL schema
> check [GraphQL Explorer](https://apps.iris.trackunit.com/graphql-public-viewer/).

### Store secrets

`irisAppProxyStoreSecrets` mutation allows you to store the secret in our vault so that later you can use it in the
`irisAppProxyFetch`:

```graphql
mutation IrisAppProxyStoreSecrets($secrets: JSONObject!) {
  irisAppProxyStoreSecrets(secrets: $secrets) {
    success
    errorMessage
  }
}
```

The JSON object can be for example `"{\"mySecretName\": \"mySecretValue\"}"`

To store the secrets you need to have an admin account - that is to have
`account.iris.app.store-secret` permission. Your app also needs to have `account.iris.app.store-secret` scope in order
to be able to use this mutation.

After executing `irisAppProxyStoreSecrets` mutation you can use the secret in the `irisAppProxyFetch` - the Iris App SDK
Proxy will search for this secret in a header and replace it like this:

```
"headers": {"name": "Authorization", "value": "Bearer {{mySecretName}}"}
```

into:

```
"headers": {"name": "Authorization", "value": "Bearer mySecretValue"}
```

### Perform the request

To perform a request to some external APIs using Proxy service you need to call `irisAppProxyFetch` GraphQL mutation.
It has 4 arguments: `headers`, `method`, `url` and `body`. All those arguments are then used to call the external API.

* `url` is the endpoint that you want to call (remember to include it in your manifest cspHeader).
* `headers` are the headers that will be used in the request. You can include your secrets there using moustache
  format (`{{mySecretName}}`)
* `method`is the method that will be used for the request - it is an enum GET, POST, PUT, DELETE, PATCH
* `body` is **base64 encoded** body that Proxy server will decode and use as the request body

**The GraphQL should respond with 200 code if it managed to perform the request regardless of the request result!**
Also, the `errorMessage` field should be empty.

To check the status of the request that the Proxy made on your behalf, you should check the `status` field. This is the
response status of the `url` that you've called.  
The `headers` field are the headers that were included in the response of the server that was called by the Proxy.  
The `body` is **base64 encoded** body that the server responded with.

Example:

```graphql
mutation IrisAppProxyFetch($url: String!, $headers: [IrisAppProxyHeader!]!, $method: HttpMethod!, $body: String) {
  irisAppProxyFetch(url: $url, headers: $headers, method: $method, body: $body) {
    body
    errorMessage
    headers {
      name
      value
    }
    status
    success
  }
}
```

The `status`, `headers` and `body` fields are coming from the endpoint specified in `url` argument.

## Common errors:

* _403 Token does not contain App Id_ - this error occurs when your app doesn't use the AppToken. It happens when you
  didn't publish the app for the first time, or after the change of manifest. To solve - publish the app
* _403 CSP 'connect-src' directive does not contain provided URL host_ - this happens when the `url` argument of the
  GraphQL call doesn't match with the `connect-src` from the cspHeader in your manifest. To solve - update the cspHeader
  with your url and publish the app
* _409 Unresolved placeholders X in header Y_ - this happens when you've used moustache template in the header like
  `{{secret}}` but didn't store the `secret` using `irisAppProxyStoreSecrets`. To solve - use the
  `irisAppProxyStoreSecrets` endpoint with the `secret` value or remove the `{{secret}}` from your headers.
