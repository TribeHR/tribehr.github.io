---
category: API v3
title: 'Deleting Resources'
type: 'DELETE'
path: '/[any resource]/{id}'

layout: default
---

All resources are deleted in the same way - just send a **`DELETE`** request to a resource's URL.
**`DELETE`** requests may only be sent to URLs that represent a *single* item (such as **`/events/{id}.json`**)
but may not be sent to URLs that represent collections of resources (such as **`/events.json`**).
You **must** include an **`:id`** parameter that matches the ID in the URL.
 

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