---
title: Pivotal Elastic Runtime v1.4.0.0 Release Notes
---

## Changes since v1.3.5.0:

## Elastic Runtime

### New Features 

##### New Stack: Trusty 14.04

There is a new stack based on Ubuntu Trusty 14.04 LTS.  

The lucid64 stack that has been part of PCF ER for several years as the root file 
system for containers will reach end of support for security fixes on April 29th, 2015 by Canonical. Developers or Operators will need to take action to ensure existing applications migrate to using the new stack.

In PCF ER 1.4 support has been added for the new stack called cflinuxfs2 derived from Ubuntu Trusty 14.04. 

##### What do you need to do? 

If you have an application or app as a service running on Pivotal Cloud Foundry, ensure that your application works when run with the new stack and the corresponding new buildpacks.  We recommend using a blue/green deployment strategy to ensure there is no down time for the app.  Simply running the following command will result in a small amount of down time as old instances are stopped and the app is restaged with the new stack.

	cf push app-name -s cflinuxfs2

If you have custom buildpacks, you need to ensure that your buildpacks work when run with the new stack.

###### List of buildpacks that now support cflinuxfs2:

* Java buildpack
* NodeJS buildpack
* PHP buildpack
* Go buildpack
* Python buildpack
* Ruby buildpack

###### Operator process for rolling out the new stack

To stay current with security fixes, operators should configure the default stack for new apps to cflinuxfs2 in the Elastic Runtime configuration tab. This means all new applications will get the new default stack:

[insert image here]

Applications that were created prior to cflinuxfs2 being the default stack will have the lucid64 stack set and therefore developers or operators need to take action.

Operators should decide when to notify users that they’ll be vulnerable to not getting new security patches once lucid64 reaches end of support.
Operators should send notice that lucid64 is close to end of life, and developers should migrate to the new cflinuxfs2 stack.
Larger deployments should manage carefully forcing restaging of apps onto the new stack.

###### lucid64 reaches end of support for security fixes on April 29th, 2015

The lucid64 stack will be removed from the Elastic Runtime tile in the next minor release.

When an Elastic Runtime release without lucid64 is deployed, apps that have not yet switched to cflinuxfs2 will not start because their stack will no longer be available. 

