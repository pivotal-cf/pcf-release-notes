---
title: Pivotal Elastic Runtime v1.6.0.0 Release Notes
---
### Versions 1.6.8 and higher versions of Elastic Runtime consist of these Cloud Foundry versions:
- CF Release version: 225
- Diego version: 0.1441
- Garden version: 0.330
- CF MySQL version: 23
- etcd version: 18

### Versions 1.6.4 and higher versions of Elastic Runtime consist of these Cloud Foundry versions:
- CF Release version: 225
- Diego version: 0.1441
- Garden version: 0.327
- CF MySQL version: 23
- etcd version: 18

### Versions 1.6.0 to 1.6.3 of Elastic Runtime consist of these Cloud Foundry versions:
- CF Release version: 222
- Diego version: 0.1437
- Garden version: 0.308
- CF MySQL version: 23
- etcd version: 16

## v1.6.30

Patches CVE-2016-0928. Additional info can be found at https://pivotal.io/security.

This also addresses an issue with rare occurrences of application containers being assigned duplicate IP addresses.

## v1.6.29

Improved reliability of Elastic Runtime. Patches CVE-2016-4468. Additional info can be found at https://pivotal.io/security.

## v1.6.28 Patch

Patches USN-3001-1. Additional info can be found at https://pivotal.io/security.

## v1.6.27 Patch

Patches USN-2985-1, USN-2985-2, USN-2981-1, USN-2970-1, USN-2966-1, USN-2994-1, USN-2987-1, USN-2990-1, USN-2983-1, and USN-2961-1. Additional info can be found at https://pivotal.io/security.

This also addresses an issue with rare occurrences of application containers being assigned duplicate IP addresses.

## v1.6.26 Patch

This just updates your Diego Cell and Diego BBS jobs to not use static IPs. This is useful if you want to scale up Diego jobs and do not have enough IP addresses reserved on your network.

## v1.6.25 Patch

