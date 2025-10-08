---
title: Account Terms and Conditions API - Introduction
category:
  uri: "/branches/1.0/categories/reference/Account Terms And Conditions"
---
The Account Terms and Conditions API is a REST API that enables organization administrators to verify approval of terms and conditions inside their Account Hierarchy.

> ℹ️ Account management permission is required to use the API

[Try it out here](ref:gettermsandconditions)

Example:
```json
{
  "content": [
    {
      "accountId": "27262d98-0be4-4d95-8bbf-f89e1578d60e",
      "accountName": "Acme Corporation",
      "externalReference": "Acme",
      "termsAndConditions": [
        {
          "appName": "TrackunitManager",
          "date": "2024-04-26T13:36:12.745Z",
          "lastConsentDate": "2024-04-26T13:36:12.745Z",
          "name": "Data processing",
          "version": 1
        }
      ]
    }
  ],
  "number": 0,
  "numberOfElements": 1,
  "size": 20,
  "totalElements": 1,
  "totalPages": 1
}
```
