---
title: Pivotal Cloud Foundry Ops Manager v1.4.0.0 Known Issues
---

## New issues

* PCF products with Ruby BOSH Agent Stemcells must be upgraded prior to importing into this version of Ops Manager
* IP reassignment must be handled by scaling a job down to zero instances and re-entering new IP addresses before scaling the job back up
* DNS and Gateway ICMP errors will occur on AWS even if ICMP is allowed
* Unnecessary job instances must be reduced manually (MySQL, HA Proxy if RDS & ELBs are used)
* Multiple users browsing Ops Manager at the same time can cause locking issues

## Existing issues

* Resource Pools cannot be deleted from Availability Zones. If a resource pool is inadvertently deleted, run `BOSH recreate`.
