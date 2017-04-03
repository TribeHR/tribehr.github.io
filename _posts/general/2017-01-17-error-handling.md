---
category: General
title: 'Error Handling'
layout: default
---

There are several error cases that you may come across while consuming the API. In each case you should
receive a non-**`2XX`** HTTP response. In most cases you should receive body data that describes the error,
in the same format, system-wide.

In some cases you may receive an error response with no body. For instance, if you make a request using
a URL that does not map to a valid resource, you will receive a **`404`** response with no body. Similarly,
if you make an unauthenticated request, you will receive a **`401`** response with no body.

Error responses provide an **`error`** object containing a single error code **`code`** (string) and an array
**`messages`** of human-readable error messages (which contains zero or more messages).

We use the following error codes:

- **`INVALID_ID`** - a single resource was requested but no ID was provided. Returned as part of a `404 (Not Found)` response.
- **`NOT_FOUND`** - a single resource was requested (for example, `GET /events/123.json`) but could not be found. Returned as part of a `404 (Not Found)` response.
- **`ID_MISMATCH`** - a `POST` or `PUT` request failed to save because the ID of the resource in the URL did not match the ID in the request body. Returned as part of a `400 (Bad Request)` response.
- **`DELETE_ERROR`** - an unknown error occurred while deleting a resource; the `messages` array may give some hints as to the reason.
- **`SAVE_ERROR`** - an unknown error occurred while creating or updating a resource; the `messages` array may give some hints as to the reason.
- **`VALIDATION_ERROR`** - a `POST` or `PUT` request failed because the data sent in the body was not valid. For instance, a required field may be missing or an end date may occure before a start date. The `messages` array should explain the invalid data to the user. Returned as part of a `400 (Bad Request)` response.
- **`RIGHTS_ERROR`** - indicates that the *account* (not the user; see "Users vs Accounts," above) does not have this feature enabled in their package. Returned as part of a `403 (Forbidden)` response.
- **`ACCESS_ERROR`** - indicates that the current user doesn't have permission to access the requested resource. Returned as part of a `403 (Forbidden)` response.
- **`CONNECTION_ERROR`** - indicates that TribeHR had trouble connecting to the account's database. Returned as part of a `500 (Internal Server Error)` response.
- **`UNKNOWN_SUBDOMAIN`** - indicates that the *account* (not the user; see "Users vs Accounts", above) could not be found. Returned as part of a `404 (Not Found)` response.
- **`MAINTENANCE`** - indicates that TribeHR is undergoing maintenance and will be back up and running later. Returned as part of a `503 (Service Unavailable)` response.
- **`ERROR`** - an unknown error occurred.

### Examples

Requesting an item that doesn't exist example:

```GET /events/1234567.json
X-API-Version: 2.0.0
```Status: 404```
```Content-Type: application/json
{
    "error": {
        "code": "NOT_FOUND",
        "messages": [
            "Invalid Event"
        ]
    }
}
```