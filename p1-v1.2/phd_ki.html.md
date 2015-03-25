---
title: Pivotal HD for PCF v1.2.1.0 Known Issues
---
* Pivotal HD for PCF v1.2.0.0 cannot be directly upgraded to v1.2.1.0.  It must first be uninstalled in Ops Manager and deployments and releases manually deleted via bosh prior to upgrading to v1.2.1.0.  Detailed instructions on how to do this documented under http://docs.pivotal.io/pivotalhd-ds/
* jvm memory allocation is currently fixed. Increasing the memory allocation for the GemFire XD locator or Slave component will not result in more memory being used by the corresponding GemFire XD processes.
* Users will not be able to remotely connect to the GemFire XD cluster due to an issue in resolving DNS names to the slaves.  The workaround for this is to add the bosh director as a DNS entry.  PCF pushed apps will not have this issue as they will have access to the bosh DNS by default.
