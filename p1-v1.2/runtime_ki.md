---
title: Pivotal Elastic Runtime v1.2.1.0 Known Issues
---

* If, after upgrading to 1.2.1.0 from 1.2.0.0, running apps appear to be down and cf push fails, the etcd job should be restarted. To do so, identify the 3 etcd job vms via the Ops Manager 'status' page in the Elastic Runtime tile. Then, via the vCenter UI restart them. 


---
Pivotal Elastic Runtime v1.2.0.0 Known Issues
---

* An app domain suffix, as entered in the System and Apps domain fields of the Cloud Controller settings, may only contain up to 5 characters.
* It is recommended that Operators upgrade to the 6.1.2 version of the CF CLI if they have an older version installed locally. http://cli.cloudfoundry.org/
* The node.js and go buildbacks require external dependencies and will not compile in an internet-less environment. 
