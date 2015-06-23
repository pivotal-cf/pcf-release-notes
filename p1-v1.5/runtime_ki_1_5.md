---
title: Pivotal Elastic Runtime v1.5 Known Issues
---

* Pivotal Apps Mananger may be unreachable for a brief period of time during the upgrade of Pivotal Elastic Runtime to v1.5. This is due to a migration of all Apps Manager instances that were running on the unsupported Lucid64 stack over to  Ubuntu Trusty Tahr 14.04.

* The HAProxy and Router Cipher fields in the Security Config of Elastic Runtime should not be completely erased once you have already supplied your own cipher sets and saved that configuration. The ciphers will not return to their default values when deleted, and will instead be interpretted as an empty cipher set.

* If you had LDAP Admin groups configured in the LDAP Configuration of Elastic Runtime from v1.4, then upon upgrade to v1.5 you will need to go back into the LDAP Config section to re-add those groups. These fields in v1.5 are now nested under a radio button selector which defaults to "No Groups" in v1.5. You can witch your selection to "Enable Admin Groups" and fill in the corresponding fields with the same values you used in configuring v1.4.

* If upgrading PCF Elastic Runtime from v1.4 to v1.5, you may want to move the new static buildpack that was introduced in v1.5 to be the first buildpack in your system's list of buildpacks, so that any application with a static file will detect the presence of the static buildpack first. New installations of PCF Elastic Runtime v1.5 will have this static buildpack positioned at the front of the list automatically.

#### Pivotal Elastic Runtime v1.4 Known Issues Which Still Apply in v1.5

* When selecting between internal and external System Database and/or File Storage config, if saved values for external systems fail verification (e.g. a host is not reachable from Ops Manager), the values will persist if you then select 'Internal Databases' or 'Internal File Store'. To resolve this issue, return to your Ops Manager Installation Dashboard and click **Revert**, located in the upper right corner of the page.

* With PCF 1.4, we have added the ability to map LDAP groups to the Administrator role. This allows LDAP users belonging to that group to perform the administrator activities rather than using an internal admin account which is created by the installer.

We have introduced two new fields under the LDAP Configuration in Elastic Runtime Tile: LDAP Group Search Base and Group Search Filter.
If LDAP is enabled for Pivotal Cloud Foundry, please follow the steps below after upgrade to set the LDAP Group Search Base and LDAP Group Search Filter. If these values are not set, LDAP authentication will not function.

The LDAP group search base is the location in the LDAP directory tree from which the LDAP Group search begins. For example, a domain named “cloud.example.com” typically uses the following LDAP Group Search Base: `ou=Groups,dc=example,dc=com`. The LDAP Group Search filter is a string that defines LDAP Group search criteria. The standard value is `member={0}`.
