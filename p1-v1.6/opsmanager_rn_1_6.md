---
title: Pivotal Cloud Foundry Ops Manager v1.6.0 Release Notes
---

## Version 1.6.0 (changes since v1.5.5)

### Major Features

* EBS encryption is now available for AWS deployments.  This enables AWS customers to have encrypted data at rest on persistent disks.
* 

### API Changes
* Previously, Ops Manager provided an API endpoint called `/api/users` that allowed for the creation of multiple user accounts, though only the first one was functional.  To correct this, `/api/users` has been replaced by `/api/setup` that provides the same functionality for creating the first user, but does not attempt to create secondary, tertiary, etc., users, since these user accounts would not be functional.  Please see API documentation at `http://your-ops-man-ip/docs` for more information.  **Please note that the API is not officially support and may change without warning in the future.**

### Security Features

* Multiple CVE fixes per [pivotal.io/security](http://pivotal.io/security)
* VM passwords are now scrubbed from the output logs and replaced with asterisks.

### Minor Features

* On vSphere, the operator is now able to split availability zones by resource pool in the same cluster.

### Bug Fixes

* Coming soon...

### Product Author Features

* New product author documentation has been made available here:  http://docs.pivotal.io/pivotalcf/packaging/index.html

### Notes
Embedded stemcell 3074
