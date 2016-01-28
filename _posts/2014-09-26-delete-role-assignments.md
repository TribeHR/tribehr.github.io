---
category: API v3
title: 'Removing Role Assignments from a User'
type: 'DELETE'
path: '/users/{id}/roles.json'

layout: default
---

Unassign roles for a given user.

Specify any roles to remove from a user's existing assigned roles.
The {id} in the URL is the ID of the user to remove the role assignments from.

If successful, the response to your request will include the list of all roles currently assigned to the specified user.

### Request

Parameters:

- **`:role_id`** *(integer array; required)* - an array of role IDs to add to assign

```POST /users/{id}/roles.json
X-API-Version: 3.0.0
```
```role_id%5B%5D=12&role_id%5B%5D=7
```

### Response
```Status: 200 OK```
```{
    "id": 34,
    "role_id": 1,
    "user_id": 17
},
{
    "id": 43,
    "role_id": 3,
    "user_id": 17
}
```