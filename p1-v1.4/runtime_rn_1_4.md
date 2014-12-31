---
title: Pivotal Elastic Runtime v1.4.0.0 Release Notes
---

## Changes since v1.3.3.0: 

* Buildpack updates:
* Java (2.6)
* nodejs (1.1.1)
* Go (1.1.1)
* Python (1.1.1)
* Ruby (1.2)
* PHP (1.0.2)

195:
Updated git inside warden container to 2.2.1 details
Add possibility to specify postgres role permissions in manifest details
Allow core files to be generated in warden details
Add in the ability to configure IP restrictions for the UAA and Login Server HTTP ports. details
Make the logging level of the collector configurable details
Randomize nats server selection details
make ha_proxy respect disabling timeout details
Fixed an issue where the DEA needed twice the space requested to successfully place an app details
More flexible nested domain creation rules details
DEA sends nats heartbeat even when there are no running instances This keeps HM9000 from thinking there are problems. details
Retry polling on the state of the upload if error is an HTTP timeout details
Sets the status code for upgrade to Websocket and TCP scenarios details
Bump apcera/nats to v1.0.6 details
Fixed issue where router does not start if dropsonde is misconfigured details
Prune routes when no connection to NATS is established details
Fixed an issue with leaking file descriptors details
Fix key type issue in graphite historian details
Enhanced Graphite and router metrics details
Fixed Mysql 5.6 issue on timestamp creation details
Fixed issue where deadlocks were happening on delayed job workers details
Work continues on Application Process Types details
Update Service Plan completed details
Work continues on Service Audit Events details
Removed unnecessary warning when plans without instances are deleted during broker catalog sync details
Fixed SpaceDeveloper able to move a service instance from one space to anotherdetails
Pass through message from broker to client for 409 responses details

194:
Add timestamp prefix to postgres logs. details
Fixed bin/console on the api vms. details
Fixed issue with nfs mounter job that was broken in cf-release v193 details 1 2
Provide a default value for cc.internal_api_user details
Add notifications preferences as default scopes for all future UAA users. details
Fixed dead fiber issue on DEAs details
Fixed orphan container issue on DEAs details
Allow pprof to be enabled on the gorouter details
Improve GoRouter stability (memory & GC times) details
Bumped apcera's NATS client in yagnats and handle callbacks details
Default GOMAXPROCS to the number of available CPUs details
Fixed issue with collector leaking CLOSE_WAIT sockets details
Work continues on Application Process Types details
Work continues on Updating Service Plans details
193:
Work continued on Application Process Types (Experimental) details
Fixed an issue introduced in cf-release 192 where DEA logging agent deadlocks sometimes when removing an app details
Updated Cloud Controller's Ruby version to 2.1.4 details
Allow timeouts for CATs to be configurable details
Inlined relations api performance enhancements details
Added new endpoint to return memory usage of an org /v2/organizations/:guid/memory_usage details
Route endpoints can now request their own staleness threshold details
Fixed an issue with collocating cloud_controller_ng and cloud_controller_worker with NFS details
Upgraded dropsonde details
Update default request_timeout_in_seconds to 900s (15min) details
Periodically clean up packages that have been pending for too long details
192:
Release Highlights
Changed HM9000 to communicate with Cloud Countroller over HTTP, and not NATS to address an issue where HM9000's API stops responding to requests details
Deprecated AppEvent in Cloud Controller details
Cloud Controller worker names now include job index details
Reverted a commit using git: urls details
Fixed an issue where dir_server was leaking inotify watches details
Allowed login server to be disabled via spiff templates details
Fixed an issue where logs were not being captured when an app is shutting downdetails
Fixed a bug where 2 apps in 2 different orgs could be mapped to the same routedetails
The format for graphite keys that collector will emit is changing to include the ip address of the job that is reporting metrics.
Originally it was sending: Deployment.Job.0.some_key
Now it will be sending: Deployment.Job.0.1-2-3-4.some_key
Started work on Process Types (experimental) details
Users can change the plan for a service instance, if support for the feature is declared by the service broker details
Loggregator
Loggregator firehose details
Property changes for firehose details
Bug fixed where application shutdown logs were not being collected by loggregator
Loggregator streaming endpoint can use a cookie to get the oauth token (allows js clients to stream logs)
Bug fixes for recovering when NATS connection is lost
Syslog
Syslog configuration consolidated into metron package
Syslog aggregator package removed (use metron package for syslog forwarding)
UAA
Property changes for loggregator firehose details
Login Server
Change Email functionality
The Login Server now supports Change Email for users. Authenticated users can request a change to their email from the Account Settings page and verify the new email via the same process as Account Creation. Once verified, the new email is reflected on the user account. If the Username is same as the email, both get updated at the same time. This feature is only restricted to users stored in the internal UAA user store. The users from external sources such as LDAP and SAML are treated as read-only
Integration with Notifications Server
Login Server now supports integration with a central Notifications Server which provides the ability to manage and send emails. Standard flows like Create New Account , Password Reset & Change Email can now use the Notifications Server for sending emails to users if configured.
Updated to Spring Security OAuth V2 -The Spring Security OAuth library has been updated from version 1.0.5 to 2.0.3.
Apart from bug fixes, major highlights include modernization and ease of use for OAuth server and client apps on Spring. More details about the changes can be found here:
https://spring.io/blog/2014/04/18/spring-security-oauth-2-0-0-rc1-available
https://spring.io/blog/2014/09/01/spring-security-oauth-2-0-3-available-now
191:
Updated HAProxy to disable SSLv3. This addresses POODLE CVE-2014-3566
Reverted default AWS instance types back to m1 and c1 due to instability experienced with m3 and c3 instance types
Added VCAP_APPLICATION to the /v2/apps/:guid/env endpoint
Added /v2/apps/:guid/copy_bits endpoint (Experimental)
Updated to latest gnatsd as of October 7th, 2014
190:
Removed syslog forwarder from cloud_controller; metron_agent is responsible for this now.
Added drain for restarts due to memory usage
189:
We are now always registering routes through nats on an interval
cc_ng, cc_clock, and cc_worker jobs have configurable memory limits for alert and restart
188:
NO: Updated the rootfs. Addresses BASH Shellshock CVE-2014-6271, CVE-2014-7169, CVE-2014-7186, and CVE-2014-7187
Update fog to 1.23.0
-- Java Buildpack v2.5
-- Improved Access Logging (via Guillaume Berche and and Kevin Kessler)
-- Improved AppDynamics Integration (via Troy Astle, Max Brunsfeld, Mike Youngstrom, and Shaozhen Ding)
-- New Relic on Java 8
-- Secure Dependency Retrieval via HTTPS
-- Needs more detail: Java 8 as Default
-- Tomcat 8 as Default (via Dave Head-Rapson)
-- Fixed an issue for mysql ccdb where java apps with start commands greater than 255 characters failed to start 1
Fixed an issue where users could not list other users in the org/space 1
187:
NO: Updated the rootfs to address BASH Shellshock CVE-2014-6271 & CVE-2014-7169








