---
category: General
title: 'Known Issues'
layout: default
---

- Some URLs returned in API responses point to API endpoints which are not implemented.

- In some cases API returns the wrong HTTP code "404 NOT FOUND" instead of "403 FORBIDDEN" if the user doesn't have the authorization for the requested source. 
  In these cases the correct error message is also missing. 