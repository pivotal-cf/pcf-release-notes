---
title: Pivotal Elastic Runtime v1.5 Known Issues
---

#### Pivotal Elastic Runtime v1.5 Known Issues That Still Apply in v1.6

* The HAProxy and Router Cipher fields in the Security Config of Elastic Runtime should not be completely erased once you have already supplied your own cipher sets and saved that configuration. The ciphers will not return to their default values when deleted, and will instead be interpreted as an empty cipher set.

* When selecting between internal and external System Database and/or File Storage config, if saved values for external systems fail verification (e.g. a host is not reachable from Ops Manager), the values will persist if you then select 'Internal Databases' or 'Internal File Store'. To resolve this issue, return to your Ops Manager Installation Dashboard and click **Revert**, located in the upper right corner of the page.

* Recent versions of the cf CLI, including the version shipped with v1.6, will report a version mismatch with Elastic Runtime. The message is harmless and ignorable, there is no need to upgrade the CLI. This will be fixed in a future version of the cf CLI.å
