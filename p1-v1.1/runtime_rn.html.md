# Pivotal Elastic Runtime v1.1.0.0 Release Notes

### Summary: Elastic Runtime v1.1.0.0 includes new features, bug fixes and security updates

### Changes since v1.0.0.1:

* This release upgrades Ruby to version 1.9.3-p484 for the Elastic Runtime subsystems and buildpacks.  Elastic Runtime applications using the default Ruby buildpack will receive the updated Ruby upon restaging.
* Several improvements and additions were made to the information collected by loggregator: App crash and staging data, the ability to see which app index is causing a log message, and better readability in measuring bytes of memory.
* New performance metrics for Cloud Controller have been added. The new, optional JMX extension Pivotal Ops Metrics will expose all metrics.  
* Updated the NodeJS buildpack.
* Improved enforcement of disk space quota in Linux Containers for applications.
Cloud Controller now supports scalable asynchronous workers providing more control over horizontal scalability. 
* Improved pruning of events tables in the Cloud Controller database.
Application information is now removed from the Cloud Controller database when applications are deleted.
* Updates to UAA 1.4.7 and the multiple login servers to 1.2.10. UAA now has a new scope: oauth.approvals for users to manage delegated approvals to approved OAuth client applications.
* New Cloud Controller endpoint (/v2/app_usage_events) to enable usage metering for applications. 
* Significant improvements to Linux Container isolation for noisy neighbors.
Improved Cloud Controller API performance.
* New horizontally scalable Health Manager released. The codename for this component was HM9000 during development.

## Affected Components:

* This release will install an updated Operating System image (known as a BOSH stemcell)  and will create new virtual machines for all Pivotal CF Elastic Runtime components.
