---
title: Pivotal Elastic Runtime v1.4.0.0 Release Notes
---

## Changes since v1.3.5.0:

## Elastic Runtime

CF Runtime Version: 205

### New Features

#### New Stack: Trusty 14.04

There is a new stack based on Ubuntu Trusty 14.04 LTS.

The lucid64 stack that has been part of Pivotal Cloud Foundry Elastic Runtime for several years as the root file system for containers will reach end of support for security fixes on April 29th, 2015 by Canonical. Developers or Operators will need to take action to ensure existing applications migrate to using the new stack.

In PCF Elastic Runtime 1.4 support has been added for the new stack called cflinuxfs2 derived from Ubuntu Trusty 14.04.

##### What do you need to do?

If you have an application or app as a service running on Pivotal Cloud Foundry, ensure that your application works when run with the new stack and the corresponding new buildpacks. We recommend using a blue/green deployment strategy to ensure there is no down time for the app. Simply running the following command will result in a small amount of down time as old instances are stopped and the app is restaged with the new stack.

	cf push app-name -s cflinuxfs2

If you have custom buildpacks, you need to ensure that your buildpacks work when run with the new stack.

##### List of buildpacks that now support cflinuxfs2:

* Java buildpack
* NodeJS buildpack
* PHP buildpack
* Go buildpack
* Python buildpack
* Ruby buildpack

##### Operator process for rolling out the new stack

To stay current with security fixes, operators should configure the default stack for new apps to cflinuxfs2 in the Elastic Runtime configuration tab. This means all new applications will get the new default stack:

![Root Filesystem Page](rootfs-er.png)

Applications that were created prior to cflinuxfs2 being the default stack will have the lucid64 stack set and therefore developers or operators need to take action.

Operators should decide when to notify users that they will be vulnerable to not getting new security patches once lucid64 reaches end of support.
Operators should send notice that lucid64 is close to end of life, and developers should migrate to the new cflinuxfs2 stack.
Larger deployments should manage carefully forcing restaging of apps onto the new stack.

##### lucid64 reaches end of support for security fixes on April 29th, 2015

The lucid64 stack will be removed from the Elastic Runtime tile in the next minor release.

When an Elastic Runtime release without lucid64 is deployed, apps that have not yet switched to cflinuxfs2 will not start because their stack will no longer be available.

