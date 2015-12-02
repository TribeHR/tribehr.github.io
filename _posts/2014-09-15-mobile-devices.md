---
category: Internal
title: 'Mobile Devices'
type: 'POST'
path: '/mobile_devices'

layout: default
---

The mobile app uses this API in order to register the user's device with TribeHR 
in order to support push notifications, as well as providing a list of devices
that the user has signed into the iOS app on.

Add or Update Mobile Device Registration

This endpoint deviates from the pattern we've established of **`POST`** requests 
creating resources (and thus being non-idempotent) and **`PUT`** requests being
used to update existing resources. In the case of this endpoint, we do not
expect the API consumer to know whether the device registration is being created
or updated; so we use a **`POST`** request for both.

In order to update an existing mobile device registration, the **`POST`** request
must include the same **`device_identifier`**. If a mobile device is already registered
with the same **`device_identifier`**, its record will be updated; otherwise a new
record will be created.

In both cases, the API response is identical.

**Note** that if a different user already has a device registered with the
**`device_identifier`** specified in the request, that user's registration will be
deleted, and a *new* device registration will be created based on the request.
(This is because **`device_identifier`** must be unique.) In this particular case, 
a delete followed by a create occurs; not an edit. This is in order to protect 
the privacy of the other fields (such as device name) that belonged to the old 
user.

Parameters:

 - **`device_identifier`** *(string; required; unique)* - a unique device identifier
 - **`notification_token`** *(string; required)* - the token required to send push notifications to this device
 - **`operating_system`** *(string; required)* - must be **`"ios"`** or **`"android"`**
 - **`device_model`** *(string)* - the model of the mobile device, eg **`"iPhone 5s"`**
 - **`device_name`** *(string)* - a name for the device. In the case of iOS devices, this should ideally match the name that appears in iTunes
 - **`mobile_app_version`** *(string)* - the version of the mobile app sending the request, eg **`"1.2.0"`**

```POST /mobile_devices.json
X-API-Version: 2.0.0
device_identifier=some-device-id&
notification_token=some-notification-token&
device_model=iPhone%205s&operating_system=ios&device_name=Jason%20Smith%27s%20iPhone
```

```Status: 200 OK```
```Content-Type: application/json
{
    "success": {
        "code": "CREATED",
        "messages": [
            "The Mobile Device was successfully registered"
        ]
    }
}
```