---
title: Pivotal Cloud Foundry Ops Manager v1.5.0.0 Release Notes
---

## v1.5.4.0 patch release:
Ops Manager 1.5.4.0 is an invitation-only release for vCloud Air and vCloud Director customers.  It fixes a bug to allow use of the 6.0 and higher vCA API.  If you are a vCA/vCD customer and would like access to this release, please contact Pivotal Support.  (Embedded stemcell 3056, Ops Manager build ea7ddc)

## v1.5.3.0 patch release:
Ops Manager 1.5.3.0 adds two configuration options on OpenStack:  "Disable DHCP" checkbox (which controls BOSH's "use_dhcp" flag) and an advanced section called "Advanced Infrastructure Config" that allows operators to set an Openstack connection_options string, which acccepts JSON.  Release notes starting with 1.5.2.0 will now include the version number of the embedded stemcell.  Text area fields have been widened in the Ops Manager user interface.  (Embedded stemcell 3026, Ops Manager build f7555)

## v1.5.2.0 patch release:

Ops Manager 1.5.2.0 fixes a bug on OpenStack in which availability zones specified in Director tile were not passed to BOSH, as well as a bug in which certain fields became disabled after a failed deploy.  It also includes a new BOSH stemcell with important security updates to Ubuntu.  (Embedded stemcell:  3026)

## v1.5.1.0 patch release:

This release was made available prematurely and then quickly withdrawn.  To avoid confusion, the next release after 1.5.0.0 will be called 1.5.2.0.  We apologize for the confusion.

## Version 1.5.0.0 (changes since v1.4.2.0)

### Major Features

* OpenStack support (beta)
* vSAN support
* VMs use disks local to a cluster [*]
* vSphere 6.0 is now supported
* AWS multi-region support
* An AWS CloudFormation template is now provided that vastly simplifies AWS configuration

[*] This means that operators can now ensure that each set of VMs are created using the right combination of clusters and datastores when deploying to more than one availability zone on vSphere.

### Security Features

* Multiple CVE fixes per [pivotal.io/security](http://pivotal.io/security)

### Minor Features
* Ops Manager now informs the user when a stemcell needs to be downloaded
* Commonly used legacy stemcells are now available on Pivotal Network
* Import/export process has been improved to warn users that certain sequences of product upgrades may corrupt the Ops Manager state
* Ops Manager now deletes uploaded bosh assets (stemcells/releases) from the IaaS when deleting an installation
* For proof-of-concept deployments, it is now possible to have BOSH deploy all VMs with the same password instead of choosing random passwords
* Installation log now includes time stamps before every BOSH command

### Bug Fixes

* Ops Manager Director's persistent disk now defaults to 40 GB (up from 20 GB)
* An issue was resolved involving LDAP configuration changes not being saved
* Product exports should not timeout anymore
* An issue was resolved involving some installation log messages being hidden
* Import of older product tiles that contain precompiled packages now works correctly
* A bug that caused "File not found" errors during export has been fixed
* Out of memory errors should no longer occur during export
* A bug was fixed involving VM Resurrector being impossible to disable
* Timeouts have been added on AWS to reduce problems associated with API throttling by Amazon
* Ops Manager Director's logs download link has been eliminated since this is not supported

### Product Author Features
* The RSA key generator property type now generates the public key in OpenSSH format rather than PEM

