---
category: API v3
title: 'Getting Attachments'
type: 'GET'
api_path: '/attachments'

layout: default
---

From TribeHr Api you can download some uploaded files.

## Get User Avatar 

Download actual avatar for selected User. 

### Request

* The headers must include a **valid authentication token**.

```
GET /attachments/User/avatar/11.json
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0
```

### Response

Expected header:

```
Status: 200 OK
Content-Type: image/<png/jpeg/other allowed format>
```

Response body is user avatar(image). 
