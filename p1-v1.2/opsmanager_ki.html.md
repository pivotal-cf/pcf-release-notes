---
title: Ops Manager v1.2.0.0 Known Issues
---

##Issues

* Persistent storage sizes should not be reduced on any VM that Ops Manager deployed.
* App domain changes made in Ops Manager must also be changed manually using the CF CLI tool
* Products should not be imported while an installation is occurring
* Products should not be deleted while other products are simultaneously being modified. Instead, apply the changes separately.
* You cannot install a 1.1 product in the 1.2 Ops Manager. (Imported 1.1 installations will function properly.)
* Deleting an installation can result in reconciliation issues if Ops Manager is paused during the delete. VMs must be manually deleted from vCenter.
* **vCloud Air/vCloud only**: When installing Ops Manager, the organization name you supply when entering vCloud Air/vCloud Director credentials cannot include uppercase letters. You must substitute lowercase letters for any uppercase letters present in the vCD organization name.

##Tips

* You must check the 'Accept Self-Signed Certs' checkbox if you want to use a self-signed cert.
