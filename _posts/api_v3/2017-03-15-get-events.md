---
category: API v3
title: 'Getting Events'
type: 'GET'
api_path: '/events'

layout: default
---

### Request

- The **`:notes`** field is a Rich Text field, but currently does not support BBCode. Therefore, the **`:notes`**
field may return an HTML string, but API consumers should only use plain text in **`POST`** and **`PUT`**
requests.
- Includes events that are currently ongoing (their start date is in the past but their end date is in the
future) and events that start in the future.
- Events are sorted by start date, and the response contains all "upcoming" events (as defined above) or
the 50 soonest "upcoming" events, whichever is less.
- Birthdays, anniversaries are not included in response. 

**`/events.json`** is an alias to this API endpoint.

```
GET /events/upcoming.json
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
        "id": 20,
        "name": "Company Picnic",
        "start_date": "2013-08-29T11:00:00+00:00",
        "end_date": "2013-08-29T14:30:00+00:00",
        "notes": "<p>We'll have some BBQs on the lawn behind the building.</p>\r\n<p>Hope to see you there!</p>",
        "url": "/events/20.json",
        "event_type": {
            "id": 1,
            "name": "Lunch",
            "url": "/event_types/1.json"
        },
        "locations": {
            "id": 3,
            "name": "London Office [Product and Development]",
            "url": "/locations/view/3.json"
        }
    },
    {
        "id": 252,
        "name": "Product Launch",
        "start_date": "2013-08-30T17:00:00+00:00",
        "end_date": "2013-08-30T22:00:00+00:00",
        "notes": "<p>Spouses and significant others are welcome, too!</p>",
        "url": "/events/252.json",
        "event_type": {
            "id": 2,
            "name": "Company Gathering",
            "url": "/event_types/2.json"
        },
        "locations": {
            "id": 3,
            "name": "London Office [Product and Development]",
            "url": "/locations/view/3.json"
        }
    }
]
```

### Request
List of all upcoming event. Data are filtered according to users permissions.

Events are sorted by start date ascending, and by default all holidays are returned.

Available Filters:

- **`days`** *(integer, optional)* *default:30* - count of days you want to see.

```
GET /calendar/upcoming.json?days=30
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
    "type": "company_event",
    "title": "Big Company Event",
    "description": "rest",
    "recurrence": null,
    "start_date": "2017-03-30T14:16:00",
    "end_date": "2017-03-31T14:16:00",
    "event": {
      "id": 34,
      "name": "Big Company Event",
      "notes": "<p>Awesome description</p>",
      "url": "/events/34.json",
      "start_date": "2017-03-30T14:16:00",
      "end_date": "2017-03-31T14:16:00",
      "event_type": {
        "id": 3,
        "name": "Training Day",
        "url": "/event_types/3.json"
      }
    }
  },
  {
    "type": "birthday",
    "title": "Althea Cienfuegos",
    "description": "Birthday",
    "recurrence": "yearly",
    "start_date": "2017-04-04",
    "end_date": null,
    "first_occurrence": "1973-04-04",
    "user": {
      "id": "15",
      "username": "Althea",
      "avatar": {
        "url": "/attachments/view/User/avatar/15"
      },
      "email": "FakeEmail+13@ribbitco.biz",
      "display_name": "Althea Cienfuegos",
      "employee_record": {
        "first_name": "Althea",
        "last_name": "Cienfuegos",
        "url": "/employee_records/109.json"
      },
      "url": "/users/15.json"
    }
  },
  ...
 ]
```

### Request
List events that have been marked as official holidays in TribeHR.

Events are sorted by start date ascending, and by default all holidays are returned.

Available Filters:

- **`year`** *(integer, optional)* - you may provide a 4-digit year, to return 
only the events occuring in that year. Includes events which have at least one day in the given year.

```
GET /events/holidays.json?year=YYYY
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
    "id": 12,
    "name": "New Year's Day",
    "notes": "<p>Official Holiday, no work.<\\/p>",
    "url": "/events/view/12",
    "start_date": "2013-01-01T00:00:00",
    "end_date": "2013-01-01T00:00:00",
    "event_type": {
      "id": 5,
      "name": "Official Holiday",
      "url": "/event_types/view/5.json"
    },
    "locations": [
      {
        "id": 2,
        "name": "Corporate Office [Headquarters]  ",
        "url": "/locations/view/2.json"
      }
    ]
  },
  {
    "id": 33,
    "name": "Boxing Day",
    "notes": "<p>Official Holiday, no work.<\\/p>",
    "url": "/events/view/33",
    "start_date": "2013-12-26T00:00:00",
    "end_date": "2013-12-26T00:00:00",
    "event_type": {
      "id": 5,
      "name": "Official Holiday",
      "url": "/event_types/view/5.json"
    },
    "locations": [
      {
        "id": 3,
        "name": "London Office [Product and Development]",
        "url": "/locations/view/3.json"
      }
    ]
  }
]
```

### Request

View details about an individual event.

```
GET /events/{id}.json
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
  "id": 252,
  "name": "Fun Family Event",
  "notes": "<p>Spouses and significant others are welcome, too!</p>",
  "is_official_holiday": false,
  "created": "2013-01-28T11:41:07+00:00",
  "modified": "2013-01-28T11:41:07+00:00",
  "url": "/events/view/12",
  "start_date": "2013-08-30T00:00:00",
  "end_date": "2013-08-30T00:00:00",
  "event_type": {
    "id": 5,
    "name": "Official Holiday",
    "url": "/event_types/view/5.json"
  },
  "locations": [
    {
      "id": 2,
      "name": "Corporate Office [Headquarters]  ",
      "url": "/locations/view/2.json"
    }
  ]
}
```