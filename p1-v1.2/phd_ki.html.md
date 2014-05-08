---
title: Pivotal HD for Pivotal CF v1.2.0.0 Known Issues
---
* jvm memory allocation is per process is currently fixed. Increasing the memory allocation for the GemFire XD locator or Slave component will not result in more memory being used by the corresponding GemFire XD processes.
