---
category: General
title: 'Permissions and Visibility'

layout: default
---

All API requests are made on behalf of the user represented by the HTTP Basic Authentication information
that is included in each request. All resources in TribeHR are subject to authorization and visibility
checks. Some users will not have permission to see certain resources, and some users will have 
permission to see resources which have properties which they are *not* allowed to see.

**Any information that the user does not have permission to see will be *absent* from any API requests.**

This is in contrast to information that is *present*, but the value of which is empty or null.  Empty
or null data always means that the user has visibility on that data, but the value is literally empty
or null.

## User Groups
Each user is assigned to a particular group: **`Employees`**, **`Managers`**, or **`Administrators`**. 

- Administrators have access to all data in TribeHR. 

- Employees have access to all data whose privacy is marked "Everyone". Employees also have access to 
  data that is owned by them and marked as "Manager and Employee".

- Managers have access to all data whose privacy is marked "Everyone". Managers also have access to data
  belonging to other users based on the management style.

Details about what information a given user has permission to see or act upon is documented in 
[this FAQ](https://tribehr.zendesk.com/entries/21611308-Who-can-see-what-privacy-settings-in-TribeHR-).
