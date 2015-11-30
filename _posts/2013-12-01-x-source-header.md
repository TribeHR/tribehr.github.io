---
category: General
title: 'X-Source Header'
---

Some of the resources available in the TribeHR API support the concept of a source - that is, they keep
track of where they came from. TribeHR uses this functionality internally in order to apply "via TribeHR
for iOS" tags to kudos and comments that originate from our 
[iPhone app](https://itunes.apple.com/us/app/tribehr-for-ios/id692120052).

You can opt to send an *X-Source* header with your request in order to get similar treatment in TribeHR.
Sources **must** represent the name of the consumer of the API, and may be any string; they **must not**
change from request to request, and they **must** be identical for all users of the same API consumer or app.

The following resources support the X-Source header:

- Kudos
- Comments
- **Note:** The source is applied to resources on their creation; sending an `X-Source` header with a `PUT` request
does not change a resource's source property.