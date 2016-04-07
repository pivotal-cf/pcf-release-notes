---
title: Pivotal Cloud Foundry&reg; Metrics v1.0.2 Release Notes
owner: Metrix
---

## Version 1.0.2-beta

### Known issues
For Known Issues, please see [PCF Metrics Known Issues](../p1-v1.7/pcfmetrics_ki_1_7.html).

### Notes
* This beta requires Elastic Runtime v1.6.16 or greater. 
* The route for the PCF Metrics application is registered as `metrics.<system-domain>` in this v1.0.2 release.   The application can be accessed at `https://metrics.<system-domain>`
* The install will create a small deployment suitable for hundreds of apps. This is not configured for thousands of apps.
