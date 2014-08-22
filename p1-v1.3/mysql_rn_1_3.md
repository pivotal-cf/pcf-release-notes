---
title: MySQL for Pivotal CF v1.3 Release Notes
---

- Syslogs are now forwarded to the same location configured in Elastic Runtime.
- Admin now manages instance capacity using only persistent disk allocated to mysql nodes; available instance capacity is determined dynamically based on a safe estimate of headroom for system requirements and reserved resources for provisioned instances.
- Default stemcell is now Trusty go_agent 2682.
- Dashboard uses more limited permissions to determine whether a user currently has access to a service instance; the cloud_controller_service_permissions.read OAuth scope instead of cloud_controller.read.
- Timestamps have been added to logs for Monit start processes.
