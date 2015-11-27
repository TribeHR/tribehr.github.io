---
category: Intro
title: 'Making API Requests'
---

TribeHR differentiates API requests from regular web requests based on the end of the URL. TribeHR assumes
that any request ending with `.json` or `.xml` is an API request; all other requests are treated as 
regular web requests and are returned as HTML.

All requests made against API v2 **must** include the `X-API-Version` header. Otherwise your request
will be treated as an API v1 request, and you will miss out on improvements, modifications, and new 
features that will be made available in the future.

All requests **must** be made over HTTPS. Regular HTTP requests are automatically redirected to HTTPS but
relying on this behaviour is a bad idea for [security reasons](https://www.owasp.org/index.php/Transport_Layer_Protection_Cheat_Sheet#Rule_-_REMOVED_-_Do_Not_Perform_Redirects_from_Non-TLS_Page_to_TLS_Login_Page).
