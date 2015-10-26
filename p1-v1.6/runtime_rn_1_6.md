## Changes since v1.5.0.0:

## Elastic Runtime

* CF Release version: 222
* Diego version: 0.1437.0
* Garden version: 0.308.0
* CF MySQL version: 23

### New Features

#### Default Stack: cflinuxfs2

This release completely removes the lucid64 stack from Pivotal Cloud Foundry. After upgrading to this release, apps that have not been migrated to cflinuxfs2 will fail to start.

Operators are encouraged to migrate all apps to cflinuxfs2 as mentioned in the v1.4 release notes, before upgrading to v1.6.

Further details can be found [here](https://support.pivotal.io/hc/en-us/articles/205751277-New-cflinuxfs2-Stack).

#### Cloud Foundry Runtime - Diego

Diego is the new application runtime that Pivotal Cloud Foundry will use by default to run your apps.

Diego enables many new features and enhancements, details for which can be found here.

#### Windows 2012 stack

You can use the Windows .NET MSI to run you applications on Windows containers. Further details on enabling this feature can be found [here](../../opsguide/deploying-diego.html)

#### Docker

Docker support for Pivotal Cloud Foundry is in beta currently. To enable Docker support in your deployment, you can use a CLI command as a user with the admin role: `cf enable-feature-flag diego_docker`. For additional details about current Docker support, see details here. 

#### Security Configuration of Runtime

This section allows you to configure security settings for your Pivotal Cloud Foundry Elastic Runtime components, such as HAProxy, Router, and the DEA/Diego Cells.

The SSL Termination Certificate input now applies to both HAProxy (if you use this component) and the Cloud Foundry Router. This field is not optional, even if you use an external load-balancer instead of HAProxy, since it will be applied to the Router. It does not have to be the same certificate as the one used by your external load-balancer, as this certificate is only used for SSL traffic between the load-balancer and Router. You can enable SSL termination on the Router with a checkbox in this same section, "Enable TLS on the Router". More details [here](http://docs.pivotal.io/pivotalcf/adminguide/enabling-https-to-routers.html) about securing connections to the Router.

If you have multiple domains to map to the Router, such as separate system and apps domains, you can only use one SSL certificate. The Router does not yet support multiple certificates. However, one SSL certificate with multiple domains attributed to it is acceptable.

The "Enable cross-container traffic" checkbox now controls the restriction of cross-container traffic for both DEAs and Diego Cells, depending on which runtime backend platform is chosen. It is not recommended to check this checkbox within multi-tenant environments. The feature enables using application containers to connect to other application containers directly, without going through the router. This setup may be desired for microservices, which may be optionally used with Pivotal Spring Cloud Services.

The Security Configuration section also includes fields that allow specifying the HAProxy and Router ciphers, both of which are optional fields.

#### Other Runtime Features

##### S3-Compatible Filestore Configuration

It is now possible to configure four different S3 buckets to comprise the Cloud Controller's filesystem, instead of just one.

You can choose to use four different buckets if you are installing Pivotal Cloud Foundry for the first time, but not for an upgrade (i.e., from Pivotal Cloud Foundry v1.5 to v1.6). This is because the data will not be automatically migrated from the one bucket configuration in 1.5 to separate buckets in 1.6. It is recommended to use separate buckets for new deployments. Existing deployments are supported with one bucket.

##### Experimental Features

There are no experimental features being introduced in PCF Elastic Runtime for v1.6.

#### Improved MySQL Service
MySQL, used by some of the Pivotal Cloud Foundry system applications in the past, is now available as a data store for every Pivotal Cloud Foundry system component and application, including Cloud Controller and UAA. This is an improvement over the non-highly-available Postgresql databases that these components and applications relied upon in previous releases.

You can choose to use this MySQL service if you are installing Pivotal Cloud Foundry for the first time, but not for an upgrade (e.g.: from Pivotal Cloud Foundry v1.5 to v1.6). This is because the data will not be automatically migrated from an existing database to a new one. A future release is planned that will address data migration for installations that started with a postgres database.

#### API/cf CLI

Note: These features are available via API only; cf CLI support coming soon
- Org Managers and Space Managers can now manage roles without requiring admin privileges
- Max number of private domains can be specified in the Organization Quota.
- Max number of app instances can be specified in the Organization Quota and Space Quota
- Admins can purge a single service instance and its bindings.  This is a more targeted purge to resolve a single service instance than the purge service offering.

#### Apps Manager

This release adds support for the Diego Runtime, and features numerous fixes and enhancements for it. 

Two new environment variables are introduced and one is removed in v1.6: 

* The new `ENABLE_INTERNAL_USER_STORE` environment variable controls org and space user invitations, new user registrations, and password updates to the PCF internal user store. The default is set to `false`, which means that none of the features are exposed in Apps Manager. Set to `true` to expose these features. 
* The new `ENABLE_NON_ADMIN_ROLE_MANAGEMENT` environment variable allows org managers and spaces managers to manage user roles regardless of where these users are created. The default is set to `false`, which means that none of the features are exposed in Apps Manager. Set to `true` to expose these features. 
* The previous `ENABLE_NON_ADMIN_USER_MANAGEMENT` environment variable that controlled many of these same features is removed in v1.6.

#### DEAs

Multiple stability and performance improvements were made to DEAs. They can now handle many more simultaneous connections, for instance.

## UAA and Login Server
#### Feature name here...

#### Bug Fixes


## Logging, Analytics and Metrics

### New Features


### Bug Fixes

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
We fixed an issue with the v1.5.6 patch for Openstack deployments. The BOSH stemcell v3094, which this version of Elastic Runtime references, has a limiation affecting Openstack users only: * Elastic Runtime 1.5.6 on Openstack does not work with S3/Swift blobstores. * Elastic Runtime 1.5.6 on Openstack users must configure their object storage to use the internal blobstore option. * vSphere, AWS and vCloud users are not affected. * This is fixed in v1.6.0

