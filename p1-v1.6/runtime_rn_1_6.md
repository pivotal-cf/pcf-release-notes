## Changes since v1.5.0.0:

## Elastic Runtime

* CF Release Version: 222

### New Features

#### Default Stack: cflinuxfs2

This release completely removes the lucid64 stack from Pivotal Cloud Foundry. After upgrading to this release, apps that have not been migrated to cflinuxfs2 will fail to start.

Operators are encouraged to migrate all apps to cflinuxfs2 as mentioned in the v1.4 release notes, before upgrading to v1.6.

Further details can be found [here](https://support.pivotal.io/hc/en-us/articles/205751277-New-cflinuxfs2-Stack).

#### Cloud Foundry Runtime - Diego

Diego is the new application runtime that Pivotal Cloud Foundry will use by default to run your apps.

Diego enables many new features and enhancements, details for which can be found here.

#### Windows 2012 stack

You can use the Windows .NET MSI to run Windows containers.

#### Docker

Docker support for Pivotal Cloud Foundry is in beta currently. To enable Docker support in your deployment, you can use a CLI command as a user with the admin role: `cf enable-feature-flag diego_docker`

#### Security Configuration of Runtime

This section allows you to configure security settings for your Pivotal Cloud Foundry Elastic Runtime components, such as HAProxy, Router, and the DEA/Diego Cells.

The SSL Termination Certificate input now applies to both HAProxy (if you use this component) and the Cloud Foundry Router. This field is not optional, even if you use an external load-balancer instead of HAProxy, since it will be applied to the Router. It does not have to be the same certificate as the one used by your external load-balancer, as this certificate is only used for SSL traffic between the load-balancer and Router. You can enable SSL termination on the Router with a checkbox in this same section, "Enable TLS on the Router". More details [here](http://docs.pivotal.io/pivotalcf/adminguide/enabling-https-to-routers.html) about securing connections to the Router.

If you have multiple domains to map to the Router, such as separate system and apps domains, you can only use one SSL certificate. The Router does not yet support multiple certificates. However one SSL certificate with multiple domains attributed to it is acceptable.

The "Enable cross-container traffic" checkbox now controls the restriction of cross-container traffic for both DEAs and Diego Cells, depending on which runtime backend platform you choose. It is not recommended to check this checkbox for multi-tenant environments, but this does enable using application container to connect to other application containers directly without going through the router which may be desired for microservices, which may be optionally used with Pivotal Spring Cloud Services.

This section also includes fields which allow specifying the HAProxy and Router ciphers, both of which are optional fields.

#### Other Runtime Features

##### S3-Compatible Filestore Configuration

It is now possible to configure four different S3 buckets to comprise the Cloud Controller's filesystem, instead of just one.

You can choose to use four different buckets if you are installing Pivotal Cloud Foundry for the first time, but not for an upgrade (i.e., from Pivotal Cloud Foundry v1.5 to v1.6). This is because the data will not be automatically migrated from the one bucket configuration in 1.5 to separate buckets in 1.6. It is recommended to use separate buckets for new deployments, but existing deployments are supported with one bucket.

##### Experimental Features

There are no experimental features being introduced in PCF Elastic Runtime for v1.6.

#### Improved MySQL Service
MySQL, used by some of the Pivotal Cloud Foundry system applications in the past, is now usable for every Pivotal Cloud Foundry system component and application, including Cloud Controller and UAA. This is an improvement over the non-highly-available Postgresql databases that these components and applications may have solely relied upon in previous versions.

You can choose to use this MySQL service if you are installing Pivotal Cloud Foundry for the first time, but not for an upgrade (i.e., from Pivotal Cloud Foundry v1.5 to v1.6). This is because the data will not be automatically migrated from one database to a new one. A future releases is intended to address a data migration for installations that started with a postgres database.

#### API/cf CLI

Add points about CLI, e.g for Diego, here...

Note: These features are available via API only; cf CLI support coming soon
- Org Managers and Space Managers can now manage roles without requiring admin privileges
- Max number of private domains can be specified in the Organization Quota.
- Max number of app instances can be specified in the Organization Quota and Space Quota
- Admins can purge a single service instance and its bindings.  This is a more targeted purge to resolve a single service instance than the purge service offering.

### Bug Fixes

## UAA and Login Server
#### FEature name here...

#### Bug Fixes


## Logging, Analytics and Metrics

### New Features


### Bug Fixes

## Buildpacks

##### Smaller Buildpacks

##### Binary Buildpack


## Security - CVE fixes have been implemented since v1.5.0.0 and released via security patches.

* Canonical Ubuntu USN-

