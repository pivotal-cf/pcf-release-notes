---
title: Pivotal HD for Pivotal CF v1.2.1.0 Known Issues
---
* Pivotal HD for Pivotal CF v1.2.0.0 cannot be directly upgraded to v1.2.1.0.  It must first be uninstalled in Ops Manager and deployments and releases manually deleted via bosh prior to upgrading to v1.2.1.0.  Detailed instructions on how to do this documented under http://docs.gopivotal.com/pivotalhd-ds/
* jvm memory allocation is currently fixed. Increasing the memory allocation for the GemFire XD locator or Slave component will not result in more memory being used by the corresponding GemFire XD processes.
