---
title: Pivotal Elastic Runtime v1.2.1.0 Known Issues
---

An issue was introduced in the Elastic Runtime 1.2.0.0 release that requires manual intervention when upgrading from that release in a running Pivotal Cloud Foundry installation. The following steps must be run to avoid the possibility of running apps stopping and cf push failing to respond.

PRIOR to doing the upgrade we need certain directories in the etcd jobs to be emptied out and the processes stopped. 

STEP 1: Login to each etcd node and clear out these directories as follows: 

```
  bosh ssh etcd_and_metrics/0 
  sudo su 
  monit summary 
  cd /var/vcap/store 
  monit stop all 
  rm rf /var/vcap/store/etcd 
  exit 

  bosh ssh etcd_and_metrics/1 
  sudo su 
  monit summary 
  cd /var/vcap/store 
  monit stop all 
  rm rf /var/vcap/store/etcd 
  exit 

  bosh ssh etcd_and_metrics/2 
  sudo su 
  monit summary 
  cd /var/vcap/store 
  monit stop all 
  rm rf /var/vcap/store/etcd 
  exit 
```
STEP 2: UPGRADE to 1.2.1 in Ops Manager (or to subsequent releases from 1.2.0 - the same issue will occur from 1.2.0 onward). 

---
Pivotal Elastic Runtime v1.2.0.0 Known Issues
---

* An app domain suffix, as entered in the System and Apps domain fields of the Cloud Controller settings, may only contain up to 5 characters.
* It is recommended that Operators upgrade to the 6.1.2 version of the CF CLI if they have an older version installed locally. http://cli.cloudfoundry.org/
* The node.js and go buildbacks require external dependencies and will not compile in an internet-less environment. 
