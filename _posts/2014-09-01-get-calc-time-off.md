---
category: Internal
title: 'Calculate Time Off'
type: 'GET'
path: '/leave_requests'

layout: default
---

The mobile app uses this endpoint to present the user with an **estimate** of the number of work days between two dates, so that the users can submit informed time off requests with the 'days' and 'hours' fields populated correctly.
This is the same calculation that gets applied in the web app when a user is submitting or editing a leave request. It takes into consideration weekends, public holidays, and the number of hours the user works per day (in order to return the correct number of hours).

Parameters:
 - **`user_id`** *(int; required)* - The ID of the user for whom we're calculating time off. MUST be the user who submits the API request - you can not perform this calculation on behalf of someone else.
 - **`start_date`** *(ISO-8601 date; required)* - The start date (inclusive) for the time off calculation. Format: yyyyMMdd
 - **`end_date`** *(ISO-8601 date; required)* - The end date (inclusive) for the time off calculation. Format: yyyyMMdd
 
In the example below, the request is submitted by the user with ID 123, who works 7.5 hours per day and resides in Canada. The date range covers a full weekend and Labour Day.
    
```GET /leave_requests/calculateTimeOff.json
X-API-Version: 2.0.0
user_id=123&start_date=20150904&end_date=20150909
```

```Status: 200 OK```
```Content-Type: application/json
{
    "leave_request":{
        "start_date":"20150904",
        "end_date":"20150909",
        "estimated_days_off":3,
        "estimated_hours_off":22.5
    }
}
```