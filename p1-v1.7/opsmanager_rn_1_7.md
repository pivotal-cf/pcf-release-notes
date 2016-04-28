---
title: Pivotal Cloud Foundry&reg; Ops Manager v1.7 Release Notes
owner: Ops Manager
---

# v1.7.x Patches
None as of 2016-03-31.

# Version 1.7.0 New Features

Upgrading Pivotal Cloud Foundry is documented [here](http://docs-pcf-pre-release.cfapps.io/pivotalcf/customizing/upgrading-pcf.html#pcf16upgrade).

## Major Features

### Security
* Admin user is migrated into CF UAA using password as passphrase
* Support for multiple user accounts using local identity management
* Support for multiple user accounts using remote SAML service
* All Ops Manager pages are protected using CF UAA
* Support for custom certificates provisioned by BOSH
* Both BOSH and Ops Manager use same identity management system
* Automatic cleanup of /tmp directory for 24 hour old files
* Users can only upgrade stemcells
* Import installation occurs before login
* When a second user attempts to login - ask to logout initial 
* Stemcells can be updated using floating third digit (patch release)
* Security groups are now referenced by id
* Operators can only import light HVM stemcells

### Networks and Availability
* Networks are now a logical collection of subnets
* Users can add one or many subnets to a network
* Users can create more than one network
* Users can add more than one availability zone
* Users can assign products to networks and availability zone
* Jobs in a deployment will be balanced across subnets and availability zones


* Instance types operate the same way across IaaS
* Rescue mode exists in case CF UAA fails or is misconfigured
* Credentials page nolonger shows secrets as HTML

* Operator can see change log by user
* Operators can select and deselect errands before applying changes
* BOSH is deployed using new init implementation
* Existing BOSH installations will be upgraded to new init method
* Ops Manager director is limited to one network to avoid assymetric routing
* Support for compiled releases
* Users can disable ICMP checks (default off on AWS)
* Checkbox exists to run "bosh deploy --recreate" (recreates all VMs)
* Support for monitoring and pager duty BOSH plugins
* UAAC gem added to Ops Manager VM

### API Endpoints

* All API endpoints protected by CF UAA
* List installed products
* List vm credentials by product
* Unlock Ops Manager with passphrase
* CRUD disk types and vm types
* List static ips
* Private keys are optional for SSL certs
* Manifests before and after deployments
* Token expiration time can be configured
* Diagnostic information to attach to support tickets
* Get a bosh manifest for bosh-init deployment

### AWS 
For AWS installations, EBS is not supported on all instances. For more information on EBS encryption, please see [Configuring Amazon EBS Encryption](http://docs.pivotal.io/pivotalcf/customizing/cloudform-om-ebs-config.html) Amazon Machine Images (AMIs) are now built in Frankfurt and Seoul. Additionally, AWS S3 version 4 is now supported.

Several changes have been made for CloudFormation on AWS. The script now considers RDS (Relational Database Service) as optional and supports an HA NAT instance and multiple AZs. For more information, please see the
[Deploying the CloudFormation Template for PCF on AWS](http://docs-pcf-pre-release.cfapps.io/pivotalcf/customizing/cloudform-template.html) document.




### vSphere 

* Datastores can be split by Ephemeral and Persistent disk types
* Subnets can span availability zones (possible prior - distinct from other IaaS)
* vCenter IP field now supports IP or host

### OpenStack

* Support for connection options
* Support for Keystone version 3

### Tile Authors

* PCF product tiles are upgraded using ECMA (JavaScript) migration syntax
* Imports into 1.7 are limited to ECMA script migrations only
* Invalid user input can be rejected using regular expressions
* Form fields support placeholder text
* A job's instance count can be toggled to 0 based on a selector value
* Markdown can be used above a form
* Product template must include minimum_version_for_upgrade
* Products with pre 1.7 metadata are limited to single subnet
* Products either get persistent disk or not. Can't be optional
* First-network-deprecated has been removed as an key / value pair
* Tile authors can limit a product's jobs to a single AZ
* Accessor available for trusted certificates

### Bug Fixes

* Some products could not be uploaded via API
* Wrong tile version shown in error messages
* Passwords aggressively scrubbed from logs resulting in non-secret obfuscation
* Job logs cleaned up by file cleaner
* Hints in selectors fixed
* Users had to specify resource pools on vSphere
* Installations were slower by writing logs to database
* When DNS is unreachable 500 error
* Importing installation errors with resource pools result in 500 error
* Partial selection of errands results in all errands checked
* Powering off VM can result in empty installation.yml under certain conditions
* Many API docs errata fixes
* Broken EULA links
* Selector checkboxes were not persisting
* Exports with empty releases causes 500 error

## Operational Improvements
In addition to the major features, there are a number of smaller improvements that will enhance the Operator's experience with installing and maintaining Pivotal Cloud Foundry.


