## Changes since v1.5.0.0:

## Elastic Runtime

##### CF Release Version: 222

### New Features

#### Default Stack: cflinuxfs2

New deployments will no longer have the lucid64 stack available.

Operators are encouraged to migrate all apps to cflinuxfs2 as mentioned in the v1.4 release notes.

A future release will completely remove the lucid64 stack from Pivotal Cloud Foundry. After upgrading to this subsequent release, apps that have not been migrated to cflinuxfs2 will fail to start.

Further details can be found [here](https://support.pivotal.io/hc/en-us/articles/205751277-New-cflinuxfs2-Stack).

#### Diego-beta Tile and Windows 2012 stack

You can use Diego to run your apps in Pivotal Cloud Foundry v.1.5. However, you will need to download and install and additional tile. [Details](../../opsguide/diego-overview.html)

#### Security Configuration of Runtime

This new section allows you to configure security settings for your Pivotal Cloud Foundry Elastic Runtime components, such as HAProxy, Router, and the DEAs.

The SSL Termination Certificate input (for HAProxy) and the "Trust Self-Signed Certificates" checkbox have been moved to this section.

By checking the "Enable cross-container traffic within each DEA" checkbox, you can disable a restriction on the DEA that disallows containers on a particular DEA from communicating with each other.  It is not recommended to check this checkbox for multi-tenant environments.

This section also includes fields which allow configuring the HAProxy SSL certificate and HAProxy cipher string, the latter of which is an optional field. The SSL certificate is not optional, even if you use an external load-balancer instead of HAProxy, since it could potentially be referenced by other Pivotal Cloud Foundry services that you may choose to install.

#### Other Runtime Features

##### S3-Compatible Filestore Configuration

It is now possible to configure four different S3 buckets to comprise the Cloud Controller's filesystem.

##### Experimental Features

There are no experimental features being introduced in PCF Elastic Runtime for v1.6.

#### Improved MySQL Service
MySQL, used by some of the Pivotal Cloud Foundry system applications in the past, is now usable for every Pivotal Cloud Foundry system component and application, including Cloud Controller and UAA.

#### API/cf CLI

Add points about CLI, e.g for Diego, here...

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
