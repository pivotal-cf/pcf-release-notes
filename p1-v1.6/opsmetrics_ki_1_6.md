---
title: Pivotal Cloud Foundry&reg; Ops Metrics v1.6.X and v1.5.X Known Issues
owner: PCF Metrics
---
## New Issues for 1.6.X
Some of these issues may be fixed in subsequent patch releases to 1.6. Consult the Ops Metrics 1.6 [Release Notes](opsmetrics_rn_1_6.html) - any additional fixes will be added immediately.

For all 1.6.X releases:
* To fix the possibility of installation deadlock with Elastic Runtime 1.6.X, the OpenTSDB Firehose Nozzle job (responsible for receiving Diego metric data) has been disabled by default.
* There is nothing that prevents the user from turning on the Nozzle deployment when Elastic Runtime is not present.
  * Enabling the nozzle when Elastic Runtime is not deployed or enabled will produce the following error:
  * "RuntimeError - unknown product 'cf' in (( ..cf.cloud_controller.system_domain.value ))"
  * To fix this, reduce the number of nozzle counts to zero until Elastic Runtime is enabled.
* Because deploying the OpenTSDB firehose nozzle is now optional, smoke tests for Elastic Runtime have been disabled until a later release.

For the 1.6.0 release:
* Leaving the port blank in Elastic Runtime would cause the OpenTSDB firehose nozzle to try to listen to port 0.   To fix, enter port 443 in Elastic Runtime or use Ops Metrics 1.6.1 .

## New Issues for 1.5.X

Note: The 1.5.X line has been completely deprecated in favor of 1.6.X.  Please use 1.6.X if at all possible.

Some of these issues may be fixed in subsequent patch releases to 1.5. Consult the Ops Metrics 1.5 [Release Notes](opsmetrics_rn_1_6.html) - any additional fixes will be added immediately.

* On a new [Pivotal Cloud Foundry&reg;](https://network.pivotal.io/products/pivotal-cf) (PCF) Ops Manager install, you must install an Elastic Runtime tile before installing Ops Metrics 1.5.X . Ops Metrics 1.5.X may fail with a "500 error" if the Elastic Runtime tile is not present. Ops Manager will continue to produce errors for subsequent deployments of Ops Metrics, even if you add the Elastic Runtime tile after.
* To resolve this issue:
  * Uninstall the Ops Metrics tile 1.5.X tile.
  * Install the Elastic Runtime 1.6.X tile, if you have not done so already.  (There is no need to remove an already present Elastic Runtime tile for this fix to work.)
  * Verify your Elastic Runtime 1.6.X tile is running.
  * Finally re-install Ops Metrics 1.5.X .

* If you would like to deploy Ops Metrics solely for Bosh data, please install a 1.4 version of Ops Metrics. Do not upgrade to Ops Metrics 1.5 unless you have an Elastic Runtime tile installed.