As part of this release, there is a checkbox in the Elastic Runtime tile configuration that asks for every operator/administrator of the deployment to acknowledge that they understand how to implement application security groups successfully to secure their deployments. More info about this topic can be found here, in the [Application Security Groups](http://docs.pivotal.io/pivotalcf/1-7/adminguide/app-sec-groups.html) topic of our documentation.

This also patches USN-2977-1. Additional info can be found at https://pivotal.io/security. Also increases the robustness of etcd. This also patches a regression bug that was introduced by Elastic Runtime 1.6.24 which reverted a patch for Diego introduced in Elastic Runtime 1.6.21 that fixed descriptor limits on listeners.

## v1.6.23 Patch

Patches USN-2959-1, USN-2957-1, USN-2949-1, USN-2943-1, and USN-2935-2. Additional info can be found at https://pivotal.io/security

## v1.6.22 Patch

This patch addresses a race condition experienced in some multi-node Diego DB (BBS) clusters. It also adds the Cloud Controller statsd metrics to the firehose output.

## v1.6.21 Patch

This release fixes an issue with connection flooding in the Loggregator traffic controller.

It also updates Digeo to version 0.1446.5 which includes fixes for NOAA and file descriptor limits on listeners.

<p class="note"><strong>Known Issue</strong>: A race condition experienced in some 3-node Diego DB clusters will be fixed in a follow-on release.</p>

## v1.6.20 Patch
Patches CVE-2016-0781 and CVE-2016-2165. Additional info can be found at https://pivotal.io/security.

## v1.6.19 Patch

Patches USN-2939-1. Additional info can be found at https://pivotal.io/security.

## v1.6.18 Patch

Patches USN-2929-1. Additional info can be found at https://pivotal.io/security.

## v1.6.17 Patch

Patches USN-2900-1 (this one is a critical GNU C lib (glibc) CVE), [CVE-2016-0761](http://pivotal.io/security/cve-2016-0761) (critical Cloud Foundry Garden CVE with respect to Docker Host File managment), USN-2910-1 (high CVE in the Linux kernel), USN-2897-1, and USN-2896-1.

This also fixes an IP allocation issue with v1.6.16 where Cloud Controller would sometimes try to take the IP address of another job.

This also fixes an issue with v1.6.15 where UAA startup fails for installs that use LDAP, when upgrading from Elastic Runtime v1.5.x or v1.6.0-1.6.14.

## v1.6.15 Patch

This fixes a critical Linux kernel bug that led to unkillable AUFS container processes that make the Diego Cells and DEAs unresponsive. The bug was introduced in the previous kernel releases that addressed CVEs. The stemcell in this version of Elastic Runtime patches the bug.

This release also updates the UAA, Diego, Consul, and etcd releases for increased stability and lifecycle operations. The Diego release update (now version 0.1446) allows for larger customized buildpacks to be used in your deployment.

This release addresses known issues around applications with long file names failing to stage on the Windows 2012 R2 stack. File paths are still subject to the Microsoft Windows MAX_PATH limit of 260 characters. Note that the Diego operating directory adds approximately 40 characters to the path length, in addition to anything in the application directory.

There is known issue with UAA startup when LDAP is configured, please prefer to the Known Issues section for more details and remediation.

## v1.6.14 Patch

This introduces patches for [CVE-2016-0732](https://pivotal.io/security/cve-2016-0732), [USN-2882-1](http://www.ubuntu.com/usn/usn-2882-1), [USN-2879-1](http://www.ubuntu.com/usn/usn-2879-1), [USN-2875-1](http://www.ubuntu.com/usn/usn-2875-1), and [USN-2874-1](http://www.ubuntu.com/usn/usn-2874-1). Additional info can be found at https://pivotal.io/security.

It was also discovered that several CVE patches since early Dec 2015, while resolved in the BOSH stemcell, were not applied to the root filesystem of application containers running on Diego in PCF Elastic Runtime. PCF Elastic Runtime versions 1.6.5 through 1.6.13 therefore had versions of this root filesystem on Diego that remained vulnerable to several of the CVEs identified and addressed from December 2015 through January 2016. It is recommended that 1.6.13 and below installations of Elastic Runtime running Diego upgrade to 1.6.14 or higher versions to address these CVEs.

## v1.6.13 Patch

This patches [USN-2871-1](http://www.ubuntu.com/usn/usn-2871-1). Additional information can be found at https://pivotal.io/security.

## v1.6.12.0 Patch

This patches [CVE-2016-0715](https://pivotal.io/security/cve-2016-0715). Additional information can be found at https://pivotal.io/security.

## v1.6.11.0 Patch

This patches [CVE-2016-0708](https://pivotal.io/security/cve-2016-0708), [USN-2869-1](http://www.ubuntu.com/usn/usn-2869-1), [USN-2868-1](http://www.ubuntu.com/usn/usn-2868-1), [USN-2865-1](http://www.ubuntu.com/usn/usn-2865-1), and [USN-2861-1](http://www.ubuntu.com/usn/usn-2861-1). Additional information can be found at https://pivotal.io/security.

## v1.6.10.0 Patch

This patch is only applicable for deployments that have not yet migrated to Diego cells from DEAs. In this patch release, the notifications and autoscale applications that come with Elastic Runtime were fixed to deploy to DEAs if you chose not to use Diego as the default runtime backend for your platform.

All the system applications for Elastic Runtime will be deployed to whichever backend, Diego or DEAs, you select as the default in the Elastic Runtime tile. No manual migration should be necessary.

## v1.6.9.0 Patch

This patches [USN-2857-1](http://www.ubuntu.com/usn/usn-2857-1), [USN-2842-1](http://www.ubuntu.com/usn/usn-2842-1), [USN-2842-2](http://www.ubuntu.com/usn/usn-2842-2), [USN-2837-1](http://www.ubuntu.com/usn/usn-2837-1), [USN-2836-1](http://www.ubuntu.com/usn/usn-2836-1), [USN-2835-1](http://www.ubuntu.com/usn/usn-2835-1), [USN-2834-1](http://www.ubuntu.com/usn/usn-2834-1), [USN-2830-1](http://www.ubuntu.com/usn/usn-2830-1), and [USN-2829-1](http://www.ubuntu.com/usn/usn-2829-1). Additional information can be found at https://pivotal.io/security.

There is also a fix to ensure that Consul server is launched before the etcd and Diego BBS jobs, so that the Consul DNS service is ready before those jobs start.

Also, by default the Postgres DBs included in Elastic Runtime now default to zero instances, since we encourage every 1.6.x deployment of Elastic Runtime to not use the Postgres DBs and instead only use MySQL.

## v1.6.8.0 Patch

This version patches a Garden CVE, [CVE-2015-5350](http://pivotal.io/security/cve-2015-5350).

This version also fixes a few issues on Garden containers, such as the inability to run Docker images that are larger than 120 MB and a network communication issue with the Openstack GRE Tunnel network for Pivotal Cloud Foundry deployments to Openstack (the Garden network MTU was lowered from 1500 to 1454 to address this). This also addresses a DNS resolution issue with Consul that causes several CF CLI command requests to take longer than expected.

As as result of these fixes, the OSS Cloud Foundry release for Garden was bumped to version 0.330.

## v1.6.7.0 Patch

This version fixes an issue for applications running on Windows containers that have very long file paths in their application project. You don't need to upgrade to this version unless you use Windows .NET applications with long file paths.

## v1.6.6.0 Patch

This patch includes CVE patches for [USN-2821-1](http://www.ubuntu.com/usn/usn-2821-1/) and [USN-2820-1](http://www.ubuntu.com/usn/usn-2820-1/). Additional information can be found at https://pivotal.io/security

## v1.6.5.0 Patch

This patch includes CVE patches for [USN-2815-1](http://www.ubuntu.com/usn/usn-2815-1/), [USN-2812-1](http://www.ubuntu.com/usn/usn-2812-1/) and [USN-2810-1](http://www.ubuntu.com/usn/usn-2810-1/). Additional information can be found at https://pivotal.io/security

Also moves Apps Usage service to an HTTPS route intead of plain HTTP.

## v1.6.4.0 Patch

This patch release includes CVE patches for [USN-2788-1](http://www.ubuntu.com/usn/usn-2788-1/), [USN-2787-1](http://www.ubuntu.com/usn/usn-2787-1/) and [USN-2788-2](http://www.ubuntu.com/usn/usn-2788-2/). Additional information can be found at https://pivotal.io/security

This patch also includes a migration from btrfs to aufs as the filesystem for application containers on Diego, for improved performance. It also fixes an issue with Cloud Controller returning a 503 error code whenever a user requests the status of an application that is still staging.

This patch also updates the Docker registry API to v2 instead of v1.

As as result of these fixes, the OSS Cloud Foundry components were bumped to these versions:
- CF Release version: 225
- Diego version: 0.1441
- Garden version: 0.327
- etcd version: 18

## v1.6.3.0 Patch

This patch release includes CVE patches for [USN-2806-1](http://www.ubuntu.com/usn/usn-2806-1/) and [USN-2798-1](http://www.ubuntu.com/usn/usn-2798-1/). Additional information can be found at https://pivotal.io/security

This also enables setting the Health Manager instance count to zero, since Health Manager is not used by the Diego runtime components. If you are using DEAs, you should continue to keep Health Manager around.

## v1.6.2.0 Patch

This release fixes an issue with application security groups not enforcing expected egress traffic rules for applications running on Diego.

## v1.6.1.0 Patch

This patch release includes CVE patches for [USN-2778-1](http://www.ubuntu.com/usn/usn-2778-1/). Additional information can be found at https://pivotal.io/security

## Changes since v1.5.0.0:

## Elastic Runtime

### New Features

#### Default Stack: cflinuxfs2

This release completely removes the lucid64 stack from [Pivotal Cloud Foundry&reg;](https://network.pivotal.io/products/pivotal-cf) (PCF). After upgrading to this release, apps that have not been migrated to cflinuxfs2 will fail to start.

Operators are encouraged to migrate all apps to cflinuxfs2, as mentioned in the v1.4 release notes, before upgrading to v1.6.

Further details can be found [here](https://support.pivotal.io/hc/en-us/articles/205751277-New-cflinuxfs2-Stack).

#### Cloud Foundry Runtime - Diego

Diego is the new application runtime that Pivotal Cloud Foundry&reg; will use by default to run your apps.

Diego enables many new features and enhancements, such as allowing the deployment of thousands of applications and resurrecting crashed applications within seconds. It also supports new workloads, such as .NET applications on Windows, Docker on Linux, and enables SSH access to containers.

Details about how Diego works can be found [here](../../concepts/diego/diego-auction.html). Details about its architecture can be found [here](../../concepts/diego/diego-architecture.html)

To enable SSH access to your application containers on Diego, you will need to make sure that your external load-balancer, if you have one, is listening on port 2222 and forwarding to port 2222 on the Diego Brain. Also, if you are using an external load-balancer for SSH access, separate of the one you have pointed to the Router for general access to Cloud Foundry, you will need to add ssh.(your-domain) to your DNS, pointing to this load-balancer. Details about SSH access to application containers on Diego can be found [here](../../devguide/deploy-apps/app-ssh-overview.html). Instructions for setting up the SSH ELB for AWS can be found [here](../../customizing/cloudform_elb_ssh_proxy.html).

There is a new field, "Application Containers Subnet Pool", which allows you to configure a specific subnet pool for your applications running on Diego. You can leave this field as its default value unless you specifically want to use a different subnet, say if you have a third-party service or other VMs running with the same IPs in your network. This features is only usable on Diego, not on DEAs. You can only specify a single CIDR subnet, no "excluded IPs" can be specified.

#### Windows 2012 stack

By instantiating and setting up Windows cells in your Cloud Foundry environment, users will be able to deploy Windows .NET applications with the same familiar `cf push` commands they are used to. These applications run inside Windows containers on Windows 2012 R2 servers within your environment. 

Diego must be enabled for applications to run on the new Windows 2012R2 stack. It can either be enabled by default or must be enabled for the individual application before that app can be started. Further documentation can be found [here](../../opsguide/deploying-diego.html). 

At this time, Windows cells cannot be managed by BOSH, but server deployment can easily be integrated with any number of existing infrastructure tools.

#### Docker

Docker support for Pivotal Cloud Foundry&reg; is in beta currently. To enable Docker support in your deployment, you can use a CLI command as a user with the admin role: `cf enable-feature-flag diego_docker`. Further details about Docker on Diego can be found [here](../../concepts/docker.html)

#### Security Configuration of Runtime

This section allows you to configure security settings for your Pivotal Cloud Foundry&reg; Elastic Runtime components, such as HAProxy, Router, and the DEA/Diego Cells.

The SSL Termination Certificate input now applies to both HAProxy (if you use this component) and the Cloud Foundry Router. This field is not optional, even if you use an external load-balancer instead of HAProxy, since it will be applied to the Router. It does not have to be the same certificate as the one used by your external load-balancer, as this certificate is only used for SSL traffic between the load-balancer and Router. You can enable SSL termination on the Router with a checkbox in this same section, "Enable TLS on the Router". More details [here](http://docs.pivotal.io/pivotalcf/adminguide/enabling-https-to-routers.html) about securing connections to the Router.

If you have multiple domains to map to the Router, such as separate system and apps domains, you can only use one SSL certificate. The Router does not yet support multiple certificates. However, one SSL certificate with multiple domains attributed to it is acceptable.

The "Enable cross-container traffic" checkbox now controls the restriction of cross-container traffic for both DEAs and Diego Cells, depending on which runtime backend platform is chosen. Pivotal does not recommend that you select this checkbox within multi-tenant environments. The feature enables using application containers to connect to other application containers directly, without going through the router. This setup may be desired for microservices, which may be optionally used with Pivotal Spring Cloud Services.

The Security Configuration section also includes fields that allow specifying the HAProxy and Router ciphers, both of which are optional fields.

#### Other Runtime Features

##### S3-Compatible Filestore Configuration

It is now possible to configure four different S3 buckets to comprise the Cloud Controller's filesystem, instead of just one.

You can choose to use four different buckets if you are installing Pivotal Cloud Foundry&reg; for the first time, but not for an upgrade (i.e., from Pivotal Cloud Foundry&reg; v1.5 to v1.6). This is because the data will not be automatically migrated from the one bucket configuration in 1.5 to separate buckets in 1.6. It is recommended to use separate buckets for new deployments. Existing deployments are supported with one bucket.

##### Experimental Features

There are no experimental features being introduced in PCF Elastic Runtime for v1.6.

#### Improved MySQL Service
MySQL, used by some of the Pivotal Cloud Foundry&reg; system applications in the past, is now available as a data store for every Pivotal Cloud Foundry&reg; system component and application, including Cloud Controller and UAA. This is an improvement over the non-highly-available Postgresql databases that these components and applications relied upon in previous releases.

You can choose to use this MySQL service if you are installing Pivotal Cloud Foundry&reg; for the first time, but not for an upgrade (e.g.: from Pivotal Cloud Foundry&reg; v1.5 to v1.6). This is because the data will not be automatically migrated from an existing database to a new one. The Pivotal team is currently working on the migration scripts that will allow for the migration of all databases in Postregesql to the HA MySQL service. We will announce when these scripts are ready for use, the timeframe of which is currently aiming for sometime during the first half of 2016.

If you do install Pivotal Cloud Foundry&reg; on the MySQL databases only, then you can scale down the Apps Manager Database (Postgres), Cloud Controller Database (Postgres), and UAA Database (Postgres) to zero instances. Those components will instead use the MySQL cluster.

#### API/cf CLI

Note: These features are available via API only; cf CLI support coming soon.
- Org Managers and Space Managers can now manage roles without requiring admin privileges.
- Max number of private domains can be specified in the Organization Quota.
- Max number of app instances can be specified in the Organization Quota and Space Quota.
- Admins can purge a single service instance and its bindings. This is a more targeted purge to resolve a single service instance than the purge service offering.

#### Apps Manager

This release adds support for the Diego Runtime, and features numerous fixes and enhancements for it.

Two new environment variables are introduced and one is removed in v1.6:

* The new `ENABLE_INTERNAL_USER_STORE` environment variable controls org and space user invitations, new user registrations, and password updates to the PCF internal user store. The default is set to `false`, which means that none of the features are exposed in Apps Manager. Set to `true` to expose these features.
* The new `ENABLE_NON_ADMIN_ROLE_MANAGEMENT` environment variable allows org managers and spaces managers to manage user roles regardless of where these users are created. The default is set to `false`, which means that none of the features are exposed in Apps Manager. Set to `true` to expose these features.
* The previous `ENABLE_NON_ADMIN_USER_MANAGEMENT` environment variable that controlled many of these same features is removed in v1.6.

#### DEAs

Multiple stability and performance improvements were made to DEAs. They can now handle many more simultaneous connections, for instance.

##  Identity (aka UAA Server)

- UAA now enforces HTTPS only communication. This was an experimental feature in PCF 1.5.x
- Added support for UAA Log Rotation via BOSH
- SAML SSO Integration Updates
  - Allow Identity Provider Metadata with missing XML Declaration tag
  - Strict checking for duplicate SAML Entity IDs
- Token Format Updates
 - UAA tokens now contain an origin field which signifies the Identity Provider used for authentication. If SAML IDP is used for authentication, the Identity Provider alias is set in as the origin value.
 - Support for nonce parameter in OAuth requests to prevent against CSRF attacks
 
## Logging and Metrics

* Diego metrics now flow through the Loggregator subsystem. 
  * Collector is deprecated.
  * DEA and HM9000 continue to use Collector.
  * A varz nozzle is available for directing metrics coming through Loggregator to Collector.
* There is a new field, "Syslog Drain Buffer Size", which allows you to configure the number of messages that your Doppler server will keep before starting to drop messages. Note that a larger buffer may overload your system.

## Buildpacks

### Smaller, More Secure Buildpacks

Buildpacks in PCF 1.6 are smaller than in PCF 1.5, since older,
unsupported versions of third-party dependencies are no longer being
packaged.

An example of this is Ruby 1.9.x, which reached
[End Of Life on February 23, 2015][ruby-eol] and was removed in
[ruby-buildpack v1.4.0][ruby-140].

  [ruby-eol]: https://www.ruby-lang.org/en/news/2014/01/10/ruby-1-9-3-will-end-on-2015/
  [ruby-140]: https://github.com/cloudfoundry/ruby-buildpack/releases/tag/v1.4.0

PCF 1.6 also is only providing the __last two__ patch releases on any
`major.minor` branch, with the goal of allowing an upgrade path, while
also encouraging developers to upgrade to the latest security releases
whenever possible.

The smaller buildpacks sizes also means a faster PCF installation, as
well as improved staging performance.

For any customers who want to customize the binaries that are shipped
with a buildpack, the tooling for generating custom buildpacks has
been open-sourced:

  * [buildpack-packager](https://github.com/cloudfoundry/buildpack-packager)
  * [binary-builder](https://github.com/cloudfoundry/binary-builder)


### Binary Buildpack

PCF 1.6 also provides a "binary buildpack", for customers to run
precompiled binaries, for those occasions when developers want a bit
more control over the executables that are running in the container.

The [binary-builder](https://github.com/cloudfoundry/binary-builder)
tooling can also be used to help build executables for a specific
rootfs in a maintainable manner.


## Security - CVE fixes have been implemented since v1.5.0.0 and released via security patches.

* Canonical Ubuntu USN-2765-1
* Canonical Ubuntu USN-2756-1
* Canonical Ubuntu USN-2751-1
* Canonical Ubuntu USN-2740-1
* Canonical Ubuntu USN-2739-1
* Canonical Ubuntu USN-2738-1
* Canonical Ubuntu USN-2726-1
* Canonical Ubuntu USN-2722-2
* Canonical Ubuntu USN-2718-1
* Canonical Ubuntu USN-2710-1
* Canonical Ubuntu USN-2710-2
* Canonical Ubuntu USN-2698-1
* Canonical Ubuntu USN-2696-1
* Canonical Ubuntu USN-2694-1
* Canonical Ubuntu USN-2690-1
* Canonical Ubuntu USN-2684-1
* Canonical Ubuntu USN-2670-1
* Canonical Ubuntu USN-2639-1
* CVE 2015-3281
* CVE 2015-1420
* CVE 2015-1330

### Other Bug Fixes
We fixed an issue with the v1.5.6 patch for OpenStack deployments. The BOSH stemcell v3094, which this version of Elastic Runtime references, has a limitation affecting OpenStack users only:

* Elastic Runtime 1.5.6 on OpenStack does not work with S3/Swift blobstores.
* Elastic Runtime 1.5.6 on OpenStack users must configure their object storage to use the internal blobstore option.
* vSphere, AWS and vCloud users are not affected.
* This is fixed in v1.6.0
