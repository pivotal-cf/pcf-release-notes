---
title: Pivotal Ops Manager v1.1.0.0 Release Notes
owner: Ops Manager
---

### Operations Manager v1.1.0.0 includes new features, bug fixes and security updates.

## Changes since v1.0.0.1:

- Pivotal Ops Manager is now a separate product from Elastic Runtime and MySQL Dev.
- Elastic Runtime, MySQL Dev, and other Pivotal products must be imported into Ops Manager.
- Imported products have greater flexibility to present forms and properties.
- Changed to Ruby version 1.9.3-p484.
- Created migrations for upgrading from 1.0.0.1 to 1.1.0.0 of Ops Manager.
- Created migrations for upgrading from 1.0.0.1 to 1.1.0.0 of products installed by Ops Manager.
- Updated the MicroBOSH stemcell.
- Infrastructure support abstraction in preparation for vCloud Air support.
- User can enter paths to vSphere networks.
- Products now specify which infrastructure verifications to run.
- Snapshots of installation settings are automatically saved.
- Snapshots of installation settings are restorable.
- Parallel deploys are supported.
- Compiled packages are supported.
- New user interface at macro and micro levels.
- Debug pages are secure.
- Renamed many objects and fields to be more consistent and logical.
- Flash messages with no actions are dismissible.
- Fully documented API for product teams to automate every action available in web UI.
- Deploy log scrolls to top.
- Virtual Machine health metrics appear on the Status page.
- Product teams can use max-in-flight settings for BOSH as an integer or ratio.