Operators will need to force the change to the cflinuxfs2 stack and 
restart the applications. There is a cf CLI plugin [stack-changer](https://github.com/simonleung8/cli-stack-changer) available that can be used by administrators to help determine what applications have not migrated.  It can then also be used to move apps to the new stack in batches. 

Once the migration is complete, to remove lucid64 from the list of stacks that cloud controller returns, an admin will need to delete the stack via the cc api.

	cf curl /v2/stacks/:lucid64_stack_guid -X DELETE

<b>Known issue: For apps that use native compiled binaries, when the stack is changed, the app may fail to start.  If this occurs, the current work around is to delete the app and then push the app again.</b> 

###### External RDS and S3 Options:
There are new features in the tile which allow for utilization of an external relational-database service for the Elastic Runtime databases and an external Amazon S3 bucket for Elastic Runtime’s file storage. This feature is especially useful for those who want to install their product on AWS and take advantage of the RDS and S3 services, and also reduce the number of VMs that Elastic Runtime would otherwise require to serve as the databases.

###### API/cf CLI
* Org and space users can now list other users in the org/space details
	* cf org-users ORG
	* cf space-users ORG SPACE
* Allow admins to create wildcard routes details
	* This feature allows cf admins to specify a wildcard route cf create-route SPACE DOMAIN -n "*"
	* The host name must be specified exactly as "*"
	* If you map this wildcard route to an app, requests to any matching routes will be routed to the app. Exact matches of routes will take precedence over the wildcard route.
* Org Managers can now share private domains across specific organizations details
* Added VCAP_APPLICATION to the /v2/apps/:guid/env endpoint details
	* cf env APP_NAME
* Added /v2/apps/:guid/copy_bits endpoint details
	* cf env APP_NAME
* Added new endpoint to return memory usage of an org /v2/organizations/:guid/memory_usage details
* More flexible nested domain creation rules details
* Deprecated AppEvent in Cloud Controller details
* Inlined relations api performance enhancements details
* Respect true, t, false, and f when querying boolean values details
* /v2/apps can now be filtered by organization_guid details
* Users can now specify via the api longer start commands details
* /v2/routes can now be queried by organization guid details

###### Improved stability
* Added drain for restarts due to memory usage details
* Changed HM9000 to communicate with Cloud Controller over HTTP, and not NATS to address an issue where HM9000's API stops responding to requests details
* Updated Cloud Controller's Ruby version to 2.1.4 details
* Improve GoRouter stability (memory & GC times) details
* Bumped apcera's NATS client in yagnats and handle callbacks details
* Bump apcera/nats to v1.0.6 details
* Retry polling on the state of the upload if error is an HTTP timeout details
* Change v2 directory server port to 32766 details
* Updated golang version in cf-release to 1.3.1
* Upgraded gorouter, hm9000 to golang 1.4.2 details
* Upgraded DEA and Warden to Ruby 2.1.4 details
* Update collector, login, and uaa to Ruby 2.1.4 and remove Ruby 1.9.3 details

###### Services API
* Update Service Plan completed details
* Users can change the plan for a service instance, if support for the feature is declared by the service broker details
* Removed unnecessary warning when plans without instances are deleted during broker catalog sync details
* Pass through message from broker to client for 409 responses details
* Work completed on Service Audit Events details
* Cloud Controller now correctly returns a 502 when broker returns a malformed response details
* Service Broker client in Cloud Controller now uses a different library to prevent retry on timeout, as retries are now handled by orphan mitigation mechanisms details
* Service Instance Orphan Mitigation improvements details
* /v2/managed_service_instances is now deprecated details
* Renaming broker does not cause CC to fetch service broker catalog details
* Work continues on support for Asynchronous Service Instance Operations details
	* Improved error handling and descriptive error messages
	* Operations are block while in progress
	* Brokers can declare a polling interval, admins can configure a default interval and max attempts
	* Audit events created for async operations
	* API docs being published, changes for this feature are marked Experimental and subject to backward incompatible change

###### Misc
* Update default request_timeout_in_seconds to 900s (15min) details
* Upgrade HAProxy to 1.5.10 details
* make ha_proxy respect disabling timeout details
* Expose IP address and port on vars with prefix CF_INSTANCE in the container details
* VCAP_SERVICES, DATABASE_URL, and VCAP_APPLICATION no longer does BASH variable substitution details
* Route endpoints can now request their own staleness threshold details
* Cloud Controller worker names now include job index details
* Allow core files to be generated in warden details
* Sets the status code for upgrade to Websocket and TCP scenarios details
* Update nginx for cloud controller to nginx-1.6.2 and pcre to pcre-8.36 details
* Re-enabled SIGCHLD on children of wshd details
* Write hm9000 logs to a file instead of STDOUT details
* cloud controller worker and clock jobs now logs to files instead of STDOUT details
* Output timestamps in all ctl logs details
* nginx_status endpoint is always enabled details
* Org Auditors can now see space related /v2/events details
* Escape VCAP_SERVICES and VCAP_APPLICATION env variables details
* cloudfoundry/gorouter #75: Allow keepalives to the front-end proxy details
* Add content-type to blobstore file creation details
* Security Groups applied to the space are visible to non-admins with correct permissions details

###### Bug Fixes
* Fixed several NATS split brain issues
* Fixed several container transitions on the DEA
* Fixed an issue where logs were not being captured when an app is shutting down
* Fixed an issue where the DEA needed twice the space requested to successfully place an app details
* Fix key type issue in graphite historian details
* Fixed Mysql 5.6 issue on timestamp creation details
* Fixed issue where deadlocks were happening on delayed job workers details
* Fixed SpaceDeveloper able to move a service instance from one space to another details
* Fix incompatibility with MySQL 5.5 when setting timezone details
* Fixed time consistency in cloud controller details
* Renaming a service instance no longer causes instance to become stuck in 'update in progress' details
* Fixed an issue where deleting a route bound to a running app with multiple routes would actually result in a small amount of downtime for the app details
* Fixed a bug when an app has a lot of fingerprints matched during resource matching, it should still be able to stage details
* Recursive deletion of a space no longer aborts after first failure to delete a resource within (deleting all resources that can be deleted) and deletion of service instances and bindings are not rolled back, preventing orphans. Deletion of applications during recursive deletion of a space remains in a transaction; failure to delete one app will roll back deletion of all apps in the space.

## UAA and Login Server
###### New Features
* Improved SAML SSO Setup via Ops Manager Console

	Earlier Single Sign-On for the platform could be 
	set up only by providing the Meta Data URL for the SAML Identity Provider.We now support two ways to set up the Identity provider for SSO : Meta Data URL and Meta Data XML. This feature extends support for Identity Providers which don’t support a Meta Data URL.
	<Need to add the link to the doc page containing SSO Configuration>

* Mapping LDAP Groups to Administrator Role  via Ops Manager


	The LDAP Configuration page now supports configuring the LDAP Group information. This allows for LDAP groups to mapped to the Administrator Role in Cloud Foundry.
	<Need to add the link to the doc page containing LDAP Configuration>

## Logging, Analytics and Metrics
###### New Features
* Loggregator Firehose.
* Changing syslog drain location no longer requires application restaging.
* Updated LoggregatorEmitter to 4.0.0
* System now Diego-enabled.
* Application forcibly closing output stream closes both standard out and standard error to logging system - fixes logging agent stability issues.
* New tuning parameters for cc polling
	* properties.syslog_drain_binder.update_interval_seconds
	* properties.syslog_drain_binder.polling_batch_size
* Standardized --config flag across all components.

###### Component Features And Bug Fixes
* Numerous general system fixes 
	* golang 1.3.X now default for most components
	* Bug fixes for recovering when NATS connection is lost	* Honor system’s use_ssl_flag
	* Add timestamps to every HttpStartStop envelope
* Metron specific features and fixes
    * Syslog configuration consolidated into Metron package
	* No longer report metrics for downed component
	* Fixed where application shutdown logs were not being collectedt
	* Stability fixes between dropsonde and Metron
	* Tracks cumulative values now in counters
* Doppler features and fixes
	* Increased buffer size for messages to better handle drops
	* Improved channel operations for better durability
* TrafficController / NOAA features and fixes
	* Streaming endpoint can use a cookie to get the oauth token (allows js clients to stream logs)
* Numerous NOAA additions for firehose
	* Attempts to reconnect after unexpected disconnect	* Can fulfill Diego container metrics requests
 * Syslog
 	* Syslog configuration consolidated into metron package
 	* Syslog aggregator package removed (use metron package for syslog forwarding)

