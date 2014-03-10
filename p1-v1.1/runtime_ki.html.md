# Pivotal CF Elastic Runtime 1.1.0.0 Known Issues 

* It's possible for the auth token to expire right before we make a request to Loggregator, which means that users will be unable to see logs for their app. They will also see an "Error: Invalid authorization" message in Loggregator. Logging in again will fix the issue. 
* The ‘system’ org is reserved for the Developer Console. Spaces cannot be created in the ‘system’ org.
* After installation of the “Pivotal Metrics” product (currently in Beta release), operators will need to increase the collector vm instance count to 1 and re-push Elastic Runtime to have the setting take effect. 
* Deleting a deployment of a service product  (e.g. HD, MySQL) will leave orphan rows in the cloud controller db. Before the same service product can be deployed again, Elastic Runtime must be deleted and re-deployed.
* Quotas are not configurable for the plan offered by MySQL Dev. 
* If upgrading from 1.0 to 1.1, in the Resource Sizes for Pivotal Elastic Runtime change the following values:
	* RAM (MB) for Cloud Controller must be 4096 (or greater)
	* Ephemeral Disk (MB) for Compilation must be 6144 (or greater)
* SSO integration is only supported when using Pivotal CF on vSphere 5.5. SSO integration is a beta feature with the 1.1.0.0 release. 
* Binding a service to an app will cause an error when requesting status from the app until it is restarted. 
* cf cli v6.0.1, included with the Developer Console in PCF v1.1, has a bug that will prevent Windows users from pushing archived apps like zips, jars, wars, etc. v6.0.2 has the fix and can be downloaded from here: https://console.run.pivotal.io/tools
