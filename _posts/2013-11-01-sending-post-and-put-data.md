---
category: Intro
title: 'Sending `POST` and `PUT` data'
---

> All `PUT` requests **must** include an `id` parameter in their body text, and it **must** match
> the ID specified in the request's URL. (See `"ID_MISMATCH"` in the Error Handling section.)

All data that you send to TribeHR through the API is form-encoded. For most parameters, this is simple -
just URL-escape your values and do regular form encoding:

    PUT /users/53.json
    id=53&twitter_username=%40tribehr&blog_url=blog_url=http%3A%2F%2Fdevelopers.tribehr.com
Sometimes you'll need to specify values for sub-objects, such as modifying fields in a user's assignment
record. In this case you'll need to use `object[property]` syntax as the key in your form-encoded request
body. (The square brackets in the key should be URL-encoded.) In the following example, we modify a user's phone number, which is part of their assignment record.

    PUT /users/5.json
    id=5&assignment_record%5Bphone%5D=519-555-1234
In other cases, you will need to reference another resource when creating or updating a resource. For example,
Events are associated with Event Types, which are defined in the administration section of the TribeHR web
app. In this case, you should reference the existing resource's ID, usually via a `resource_name[id]` key. 
In the case where you need to specify an array of existing resources (for instance, events can apply to
zero or more locations, which are also defined in the administration section of the web app), you can 
use `resource_name[][id]` key. (Remember to URL-encode the square brackets!) The following example illustrates
both cases, by specifying a single Event Type and multiple Locations.

    PUT /events/252.json
    id=252&name=Updated%20Event&event_type%5Bid%5D=1&location%5B%5D%5Bid%5D=1&location%5B%5D%5Bid%5D=7    
## Differences between POST and PUT
*`POST` requests create new items; `PUT` requests update existing ones.*

`POST` requests are documented below with a list of parameters, some of which may be marked "required."
Unless otherwise documented, the corresponding `PUT` requests for each resource type support all of the
same parameters as the `POST` request, but *all parameters except for `id`* are optional (again, unless
otherwise documented). If you leave a parameter out of a `PUT` request, it means that you do not wish to
change the existing value.

Other validation constraints (such as "date X must occur before date Y") still apply, and will take into
account existing values for any parameters that are not included in the `PUT` request.

For example, if an Event with ID 53 already exists and has start date and end date set to Sept 1, 1:30pm
and Sept 1, 2:30pm respectively, then sending the following `PUT` request that changes the start date will
fail, since the end date would end up *before* the start date:

    PUT /events/53.json
    id=53&start_date=2013-09-01T15:30:00+00:00
> **Remember:** if you fail to supply `id`, or your `id` parameter does not match the ID in the URL, you 
> will be returned a `400` HTTP response with an `"ID_MISMATCH"` error code. (See Error Handling, below.)
