---
title: Pivotal Elastic Runtime v1.5 Known Issues
---

* Diego Cells may sometimes fail, but we have a workaround...

* The CLI command for seeing application files, "cf files", does not work with applications on Diego.

* The Diego BBS may output a TLS handshake error every 3 seconds in the sys logs. This is fine to ignore, and will be fixed in a future release of Diego.

* To SSH into an application container on Diego, the CF user that you use must have the SpaceDeveloper role attached to it, per the space that your application is in. 

* If you have Postgresql databases in your deployment, the version of Postgres has been upgraded to 9.4.2, and so during the upgrade, Cloud Controller and UAA will be unavailable.
In case that upgrade fails, there are some mitigations [documented here](https://github.com/cloudfoundry/cf-release/releases/tag/v211).

* After you upgrade to Pivotal Cloud Foundry 1.6, you may want to call [this end point](http://apidocs.cloudfoundry.org/222/blobstores/delete_all_blobs_in_the_buildpack_cache_blobstore.html) that deletes all buildpack caches from the blobstore after the v1.6 upgrade is complete, to reclaim some blobstore space due to some orphaned blobs.

* This upgrade includes a migration that modifies the events table on the Cloud Controller database. This table may be very large, and the migration may cause the upgrade to fail if it takes too long to run. If the migration causes the deployment to fail, the api_z1/0 job will fail to start. If this happens, do not restart the deploy until the migration has finished running. The deploy can be restarted once the space_id foreign key constraint has been removed from the events table.
To avoid the possibility of the migration causing a failure, truncate the events table before the deployment starts. The data in the events table are audit and log data, and Cloud Foundry can function without it.

* .NET support on Windows cells does not support the same level of security and isolation as seen on Linux cells. At this time, it is only recommended to run "trusted" apps.

#### Pivotal Elastic Runtime v1.5 Known Issues That Still Apply in v1.6

* The HAProxy and Router Cipher fields in the Security Config of Elastic Runtime should not be completely erased once you have already supplied your own cipher sets and saved that configuration. The ciphers will not return to their default values when deleted, and will instead be interpreted as an empty cipher set.

* When selecting between internal and external System Database and/or File Storage config, if saved values for external systems fail verification (e.g. a host is not reachable from Ops Manager), the values will persist if you then select 'Internal Databases' or 'Internal File Store'. To resolve this issue, return to your Ops Manager Installation Dashboard and click **Revert**, located in the upper right corner of the page.

* Recent versions of the cf CLI, including the version shipped with v1.6, will report a version mismatch with Elastic Runtime. The message is harmless and ignorable, there is no need to upgrade the CLI. This will be fixed in a future version of the cf CLI. 

