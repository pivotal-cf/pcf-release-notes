---
title: Pivotal Cloud Foundry&reg; Ops Metrics v1.5.X Known Issues
---

## New Issues

Some of these issues may be fixed in subsequent patch releases to 1.5. Consult the Ops Metrics 1.5 [Release Notes](opsmetrics_rn_1_5.html) - any additional fixes will be added immediately.

* On a new [Pivotal Cloud Foundry&reg;](https://network.pivotal.io/products/pivotal-cf) (PCF) Ops Manager install, you must install an Elastic Runtime tile before installing Ops Metrics 1.5.X . Ops Metrics 1.5.X may fail with a "500 error" if the Elastic Runtime tile is not present. Ops Manager will continue to produce errors for subsequent deployments of Ops Metrics, even if you add the Elastic Runtime tile after.
* To resolve this issue:
  * Uninstall the Ops Metrics tile 1.5.X tile.
  * Install the Elastic Runtime 1.6.X tile, if you have not done so already.  (There is no need to remove an already present Elastic Runtime tile for this fix to work.)
  * Verify your Elastic Runtime 1.6.X tile is running.
  * Finally re-install Ops Metrics 1.5.X .

* If you would like to deploy Ops Metrics solely for Bosh data, please install a 1.4 version of Ops Metrics. Do not upgrade to Ops Metrics 1.5 unless you have an Elastic Runtime tile installed.

