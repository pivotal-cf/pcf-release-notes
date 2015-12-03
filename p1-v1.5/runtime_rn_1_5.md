---
title: Pivotal Elastic Runtime v1.5.0.0 Release Notes
---

## v1.5.9.0 Patch

This patch includes CVE patches for [USN-2821-1](http://www.ubuntu.com/usn/usn-2821-1/) and [USN-2820-1](http://www.ubuntu.com/usn/usn-2820-1/). Additional information can be found at https://pivotal.io/security

## v1.5.8.0 Patch

This patch release includes CVE patches for [USN-2806-1](http://www.ubuntu.com/usn/usn-2806-1/) and [USN-2798-1](http://www.ubuntu.com/usn/usn-2798-1/). Additional information can be found at https://pivotal.io/security

## v1.5.7.0 Patch

This patch release includes CVE patches for [USN-2778-1](http://www.ubuntu.com/usn/usn-2778-1/) and [USN-2767-1](http://www.ubuntu.com/usn/usn-2767-1/). Additional information can be found at https://pivotal.io/security

## v1.5.6.0 Patch
This release includes CVE fixes for several low / medium vulnerabilities as part of the monthly patch release schedule for the PCF Suite of products (Ops Manager, Elastic Runtime, MySQL, Ops Metrics, Gemfire SSC, Redis and RabbitMQ for Pivotal Cloud Foundry). The CVEs being fixed are [USN-2765-1](http://www.ubuntu.com/usn/usn-2765-1/), [USN-2756-1](http://www.ubuntu.com/usn/usn-2756-1), [USN-2751-1](http://www.ubuntu.com/usn/usn-2751-1), [USN-2740-1](http://www.ubuntu.com/usn/usn-2740-1/), [USN-2739-1](http://www.ubuntu.com/usn/usn-2739-1/), [USN-2738-1](http://www.ubuntu.com/usn/usn-2738-1/), [USN-2726-1](http://www.ubuntu.com/usn/usn-2726-1/) and [USN-2722-2](http://www.ubuntu.com/usn/usn-2722-1/). Additional details regarding each fix can be found at https://pivotal.io/security. 

Note one important known issue with the 1.5.6 patch for OpenStack deployments. 
Please note that BOSH stemcell v3094, which this version of Elastic Runtime references, has a limitation affecting OpenStack users only: 

  * Elastic Runtime 1.5.6 on OpenStack does not work with S3/Swift blobstores.
  * Elastic Runtime 1.5.6 on OpenStack users must configure their object storage to use the internal blobstore option. 
  * vSphere, AWS and vCloud users are not affected. 
  * This will be fixed in the next release.

## v1.5.4.0 Patch
This release includes CVE fixes for several low / medium vulnerabilities as part of the monthly patch release schedule for the PCF Suite of products (Ops Manager, Elastic Runtime, MySQL, Ops Metrics, Gemfire SSC, Redis and RabbitMQ for Pivotal Cloud Foundry). The CVEs being fixed are [USN-2718-1](http://www.ubuntu.com/usn/usn-2718-1/), [USN-2694-1](http://www.ubuntu.com/usn/usn-2694-1), [USN-2698-1](http://www.ubuntu.com/usn/usn-2698-1), [USN-2710-1](http://www.ubuntu.com/usn/usn-2710-1/) and [USN-2710-2](http://www.ubuntu.com/usn/usn-2710-2/). Additional details regarding each fix can be found at https://pivotal.io/security. 


## v1.5.3.0 Patch

This patch release includes a CVE patch for [USN-2696-1](http://www.ubuntu.com/usn/usn-2696-1/) and fixes an intermittent issue where Windows 7 users could encounter cli commands dropping with an error that the connection was “forcibly dropped”. Additional information can be found at https://pivotal.io/security

## v1.5.2.0 Patch

This patch release includes CVE patches for [USN-2670-1](http://www.ubuntu.com/usn/usn-2670-1/), [USN-2684-1](http://www.ubuntu.com/usn/usn-2684-1/) and [USN-2690-1](http://www.ubuntu.com/usn/usn-2690-1/). Additional information can be found at https://pivotal.io/security

## v1.5.1.0 Patch

Elastic Runtime v1.5.1.0 includes CVE patches for [CVE-2015-1420](http://www.pivotal.io/security/cve-2015-1420), [CVE-2015-1330](http://www.pivotal.io/security/cve-2015-1330), [CVE-2015-3281](http://www.pivotal.io/security/cve-2015-3281), and [USN-2639-1](http://www.pivotal.io/security/usn-2639-1). There are also some updates to Apps Manager ([details](http://docs.pivotal.io/pivotalcf/pcf-release-notes/p1-v1.5/apps_manager_rn_1_5.html)), and a notifications bug fix for incorrect setting of a verify_ssl flag variable.

## Changes since v1.4.0.0:

## Elastic Runtime

##### CF Release Version: 208

### New Features

#### Default Stack: cflinuxfs2

New deployments will no longer have the lucid64 stack available.

Operators are encouraged to migrate all apps to cflinuxfs2 as mentioned in the v1.4 release notes.

A future release will completely remove the lucid64 stack from Pivotal Cloud Foundry. After upgrading to this subsequent release, apps that have not been migrated to cflinuxfs2 will fail to start.

Further details can be found [here](https://support.pivotal.io/hc/en-us/articles/205751277-New-cflinuxfs2-Stack).

#### Diego-beta Tile and Windows 2012 stack

You can use Diego to run your apps in Pivotal Cloud Foundry v.1.5. However, you will need to download and install an additional tile. [Details](../../opsguide/diego-overview.html)

#### Security Configuration of Runtime

This new section allows you to configure security settings for your Pivotal Cloud Foundry Elastic Runtime components, such as HAProxy, Router, and the DEAs.

The SSL Termination Certificate input (for HAProxy) and the "Trust Self-Signed Certificates" checkbox have been moved to this section.

By checking the "Enable cross-container traffic within each DEA" checkbox, you can disable a restriction on the DEA that disallows containers on a particular DEA from communicating with each other. We do not recommend that you select this checkbox in multi-tenant environments.

This section also includes fields which allow configuring the HAProxy SSL certificate and HAProxy cipher string, the latter of which is an optional field. The SSL certificate is not optional, even if you use an external load-balancer instead of HAProxy, since it could potentially be referenced by other Pivotal Cloud Foundry services that you may choose to install.

#### Other Runtime Features

##### S3-Compatible Filestore Configuration

OpenStack allows for use of an external filestore that is compatible with Amazon's AWS S3 buckets. You can now choose whether you want to deploy Pivotal Elastic Runtime using an internal filestore or an external S3-compatible bucket, whether it is hosted by AWS or OpenStack. Note that Swift buckets are NOT known to be compatible at this time; however, Ceph-backed containers are compatible.

If using an external filestore, you can configure the URL endpoint of your S3-compatible filestore under the File Storage Config section. For example, if you are using AWS S3, you can keep this field configured with the default value https://s3.amazonaws.com. Note that this default points to US East region.

##### Experimental Features

These are features that you should be cautious about enabling if you have other Pivotal Cloud Foundry service tiles installed in your Pivotal Cloud Foundry deployment. Not all of the services are guaranteed to work as expected with these features enabled.

If you check the "Disable HTTP traffic to HAProxy" checkbox, all port 80 traffic to HAProxy will be rejected and the VCAP_ID cookie generated by the GoRouter will have the secure flag enabled. If this checkbox is checked and your deployment is not using HAProxy, your external load balancer should be configured to not accept port 80 traffic. If this is not done, traffic to port 80 will still be forwarded to applications but would lose session stickiness.

IF you check the "Disable HTTP traffic to UAA" checkbox, all port 80 traffic to the UAA authentication server will be rejected.

#### Improved MySQL Service
MySQL, used by Notifications, Autoscaling, and Apps Manager, has been upgraded with a new proxy tier that has improved availability and a dashboard that displays node health in real time.

#### API/cf CLI

A space developer can create a wildcard route for private domains. Previously, only admins were allowed to create wildcard routes.

`cf create-route SPACE DOMAIN -n "*"`

For example, you could create a wildcard route *.example.com to be mapped to a special 404 app called my404app and myapp.example.com to be mapped to myapp.
Traffic to myapp.example.com would be routed to myapp and traffic to unknown.example.com would be routed to my404app.

### Bug Fixes
* Fixed an issue where buildpack_cache was not busted when switching stacks

## UAA and Login Server
#### UAA & Login Server Merger
UAA and Login Server have been merged into a single component. For Pivotal Cloud Foundry deployments, this translates to fewer virtual machines and increased ease of operation. [Details](https://github.com/cloudfoundry/uaa/releases/tag/2.0.0)

#### Single Sign-On for Applications on Pivotal Cloud Foundry
Muti-tenancy support has been added to UAA, which is leveraged by the new Pivotal Single Sign-On Services for Application on Pivotal Cloud Foundry. [Details](https://github.com/cloudfoundry/uaa/releases/tag/2.1.0)

Pivotal Single Sign-On service provides a quick and hassle-free way for your applications to be secured by federated identity providers with minimal coding effort. It connects your applications via Single Sign-On while streamlining the end user experience. It is a multi-tenant service which allows both Applications & Identity Providers to be segregated based on organizational needs. [Details](../../../p-identity/index.html)

#### Runbooks available for CA SiteMinder and Ping Identity Single Sign-On
Detailed steps for configuring Single Sign-On between Pivotal Cloud Foundry and industry standard identity providers like CA SiteMinder & Ping Identity are now available. [Details](../../opsguide/sso.html#configure-identity-provider)

#### Bug Fixes
The issue from 1.4 with LDAP authentication not working if LDAP Group Search base is not specified has been addressed.
[Details](../p1-v1.4/runtime_ki_1_4.html)

When LDAP is configured via Ops Manager console, the operator is now provided the option of whether they want to enable Admin Group Mapping. This is an optional configuration.
For existing deployments using the LDAP Admin group mapping, please manually make the right radio button selection and populate the Admin Group Search Base and the Group Search Filter before applying the changes in the Elastic Runtime tile for upgrade to 1.5.

## Logging, Analytics and Metrics

### New Features
* Metron now supports statsd protocol endpoint.
  * Conduit support for statsd. [Details](https://www.pivotaltracker.com/story/show/74358484)
  * Support for:
    * gauges [Details](https://www.pivotaltracker.com/story/show/91452210)
    * counters [Details](https://www.pivotaltracker.com/story/show/91450340)
    * timers [Details](https://www.pivotaltracker.com/story/show/91452204)
  * Sample statsd implementation:
    * in Go [Details](https://www.pivotaltracker.com/story/show/91449852)
    * in Ruby [Details](https://www.pivotaltracker.com/story/show/91449874)
    * in Java [Details](https://www.pivotaltracker.com/story/show/91450916)
  * Verified that increment/decrement function correctly. [details](https://www.pivotaltracker.com/story/show/91697848)
* Loggregator now generates UUID for components. [Details](https://www.pivotaltracker.com/story/show/91691260)
* Additional Doppler integration tests to prevent regression:
  * for metrics emission. [Details](https://www.pivotaltracker.com/story/show/89116544)
  * ... and for goroutine dumps. [Details](https://www.pivotaltracker.com/story/show/89069346)
* PR: Updated go package path. [Details](https://www.pivotaltracker.com/story/show/90392586)
* PR: InstrumentedResponseWriter conforms to CloseNotifier interface. [Details](https://www.pivotaltracker.com/story/show/91151056)
* All components are now built using Go 1.4

### Bug Fixes
* Fixed an issue where an incorrect typecast would cause a Doppler panic. [Details](https://www.pivotaltracker.com/story/show/91277702)
* Fixed Doppler incorrectly computing totalDroppedMessages as a result of fixing typecast issue.  [Details](https://www.pivotaltracker.com/story/show/91862858)
* PR: Fixed an issue where syslog drain binder assumes that cc is available via http by default.  [Details](https://www.pivotaltracker.com/story/show/89053898)
* PR: Additional typos and broken links. [Detail 1](https://www.pivotaltracker.com/story/show/90569414) [Detail 2](https://www.pivotaltracker.com/story/show/91918380)

## Buildpacks

##### Static File Buildpack

A new buildpack was added, named `staticfile_buildpack` by default,
which allows the deployment of an application made up solely of static
assets.

The application uses a minimal nginx instance to serve the assets, and
so may be deployed with a lower memory quota than generally required
for a full-blown web application.

Full documentation is available at
[github.com/cloudfoundry/staticfile-buildpack](https://github.com/cloudfoundry/staticfile-buildpack).

## Security - CVE fixes have been implemented since v1.4.0.0 and released via security patches.

* Cloud Foundry CVE-2015-1855 Cloud Controller Path Traversal
* Canonical Ubuntu USN-2617-1 FUSE vulnerability
* Canonical Ubuntu USN-2635-1
* Canonical Ubuntu CVE-2015-1328

