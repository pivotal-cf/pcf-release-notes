---
title: Pivotal Elastic Runtime v1.5.0.0 Release Notes
---

## Changes since v1.4.0.0:

## Elastic Runtime

### New Features

#### Default Stack: Trusty 14.04

The lucid64 stack that has been part of Pivotal Cloud Foundry Elastic Runtime for several years as the root file system for containers will reach end of support for security fixes on April 29th, 2015 by Canonical. Developers or Operators will need to take action to ensure existing applications migrate to using the new stack.

Lucid64 is no longer an option as the default stack for Elastic Runtime. The default will be cflinuxfs2 derived from Ubuntu Trusty 14.04.

##### What do you need to do?

If you have an application or app as a service running on Pivotal Cloud Foundry, ensure that your application works when run with the new stack and the corresponding new buildpacks. We recommend using a blue/green deployment strategy to ensure there is no down time for the app. Simply running the following command will result in a small amount of down time as old instances are stopped and the app is restaged with the new stack.

	cf push app-name -s cflinuxfs2

If you have custom buildpacks, you need to ensure that your buildpacks work when run with the new stack.

##### List of buildpacks that now support cflinuxfs2:

* Java buildpack
* NodeJS buildpack
* PHP buildpack
* Go buildpack
* Python buildpack
* Ruby buildpack

<b>Known issue: For apps that use native compiled binaries, when the stack is changed, the app may fail to start. If this occurs, the current work around is to delete the app and then push the app again.</b>

#### Improved MySQL Service
MySQL, used by Notifications, Autoscaling, and Apps Manager, ... explain switchboard + improved failure recovery

#### API/cf CLI
* 

#### Improved stability
* 

#### Services API
* 

#### Misc
* 

### Bug Fixes
* Fixed 

## UAA and Login Server
### New Features
* 

## Logging, Analytics and Metrics
### New Features

* 

### Component Features And Bug Fixes
* Numerous general system fixes.

### Bug Fixes

* Bug fixed 

## Buildpacks

### New Features

* 

## Security - CVE fixes have been implemented since v1.3.0.0 and released via security patches.

* 

