---
category: API v2
title: 'Creating Leave Requests'
type: 'POST'
path: '/leave_requests'

layout: default
---

Create a new leave request.

Note that it is currently the API consumer's responsibility to calculate the number of working days (or
hours) that the leave request represents. We are looking at changing this in the future.

TribeHR represents the length of time that an employee is away from work using a combination of days
and hours. You must specify **one** the two fields; TribeHR will calculate the value of the other one
automatically using the employee's work hour records.

### Request

Parameters:

- **`:date_start`** *(date; required)* - the date of the first day of leave
- **`:date_end`** *(date; required)* - the date of the last day of leave
- **`:days`** *(integer; either **`days`** or **`hours`** must be present, but not both)* - the number of working days
  that this leave request represents. If **`hours`** is also present, the value of **`days`** will be ignored.
- **`:hours`** *(integer; either **`days`** or **`hours`** must be present, but not both)* - the number of working hours
  that this leave request represents. If **`days`** is also present, its value will be ignored in favour of the
  value of **`hours`**.
- **`:status`** *(string; defaults to **`"PENDING"`**)* The status of the leave request. Users submitting a request on 
  behalf of a subordinate may supply **`"PENDING"`** or **`"REJECTED"`** or **`"APPROVED"`**
- **`:user[id]`** *(integer; defaults to currently authenticated user)* - the user to whom this leave request applies
- **`:leave_type[id]`** *(integer; required)* - the ID of the type of leave being requested. See **`/leave_types.json`**
- **`:comments`** *(string)* - Text written by the employee addressed to their manager

```POST /leave_requests.json
X-API-Version: 2.0.0
```
```comments=I%27m%20off%20to%20visit%20my%20family%20in%20Ottawa%21&
date_start=2013-11-15&
date_end=2013-11-18&
days=2&
status=pending&
user%5Bid%5D=20&
leave_type%5Bid%5D=1
```

### Response
```Status: 200 OK```
```{
    "id": 34,
    "comments": "I'm off to visit my family in Ottawa!",
    "date_start": "2013-11-15",
    "date_end": "2013-11-18",
    "days": 2,
    "hours": 11,
    "status": "PENDING",
    "created": "2013-10-16T21:22:12+00:00",
    "modified": "2013-10-16T21:22:12+00:00",
    "url": "/leave_requests/34.json",
    "user": {
        "id": 20,
        "username": "salleyfitzgibbon",
        "email": "devnull+salleyfitzgibbon@tribehr.com",
        "display_name": "Salley Fitzgibbon",
        "employee_record": {
            "first_name": "Salley",
            "last_name": "Fitzgibbon",
            "url": "/employee_records/51.json"
        },
        "url": "/users/20.json"
    },
    "leave_type": {
        "id": 1,
        "name": "Vacation",
        "accrual": "BIWEEKLY",
        "url": "/leave_types/1.json"
    }
}
```