---
title: Customer API v1
type: added
---

Released stable version v1 of Customer API as REST and GraphQL endpoint.
For more information, see the documentation and introduction of the endpoints.

# GraphQL

> ➕ Trackunit Iris GraphQL API

Example:
```
query GetCustomers(
  $before: Cursor
  $after: Cursor
  $last: Int
  $first: Int = 20
) {
  customers(before: $before, after: $after, first: $first, last: $last) {
    edges {
      node {
        id
        name
        type
      }
    }
    pageInfo {
      hasPreviousPage
      hasNextPage
      startCursor
      endCursor
      count
    }
  }
}
```

[See all relevant GQL documentation](https://developers.trackunit.com/reference/graphql-api-introduction)

# REST

Below a list of all available REST endpoints:

## Customer:

> ➕ GET: /customer/v1/customers/{customerId}

[Get customer](ref:getcustomer)

> ➕ GET: /customer/v1/customers

[Get customers](ref:getcustomers)

> ➕ POST: /customer/v1/customers

[Create customer](ref:createcustomer)

> ➕ PATCH: /customer/v1/customers/{customerId}

[Update customer](ref:updatecustomer)

> ➕ DELETE: /customer/v1/customers/{customerId}

[Delete customer](ref:deletecustomer)

## Customer Contact:

> ➕ GET: customer/v1/customers/{customerId}/contacts/{contactId}

[Get contact](ref:getcontact)

> ➕ GET: customer/v1/customers/{customerid}/contacts

[Get contacts](ref:getcontacts)

> ➕ POST: customer/v1/customers/{customerid}/contacts

[Create contact](ref:createcontact)

> ➕ PATCH: customer/v1/customers/{customerid}/contacts/{contactId}

[Update contact](ref:updatecontact)

> ➕ DELETE: customer/v1/customers/{customerid}/contacts/{contactId}

[Delete contact](ref:deletecontact)

@@ Customer Asset assignments:

> ➕ GET: customer/v1/customers/{customerid}/assets

[Get assets](ref:getassets)

> ➕ POST: customer/v1/customers/{customerid}/assets

[Update assets](ref:updateassets)
