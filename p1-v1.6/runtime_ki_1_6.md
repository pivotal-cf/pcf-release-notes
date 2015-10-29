---
title: Pivotal Elastic Runtime v1.5 Known Issues
---

#### New Issues

* The PCF Elastic Runtime tile v.1.6.0 will show "1.6.0-build.315" in the tile version. This is fine.

* Diego Cells may sometimes experience slow performance for various actions like staging new applications. If you experience slow performance, you can SSH into the Ops Manager VM and `bosh-recreate` the affected Diego Cell VM.

* The CLI command for viewing application files, `cf files`, does not work with applications on Diego.

* The Diego BBS may output a TLS handshake error every three seconds in the sys logs. This error is fine to ignore, and will be fixed in a future release of Diego.

* To SSH into an application container on Diego, your CF user must have the Space Developer role attached to it for the application space.

* The Smoke Tests may occasionally fail at the logging test suite. The Smoke Tests errand is fine to re-run in case of any failures. 

* The version of Postgres has been upgraded to 9.4.2. If you have Postgresql databases in your deployment, Cloud Controller and UAA will be unavailable during the upgrade.
In case that upgrade fails, there are mitigations [documented here](https://github.com/cloudfoundry/cf-release/releases/tag/v211).

* After you upgrade to Pivotal Cloud Foundry 1.6, you may want to reclaim some blobstore space due to some orphaned blobs. To reclaim space, call [this end point](http://apidocs.cloudfoundry.org/222/blobstores/delete_all_blobs_in_the_buildpack_cache_blobstore.html) to delete all buildpack caches from the blobstore after the v1.6 upgrade is complete.

* This upgrade includes a migration that modifies the events table on the Cloud Controller database. This table may be very large, and the migration may cause the upgrade to fail at the Cloud Controller job if it takes too long. If this happens, do not restart the deploy until the migration has finished running. The deploy can be restarted once the space_id foreign key constraint has been removed from the events table.
To avoid the possibility of the migration causing a failure, truncate the events table before the deployment starts. The data in the events table are audit and log data, and PCF can function without it.

* .NET support on Windows cells does not support the same level of security and isolation as seen on Linux cells. At this time, it is only recommended for running "trusted" apps.

* At this time, the container accounts on Windows must have permissions to log on locally, which may not be the default.

* Apps Manager now has a zero-downtime blue green deploy. As of v1.6, any `NON_ADMIN` environment variable changed from the default setting will not be applied to the second app version. You will need to set `NON-ADMIN` environment variables on both versions in order to keep the configuration consistent.

#### Existing Issues

* On the Security Config page of Elastic Runtime, after you supply your own cipher sets and click Save, do not erase the HAProxy and Router Cipher fields. The ciphers will not return to their default values when deleted, and will instead be interpreted as an empty cipher set.

* When selecting between internal and external System Database and/or File Storage config, if saved values for external systems fail verification (e.g. a host is not reachable from Ops Manager), the values will persist if you then select 'Internal Databases' or 'Internal File Store'. To resolve this issue, return to your Ops Manager Installation Dashboard and click **Revert**, located in the upper right corner of the page.

* Recent versions of the cf CLI, including the version shipped with v1.6, will report a version mismatch with Elastic Runtime. You can ignore this message, and there is no need to upgrade the CLI. This error will be fixed in a future version of the cf CLI.