Operators will need to force the change to the cflinuxfs2 stack and
restart the applications. There is a cf CLI plugin [stack-changer](https://github.com/simonleung8/cli-stack-changer) available that can be used by administrators to help determine what applications have not migrated. It can then also be used to move apps to the new stack in batches.

Once the migration is complete, to remove lucid64 from the list of stacks that cloud controller returns, an admin will need to delete the stack via the CC API.

	cf curl /v2/stacks/:lucid64_stack_guid -X DELETE

<b>Known issue: For apps that use native compiled binaries, when the stack is changed, the app may fail to start. If this occurs, the current work around is to delete the app and then push the app again.</b>

#### External RDS and S3 Options:
There are new features in the tile which allow for utilization of an external relational-database service for the Elastic Runtime databases and an external Amazon S3 bucket for Elastic Runtime’s file storage. This feature is especially useful for those who want to install their product on AWS and take advantage of the RDS and S3 services, and also reduce the number of VMs that Elastic Runtime would otherwise require to serve as the databases.

#### Highly Available MySQL Service
MySQL, used by Notifications, Autoscaling, and Apps Manager, can now be deployed in a highly-available configuration. This introduces a proxy tier which routes MySQL connections from internal components to healthy cluster nodes.

#### API/cf CLI
* Org and space users can now list other users in the org/space [details](https://www.pivotaltracker.com/n/projects/966314/stories/63345104)
	* `cf org-users ORG`
	* `cf space-users ORG SPACE`
* Allow admins to create wildcard routes [details](https://www.pivotaltracker.com/n/projects/966314/stories/84533566)
	* This feature allows cf admins to specify a wildcard route `cf create-route SPACE DOMAIN -n "*"`
	* The host name must be specified exactly as `"*"`
	* If you map this wildcard route to an app, requests to any matching routes will be routed to the app. Exact matches of routes will take precedence over the wildcard route.
* Org Managers can now share private domains across specific organizations [details](https://www.pivotaltracker.com/n/projects/966314/stories/81780716)
* Added `VCAP_APPLICATION` to the /v2/apps/:guid/env endpoint [details](https://www.pivotaltracker.com/n/projects/966314/stories/80664762)
	* `cf env APP_NAME`
* Added /v2/apps/:guid/copy_bits endpoint [details](https://www.pivotaltracker.com/n/projects/966314/stories/78847148)
	* `cf env APP_NAME`
* Added new endpoint to return memory usage of an org /v2/organizations/:guid/memory_usage [details](https://www.pivotaltracker.com/n/projects/966314/stories/81065364)
* More flexible nested domain creation rules [details](https://www.pivotaltracker.com/n/projects/966314/stories/83505974)
* Deprecated AppEvent in Cloud Controller [details](https://www.pivotaltracker.com/n/projects/966314/stories/77626184)
* Inlined relations api performance enhancements [details](https://www.pivotaltracker.com/n/projects/966314/stories/79917792)
* Respect true, t, false, and f when querying boolean values [details](https://www.pivotaltracker.com/n/projects/966314/stories/84942534)
* /v2/apps can now be filtered by organization_guid [details](https://www.pivotaltracker.com/n/projects/966314/stories/85250536)
* Users can now specify longer start commands via the API [details](https://www.pivotaltracker.com/n/projects/966314/stories/86262896)
* /v2/routes can now be queried by organization guid [details](https://www.pivotaltracker.com/n/projects/966314/stories/85007712)

#### Improved stability
* Added drain for restarts due to memory usage [details](https://www.pivotaltracker.com/n/projects/966314/stories/79416982)
* Changed HM9000 to communicate with Cloud Controller over HTTP, and not NATS to address an issue where HM9000's API stops responding to requests [details](https://www.pivotaltracker.com/n/projects/966314/stories/80850336)
* Updated Cloud Controller's Ruby version to 2.1.4 [details](https://www.pivotaltracker.com/n/projects/966314/stories/82227520)
* Improve GoRouter stability (memory & GC times) [details](https://www.pivotaltracker.com/n/projects/966314/stories/82729858)
* Bumped apcera's NATS client in yagnats and handle callbacks [details](https://www.pivotaltracker.com/n/projects/966314/stories/82747234)
* Bump apcera/nats to v1.0.6 [details](https://github.com/cloudfoundry/gorouter/commit/45a01e2d9635ec375d7fbc97b0fcdb21292fcd8d)
* Retry polling on the state of the upload if error is an HTTP timeout [details](https://www.pivotaltracker.com/n/projects/966314/stories/81065428)
* Change v2 directory server port to 32766 [details](https://www.pivotaltracker.com/n/projects/966314/stories/87576478)
* Updated golang version in cf-release to 1.3.1
* Upgraded gorouter, hm9000 to golang 1.4.2 [details](https://www.pivotaltracker.com/n/projects/966314/stories/86466310)
* Upgraded DEA and Warden to Ruby 2.1.4 [details](https://www.pivotaltracker.com/n/projects/966314/stories/89148118)
* Update collector, login, and uaa to Ruby 2.1.4 and remove Ruby 1.9.3 [details](https://www.pivotaltracker.com/n/projects/966314/stories/89148118)

#### Services API
* Update Service Plan completed [details](https://www.pivotaltracker.com/n/projects/1211680/epics/1533368)
* Users can change the plan for a service instance, if support for the feature is declared by the service broker [details](https://www.pivotaltracker.com/n/projects/969486/stories/76633662)
* Removed unnecessary warning when plans without instances are deleted during broker catalog sync [details](https://www.pivotaltracker.com/n/projects/1211680/stories/81215738)
* Pass through message from broker to client for 409 responses [details](https://www.pivotaltracker.com/n/projects/1211680/stories/80794268)
* Work completed on Service Audit Events [details](https://www.pivotaltracker.com/n/projects/1211680/epics/1533358)
* Cloud Controller now correctly returns a 502 when broker returns a malformed response [details](https://www.pivotaltracker.com/n/projects/1211680/stories/85739060)
* Service Broker client in Cloud Controller now uses a different library to prevent retry on timeout, as retries are now handled by orphan mitigation mechanisms [details](https://www.pivotaltracker.com/n/projects/1211680/stories/84037538)
* Service Instance Orphan Mitigation improvements [details](https://www.pivotaltracker.com/n/projects/1211680/epics/1558230)
* `/v2/managed_service_instances` is now deprecated [details](https://www.pivotaltracker.com/n/projects/1211680/stories/55946682)
* Renaming broker does not cause CC to fetch service broker catalog [details](https://www.pivotaltracker.com/n/projects/1211680/stories/83801222)
* Work continues on support for Asynchronous Service Instance Operations [details](https://www.pivotaltracker.com/n/projects/1211680/epics/1561148)
	* Improved error handling and descriptive error messages
	* Operations are block while in progress
	* Brokers can declare a polling interval, admins can configure a default interval and max attempts
	* Audit events created for async operations
	* API docs being published, changes for this feature are marked Experimental and subject to backward incompatible change

#### Misc
* Update default `request_timeout_in_seconds` to 900s (15min) [details](https://www.pivotaltracker.com/n/projects/966314/stories/80931258)
* Upgrade HAProxy to 1.5.10 [details](https://www.pivotaltracker.com/n/projects/966314/stories/82271326)
* make ha_proxy respect disabling timeout [details](https://www.pivotaltracker.com/n/projects/966314/stories/84079612)
* Expose IP address and port on vars with prefix `CF_INSTANCE` in the container [details](https://www.pivotaltracker.com/n/projects/966314/stories/82311924)
* `VCAP_SERVICES`, `DATABASE_URL`, and `VCAP_APPLICATION` no longer does BASH variable substitution [details](https://www.pivotaltracker.com/n/projects/966314/stories/77045902)
* Route endpoints can now request their own staleness threshold [details](https://www.pivotaltracker.com/n/projects/966314/stories/81878766)
* Cloud Controller worker names now include job index [details](https://www.pivotaltracker.com/n/projects/966314/stories/81201540)
* Allow core files to be generated in warden [details](https://www.pivotaltracker.com/n/projects/966314/stories/83102260)
* Sets the status code for upgrade to Websocket and TCP scenarios [details](https://www.pivotaltracker.com/n/projects/966314/stories/84515474)
* Update nginx for cloud controller to nginx-1.6.2 and pcre to pcre-8.36 [details](https://www.pivotaltracker.com/n/projects/966314/stories/85449216)
* Re-enabled SIGCHLD on children of wshd [details](https://www.pivotaltracker.com/n/projects/966314/stories/83352380)
* Write hm9000 logs to a file instead of STDOUT [details](https://www.pivotaltracker.com/n/projects/966314/stories/83879376)
* cloud controller worker and clock jobs now logs to files instead of STDOUT [details](https://www.pivotaltracker.com/n/projects/966314/stories/76069390)
* Output timestamps in all ctl logs [details](https://www.pivotaltracker.com/n/projects/966314/stories/80698234)
* nginx_status endpoint is always enabled [details](https://www.pivotaltracker.com/n/projects/966314/stories/87152482)
* Org Auditors can now see space related /v2/events [details](https://www.pivotaltracker.com/n/projects/966314/stories/84973576)
* Escape `VCAP_SERVICES` and `VCAP_APPLICATION` env variables [details](https://www.pivotaltracker.com/n/projects/966314/stories/77045902)
* cloudfoundry/gorouter #75: Allow keepalives to the front-end proxy [details](https://www.pivotaltracker.com/n/projects/966314/stories/88383116)
* Add content-type to blobstore file creation [details](https://www.pivotaltracker.com/n/projects/966314/stories/89861714)
* Security Groups applied to the space are visible to non-admins with correct permissions [details](https://www.pivotaltracker.com/n/projects/966314/stories/82055042)
* Improved service broker error handling and user-facing error messages
* Improved service orphan mitigation; failed provision requests trigger delete requests with retry and backoff

### Bug Fixes
* Fixed several NATS split brain issues
* Fixed several container transitions on the DEA
* Fixed an issue where logs were not being captured when an app is shutting down
* Fixed an issue where the DEA needed twice the space requested to successfully place an app [details](https://www.pivotaltracker.com/n/projects/966314/stories/81721664)
* Fix key type issue in graphite historian [details](https://www.pivotaltracker.com/n/projects/966314/stories/83720516)
* Fixed Mysql 5.6 issue on timestamp creation [details](https://www.pivotaltracker.com/n/projects/966314/stories/78499982)
* Fixed issue where deadlocks were happening on delayed job workers [details](https://www.pivotaltracker.com/n/projects/966314/stories/84346198)
* Fixed SpaceDeveloper able to move a service instance from one space to another [details](https://www.pivotaltracker.com/n/projects/1211680/stories/84152630)
* Fix incompatibility with MySQL 5.5 when setting timezone [details](https://www.pivotaltracker.com/n/projects/966314/stories/78499982)
* Fixed time consistency in cloud controller [details](https://www.pivotaltracker.com/n/projects/966314/stories/82077856)
* Renaming a service instance no longer causes instance to become stuck in 'update in progress' [details](https://www.pivotaltracker.com/n/projects/1211680/stories/88802018)
* Fixed an issue where deleting a route bound to a running app with multiple routes would actually result in a small amount of downtime for the app [details](https://www.pivotaltracker.com/n/projects/966314/stories/88643384)
* Fixed a bug when an app has a lot of fingerprints matched during resource matching, it should still be able to stage [details](https://www.pivotaltracker.com/n/projects/966314/stories/89572944)
* Recursive deletion of a space no longer aborts after first failure to delete a resource within (deleting all resources that can be deleted) and deletion of service instances and bindings are not rolled back, preventing orphans. Deletion of applications during recursive deletion of a space remains in a transaction; failure to delete one app will roll back deletion of all apps in the space.

## UAA and Login Server
### New Features
* Improved SAML SSO Setup via Ops Manager Console:

	Earlier Single Sign-On for the platform could be
	set up only by providing the Meta Data URL for the SAML Identity Provider. We now support two ways to set up the Identity provider for SSO: Meta Data URL and Meta Data XML. This feature extends support for Identity Providers that do not support a Meta Data URL.
	For more information, refer to [Configuring Single Sign-On](../../opsguide/sso.html).

* Mapping LDAP Groups to Administrator Role via Ops Manager:

	The LDAP Configuration page now supports configuring the LDAP Group information. This allows for LDAP groups to mapped to the Administrator Role in Cloud Foundry.
	For more information, refer to [Configuring LDAP](../../opsguide/ldap-uaa.html).

## Logging, Analytics and Metrics
### New Features

* Loggregator Firehose.
* Changing syslog drain location no longer requires application restaging.
* Updated LoggregatorEmitter to 4.0.0.
* System now Diego-enabled.
* Application forcibly closing output stream closes both standard out and standard error to logging system - fixes logging agent stability issues.
* New tuning parameters for cc polling.
	* properties.syslog\_drain\_binder.update\_interval\_seconds
	* properties.syslog\_drain\_binder.polling\_batch\_size
* Standardized `--config` flag across all components.

### Component Features And Bug Fixes
* Numerous general system fixes.
	* golang 1.3.X now default for most components.
	* Bug fixes for recovering when NATS connection is lost.
	* Honor system’s use\_ssl\_flag.
	* Add timestamps to every HttpStartStop envelope.
* Metron specific features and fixes.
    * Syslog configuration consolidated into Metron package.
	* No longer report metrics for downed component.
	* Fixed where application shutdown logs were not being collected.
	* Stability fixes between dropsonde and Metron.
	* Tracks cumulative values now in counters.
* Doppler features and fixes.
	* Increased buffer size for messages to better handle drops.
	* Improved channel operations for better durability.
* TrafficController / NOAA features and fixes.
	* Streaming endpoint can use a cookie to get the oauth token (allows js clients to stream logs).
	* Numerous NOAA additions for firehose.
	* Attempts to reconnect after unexpected disconnect.
	* Can fulfill Diego container metrics requests.
* Syslog features and fixes.
 	* Syslog configuration consolidated into Metron package.
 	* Syslog aggregator package removed (use Metron package for syslog forwarding).

### Bug Fixes

* Bug fixed where application shutdown logs were not being collected by loggregator.
* Bug fixes for recovering when NATS connection is lost.

## Notifications

* A new centrally-managed application service to notify users about platform and application events such as:
	* New service invitations
	* Planned downtime alerts
	* Application performance warnings
* Manage existing internal notifications and custom messages via an API so that administrators can:
	* Create and edit custom message templates in HTML and plain text
	* Send notifications to individuals, spaces, organizations or all users
* You can configure your own SMTP server in the runtime tile.

## Autoscaling

* Auto-scaling is now officially GA after a successful beta period
* Set min and max instances by % CPU utilization or calendar schedule
* Configured from apps manager.

## Buildpacks

### New Features

* Buildpacks are now downloaded to the DEA when the DEA starts instead of waiting for first app push
* Upgrading php buildpack to v3.1.0
	* Added support for `cflinuxfs2` stack.
	* On the `lucid64` stack, the following **changes** were made to package support:
		* Removed support for PHP 5.4.35, added support for PHP 5.4.38, in addition to still-supported 5.4.36 and 5.4.37.
		* Removed support for PHP 5.5.19, added support for PHP 5.5.22, in addition to still-supported 5.5.20 and 5.5.21.
		* Removed support for PHP 5.6.3, added support for PHP 5.6.6, in addition to still-supported 5.6.4 and 5.6.5.
		* Added support for Apache httpd 2.4.12, in addition to still-supported 2.4.10.
		* Added support for mod_lua to httpd 2.4.10 (also supported in httpd 2.4.12).
		* Removed support for nginx 1.7.7, however, nginx 1.5.{11,12,13}, 1.6.{0,1,2}, and 1.7.{8,9,10} are still supported.
		* Replaced support for composer 1.0.0-alpha8 with 1.0.0-alpha9.
		* Replaced support for newrelic 4.15.0.74 with 4.18.0.89.
	* On the `cflinuxfs2` stack, **only** the following packages are supported:
		* PHP 5.4.{36,37,38}, 5.5.{20.21.22}, and 5.6.{4,5,6}.
		* HHVM 3.5.0 and 3.6.0
		* Apache httpd 2.4.{10,12}.
		* nginx 1.5.13, 1.6.{0,1,2}, and 1.7.{8,9,10}.
		* composer 1.0.0-alpha9
		* newrelic 4.18.0.89
	* The buildpack has increased significantly in size with this release, from 458M to 1.1G.
* Upgrading ruby buildpack to v1.3.0
	* Added support for `cflinuxfs2` stack.
	* Binary files now permanently hosted on a CF-managed S3 bucket.
	* On `lucid64`, the following **changes** were made to package support:
		* Removed support for ruby 1.9.2. The binary for this version, included in previous `ruby-buildpack` releases, is not functional. There is a [track of work](https://www.pivotaltracker.com/n/projects/1042066/epics/1747872) scheduled to recreate binaries for all our stacks; but for this release, generating replacement binaries was deprioritized. That said, [ruby 1.9.2 has reached end-of-life](https://www.ruby-lang.org/en/news/2014/07/01/eol-for-1-8-7-and-1-9-2/), and at this moment we do not plan to support 1.9.2 in future `cflinuxfs2` buildpack releases.
	* On `cflinuxfs2`, only the following interpreter versions are supported:
		* ruby 2.2.0, 2.1.{2,3,4,5}, 2.0.0, and 1.9.3.
		* jruby 1.7.{1-11}.
		* See [manifest.yml](https://github.com/cloudfoundry/ruby-buildpack/blob/v1.3.0/manifest.yml) for full details.
	* The buildpack has increased in size with this release, from 825M to 922M.
* Upgrading python buildpack to v1.2.0
	* Added support for `cflinuxfs2` stack.
	* Binary files now permanently hosted on a CF-managed S3 bucket.
	* On the `lucid64` stack, no changes in python version support were made.
	* The `cflinuxfs` stack supports the same python versions as `lucid64` with the following exceptions:
		* Removed support for python 2.7.1, however 2.7.{0,2,3,6,7,8,9} are still supported.
		* Removed support for python 3.2.0, however 3.2.{1,2,3} are still supported.
		* See [manifest.yml](https://github.com/cloudfoundry/python-buildpack/blob/v1.2.0/manifest.yml) for full details.
	* The buildpack has increased in size with this release, from 315M to 654M.
* Upgrading nodejs buildpack to v1.2.0
	* Added support for `cflinuxfs2` stack.
	* Binary files now permanently hosted on a CF-managed S3 bucket.
	* On the `lucid64` stack, the following **changes** were made to package support:
		* Removed binaries for node v0.8.6, v0.10.14, and 0.11.4 for all stacks. The binaries for these versions, included in previous `nodejs-buildpack` releases, are not functional. There is a [track of work](https://www.pivotaltracker.com/n/projects/1042066/epics/1747872) scheduled to recreate these binaries for all our stacks; but for this release, generating replacement binaries was deprioritized.
	* On the `cflinuxfs2` stack, the same packages are supported as on the `lucid64` stack, which are too numerous to list here. See [manifest.yml](https://github.com/cloudfoundry/nodejs-buildpack/blob/v1.2.0/manifest.yml) for full details.
	* The buildpack has decreased in size with this release, from 418M to 403M.
* Upgrading go buildpack to v1.2.0
	* Added support for `cflinuxfs2` stack.
	* The buildpack, at 675M, has not materially increased in size with this release.
	* Support version 1.4.1
	* Default to version 1.4.1 if no version specified
	* (https://www.pivotaltracker.com/story/show/86334724)
	* Update buildpack-packager to v.2.0.0
	* (https://www.pivotaltracker.com/story/show/84805200)
* Update to Java Buildpack 2.7.1 [details](https://www.pivotaltracker.com/n/projects/966314/stories/90080284) [release](https://github.com/cloudfoundry/java-buildpack/releases/tag/v2.7.1)
	* Improved Access Logging (via [Guillaume Berche](https://github.com/cloudfoundry/java-buildpack/issues/57) and [Kevin Kessler](https://github.com/cloudfoundry/java-buildpack/issues/75))
	* Improved AppDynamics Integration (via [Troy Astle](https://github.com/cloudfoundry/java-buildpack/issues/73), [Max Brunsfeld](https://github.com/cloudfoundry/java-buildpack/issues/55), Mike Youngstrom, and [Shaozhen Ding](https://github.com/cloudfoundry/java-buildpack/issues/59))
	* New Relic on Java 8
	* Secure Dependency Retrieval via HTTPS
	* Java 8 as Default
	* Tomcat 8 as Default (via [Dave Head-Rapson](https://github.com/cloudfoundry/java-buildpack/pull/95))
	* Print `OutOfMemory` diagnostics to Loggregator (via [Troy Astle](https://github.com/cloudfoundry/java-buildpack/issues/79))
	* Support for custom CA certificates when download from a repository (via Dave Head-Rapson)
	* Tomcat Redis Session Replication support for alternate Redis services (via [Neil Aitken](https://github.com/cloudfoundry/java-buildpack/issues/102))
	* Improved SSL Diagnostics
	* Support for GemFire session replication.
	* Better `JAVA_OPTS` escaping (via [Sridhar Vennela](https://github.com/cloudfoundry/java-buildpack/issues/120))
	* Documentation updates (via [Makoto Motegi](https://github.com/cloudfoundry/java-buildpack/pull/147), [Mohammad Asif Siddiqui](https://github.com/cloudfoundry/java-buildpack/pull/135), and [Ann Paungam](https://github.com/cloudfoundry/java-buildpack/pull/133))
	* Windows build improvements (via [Josh Ghiloni](https://github.com/cloudfoundry/java-buildpack/pull/117))
	* JRebel support

## Security - CVE fixes have been implemented since v1.3.0.0 and released via security patches.

* BASH Shellshock CVE-2014-6271, CVE-2014-7169, CVE-2014-7186, and CVE-2014-7187
* Updated HAProxy to disable SSLv3. This addresses POODLE CVE-2014-3566
* GHOST CVE-2015-0235 [details](https://github.com/cloudfoundry/cf-release/commit/3f2ae69)
* Updated lucid64 and cflinuxfs2 to address CVE-2013-7423, CVE-2014-9402, CVE-2015-1472, CVE-2015-1473 [detail](https://www.pivotaltracker.com/n/projects/966314/stories/89215492)
* Updated ca-certificates for lucid64 to address USN-2509-1 [detail](https://www.pivotaltracker.com/n/projects/966314/stories/88978544)
* CVE-2014-9680 [details](https://www.pivotaltracker.com/n/projects/966314/stories/90428236)
* lucid64 and cflinuxfs2. This addresses USN-2537-1, CVE-2015-0209, CVE-2015-0286, CVE-2015-0287, CVE-2015-0288, CVE-2015-0289, CVE-2015-0292, CVE-2015-0293 [details](https://www.pivotaltracker.com/n/projects/966314/stories/90713288)
* [CVE-2014-9636](http://www.ubuntu.com/usn/usn-2489-1/) [details](https://github.com/cloudfoundry/cf-release/commit/ba6f0cca707d10ebf36dfb6d4183f6f938296cbb)
* Updated rootfs to address openssl vulnerabilities [details](https://github.com/cloudfoundry/cf-release/commit/e36a1c2) [ubuntu-notice](http://www.ubuntu.com/usn/usn-2459-1/)
* Updated default cipher string for HAProxy [details](https://www.pivotaltracker.com/n/projects/966314/stories/86175600)
* Application Security Groups now support logging of the first packet of outbound tcp traffic [details](https://www.pivotaltracker.com/n/projects/966314/stories/73905126) [apidoc](http://apidocs.cloudfoundry.org/198/security_groups/creating_a_security_group.html)

