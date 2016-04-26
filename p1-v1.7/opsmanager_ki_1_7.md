---
title: Pivotal Cloud Foundry&reg; Ops Manager v1.7.0 Known Issues
owner: Ops Manager
---

## New Issues

Some of these issues may be fixed in subsequent patch releases to 1.7. Consult the Ops Manager 1.7 [Release Notes](opsmanager_rn_1_7.html) for more information.

* Ops Manager 1.7.0 limits the integration with products like CA Siteminder in that a single BOSH Director and Ops Manager can be registered. This limitation will be addressed in 1.7.1.
* Ops Manager uses new instance sizes on vSphere that may result in higher capacity VMs being deployed
* The initial setup of Ops Manager should be done using a FQDN via DNS as the UAA will use the address for redirects. If the initial setup of Ops Manager is performed by accessing Ops Manager via an IP address or URL that you do not control - that address must not change.

## Existing Issues

* If EBS encryption is initially disabled, and then later enabled, the change will not apply to the Director's persistent disk.
* If you are using OpenStack Juno, make sure you have applied this patch: https://bugs.launchpad.net/horizon/+bug/1394051
