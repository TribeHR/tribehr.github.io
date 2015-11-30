---
category: API v2
title: 'Modifying Leave Requests'
type: 'PUT'
path: '/leave_requests'

layout: default
---

Modify an existing Leave Request. Supports all of the same parameters as the
**`POST`** request above, but you **must** incldue an **`:id`** parameter that matches the
ID in the URL.

Similarly to **`POST`** requests against **`/leave_requests.json`**, if both **`:hours`** and
**`:days`** are set, **`:days`** will be ignored in favour of the value of **`:hours`**.

The exmaple request here approves a currently-pending leave request.

### Request

```PUT /leave_requests/{id}.json
X-API-Version: 2.0.0
id=1&status=APPROVED
```

### Response 

```Status: 200 OK```
```Content-Type: application/json; charset=UTF-8
{
    "id": 1,
    "comments": "My cousin is getting married!",
    "date_start": "2013-10-25",
    "date_end": "2013-10-28",
    "days": 2,
    "hours": 16,
    "status": "APPROVED",
    "created": "2012-05-09T14:46:03+00:00",
    "modified": "2013-10-18T18:48:33+00:00",
    "url": "/leave_requests/1.json",
    "user": {
        "id": 2,
        "username": "emma",
        "email": "emma@tribehr.com",
        "display_name": "Emma Employee",
        "employee_record": {
            "first_name": "Emma",
            "last_name": "Employee",
            "url": "/employee_records/2.json"
        },
        "url": "/users/2.json"
    },
    "leave_type": {
        "id": 1,
        "name": "Vacation",
        "accrual": "NONE",
        "url": "/leave_types/1.json"
    }
}```