---
category: General
title: 'Data Types'
---


We use the following data types in the documentation below as a shorthand. JSON technically only
supports, strings, numbers, arrays, and objects, so the data types all map to these in some way.

- Strings and numbers (integers and floating point numbers) can be represented natively in JSON, so
  no format translation is required
- Rich text is represented by a BBCode string, or, optionally, an HTML string. See "Rich Text" below for
  details.
- Booleans are represented in JSON responses as native `true` and `false` values, but when sending
  form-encoded requests to the API, they should be represented by integers; they must either be `0` or `1`
- Dates and Date/Times should be represented by strings adhering to [ISO 8601](http://xkcd.com/1179/)
  (details on [W3.org](http://www.w3.org/TR/NOTE-datetime))

> **A note on dates and date/times**
>
> TribeHR distinguishes between dates (formatted as `2013-09-30`) and date/times (formatted as
> `2013-09-30T14:39:21+00:00`), so make sure your parser is able to distinguish between the two.
> A common pitfall is to parse `2013-09-30` as "Midnight on Sept 30, 2013, UTC," which when translated
> to the local time zone can unintentionally actually yield a different date.
>
> Because of this, dates should be treated almost like a string literal - no time calculations should
> be performed on them; while date/times should be treated as usual and should be translated to the 
> appropriate time zone before being displayed to the user.

## Always-local date/times

Some dates in TribeHR are meant to be treated as always-local, regardless of where in the world a
particular user is. For example, in the TribeHR web app, start and end date/times for Company Events
do not have a time zone associated with them, and regardless of user or location, always show the 
exact same time of day for everyone. These are represented in the API by a slight modification on
the ISO 8601 format, by omitting the time zone information at the end of the date string. For example:
`2012-09-30T14:39:21`

## Rich Text

Some resources in TribeHR include rich text properties; for instance the `text` property of the `kudos`
resource is a rich text field. 

When sending data to the TribeHR API via a `PUT` or `POST`, the value that you send for a rich text field
**must** either be a plaintext string or a [BBCode](http://en.wikipedia.org/wiki/BBCode) string. We *do
not support* API clients sending HTML strings to TribeHR. TribeHR supports a subset of all BBCode tags;
see "BBCode" below for details.

When requesting resources that include rich text fields, you can include a `formattedTextAs` query 
parameter to specify how the rich text should be represented in the response. Valid values for this query
parameter are `html` and `bbcode`, where `bbcode` is the default.

> Note that `formattedTextAs` *only* has an effect on output. Input should always be plain text 
> or BBCode.

### BBCode

TribeHR supports a subset of all BBCode tags. The following tags are supported:
- `[b]` - bold
- `[i]` - italic
- `[u]` - underline
- `[url]` - hyperlink
- `[email]` - mailto: hyperlink
- `[hr]` - horizontal rule
- `[color]` - font color
- `[size]` - font size
- `[ul]` - unordered list
- `[ol]` - ordered list
- `[li]` - list item
- `[left]` - left-aligned block
- `[right]` - right-aligned block
- `[center]` - center-aligned block
- `[code]` - text styled in monospace as "code"
- `[quote]` - text styled as a blockquote
