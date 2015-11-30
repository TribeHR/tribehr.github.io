---
title: 'Version History'

layout: default
---

## Current Version: 2.2.0

### 2.2.0

The **`url`** property is now in the correct format. For example, the URL for User ID 32 is now **`/users/32.json`** / 
**`/users/32.xml`** instead of **`/users/view/32`**. However, some URLs returned from the API may point at
API endpoints which are not implemented.

### 2.1.0

A user's avatar URL may sometimes be an absolute URL pointing directly to S3 instead of being a URL
relative to TribeHR's servers. Avatars with URLs pointing directly to S3 are guaranteed not to change
as long as the S3 URL doesn't change. Avatars with URLs pointing back to TribeHR servers may change at
any time. This means that avatars served directly from S3 will have the dual benefit of being faster to
download and easier to cache.

### 2.0.1

Changed the rules around visibility on the **`User`** resource's **`group`** field. Users can now see their
own group. If a user's group is **`"Managers"`**, they can see the group of all of the users they have 
permission to manage. (See "Permissions and Visibility" below.) If a user's group is **`"Administrators"`**,
they can see the group of all users.

### 2.0.0

Brand new, revamped API!