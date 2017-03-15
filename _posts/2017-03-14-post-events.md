---
category: API v3
title: 'Create a New Event'
type: 'POST'
path: '/events'

layout: default
---

Parameters:

- **`name`** *(string; required; must be at least two characters long)* - the name of the event
- **`notes`** *(string; HTML allowed)* - description or other text related to the event
- **`start_date`** *(date/time; required)* - the date and time of the start of the event
- **`end_date`** *(date/time; required)* - the date and time of the end of the event; must be later than the start date.
- **`is_official_holiday`** *(boolean; defaults to false)* - whether this event should be excluded from leave request calculations
- **`event_type[id]`** *(integer; defaults to first event found in the system)* - the ID of the type of event. (Event types are set up in the administration section of the TribeHR web app.)
- **`location[][id]`** *(integer; zero or more **`location[][id]`** parameters may be present)* - the ID(s) of the locations to which this event applies. (Locations are set up in the administration section of the TribeHR web app.)

### Request

```
POST /events.json
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0

name=New%20event&
start_date=2013-08-30T17%3A00%3A00%2B00%3A00&
end_date=2013-08-30T22%3A00%3A00%2B00%3A00&
location[][id]=1&
location[][id]=7&
notes=HTML%20description%20of%20new%20event&
is_official_holiday=1&
event_type[id]=1
```

### Response
```
Status: 200 OK
Content-Type: application/json
```

```
{
    "id": 254,
    "name": "New event",
    "start_date": "2013-08-30T17:00:00+00:00",
    "end_date": "2013-08-30T22:00:00+00:00",
    "notes": "HTML description of new event",
    "is_official_holiday": true,
    "created": "2013-08-19T18:02:04+00:00",
    "modified": "2013-08-19T18:02:04+00:00",
    "url": "/events/254.json",
    "event_type": {
        "id": 1,
        "name": "Lunch",
        "url": "/event_types/1.json"
    },
    "locations": [
        {
            "id": 1,
            "name": "Central Rental",
            "url": "/locations/1.json"
        },
        {
            "id": 7,
            "name": "Headquarters",
            "url": "/locations/7.json"
        }
    ]
}
```