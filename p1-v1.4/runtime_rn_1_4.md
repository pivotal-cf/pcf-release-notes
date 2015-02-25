---
title: Pivotal Elastic Runtime v1.4.0.0 Release Notes
---

## Changes since v1.3.3.0:

* AWS support
* Configurable MySQL HAProxy tier, including ability to add an external load-balancer
* User notification service and API
* Cloud Controller feature flags for reconfiguration of core platform settings in real time
* Autoscaling service is now officially GA
* API enpoint that supports changing the plan of a running service instance
* Browser-based streaming logs and services usage billing events
* Extended the CF CLI with new custom commands
	* automate zero-downtime application deployment
	* automate common tasks (seed a new CF install with orgs, spaces, and apps)
	* streamline development
	* visualize CPI and memory usage of an app
* New commands can accept arguments, invoke other commands, make API calls, and interact with the file system or environment
* Apply new environment variables to custom groups of running applications, such as all the staging applications, for use on restart
* Map LDAP Groups to Administrator roles
* SAML XML support for SSO
* Buildpack updates:
	* Java (2.6)
		* Improved Access Logging
		* Improved AppDynamics Integration
		* New Relic on Java 8
		* Secure Dependency Retrieval via HTTPS
		* Java 8 as Default
		* Tomcat 8 as Default
	* nodejs (1.1.1)
	* Go (1.1.1)
	* Python (1.1.1)
	* Ruby (1.2)
	* PHP (1.0.2)
* Updated git inside warden container to 2.2.1
* Add possibility to specify postgres role permissions in manifest
* Allow core files to be generated in warden
* Add in the ability to configure IP restrictions for the UAA and Login Server HTTP ports.
* Make the logging level of the collector configurable
* Randomize nats server selection
make ha_proxy respect disabling timeout
* NO: Fixed an issue where the DEA needed twice the space requested to successfully place an app
* More flexible nested domain creation rules
* DEA sends nats heartbeat even when there are no running instances This keeps HM9000 from thinking there are problems.
* Retry polling on the state of the upload if error is an HTTP timeout
* Sets the status code for upgrade to Websocket and TCP scenarios
* Bump apcera/nats to v1.0.6
* Fixed issue where router does not start if dropsonde is misconfigured
* Prune routes when no connection to NATS is established
* Fixed an issue with leaking file descriptors
* Fix key type issue in graphite historian
* Enhanced Graphite and router metrics
* NO: Fixed Mysql 5.6 issue on timestamp creation
* Fixed issue where deadlocks were happening on delayed job workers
* Update Service Plan completed
* Removed unnecessary warning when plans without instances are deleted during broker catalog sync
* Fixed SpaceDeveloper able to move a service instance from one space to another
* Pass through message from broker to client for 409 responses
* Add timestamp prefix to postgres logs.
* Fixed bin/console on the api vms.
* Provide a default value for cc.internal_api_user
* Add notifications preferences as default scopes for all future UAA users.
* Fixed dead fiber issue on DEAs
* Fixed orphan container issue on DEAs
* Allow pprof to be enabled on the gorouter
* Improve GoRouter stability (memory & GC times)
* Bumped apcera's NATS client in yagnats and handle callbacks
* Default GOMAXPROCS to the number of available CPUs
* Fixed issue with collector leaking CLOSE_WAIT sockets
* Updated Cloud Controller's Ruby version to 2.1.4
* Allow timeouts for CATs to be configurable
* Inlined relations api performance enhancements
* Added new endpoint to return memory usage of an org /v2/organizations/:guid/memory_usage
* Route endpoints can now request their own staleness threshold
* Fixed an issue with collocating cloud_controller_ng and cloud_controller_worker with NFS
* Upgraded dropsonde
* Update default request_timeout_in_seconds to 900s (15min)
* Periodically clean up packages that have been pending for too long
* Changed HM9000 to communicate with Cloud Countroller over HTTP, and not NATS to address an issue where HM9000's API stops responding to requests
* Deprecated AppEvent in Cloud Controller
* Cloud Controller worker names now include job index
* Fixed an issue where dir_server was leaking inotify watches
* Allowed login server to be disabled via spiff templates
* Fixed an issue where logs were not being captured when an app is shutting down
* Fixed a bug where 2 apps in 2 different orgs could be mapped to the same route
* The format for graphite keys that collector will emit is changing to include the ip address of the job that is reporting metrics.
Originally it was sending: Deployment.Job.0.some_key.
Now it will be sending: Deployment.Job.0.1-2-3-4.some_key
* Users can change the plan for a service instance, if support for the feature is declared by the service broker
* Loggregator
	* Loggregator firehose
	* Property changes for firehose
	* Bug fixed where application shutdown logs were not being collected by loggregator
	* Loggregator streaming endpoint can use a cookie to get the oauth token (allows js clients to stream logs)
	* Bug fixes for recovering when NATS connection is lost
* Syslog
	* Syslog configuration consolidated into metron package
	* Syslog aggregator package removed (use metron package for syslog forwarding)
* UAA
	* Property changes for loggregator firehose
* Login Server
	* Change Email functionality: Login Server now supports Change Email for users. Authenticated users can request a change to their email from the Account Settings page and verify the new email via the same process as Account Creation. Once verified, the new email is reflected on the user account. If the Username is same as the email, both get updated at the same time. This feature is only restricted to users stored in the internal UAA user store. The users from external sources such as LDAP and SAML are treated as read-only
	* Integration with Notifications Server:
Login Server now supports integration with a central Notifications Server which provides the ability to manage and send emails. Standard flows like Create New Account, Password Reset, & Change Email can now use the Notifications Server for sending emails to users if configured.
	* Updated to Spring Security OAuth V2 -The Spring Security OAuth library has been updated from version 1.0.5 to 2.0.3.
Apart from bug fixes, major highlights include modernization and ease of use for OAuth server and client apps on Spring. More details about the changes can be found here:
https://spring.io/blog/2014/04/18/spring-security-oauth-2-0-0-rc1-available
https://spring.io/blog/2014/09/01/spring-security-oauth-2-0-3-available-now
* Updated HAProxy to disable SSLv3. This addresses POODLE CVE-2014-3566
* Reverted default AWS instance types back to m1 and c1 due to instability experienced with m3 and c3 instance types
* Added VCAP_APPLICATION to the /v2/apps/:guid/env endpoint
* Updated to latest gnatsd as of October 7th, 2014
* Removed syslog forwarder from cloud_controller; metron_agent is responsible for this now.
* Added drain for restarts due to memory usage
* We are now always registering routes through nats on an interval
cc_ng, cc_clock, and cc_worker jobs have configurable memory limits for alert and restart
* Update fog to 1.23.0
* Fixed an issue for mysql ccdb where java apps with start commands greater than 255 characters failed to start
* Fixed an issue where users could not list other users in the org/space







