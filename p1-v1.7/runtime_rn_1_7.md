---
title: Pivotal Elastic Runtime&reg; v1.6.0.0 Release Notes
owner: Release Engineering
---
# 1.7.x Patches
None as of 2016-03-31.

# Version 1.7.0 New Features

## Elastic Runtime

Versions 1.7.0 and higher versions of Elastic Runtime consist of these Cloud Foundry versions:

- CF Release version: 232
- Diego version: 0.1460.0
- Garden version: 0.334
- CF MySQL version: 25
- etcd version: 38
 
### Diego replaces DEAs completely
(we may have a comprehensive doc on docs.pivotal.io for this, so these details may not be necessary here)
- migrate-before-you-upgrade reference to docs
- scaling (for HA)
- architecture diagram if we have it (link)
- 

### Postgres-to-MySQL migration

(we may have a comprehensive doc on docs.pivotal.io for this, so these details may not be necessary here)
- must start with 1.6.4 ERT before you upgrade
- migration will only occur if you had Postgres data to begin with (i.e. you originally started with ERT <1.6.0)
- do not delete postgres DBs before upgrading!
- reference backup and restore doc updates
- contact Support if any issues arise
- 

### Elastic Runtime Tile UI Changes

The tile has been re-designed in layout to improve the configuration workflow for operators. Several configuration fields have been moved to different sections of the tile. Also, more advanced logic has been implemented for some sections to make configuring complicated networking use cases easier for operators.

### Compiled Releases

Installs and upgrades of Elastic Runtime are now much faster than before, as the installation now makes use of compiled binaries instead of source code.

### Automated Backups

http://docs-pcf-pre-release.cfapps.io/pivotalcf/customizing/config-er-vmware.html#internal-mysql

### Trusted Self-Signed SSL Certificates
(this is probably better explained in the Ops Mgr release notes, this is the doc we're working on: https://docs.google.com/document/d/1PJD8GOHRp_jO_j3PQd7NZsoXLlOqnj0t7-l0N2lIuTE/edit)

### Docker Private Registries

(reference docs.pivotal.io for this, http://docs-pcf-pre-release.cfapps.io/pivotalcf/opsguide/docker-registry.html)

### Route Services

(http://docs-pcf-pre-release.cfapps.io/pivotalcf/services/route-services.html)

### Experimental Feature: Disk & Memory Overcommit Settings

http://docs-pcf-pre-release.cfapps.io/pivotalcf/customizing/cloudform-er-config.html#experimental-features

### AWS Cloudformation Script Update

You can now specify whether you would like to enable HTTP traffic to port 80 of your ELB if you are setting up an environment in AWS to deploy PCF.

New Feature Details

### App Manager White Labeling
(multiple places in docs, such as http://docs-pcf-pre-release.cfapps.io/pivotalcf/customizing/config-er-vmware.html#customize-apps-man)

New feature details

### App Manager React

Space page only? Ask Mike Gresham if anything needs to be said about this

##  Identity (aka UAA Server)


### Coarse and Fine-Grained Authorization for Apps and APIs

check with Kevin Huang if he needs SSO release notes

New feature details

### UAA PW Policy Config in ERT

http://docs-pcf-pre-release.cfapps.io/pivotalcf/opsguide/pw-policy.html

### UAA SAML features
http://docs-pcf-pre-release.cfapps.io/pivotalcf/customizing/pcf-aws-manual-er-config.html#er-auth-config

### UAA Token Lifetime Settings
http://docs-pcf-pre-release.cfapps.io/pivotalcf/customizing/pcf-aws-manual-er-config.html#er-auth-config
 
## Logging and Metrics

ask Jim CF Campbell for details on what changed between CF-225 and CF-232


## Buildpacks

ask Danny Rosen for details on what changed between CF-225 and CF-232

New feature details

# Notes
