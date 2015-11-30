---
category: API v2
title: 'Deleting Resources'
type: 'DELETE'
path: '/[any resource]/{id}'

layout: default
---

All resources are deleted in the same way - just send a **`DELETE`** request to a resource's URL.
**`DELETE`** requests may only be sent to URLs that represent a *single* item (such as **`/events/{id}.json`**)
but may not be sent to URLs that represent collections of resources (such as **`/events.json`**). An example
follows:

### Request

```DELETE /events/{id}.json
X-API-Version: 2.0.0
```

### Response

```Status: 200 OK```
```{
    "success": {
        "code": "DELETED",
        "messages": [
            "Operation successfully completed."
        ]
    }
}
```