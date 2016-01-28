---
title: Pivotal Elastic Runtime v1.6 Known Issues
---

#### New Issues

*  Known issue with the Elastic Rutime 1.6.13 and 1.5.13 releases: There's a linux kernel bug that affects Garden, Docker, and almost certainly Warden for Cloud Foundry deployments on stemcell 3146.5. It manifests in containers failing to be killed properly leaving unkillable zombie processes around consuming lots of CPI and some memory. After a while, Diego cells / DEAs may experience slower performance and eventually may even become unresponsive.

* Etcd may somtimes experience orphaned processes that leads to the Diego BBS job failing. This can be remedied by `killall etcd` on the Diego BBS VMs and subsequent redeployment. This will be fixed in a future 1.6.x release soon. 

* The [Pivotal Cloud Foundry&reg;](https://network.pivotal.io/products/pivotal-cf) (PCF) Elastic Runtime tile v.1.6.0 will show "1.6.0-build.315" in the tile version. This is fine.
 
* Before upgrading to Elastic Runtime v.1.6.0 from v.1.5.x, make sure you have followed [these instructions](http://docs.pivotal.io/pivotalcf/customizing/upgrading-pcf.html#pcf16upgrade).

* The Notifications and Autoscale services in Elastic Runtime will always deploy on Diego, even if DEAs are selected as the default backend, in versions 1.6.0 to 1.6.9 (this was fixed in patch 1.6.10). The Apps Manager and Apps Usage service will deploy to Diego only if the "Use Diego by default" checkbox is enabled in the configuration of Elastic Runtime.

* Diego Cells may sometimes time-out on app pushes when any given Diego Cell receives its first app push with no buildpack specified for that app. This is because the Cell is caching all of the buildpacks for subsequent app pushes, and this may take longer than what the app staging allows.

* Diego Cells may sometimes experience slow performance for various actions like staging new applications. If you experience slow performance, you can SSH into the Ops Manager VM and `bosh-recreate` the affected Diego Cell VM.

* Docker library images require you to specify "library/" in front of the docker image name. E.g "cf p jetty -o library/jetty"

* Diego Cells may run out of disk space if they using a lot of different Docker images with different layers.

* The CLI command for viewing application files, `cf files`, does not work with applications on Diego.

* The Diego BBS may output a TLS handshake error every three seconds in the sys logs. This error is fine to ignore, and will be fixed in a future release of Diego.

* To SSH into an application container on Diego, your CF user must have the Space Developer role attached to it for the application space.

* The Smoke Tests may occasionally fail at the logging test suite. The Smoke Tests errand is fine to re-run in case of any failures. 

* The version of Postgres has been upgraded to 9.4.2. If you have Postgresql databases in your deployment, Cloud Controller and UAA will be unavailable during the upgrade.
In case that upgrade fails, there are mitigations [documented here](https://github.com/cloudfoundry/cf-release/releases/tag/v211).

* After you upgrade to PCF 1.6, you may want to reclaim some blobstore space due to some orphaned blobs. To reclaim space, call [this end point](http://apidocs.cloudfoundry.org/222/blobstores/delete_all_blobs_in_the_buildpack_cache_blobstore.html) to delete all buildpack caches from the blobstore after the v1.6 upgrade is complete.

* This upgrade includes a migration that modifies the events table on the Cloud Controller database. This table may be very large, and the migration may cause the upgrade to fail at the Cloud Controller job if it takes too long. If this happens, do not restart the deploy until the migration has finished running. The deploy can be restarted once the space_id foreign key constraint has been removed from the events table.
To avoid the possibility of the migration causing a failure, truncate the events table before the deployment starts. The data in the events table are audit and log data, and PCF can function without it.

* .NET support on Windows cells does not support the same level of security and isolation as seen on Linux cells. At this time, it is only recommended for running "trusted" apps.

* At this time, the container accounts on Windows cells must have permissions to log on locally, which may not be the default.

* Application file names on Windows cells are limited to maximum length of 100 characters. As a workaround, make sure that all filenames in an application directory are shorter than 100 characters before pushing.

* Apps Manager now has a zero-downtime blue green deploy. As of v1.6, any `NON_ADMIN` environment variable changed from the default setting will not be applied to the second app version. You will need to set `NON-ADMIN` environment variables on both versions in order to keep the configuration consistent.

* If you have installed the Diego Beta tile in a 1.5.x Elastic Runtime environment, it will need to be uninstalled prior to upgrade. The Windows MSI provided with the 1.6 Elastic Runtime release will not work with the older Diego Beta tile. 

#### Existing Issues

* On the Security Config page of Elastic Runtime, after you supply your own cipher sets and click Save, do not erase the HAProxy and Router Cipher fields. The ciphers will not return to their default values when deleted, and will instead be interpreted as an empty cipher set.

* When selecting between internal and external System Database and/or File Storage config, if saved values for external systems fail verification (e.g. a host is not reachable from Ops Manager), the values will persist if you then select 'Internal Databases' or 'Internal File Store'. To resolve this issue, return to your Ops Manager Installation Dashboard and click **Revert**, located in the upper right corner of the page.

* Recent versions of the cf CLI, including the version shipped with v1.6, will report a version mismatch with Elastic Runtime. You can ignore this message, and there is no need to upgrade the CLI. This error will be fixed in a future version of the cf CLI.

