---
title: MySQL for Pivotal CF v1.2.0.0 Known Issues
---

During SSO flow, a user is required to approve the `openid` and `cloud_controller.read` scopes for the broker so that dashboard page can display the appropriate data. Subsequently revoking those approvals will not take immediate effect; there can be a delay of up to ten minutes.
