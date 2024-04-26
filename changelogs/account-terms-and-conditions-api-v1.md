---
title: Account Terms and Conditions API v1
type: added
---

<p>Released stable version v1 of Account Terms and Conditions API.<br>
Discover the new Account Terms and Conditions API. This API allows you to retrieve all the approved terms and conditions for accounts in your organization. The API provides a list of terms and conditions for each account, including the date of approval, the name of the document and version.
</p>

Below is the new available endpoint:

> ➕ GET: /organization/v1/accounts/terms-and-conditions

[Get terms and conditions](ref:gettermsandconditions)

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
