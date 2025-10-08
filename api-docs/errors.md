---
title: Errors
category:
  uri: /branches/1.0/categories/reference/GETTING STARTED
---
Trackunit APIs use common HTTP codes to indicate a success or a failure of a request.

### `2xx` Successful responses

Most common response codes used across Trackunit APIs in this category include:

- `200 OK` - requested operation was completed successfully, and a valid JSON representation of the result was returned (e.g. a Group was successfully updated)
- `201 Created` - requested resource was successfully created (e.g. a new Group was successfully created)
- `204 No Content` - requested operation was completed successfully, however no JSON response was returned (e.g. Assets were successfully added to the group)

### `3xx` Redirection responses

### `4xx` Client error responses

Most common response codes used across Trackunit APIs in this category include:

- `400 Bad Request` - request was invalid (e.g. a telematics device was already onboarded on Trackunit platform)
- `401 Unauthorized` - valid authentication credentials were missing in the request
- `403 Forbidden` - provided credentials were insufficient to access a requested resource or perform a requested operation
- `404 Not Found` - requested resource was not found

### `5xx` Server error responses

Most common response codes used across Trackunit APIs in this category include:

- `500 Internal Server Error` -  an unexpected error occurred in the API. This might be due to a bug or temporary infrastructure problems.

## Error Object

Apart from the standard HTTP code, error responses also contain a JSON object with additional information about the error. The intent for such an error objects is to offer a standardised way to communicate use-case specific errors. Such errors may require individual handling in the consumer implementation. A key element in this case is the `code` attribute (see ② below). Consumer code may use it to distinguish between different error cases. Please refer to the documentation of a specific API operation for a list of applicable error codes.

```json Sample use-case specific error
{
    ① "status": 400,
    ② "code": "exactly_one_telematics_device_is_required",
    ③ "message": "Exactly one telematics device is required to onboard an asset. The request was missing a telematics device or had more then one telematics device."
}
```



① HTTP status code of the response
② Error code (snake case) that can be used by the consumer code to distinguish between different errors
③ Error message providing an explanation of the error

Constraint violation errors contain additional `violations` attribute  (see ④ below) that enlists all the fields, in which some constraint was violated.

```json Sample constraint violation error
{
    ④ "violations": [
        {
            "field": "name",
            "message": "value '' was rejected: must not be empty"
        }
    ],
    "message": "Constraint violation",
    "status": 400,
    "code": "constraint_violation"
}
```