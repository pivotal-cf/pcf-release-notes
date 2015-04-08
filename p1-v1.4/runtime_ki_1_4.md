---
title: Pivotal Elastic Runtime v1.4 Known Issues
---

* When selecting between internal and external System Database and/or File Storage config, saved values for external systems, if they fail verification (e.g. a host is not reachable from Ops Manager), will persist if you select 'Internal Databases' or 'Internal File Store' subsequently. To resolve, return to your Ops Manager Installation Dashboard and click 'Revert', located in the upper right corner of the page.
* Placeholder for whatever we need to communicate re: switch from lucid to trusty for Operators upgrading to 1.4

* With PCF 1.4 we have added the ability to map LDAP groups to the Administrator role. This allows LDAP users belonging to that group to peform the administrator activities rather than using an internal admin account which is created by the installer. 
Two new fields LDAP Group Search Base and Group Search Filter have been introduced under the LDAP Configuration in Elastic Runtime Tile.
If LDAP is enabled for Pivotal Cloud Foundry, please follow the steps below after upgrade to set the LDAP Group Search Base and LDAP Group Search Filter. If these values are not set, LDAP authentication will not function. 
The LDAP group search base is the location in the LDAP directory tree from which the LDAP Group search begins. For example, a domain named “cloud.example.com” typically uses the following LDAP Group Search Base: ou=Groups,dc=example,dc=com. The LDAP Group Search filter is a string that defines LDAP Group search criteria. The standard value is member={0}.
