---
category: API v3
title: 'Deleting Resources'
type: 'DELETE'
api_path: '/[any resource]/{id}'
layout: default
---

Some resources can be deleted in the same way - just send a **`DELETE`** request to a resource's URL.
**`DELETE`** requests may only be sent to URLs that represent a *single* item (such as **`/events/{id}.json`**)
but may not be sent to URLs that represent collections of resources (such as **`/events.json`**).
You **must** include an **`:id`** parameter that matches the ID in the URL.
 
We support API for deleting this resources:
 - **Events**: /events/39.json
 - **Kudos**: /kudos/79.json
 - **Leave Request**: /leave_requests/196.json


An example follows:

### Request

```
DELETE /events/254.json
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0

id=254
```

### Response

```
Status: 200 OK
```

```
{
    "success": {
        "code": "DELETED",
        "messages": [
            "Operation successfully completed."
        ]
    }
}
```