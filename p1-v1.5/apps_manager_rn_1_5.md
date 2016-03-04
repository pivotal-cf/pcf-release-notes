---
title: Pivotal Cloud Foundry Apps Manager v1.5 Release Notes
owner: Apps Manager
---

## v1.5.1.0 patch release:

* Fixed a bug where the version of Apps Manager in the page footer now correctly shows v1.5.
* Fixed a bug so that invitations created before the change from the 'console' subdomain to the 'apps' will now succeed.
* Fixed the following security vulnerabilities: [CVE-2015-1840](https://groups.google.com/forum/#!msg/rubyonrails-security/XIZPbobuwaY/fqnzzpuOlA4J), [CVE-2015-3225](https://groups.google.com/forum/#!msg/rubyonrails-security/gcUbICUmKMc/qiCotVZwXrMJ), [CVE-2015-3226](https://groups.google.com/forum/#!msg/rubyonrails-security/7VlB_pck3hU/3QZrGIaQW6cJ), and [CVE-2015-3227](https://groups.google.com/forum/#!msg/rubyonrails-security/bahr2JLnxvk/x4EocXnHPp8J )

## Changes since v1.4.0.0:

### Route change

* After retiring the Developer Console name in v1.4, the hostname 'console' has been deprecated in favor of 'apps'. Traffic to 'console' will be automatically redirected to 'apps' in v1.5. 'console' will be removed entirely in a future release.

### New features

* The new Accounting Report presents an admin-only view of app instance usage across an instance of Pivotal Cloud Foundry. Monthly average app instance counts and maximum app instance counts are shown for all orgs, minus the `system` org which is used for Pivotal apps like Apps Manager, Auto-scaling, and Notifications.
* Apps Manager now only shows `https` app routes.
* Per-org Usage Reports are now viewable by users with the Org Auditor role.

### Performance enhancements

* The Spaces tab on the Org Dashboard has been updated with new features to dynamically load data such as the count and status of each app.
* Org and space team members and their roles are now populated by a more performant endpoint, which means faster page loads and new user invitations.
* Both the Apps Manager and App Usage Service BOSH errands have optimizations to shrink deploy time and consume the smallest possible set of resources.
