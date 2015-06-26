---
title: Pivotal Cloud Foundry Ops Manager v1.5.0.0 Release Notes
---

## Changes since v1.4.2.0:

### Major Features

* OpenStack support (beta)
* vSAN support
* Local disk support on vSphere
* vSphere 6.0 is now supported
* AWS multi-region support
* An AWS CloudFormation template is now provided that vastly simplifies AWS configuration

### Security Features

* Multiple CVE fixes per [pivotal.io/security](http://pivotal.io/security)

### Minor Features
* Ops Manager now informs the user when a stemcell needs to be downloaded
* Commonly used legacy stemcells are now available on Pivotal Network
* Import/export process has been improved to warn users that certain sequences of product upgrades may corrupt Ops Manager's state
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

