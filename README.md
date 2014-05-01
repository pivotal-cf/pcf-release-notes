pcf-release
===========

A repo for release notes

# Developer Console

## Release notes

* The new Org Dashboard in v1.2 provides a count of all apps and services in each space. Additonal API calls are made to get the status -- green is running, red is crashing or crashed, and gray is stopped -- of each app, and this status is kept up-to-date every 30 seconds. On recent browsers, updating is blocked when Developer Console is not the active tab. 

## Known issues

* On the Org Dashboard, adding a new space does not update the members tab, invite flow, or site navigation; please refresh the page to see and interact with the new space. 
* On the Org Dashboard, user provided services are not shown in the services count. 
* The App Dashboard is not dynamically-updated, so current status is not refleted without a page refresh. 
* On the My Account page, leaving your last org will result in a 500 error. 
