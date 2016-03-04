---
title: PCF Developer Console v1.3.0.0 Release Notes
owner: Apps Manager
---

## Changes since v1.2.0.0:

### App dashboard
* Data on the app dashboard is refreshed every 20 seconds. When an update to the app (such as a start, stop, restart, or scale event) has been initiated on the app dashboard, data is refreshed every five seconds until the request is completed. The only exception is the recent logs feature, which requires a refresh to get the latest logs.

### Usage service
* All identical app configurations (where the number of instances and amount of memory are the same) are rolled up into one duration of time.
* The default view is of the current calendar month, with the two previous months available as options.
* Although it cannot be displayed, data on the usage report will be saved beyond the three month window.
* If you delete an app, then push a new app with the same name, they will appear as separate apps.

### Admin-only feature flags
* When the `ENABLE_NON_ADMIN_ORG_CREATION` env variable is set to `false` on the console app, only admin users will be able to create new orgs in Developer Console. This is the default behavior. When it is set to `true`, all users will be able to create new orgs in Developer Console.
* When the `ENABLE_NON_ADMIN_USER_MANAGEMENT` env variable is set to `false` on the console app, only admin users will be able to invite users and manage roles in Developer Console. This is the default behavior. When it is set to `true`, Org Managers and Space Managers will be able to invite users and manage roles in Developer Console.