---
title: Pivotal Cloud Foundry Apps Manager v1.4.0.0 Known Issues
---

## New issues

* Users with the cloud_controller.admin scope do not see events on the App Dashboard unless they also have the Space Developer role.

## Existing issues

* When running PCF with self-signed certs, streaming logs requires an extra step to accept the cert from Loggregator.
* On the Org Dashboard, user-provided services do not display in the services count.
* On the My Account page, leaving your last org results in a 500 error.
* The space page is not dynamically updated, so you must refresh to see the current status.