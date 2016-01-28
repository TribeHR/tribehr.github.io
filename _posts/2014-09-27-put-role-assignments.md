---
category: API v3
title: 'Setting Roles Assigned to a User'
type: 'PUT'
path: '/users/{id}/roles.json'

layout: default
---

Set the list of roles assigned to a given user.

The complete set of roles assigned to a user will be set to the array provided. Any previously assigned roles not in this list will be unassigned.
The {id} in the URL is the ID of the user to assign the roles to.

If successful, the response to your request will include the list of all roles currently assigned to the specified user.

### Request

Parameters:

- **`:role_id`** *(integer array; required)* - an array of role IDs to add to assign

```POST /users/{id}/roles.json
X-API-Version: 3.0.0
```
```role_id%5B%5D=12&role_id%5B%5D=3&role_id%5B%5D=7
```

### Response
```Status: 200 OK```
```{
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