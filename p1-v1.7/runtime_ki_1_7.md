---
title: Pivotal Elastic Runtime&reg; v1.7 Known Issues
owner: Release Engineering
---

#### New Issues

* 1.7 ERT will migrate any Postgres DBs you have for UAA or CC to the MySQL cluster (if you started on a version of PCF older than 1.6 originally). This will effectively cause "system downtime", but not necessarily app downtime, during the migration the CC and UAA will be unavailable. There will be app downtime also though for any app that uses UAA for authentication, such as if you use the SSO service tile.
* If you are using an external load balancer, make sure to scale HA proxies to 0. Otherwise, the HA proxy VM will unsuccessfully attempt to deploy despite having no configuration.


#### Existing Issues

* Existing issues here
