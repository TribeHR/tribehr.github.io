---
category: General
path: '/login'
title: 'Authentication'

layout: default
---

Each request **must** include the current user's authentication details, encoded as 
[HTTP Basic Authentication](http://en.wikipedia.org/wiki/Basic_access_authentication); that is, each
request must include an **`Authorization: Basic xxxx`** header, where **`xxxx`** is the [Base64](http://en.wikipedia.org/wiki/Base64)
encoding of a string constructed as **`identifier:secret`**, where **`identifier`** is either the user's username
or email, and **`secret`** is either the user's password or their API key.

> We **strongly** suggest that you use a user's API key to authenticate them, since it decreases the 
> attack surface that a hacker can use to steal their password, which the user may be using on more than
> one site.

A user's API key can be found on the edit page for their employee profile (**`https://[subdomain].mytribehr.com/users/edit/{user_id}/account`**).
Alternatively, you can make an API request (authenticating using the user's password, naturally) to
**`/users/me.json?requireApiKey=true`** (as documented in the Users section, below). The response to this
request will include the user's API key, generating one automatically if they don't already have one.
