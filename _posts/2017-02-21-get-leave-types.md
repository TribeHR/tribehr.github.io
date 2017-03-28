---
category: 'API v3' 
title: 'Getting Leave Types'
type: 'GET'
path: '/leave_types'

layout: default
---

The following endpoint and options can be used to read leave types records from TribeHR. 


## List all Leave Types

Show all leave types defined in TribeHR, in the order in which they were created.

### Request

Get all leave types in TribeHR

```
GET /leave_types.json
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
		"id": 1,
		"name": "Vacation",
		"accrual": "MONTHLY",
		"url": "/leave_types/1.json"
	},
	{
		"id": 2,
		"name": "Sick",
		"accrual": "NONE",
		"url": "/leave_types/2.json"
	},
	{
		"id": 3,
		"name": "Training",
		"accrual": "NONE",
		"url": "/leave_types/3.json"
	},
	{
		"id": 4,
		"name": "Unpaid Leave",
		"accrual": "NONE",
		"url": "/leave_types/4.json"
	}
]
```


## Get Selected Leave Requests

View details about selected Leave Type.

### Request

Get selected leave type in TribeHR

```
GET /leave_requests/1.json
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
	"id": 1,
	"name": "Vacation",
	"accrual": "MONTHLY",
	"action_phrase": "Schedule Vacation",
	"unpaid": false,
	"created": "2010-03-01T17:25:05+00:00",
	"modified": "2013-01-15T16:06:14+00:00",
	"url": "/leave_types/1.json"
}
```