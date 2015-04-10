---
title: Pivotal Cloud Foundry Ops Manager v1.4.0.0 Release Notes
---

## Changes since v1.3.4.0:

### Major Features

* AWS support
* Ops Manager saves its state to an EBS volume
* A new field exists to input an SSH keypair name and value
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
* Installation files nolonger include the bloat of stemcells of compiled packages
* Importing installation files into the wrong IaaS is handled gracefully
* Verifiers built for S3 and MySQL

### Security Features

* Private key files are destroyed
* Multiple CVE fixes per pivotal.io/security

### Bug Fixes

* Ops Manager allocates enough IPs for compilation VMs
* Jobs can be scaled down with static IPs
* MicroBOSH DNS is nolonger prepended to the DNS list in any manifest
* AZ Verifiers on vCD do not fail
* Boolean properties can be defaulted to 'true'
* Null byte errors during errands
* Ruby errors removed from BOSH install log
* NGINX Upload modules inclded across IaaS
* Compilation VMs have adequate sizes
* Uploads increased to 15GB

### Product Author Features

* Product templates offer an `ips_by_availability_zone` with a hash of AZs and IPs
* Product templates offer nested properties available in manifest snippets
* Pre-delete errands can be configurable in the UX
* Deletes are handled via API
* Stemcells can be assigned by API call
