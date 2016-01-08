---
title: Pivotal Cloud Foundry&reg; Ops Manager v1.6 Release Notes
---

## v1.6.6 patch release:
Ops Manager 1.6.6 includes patches for Ubuntu Security Notice USN-2857-1. (Embedded stemcell 3146.2, Ops Manager build 236fca1)

## v1.6.5 patch release:
Ops Manager 1.6.5 includes patches for a bug that can render important information in log files as a series of asterisks. (Embedded stemcell 3146 - same as 1.6.4, Ops Manager build c79b317)

## v1.6.4 patch release:
Ops Manager 1.6.4 includes patches for Ubuntu Security Notices USN-2821 and USN-2820-1. (Embedded stemcell 3146, Ops Manager build 511c28f)

## v1.6.3 patch release:
Ops Manager 1.6.3 includes patches for Ubuntu Security Notices USN-2815-1, USN-2812-1 and USN-2810-1.  (Embedded stemcell 3144, Ops Manager build c47f94)

## v1.6.2 patch release:
Ops Manager 1.6.2 includes patches for Ubuntu Security Notices USN-2806-1 and USN-2798-1.  (Embedded stemcell 3130, Ops Manager build 6042e5)

## v1.6.1 patch release:
Ops Manager 1.6.1 is the security patch rollup for November 2015.  (Embedded stemcell 3112)

## Version 1.6.0 (changes since v1.5.5)

### Major Features

* EBS encryption is now available for AWS deployments. This enables AWS customers to have encrypted data at rest on persistent disks.

### API Changes
* Previously, Ops Manager provided an API endpoint called `/api/users` that allowed for the creation of multiple user accounts, though only the first one was functional. To correct this, `/api/users` has been replaced by `/api/setup` that provides the same functionality for creating the first user, but does not attempt to create secondary, tertiary, etc., users, since these user accounts would not be functional. Please see API documentation at `http://your-ops-man-ip/docs` for more information. **Please note that the API is not officially supported and may change without warning in the future.**

### Security Features

* Multiple CVE fixes per [pivotal.io/security](http://pivotal.io/security).
* VM passwords are now scrubbed from the output logs and replaced with asterisks.

### Minor Features

* On vSphere, the operator is now able to split availability zones by resource pool in the same cluster.

### Bug Fixes

* Credentials no longer shows incorrect credentials when "Use default BOSH password" is selected.
* Upgrades no longer fail if product version contains a dash.
* A migration that exists but is null no longer results in a 500 error.

### Product Author Features

* New product author documentation has been made available here: http://docs.pivotal.io/pivotalcf/packaging/index.html

### Notes
Embedded stemcell in 1.6.0 is 3100
