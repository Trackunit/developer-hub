---
title: Errors in GraphQL
category: 652e3a8e279c3f001f9acdc3
---

**In GraphQL, even if part of a query encounters an error, the overall response is still valid JSON.** 
The `data` field in the response will be either the expected data or `null` if an error occurred. 
This allows you to easily differentiate between successful and unsuccessful parts of the query.

Additionally the response contains an 'errors' field: 
- GraphQL responses have an `errors` field which is an array containing error objects. 
- Each error object includes relevant information such as a user-readable error message, an error code, and optional path information indicating which field in the query caused the error. 
- This detailed information assists you in pinpointing the issue.
