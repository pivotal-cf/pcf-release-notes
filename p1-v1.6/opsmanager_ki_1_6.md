---
title: Pivotal Cloud Foundry Ops Manager v1.6.0 Known Issues
---

## New Issues

Some of these issues may be fixed in subsequent patch releases to 1.6. Consult the Ops Manager 1.6 [Release Notes](opsmanager_rn_1_6.html) for more information.

* If EBS encryption is initially disabled, and then later enabled, the change will not apply to the Director's persistent disk.
* The new "Trusted Certificates" feature does not insert the certificate (or certificate chain) that you provide into your application containers.
* The new "Trusted Certificates" feature does not insert the certificate (or certificate chain) that you provide into UAA's JVM store (which would be necessary to enable UAA -> SASL trust).
* Once the above issues with "Trusted Certificates" are resolved, "Trusted Certificates" will be moved out of the Experimental Features section.

## Existing issues

* Ops Manager 1.5 does not support AWS S3 buckets in eu-central-1 (Frankfurt) due to an issue with Amazon's authentication APIs in this region. Therefore, Pivotal does not recommend customers use the eu-central-1 region for deployments that require high performance.
* On AWS environments, it is only possible to use "light-bosh" stemcells.
* If you are using OpenStack Juno, make sure you have applied this patch: https://bugs.launchpad.net/horizon/+bug/1394051
* DNS and Gateway ICMP errors will occur on AWS even if ICMP is allowed.
* Resource Pools cannot be deleted from Availability Zones. If a resource pool is inadvertently deleted, run BOSH recreate.
* Compiled Packages are missing from installation exports, which can cause a failure if the product contained and referenced them. A fix is to SSH into the Ops Manager VM and remove references to compiled_packages in every file located in the /var/tempest/workspace/metadata directory.
* PCF products with Ruby BOSH Agent stemcells must be upgraded prior to importing into this version of Ops Manager.
IP reassignment must be handled by scaling a job down to zero instances and re-entering new IP addresses before scaling the job back up.
* Unnecessary job instances must be reduced manually (MySQL, HA Proxy if RDS & ELBs are used).
* Before upgrading tiles on Ops Manager 1.4 or earlier, Pivotal recommends that you increase the size of Ops Manager Director’s persistent disk to at least 40 GB. (This is the default in Ops Manager 1.5 and above.) To change the size of the persistent disk, navigate to Ops Manager Director tile -> Resource Config -> Ops Man Director -> Persistent Disk (MB).
* Ops Manager does not support the installation of Pivotal HD.
