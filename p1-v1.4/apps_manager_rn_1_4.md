---
title: Pivotal Cloud Foundry Apps Manager v1.4.0.0 Release Notes
---

## Changes since v1.3.0.0: 

### New name

* Apps Manager is the new name of Developer Console. 
* The push-console errand has been renamed push-apps-manager. 

### Less configuration and quicker deploys

* Apps Manager now uses the Notifications service to send registration, invitation, and password reset emails.  
* Previous versions of Apps Manager required three apps to function: the main app, the scheduler app, and the workers app. In v1.4, Apps Manager has been reduced to just the main app. Various refactoring efforts have also removed unused code from the main app. 
* As a result, the time to deploy Apps Manager is significantly faster in v1.4. 

### App dashboard 

* New streaming logs feature enables developers to monitor app and platform activity in real-time from the browser. 
* New usability improvements include better workflows for creating and binding service instances, seeing when an app was last pushed, seeing which buildpack was used to deploy, viewing recent logs, viewing and managing env variables, and viewing all system-set env variables. 
* Users with the space auditor role can now see events, logs, and a read-only list of bound service instances. 

### Org dashboard

* Adding new roles to an existing user is now possible via the invitation flow. 
* Org quota usage is now refreshed every 30 seconds and calculated from a new Cloud Controller endpoint. 

### Usage service 

* The usage report has a new streamlined design. 
* New feature exposes service usage events as a billing metric for internal chargeback or showback.
* New security constraints limit access to the Usage Service and Usage Report to users with the Org Manager role (per org) or cloud_controller.admin scope (all orgs).

### Admin-only feature flags 
* When the `ENABLE_NON_ADMIN_ORG_CREATION` env variable is set to `false` on the apps-manager app, only admin users will be able to create new orgs in Apps Manager. This is the default behavior. When it is set to `true`, all users will be able to create new orgs in Apps Manager. 
* When the `ENABLE_NON_ADMIN_USER_MANAGEMENT` env variable is set to `false` on the apps-manager app, only admin users will be able to invite users and manage roles in Apps Manager. This is the default behavior. Also, users will not be able to access the registration or password reset pages. When it is set to `true`, Org Managers and Space Managers will be able to invite users and manage roles in Apps Manager. 