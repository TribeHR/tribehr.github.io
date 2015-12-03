---
category: Internal
title: 'Find Accounts (Unauthenticated)'
type: 'GET'
path: '/find_accounts'

layout: default
---

**The following enpoint does not require user authentication.**
This endpoint provides the consumer with a list of shortnames that are associated with a given email address.

The mobile apps use this endpoint to determine what account a user wants to connect to, since they only prompt the user for their email and password and not for their shortname.

Typically, this API is called against https://www.mytribehr.com/ and not a specific account's base URL.

Parameters:
 - **`email`** *(string; required)* - The email for which we want to find associated accounts
 
```GET /find_accounts.json
X-API-Version: 2.0.0
email=someguy@netsuite.com
```

```Status: 200 OK```
```Content-Type: application/json
[
    {
        "shortname":"tribe"
    },
    {
        "shortname":"mobiledemo"
    }
]
```