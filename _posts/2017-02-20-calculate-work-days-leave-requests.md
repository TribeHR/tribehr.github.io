---
category: 'API v3' 
title: 'Calculate Work and Days'
type: 'GET'
path: '/leave_requests'

layout: default
---

## Calculate Work Days or Hour for Leave Requests

The following endpoint and options can be used to calculating works day and works hour between dates for selected user.

### Request

There are two mandatory and one optional querystring parameters for calculating working days requests:

 - **`start_date:`** *(date; required)* - the date of the first day. Use ISO date format(YYYY-MM-DD).
 - **`start_date:`** *(date; required)* - the date of the last day. Use ISO date format(YYYY-MM-DD). 
 - **`user_id:`** *(integer; defaults to currently authenticated user)* - Id of user for which we want to compute working days/hours. Authorized user need appropriate permission for it, to prevent display hidden data. 


```
GET /leave_requests/calculateTimeOff.json?end_date=2017-06-18&start_date=2017-06-08
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0
```

Or

```
GET /leave_requests/calculateTimeOff.json?end_date=2017-06-18&start_date=2017-06-08&user_id=30
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
  "leave_request": {
    "end_date": "2017-06-18",
    "start_date": "2017-06-08",
    "estimated_days_off": 7,
    "estimated_hours_off": 52.5
  }
}
```
