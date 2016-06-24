---
title: Pivotal Elastic Runtime v1.2.1.0 Known Issues
owner: RelEng
---

* If, after upgrading to v1.2.1.0 from v1.2.0.0, running apps appear to be down and `cf push` fails, you must restart the etcd job. To do so, first identify the three etcd job VMs by navigating to Ops Manager and selecting **Elastic Runtime >> Status**. Then, restart them using the vCenter UI.

## Pivotal Elastic Runtime v1.2.0.0 Known Issues##

* An app domain suffix, as entered in the System and Apps domain fields of the Cloud Controller settings, may only contain up to 5 characters.
* It is recommended that Operators upgrade to v6.1.2 of the CF CLI if they have an older version installed locally. http://cli.cloudfoundry.org/
* The node.js and go buildbacks require external dependencies and will not compile in an internet-less environment.
