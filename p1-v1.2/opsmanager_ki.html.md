---
title: Ops Manager v1.2.0.0 Known Issues
---

* User must remember to check the 'accept self signed certs' for self signed cert (not an issue per se).
* Persistent storage sizes should not be reduced on any VM deployed by Ops Manager
* App domain changes made in Ops Manager must also be changed manually using the CF CLI tool
* Products should not be imported while an installation is occurring
* Products should not be deleted and while other products modified at the same time - apply the changes seperately
* A 1.1 product cannot be installed into the 1.2 Ops Manager. (Imported 1.1 instalations will function properly)
