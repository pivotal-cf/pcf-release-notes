---
title: Pivotal Elastic Runtime v1.4.0.0 Release Notes
---

## Changes since v1.3.3.0:

* AWS support
* Configurable MySQL HAProxy tier, including ability to add an external load-balancer
* User notification service and API
* Cloud Controller feature flags for reconfiguration of core platform settings in real time
* Autoscaling service is now officially GA
* Browser-based streaming logs and services usage billing events
* Extended the CF CLI with new custom commands:
	* Automate zero-downtime application deployment
	* Automate common tasks (seed a new CF install with orgs, spaces, and apps)
	* Streamline development
	* Visualize CPI and memory usage of an app
* New commands can accept arguments, invoke other commands, make API calls, and interact with the file system or environment
* Apply new environment variables to custom groups of running applications, such as all staging applications, for use on restart
* Map LDAP Groups to Administrator roles
* SAML XML support for SSO
* Patch for GHOST security vulnerability
* Buildpack updates:
	* Java (2.7.1)
		* Improved access logging
		* Improved AppDynamics integration
		* New Relic on Java 8
		* Secure dependency retrieval via HTTPS
		* Java 8 as default
		* Tomcat 8 as default
	* Node.js (1.1.1)
	* Go (1.1.1)
	* Python (1.1.1)
	* Ruby (1.2)
	* PHP (1.0.2)
* Updated git inside Warden containers to 2.2.1
* Add possibility to specify Postgres role permissions in manifest
* Allow core files to be generated in Warden
* Add the ability to configure IP restrictions for the UAA and Login Server HTTP ports
* Make the logging level of the collector configurable
* Randomize NATS server selection
* Make ha_proxy respect disabling timeout
* NO: Fixed an issue where the DEA needed twice the space requested to successfully place an app
* More flexible nested domain creation rules
* DEA sends NATS heartbeat even when there are no running instances. This keeps HM9000 from falsely reporting problems.
* Retry polling on the state of the upload if error is an HTTP timeout
* Sets the status code for upgrade to Websocket and TCP scenarios
* Bump apcera/NATS to v1.0.6
* Fixed issue where router does not start if dropsonde is misconfigured
* Prune routes when no connection to NATS is established
* Fixed an issue with leaking file descriptors
* Fix key type issue in Graphite historian
* Enhanced Graphite and router metrics
* NO: Fixed Mysql 5.6 issue on timestamp creation
* Fixed issue where deadlocks were happening on delayed job workers
* Update Service Plan completed
* Removed unnecessary warning when plans without instances are deleted during broker catalog sync
* Fixed Space Developer able to move a service instance from one space to another
* Pass through message from broker to client for 409 responses
* Add timestamp prefix to Postgres logs.
* Fixed bin/console on the API VMs.
* Provide a default value for cc.internal\_api\_user
* Add notifications preferences as default scopes for all future UAA users.
* Fixed dead fiber issue on DEAs
* Fixed orphan container issue on DEAs
* Allow pprof to be enabled on the GoRouter
* Improve GoRouter stability (memory & GC times)
* Bumped apcera's NATS client in yagnats and handle callbacks
* Default GOMAXPROCS to the number of available CPUs
* Fixed issue with collector leaking CLOSE_WAIT sockets
* Updated Cloud Controller's Ruby version to 2.1.4
* Allow timeouts for CATs to be configurable
* Inlined relations API performance enhancements
* Added new endpoint to return memory usage of an org /v2/organizations/:guid/memory_usage
* Route endpoints can now request their own staleness threshold
* Fixed an issue with collocating cloud\_controller\_ng and cloud\_controller\_worker with NFS
* Upgraded dropsonde
* Update default request\_timeout\_in\_seconds to 900s (15min)
* Periodically clean up packages that have been pending for too long
* Changed HM9000 to communicate with Cloud Controller over HTTP, instead of NATS, to address an issue where HM9000's API stops responding to requests
* Deprecated AppEvent in Cloud Controller
* Cloud Controller worker names now include job index
* Fixed an issue where dir\_server was leaking inotify watches
* Allowed login server to be disabled via spiff templates
* Fixed an issue where logs were not being captured when an app is shutting down
* Fixed a bug where two apps in two different orgs could be mapped to the same route
* The format for Graphite keys that collector will emit is changing to include the IP address of the job that is reporting metrics. 
Originally it was sending: `Deployment.Job.0.some\_key`. 
Now it will be sending: `Deployment.Job.0.1-2-3-4.some_key`. 
* Users can change the plan for a service instance, if the feature is supported by the service broker
* Loggregator:
	* Feature: Loggregator firehose (v192)
	* Changing syslog drain location no longer requires application restaging (v198)
	* System now Diego-enabled (v198)
	* Application forcibly closing output stream closes both standard out and standard error to logging system; fixes logging agent stability issues (v194)
	* New tuning parameters for CC polling (created v198, updated v203):
		* properties.syslog\_drain\_binder.update\_interval\_seconds
		* properties.syslog\_drain\_binder.polling\_batch\_size
	* Standardized --config flag across all components (v203)
	* Numerous general system fixes:
		* Golang 1.3.X now default for most components (v194)
		* Bug fixes for recovering when NATS connection is lost (v192)
		* Honor system’s use\_ssl\_flag (v201)
		* Add timestamps to every HttpStartStop envelope (v205)
	* Metron features and fixes:
		* No longer report metrics for downed component (v186)
		* Fixed: application shutdown logs were not being collected (v192)
		* Stability fixes between dropsonde and Metron (v192, v194)
		* Tracks cumulative values now in counters (v200)
	* Doppler features and fixes:
		* Increased buffer size for messages to better handle drops (v198)
		* Improved channel operations for better durability (v200)
	* TrafficController / NOAA features and fixes:
		* Streaming endpoint can use a cookie to get the OAuth token (allows JS clients to stream logs) (v192)
	* Numerous NOAA additions for firehose (v192):
		* Attempts to reconnect after unexpected disconnect (v192, improved in v203)
		* Can fulfill Diego container metrics requests (v200)
* Syslog:
	* Syslog configuration consolidated into Metron package
	* Syslog aggregator package removed (use Metron package for syslog forwarding)
* UAA:
	* Property changes for Loggregator firehose
* Login Server:
	* Updated to Spring Security OAuth V2:

		The Spring Security OAuth library has been updated from version 1.0.5 to 2.0.3.
Apart from bug fixes, major highlights include modernization and ease of use for OAuth server and client apps on Spring. Refer to the following blog posts for more details about the changes:

	https://spring.io/blog/2014/04/18/spring-security-oauth-2-0-0-rc1-available
	https://spring.io/blog/2014/09/01/spring-security-oauth-2-0-3-available-now

* Updated HAProxy to disable SSLv3. This addresses POODLE CVE-2014-3566.
* Reverted default AWS instance types back to m1 and c1 due to instability experienced with m3 and c3 instance types
* Added VCAP_APPLICATION to the /v2/apps/:guid/env endpoint
* Updated to latest gnatsd as of October 7th, 2014
* Removed syslog forwarder from cloud\_controller; metron_agent is responsible for this now.
* Added drain for restarts due to memory usage
* We are now always registering routes through NATS on an interval
cc\_ng, cc\_clock, and cc\_worker jobs have configurable memory limits for alert and restart
* Update fog to 1.23.0
* Fixed an issue for MySQL CCDB where Java apps with start commands greater than 255 characters failed to start
* Fixed an issue where users could not list other users in the org/space







