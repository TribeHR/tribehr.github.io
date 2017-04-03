---
category: 'API v3' 
title: 'Calculate Work and Days'
type: 'GET'
api_path: '/leave_requests'

layout: default
---

## Calculate Work Days or Hour for Leave Requests

The following endpoint and options can be used to calculating works day and works hour between dates for selected user.
This is the same calculation that gets applied in the web app when a user is submitting or editing a leave request. 
It takes into consideration weekends, public holidays, and the number of hours the user works per day (in order to return the correct number of hours).

### Request

There are two mandatory and one optional querystring parameters for calculating working days requests:

 - **`start_date:`** *(date; required)* - the date of the first day. Use ISO date format(YYYY-MM-DD).
 - **`start_date:`** *(date; required)* - the date of the last day. Use ISO date format(YYYY-MM-DD). 
 - **`user_id:`** *(integer; defaults to currently authenticated user)* - Id of user for which we want to compute working days/hours. Authorized user need appropriate permission for it, to prevent display hidden data. 

In the example below, the request is submitted by the user with ID 123, who works 7.5 hours per day and resides in Canada.
The date range covers a full weekend and Labour Day.

```
GET /leave_requests/calculateTimeOff.json?user_id=123&start_date=20150904&end_date=20150909
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0
```

Or same request for myself:

```
GET /leave_requests/calculateTimeOff.json?start_date=20150904&end_date=20150909
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
    "start_date":"2015-09-04",
    "end_date":"2015-09-09",
    "estimated_days_off":3,
    "estimated_hours_off":22.5
  }
}
```
