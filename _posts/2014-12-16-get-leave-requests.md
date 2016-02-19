---
category: API v2
title: 'Getting Leave Requests'
type: 'GET'
path: '/leave_requests'

layout: default
---

The following endpoint and options can be used to read leave request records from TribeHR. With the available filters, you should be able to support many workflows.

Note that it is currently the API consumer's responsibility to calculate the number of working days (or
hours) that the leave request represents. We are looking at changing this in the future.

## List Leave Requests

Includes all leave requests in TribeHR, in the order in which they were created.

There are two optional querystring filers available for the listing of all leave requests:

 - **`status:`** Get only leave requests with the given current status. Options: **`"pending"`**,  **`"rejected"`**, **`"approved"`**, or **`ALL`**
 - **`filterByHasPermissionToApprove:`** String **`true`** or **`false`**. When true, only leave requests where the requester has full edit and approve permission will be returned

### Request

Get all leave requests in TribeHR


```GET /leave_requests.json
X-API-Version: 2.0.0
```

```GET /leave_requests.json?status=all
X-API-Version: 2.0.0
```

### Request

Get all APPROVED leave requests in TribeHR


```GET /leave_requests/approved.json
X-API-Version: 2.0.0
```

```GET /leave_requests.json?status=approved
X-API-Version: 2.0.0
```

### Request

Get all PENDING leave requests in TribeHR


```GET /leave_requests/pending.json
X-API-Version: 2.0.0
```

```GET /leave_requests.json?status=pending
X-API-Version: 2.0.0
```

### Request

Get all REJECTED leave requests in TribeHR


```GET /leave_requests/rejected.json
X-API-Version: 2.0.0
```

```GET /leave_requests.json?status=rejected
X-API-Version: 2.0.0
```

### Response
```Status: 200 OK```
```Content-Type: application/json
[
    {
        "id": 17
        "date_start": "2013-12-03"
        "date_end": "2013-12-04"
        "comments": "Headed to the beach!"
        "status": "APPROVED"
        "url": "/leave_requests/17.json"
        "user": {
            "id": "1"
            "username": "jstevens"
            "avatar": {
                "url": "/attachments/view/User/avatar/1"
            }
            "email": "jstevens@example.com"
            "display_name": "Jennifer Stevens"
            "assignment_record": {
                "current": true
                "url": "/assignment_records/176.json"
            }
            "employee_record": {
                "first_name": "Jennifer"
                "last_name": "Stevens"
                "url": "/employee_records/73.json"
            }
            "url": "/users/1.json"
        }
        "leave_type": {
            "id": 1
            "name": "Vacation"
            "accrual": "BIWEEKLY"
            "url": "/leave_types/1.json"
        }
    },
    {
        "id": 23
        "date_start": "2013-12-11"
        "date_end": "2013-12-24"
        "comments": "Off to see the family"
        "status": "PENDING"
        "url": "/leave_requests/23.json"
        "user": {
            "id": "54"
            "username": "tsmith"
            "avatar": {
                "url": "/attachments/view/User/avatar/23"
            }
            "email": "tsmith@example.com"
            "display_name": "Tanya Smith"
            "assignment_record": {
                "current": true
                "url": "/assignment_records/192.json"
            }
            "employee_record": {
                "first_name": "Tanya"
                "last_name": "Smith"
                "url": "/employee_records/47.json"
            }
            "url": "/users/23.json"
        }
        "leave_type": {
            "id": 1
            "name": "Vacation"
            "accrual": "BIWEEKLY"
            "url": "/leave_types/1.json"
        }
    }
]```