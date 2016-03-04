---
title: Ops Manager 1.3 Release Notes
owner: Ops Manager
---

## Operator Features

**Operators can...**

* modify Static IPs for products with jobs that expose them
* change instance counts and Static IPs will be recalculated and reassigned
* specify more than one network for an installation
* designate a specific network to deploy individual products
* see IP addresses for multiple networks on product status pages
* be protected from entering IP addresses that clash across products and networks
* specify which network is designated as Infrastructure vs. Deployment for Director
* be protected from changing deployment networks (Agents would be orphaned)
* change networks for any product before or after installation occurs
* deploy to networks and availability zones without configuring them when only one exists
* see helpful instructions if there are no networks or availability zones
* specify more than one availability zone (cluster + resource pool) for an installation
* balance jobs across availability zones on deployment
* re-balance jobs across availability zones if an availability zone is added or removed
* see which availability zones an instance resides on product status pages
* automatically upgrade to latest Director without needing to click "Add"
* install the most recent version by default if there is more than one Director
* be protected from reverting to old versions of Director
* use Ops Manager with some particular optimized pages (load times)
* specify a vCenter folder for my network
* make changes to networks that impact other settings without reference problems
* make changes to availability zones that impact other settings without reference problems
* specify which availability zone in which to place singleton jobs
* specify which availability zones in which to balance multi-instance jobs
* have older releases cleaned out of blobstores after installations complete

## Product Author Features

**Product Authors can...**

* add products to installations via API
* display slug fields in collection forms
* use drop-down property types
* use Ops Manager templating format rather than ERB
* specify the Ops Manager version to target
* use more than one verifier per form
* see the Ops Manager SHA in the debug page
* use Ops Manager templating to reference Director deployment_ip and NTP settings

## Bug fixes

* Logs can be downloaded.
* NFS server manifest corrections.
* Collection subfields can be optional.
* Resource pools are optional.
* Integers and booleans in collections work properly.
* Multi-select in collections work properly.
* Configuring products before Director works properly.
* Saving forms dims entire page rather than top 3/4.
* Secrets will not be confused with scientific notation (Java YAML problem).
* Clusters and resource pools are verified before installation.
* Networks are verified before installation.
* Configured status for products works properly.
* Dynamic IP allocation works properly.
