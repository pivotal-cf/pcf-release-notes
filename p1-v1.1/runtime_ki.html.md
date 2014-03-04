# Pivotal CF Elastic Runtime Known Issues
## 1.1.0.0 Release 

* It's possible for the auth token to expire right before we make a request to Loggregator, which means that users will be unable to see logs for their app. They will also see an "Error: Invalid authorization" message in Loggregator. Logging in again will fix the issue. 
* The ‘system’ org is reserved for the Developer Console. Spaces cannot be created in the ‘system’ org.
* After installation of the “Pivotal Metrics” product (currently in Beta release), operators will need to increase the collector vm instance count to 1 and re-push Elastic Runtime to have the setting take effect. 
* Deleting a deployment of a service product  (e.g. HD, MySQL) will leave orphan rows in the cloud controller db. Before the same service product can be deployed again, Elastic Runtime must be deleted and re-deployed.
* Quotas are not configurable for the plan offered by MySQL Dev. 
* If upgrading from 1.0 to 1.1, in the Resource Sizes for Pivotal Elastic Runtime change the following values:
	* RAM (MB) for Cloud Controller must be 4096 (or greater)
	* Ephemeral Disk (MB) for Compilation must be 6144 (or greater)
* SSO integration is only supported when using Pivotal CF on vSphere 5.5. SSO integration is a beta feature with the 1.1.0.0 release. 
