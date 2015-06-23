---
title: Pivotal Cloud Foundry Apps Manager v1.5.0.0 Known Issues
---

## New issues

### App Usage Service

* In the new Accounting Report, average app instance counts will be shown for all months in which data exists in the Usage Service, including the months prior to v1.5 being deployed. Maximum app instance counts will be shown only for those months in which v1.5 is running. 
* The App Usage Service worker app is not multi-threaded and should not be scaled beyond one instance. 
* Deployments with self-signed or invalid certs should have 'Trust Self-Signed Certificates' setting checked when configuring 'IPs and Ports' for Elastic Runtime in Ops Manager. If not, users will likely see redirect loops on login. 

### Miscellaneous

* The version of Apps Manager v1.5 in the page footer erroneously shows v1.4. 
* Invitations created before the change from the 'console' subdomain to the 'apps' will fail silently. 

## Existing issues

* Users with the cloud_controller.admin scope do not see events on the App Dashboard unless they also have the Space Developer role.
* When running PCF with self-signed certs, streaming logs requires an extra step to accept the cert from Loggregator.
* On the Org Dashboard, user-provided services do not display in the services count.
* On the My Account page, leaving your last org results in a 500 error.
* The space page is not dynamically updated, so you must refresh to see the current status.