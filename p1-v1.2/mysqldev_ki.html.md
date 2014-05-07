---
title: Pivotal MySQL Dev v1.2.0.0 Known Issues
---
* During SSO flow, a user is required to approve the `openid` and `cloud_controller.read` scopes for the broker so that dashboard page can display the appropriate data. Subsequently revoking those approvals will not take immediate effect; there can be a delay of up to ten minutes.
* If Elastic Runtime is deployed with a self-signed SSL certificate, and MySQL is deployed with Trust Self-Signed Certificates: false, the MySQL deploy may succeed but SSO will not be functional. The acceptance test post-deploy hook will expose the problem.
