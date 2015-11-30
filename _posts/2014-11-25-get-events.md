---
category: API v2
title: 'Getting Events'
type: 'GET'
path: '/events'

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

**`/events.json`** is an alias to this API endpoint.

```GET /events/upcoming.json
X-API-Version: 2.0.0
```

### Response

```Status: 200 OK```
```Content-Type: application/json
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
]```

### Request
List events that have been marked as official holidays in TribeHR.

Events are sorted by start date ascending, and by default all holidays are returned.

Available Filters:

- **`year`** *(integer, optional)* - you may provide a 4-digit year, to return 
only the events occuring in that year. Includes events which have at least one day in the given year.

```GET /events/holidays.json?year=YYYY
X-API-Version: 2.0.0
```

### Response
```Status: 200 OK```
``` Content-Type: application/json
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

```GET /events/{id}.json
X-API-Version: 2.0.0
```

### Response

```Status: 200 OK```
```Content-Type: application/json
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