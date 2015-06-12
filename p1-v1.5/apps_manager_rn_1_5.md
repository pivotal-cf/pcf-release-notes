---
title: Pivotal Cloud Foundry Apps Manager v1.5.0.0 Release Notes
---

## Changes since v1.4.0.0:

### Route change

* After retiring the Developer Console name in v1.4, the hostname 'console' has been deprecated in favor of 'apps'. Traffic to 'console' will be automatically redirected to 'apps' in v1.5. 'console' will be removed entirely in a future release. 

### New features

* The new Accounting Report presents an admin-only view of app instance usage across an instance of Pivotal Cloud Foundry. Monthly average app instance counts and maximum app instance counts are shown for all orgs, minus the `system` org which is used for Pivotal apps like Apps Manager, Auto-scaling, and Notifications.
* Apps Manager honors the 'HAProxy allows HTTPS traffic only' setting in Ops Manager v1.5 and will only show https app routes.
* Per-org Usage Reports are now viewable by users with the Org Auditor role. 

### Performance enhancements

* The Spaces tab on the Org Dashboard has been updated with new features to dynamically load data such as the count and status of each app. 
* Org and space team members and their roles are now populated by a more performant endpoint, which means faster page loads and new user invitations. 
* Both the Apps Manager and App Usage Service BOSH errands have optimizations to shrink deploy time and consume the smallest possible set of resources. 
