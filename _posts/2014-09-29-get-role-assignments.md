---
category: API v3
title: 'Getting Roles Assigned to a User'
type: 'GET'
path: '/users/{id}/roles.json'

layout: default
---

Get the list of all roles currently assigned to a given user.
The {id} in the URL is the ID of the user for whom to view assigned roles.


### Request

```GET /users/{id}/roles.json
X-API-Version: 3.0.0
```

### Response
```Status: 200 OK```
```{
    "id": 34,
    "role_id": 1,
    "user_id": 17
},
{
    "id": 42,
    "role_id": 12,
    "user_id": 17
},
{
    "id": 43,
    "role_id": 3,
    "user_id": 17
},
{
    "id": 44,
    "role_id": 7,
    "user_id": 17
}
```