---
title: Pivotal Elastic Runtime v1.4 Known Issues
---

* When selecting between internal and external System Database and/or File Storage config, saved values for external systems, if they fail verification (e.g. a host is not reachable from Ops Manager), will persist if you select 'Internal Databases' or 'Internal File Store' subsequently. To resolve, head back to your Ops Manager Installation Dashboard and select the 'Revert' button, located in the upper right corner of the page. 
