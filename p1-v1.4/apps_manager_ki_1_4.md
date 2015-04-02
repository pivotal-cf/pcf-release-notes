---
title: Pivotal Cloud Foundry Apps Manager v1.4.0.0 Known Issues
---

## New issues

* Users with the cloud_controller.admin scope will not see events on the App Dashboard unless they also have the Space Developer role. 

## Existing issues

* When running PCF with self-signed certs, streaming logs requires an extra step to accept the cert from Loggregator. 
* On the Org Dashboard, user provided services are not shown in the services count.
* On the My Account page, leaving your last org will result in a 500 error.
* This space page is not dynamically updated, so current status is not reflected without a page refresh.