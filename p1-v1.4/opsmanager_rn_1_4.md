---
title: Pivotal Cloud Foundry Ops Manager v1.4.0.0 Release Notes
owner: Ops Manager
---

## v1.4.2 patch release:

Ops Manager 1.4.2.0 fixes a problem in both 1.4.0.0, and 1.4.1.0, in which jobs with persistent disk, known as 'singletons,' are improperly placed in the first availability zone for balanced jobs. As of 1.4.2.0 jobs will be properly placed in the singleton availability zone.

## v1.4.1 patch release:

Ops Manager 1.4.1.0 has an increased timeout setting of 30 minutes for thin web server to prevent exports from failing.

## Changes since v1.3.4.0:

### Major Features

* AWS support
* Ops Manager saves its state to an EBS volume
* A new field exists to input an SSH key pair name and value
* New Selector field allows for different sets of fields to be chosen
* Resource page for IaaS that have instance types shows a list of instance types with defaults
* Delete installation is performed via BOSH delete rather than writing directly to IaaS API
* Pre-delete errands can be toggled on or off
* All instance types use EBS for ephemeral disk
* S3 blobstores are supported for products and Ops Manager Director
* External MySQL supported for products and Ops Manager Director
* Validation of values works in selectors
* Elastic Load Balancer support
* Compilation VMs are re-used
* Installation files no longer include the bloat of stemcells of compiled packages
* Importing installation files into the wrong IaaS is handled gracefully
* Verifiers built for S3 and MySQL

### Security Features

* Private key files are destroyed
* Multiple CVE fixes per pivotal.io/security

### Bug Fixes

* Ops Manager allocates enough IPs for compilation VMs
* Jobs can be scaled down with static IPs
* MicroBOSH DNS is no longer prepended to the DNS list in any manifest
* AZ Verifiers on vCD do not fail
* Boolean properties can be defaulted to 'true'
* Null byte errors during errands
* Ruby errors removed from BOSH install log
* NGINX Upload modules included across IaaS
* Compilation VMs have adequate sizes
* Uploads increased to 15GB

### Product Author Features

* Product templates offer an `ips_by_availability_zone` with a hash of AZs and IPs
* Product templates offer nested properties available in manifest snippets
* Pre-delete errands can be configurable in the UX
* Deletes are handled via API
* Stemcells can be assigned by API call
