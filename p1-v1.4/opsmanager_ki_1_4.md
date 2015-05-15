---
title: Pivotal Cloud Foundry Ops Manager v1.4.0.0 Known Issues
---

## New Issues

Some of these issues have been fixed in subsequent patch releases to 1.4. Consult release notes for more info.

* Compiled Packages are missing from installation exports, which can cause a failure if the product contained and referenced them. A fix is to SSH into the Ops Manager VM and remove references to compiled_packages in every file located in /var/tempest/workspace/metadata directory.
* Thin Web Server timeout needs to be increased to 30 minutes to prevent export failures.
* This version improperly places singleton jobs into balanced zones.
* PCF products with Ruby BOSH Agent Stemcells must be upgraded prior to importing into this version of Ops Manager
* Ops Manager 1.4 does not support the installation of Pivotal HD.
* IP reassignment must be handled by scaling a job down to zero instances and re-entering new IP addresses before scaling the job back up
* DNS and Gateway ICMP errors will occur on AWS even if ICMP is allowed
* Unnecessary job instances must be reduced manually (MySQL, HA Proxy if RDS & ELBs are used)
* Multiple users browsing Ops Manager at the same time can cause locking issues

## Existing issues

* Resource Pools cannot be deleted from Availability Zones. If a resource pool is inadvertently deleted, run `BOSH recreate`.
