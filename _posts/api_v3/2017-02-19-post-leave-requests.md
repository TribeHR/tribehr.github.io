---
category: API v3
title: 'Creating Leave Requests'
type: 'POST'
api_path: '/leave_requests'

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

- **`:date_start`** *(date; required)* - the date of the first day of leave. Use ISO date format(YYYY-MM-DD).
- **`:date_end`** *(date; required)* - the date of the last day of leave. Use ISO date format(YYYY-MM-DD).
- **`:days`** *(integer; either **`days`** or **`hours`** must be present, but not both)* - the number of working days.
  that this leave request represents. If **`hours`** is also present, the value of **`days`** will be ignored.
- **`:hours`** *(integer; either **`days`** or **`hours`** must be present, but not both)* - the number of working hours.
  that this leave request represents. If **`days`** is also present, its value will be ignored in favour of the
  value of **`hours`**.
- **`:status`** *(string; defaults to **`"PENDING"`**)* The status of the leave request. Users submitting a request on 
  behalf of a subordinate may supply **`"PENDING"`** or **`"REJECTED"`** or **`"APPROVED"`**,
- **`:user_id`** *(integer; defaults to currently authenticated user)* - the user to whom this leave request applies.
- **`:leave_type_id`** *(integer; required)* - the ID of the type of leave being requested. See **`/leave_types.json`**.
- **`:comments`** *(string)* - Text written by the employee addressed to their manager.

```
POST /leave_requests.json
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0
Content-Type: application/x-www-form-urlencoded

comments=I%27m%20off%20to%20visit%20my%20familyi%21&
date_start=2017-03-04&
date_end=2017-03-06&
days=2&
user_id=4&
leave_type_id=1
```

### Response
```
Status: 200 OK
```

```
{
	"id": 194,
	"comments": "I'm off to visit my family!",
	"date_start": "2017-03-04",
	"date_end": "2017-03-06",
	"days": 2,
	"hours": 15,
	"status": "PENDING",
	"created": "2017-03-20T12:15:48+00:00",
	"modified": "2017-03-20T12:15:48+00:00",
	"url": "/leave_requests/194.json",
	"user": {
		"id": "4",
		"username": "Javier",
		"avatar": {
			"url": "/attachments/view/User/avatar/4"
		},
		"email": "testing@ribbitco.biz",
		"display_name": "Javier Nold",
		"assignment_record": {
			"current": true,
			"url": "/assignment_records/165.json"
		},
		"employee_record": {
			"first_name": "Javier",
			"last_name": "Nold",
			"url": "/employee_records/128.json"
		},
		"url": "/users/4.json"
	},
	"leave_type": {
		"id": 1,
		"name": "Vacation",
		"accrual": "MONTHLY",
		"url": "/leave_types/1.json"
	}
}
```