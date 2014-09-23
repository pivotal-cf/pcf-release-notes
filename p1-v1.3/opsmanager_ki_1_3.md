---
title: Ops Manager 1.3 Known Issues
---


* Changes to products cannot be combined with deletions. Make a change, click Apply, and wait for the change to be installed. Do a deletion separately.
* Resource Pools cannot be deleted from Availability Zones. If a resource pool is inadvertently deleted, run `BOSH recreate`.
* Exporting an installation can result in a 500 error if the Ops Manager VM is less than 2GB in RAM.
* The progress bar can stall during an installation, which requires the user to refresh the page.
* The subnet form on the Network page can take invalid formats. The correct format is CIDR notation.
