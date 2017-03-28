---
category: API v3
title: 'Creating Kudos'
type: 'POST'
path: '/kudos'

layout: default
---

### Request

Parameters:

- **`:recipients[][id]`** *(integer; one or more **`:recipients[][id]`** parameters should be present)* - the 
  ID(s) of the recipients of this kudos
- **`:text`** *(string)* - the text of the kudos
- **`:picture`** *(image)* - a picture to attach to the kudos.  To attach a picture to a kudos, you'll need
   to send your request encoded as **`multipart/formdata`**. Your picture should be included in a part with 
   the name **`:picture`**.
- **`:values[][id]`** *(integer; zero or more **`:values[][id]`** parameters may be present)* - the ID(s) of
  any values that should be attached to this kudos
   
Each kudos **should** contain at least one of **`:text`** and **`:picture`**, although this is currently
not enforced by the API. 
Likewise, at least one recipient **should** be listed, but again, this is not
enforced.
The **`poster`** of the kudos is assumed to be the user authenticated on this request; you **should not**
specify the **`poster`** in your request.


```
POST /kudos.json?formattedTextAs=html
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0
recipients[][id]=6&
recipients[][id]=17&
text=You%27ve%20done%20a%20%3Ci%3Ewonderful%3C%2Fi%3E%20job%20recently.&
values[][id]=11
```

### Response

```
Status: 200 OK
```

```
{
    "id": 88,
    "poster": {
        "id": 1,
        "username": "admin",
        "email": "devnull+admin@tribehr.com",
        "display_name": "Tribe Admin",
        "employee_record": {
            "first_name": "Tribe",
            "last_name": "Admin",
            "url": "/employee_records/58.json"
        },
        "url": "/users/1.json"
    },
    "recipients": [
        {
            "id": 6,
            "username": "abbyring",
            "email": "devnull+abbyring@tribehr.com",
            "display_name": "Abby Ring",
            "employee_record": {
                "first_name": "Abby",
                "last_name": "Ring",
                "url": "/employee_records/46.json"
            },
            "url": "/users/6.json"
        },
        {
            "id": 17,
            "username": "willytrainer",
            "email": "devnull+willytrainer@tribehr.com",
            "display_name": "Willy Trainer",
            "employee_record": {
                "first_name": "Willy",
                "last_name": "Trainer",
                "url": "/employee_records/55.json"
            },
            "url": "/users/17.json"
        }
    ],
    "values": [
        {
            "id": 11,
            "name": "Teamwork",
            "image": {
                "url": "teamwork/icon.png"
            },
            "url": "/values/11.json"
        }
    ],
    "text": "You've done a <i>wonderful</i> job recently.",
    "comment_count": 0,
    "url": "/notes/88.json",
    "source": "Awesome Kudos-Posting App",
    "created": "2013-08-20T20:05:18+00:00"
}
```