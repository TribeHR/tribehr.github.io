---
category: General
title: 'Representations of Resources'
---

All resources have exactly two representations that may be returned to you by the API: the full object,
and the partial object.

> All representations of resources are subject to visibility. An object will not be returned if the user
> does not have permission to access it; a field in an object will not be returned if the user has permission to 
> access the object, but not that individual field.

- **Full Object** - this representation includes all available information about a given resource. This
  representation is returned as part of a request that asks for a *specific object* of that resource's
  type.  For instance, the full object representation of a user would be returned by a request to
  `/users/12.json`
  
- **Partial Object** - this representation is a strict subset of the full object representation of a
  given resource. This representation is returned from requests to a collection of objects (eg, `/users.json`),
  or when an object is returned *contained inside* another object. For example, a Kudos object *contains*
  a user object in its `poster` property. When the full object representation of a kudos is fetched,
  it includes a *partial object representation of the poster* as part of the kudos object.
  
> There is only one root object in each response. This object may be an array containing other objects,
> or it may be a single object that may contain sub-objects. But if multiple objects are returned from
> a single request, they are always *nested* inside something else.