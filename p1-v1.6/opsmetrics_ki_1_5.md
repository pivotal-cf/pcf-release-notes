---
title: Pivotal Cloud Foundry Ops Metrics v1.5.0 Known Issues
---

## New Issues

Some of these issues may be fixed in subsequent patch releases to 1.5. Consult the Ops Metrics 1.5 [Release Notes](opsmetrics_rn_1_5.html) for more information.

* On a new PCF Ops Manager install, you must install an Elastic Runtime tile before installing Ops Metrics 1.5.0   Ops Metrics 1.5.0 may fail with a "500 error" if the Elastic Runtime tile is not present, and Ops Manager will continue to produce errors for subsequent deployments of Ops Metrics.  To resolve this issue, uninstall the Ops Metrics tile, then install Elastic Runtime, and finally re-install Ops Metrics 1.5.0

* If you would like to deploy Ops Metrics solely for Bosh data, please install a 1.4 version of Ops Metrics.  Do not upgrade to Ops Metrics 1.5 unless you have an Elastic Runtime tile installed.

