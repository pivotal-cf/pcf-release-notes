---
title: Pivotal Elastic Runtime v1.5 Known Issues
---

* If your Apps Manager and Apps Usage Service applications are running on the unsupported lucid64 stack, you should keep certain errands, Push Apps Manager and Push App Usage Service, on Pivotal Elastic Runtime turned on for the v1.5 upgrade, so that they migrate the appropriate system applications over to the new cflinuxfs2 stack. These applications may be unreachable for a brief period of time during the upgrade of Pivotal Elastic Runtime to v1.5.  More details about migrating to the new stack can be found at: https://support.pivotal.io/hc/en-us/articles/205751277-New-cflinuxfs2-Stack

* The HAProxy and Router Cipher fields in the Security Config of Elastic Runtime should not be completely erased once you have already supplied your own cipher sets and saved that configuration. The ciphers will not return to their default values when deleted, and will instead be interpretted as an empty cipher set.

* If you had LDAP Admin groups configured in the LDAP Configuration of Elastic Runtime from v1.4, then upon upgrade to v1.5 you will need to go back into the LDAP Config section to re-add those groups. These fields in v1.5 are now nested under a radio button selector which defaults to "No Groups" in v1.5. You can switch your selection to "Enable Admin Groups" and fill in the corresponding fields with the same values you used in configuring v1.4.

* If upgrading PCF Elastic Runtime from v1.4 to v1.5, you may want to move the new static buildpack that was introduced in v1.5 to be the first buildpack in your system's list of buildpacks, so that applications with a file named Staticfile will be detected by the static buildpack and not by the Ruby or Node buildpacks. New installations of PCF Elastic Runtime v1.5 will have this static buildpack positioned at the front of the list automatically.

#### Pivotal Elastic Runtime v1.4 Known Issues Which Still Apply in v1.5

* When selecting between internal and external System Database and/or File Storage config, if saved values for external systems fail verification (e.g. a host is not reachable from Ops Manager), the values will persist if you then select 'Internal Databases' or 'Internal File Store'. To resolve this issue, return to your Ops Manager Installation Dashboard and click **Revert**, located in the upper right corner of the page.

