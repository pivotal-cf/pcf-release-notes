---
title: Pivotal CF Developer Console v1.3.0.0 Release Notes
---

## Changes since v1.2.0.0:

### App dashboard
* Data on the app dashboard is refreshed every 20 seconds. When an update to the app (such as a start, stop, restart, or scale event) has been initiated on the app dashboard, data is refreshed every five seconds until the request is completed. 

### Usage service
* All identical app configurations (where the number of instances and amount of memory are the same) are rolled up into one duration of time.
* The default view is of the current calendar month, with the two previous months available as options.
* Although it cannot be displayed, data on the usage report will be saved beyond the three month window. 

### Org creation
* When the 'user_org_creation' feature flag is disabled in Elastic Runtime, users will not be able to create new orgs in Developer Console. 

### Space dashboard
* This page is not dynamically updated, so current status is not reflected without a page refresh.