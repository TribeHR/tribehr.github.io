---
category: General
title: 'XML vs JSON'
---

The TribeHR API responds to requests with a response either formatted as JSON or XML. Both are supported
equally, but for simplicity the rest of this documentation refers only to the JSON output. TribeHR decides
which format to send you depending on the end of the URL you send. A URL ending in `.json` will return
JSON; a URL ending in `.xml` will return XML.

Input to the API is always form-encoded, and never JSON or XML encoded.