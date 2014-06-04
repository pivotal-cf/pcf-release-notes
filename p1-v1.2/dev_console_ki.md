---
title: Pivotal Developer Console v1.2.0.0 Known Issues
---

##Issues

* On the Org Dashboard, adding a new space does not update the members tab, invite flow, or site navigation; please refresh the page to see and interact with the new space.
* On the Org Dashboard, user provided services are not shown in the services count.
* On the Org Dashboard, the quota graph is not dynamicly updated and does not account for multiple instances. 
* The App Dashboard is not dynamically-updated, so current status is not reflected without a page refresh.
* On the My Account page, leaving your last org will result in a 500 error.
* Developer Console in Pivotal CF v1.2 does not honor the value of `ssl.skip_cert_verify` set in Ops Manager, which means SSL certs are not verified in Developer Console by default. This will be fixed in Pivotal CF v1.3. 

##Workaround

In order to verify SSL certs in Developer Console:

  1. Use the cf CLI to login to your PCF as the admin user: `cf login -a API -u admin`
  1. Target the 'system' org and 'console' space: `cf target -o system -s console`
  1. Change the `VERIFY_SSL` environment variable on the 'console' app: `cf set-env console VERIFY_SSL true`
  1. Restart the 'console' app: `cf restart console`
