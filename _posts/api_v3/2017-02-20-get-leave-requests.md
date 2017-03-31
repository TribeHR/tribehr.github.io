---
category: 'API v3' 
title: 'Getting Leave Requests'
type: 'GET'
api_path: '/leave_requests'

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


```
GET /leave_requests.json
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0
```

```
GET /leave_requests.json?status=all
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0
```

### Request

Get all APPROVED leave requests in TribeHR


```
GET /leave_requests/approved.json
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0
```

```
GET /leave_requests.json?status=approved
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0
```

### Request

Get all PENDING leave requests in TribeHR


```
GET /leave_requests/pending.json
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0
```

```
GET /leave_requests.json?status=pending
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0
```

### Request

Get all REJECTED leave requests in TribeHR


```
GET /leave_requests/rejected.json
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0
```

```
GET /leave_requests.json?status=rejected
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0
```

### Response
```
Status: 200 OK
Content-Type: application/json
```
```
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
]
```


## Get Selected Leave Requests

View details about selected Leave Request, remember, data are filtered according to authorized user permission.

### Request

Get selected leave request in TribeHR.

```
GET /leave_requests/2.json
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0
```

### Response
```
Status: 200 OK
Content-Type: application/json
```
```
{
  "id": 2,
  "comments": "Approved request",
  "date_start": "2012-01-24",
  "date_end": "2012-01-27",
  "days": 3,
  "hours": 22.5,
  "status": "APPROVED",
  "created": "2012-01-24T00:00:00+00:00",
  "modified": "2012-11-19T14:15:12+00:00",
  "url": "/leave_requests/2.json",
  "user": {
    "id": "18",
    "username": "Annabelle",
    "avatar": {
      "url": "/attachments/view/User/avatar/18"
    },
    "email": "FakeEmail+15@ribbitco.biz",
    "display_name": "Annabelle Skyles",
    "assignment_record": {
      "current": true,
      "url": "/assignment_records/153.json"
    },
    "employee_record": {
      "first_name": "Annabelle",
      "last_name": "Skyles",
      "url": "/employee_records/116.json"
    },
    "url": "/users/18.json"
  },
  "leave_type": {
    "id": 1,
    "name": "Vacation",
    "accrual": "MONTHLY",
    "url": "/leave_types/1.json"
  }
}
```