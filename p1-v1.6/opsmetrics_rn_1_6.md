---
title: Pivotal Cloud Foundry&reg; Ops Metrics v1.6.X and v1.5.X Release Notes
owner: Metrix
---
## v1.6.9 patch release:
* Changed the JMX metrics tree structure.

Instead of `opentsdb-firehose-nozzle` as the folder name in the tree, it will be called `maximus`. The names of the opentsdb-firehose-nozzle metrics will remain unchanged.

```
deployment:	{p-metrics}
  job:	{opentsdb-firehose-nozzle -> maximus}
    ip: {127.0.0.1}
      instance: {0}
	     metric: {opentsdb.nozzle.totalMetricsSent}
```

## Version 1.6.X (changes since v1.5.x)

### Known issues
For Known Issues, please see the [Ops Metrics Known Issues](./opsmetrics_ki_1_6.html) documentation.  For Ops Metrics 1.6.X there is one important install ordering dependency before enabling the OpenTSDB firehose nozzle job.

### Major Features
* The addition of CF loggregator data via the firehose is still available, but disabled by default.
  *  This allows the user to install Ops Metrics without Elastic Runtime to monitor Bosh data.
  *  The nozzle should not be enabled until after the user successfully deploys Elastic Runtime (see known issues)
* Ops Metrics still supports the firehose in addition to Bosh and the Collector for data.
* Ops Metrics now asks Elastic Runtime for the port that firehose data comes from.

### Bug Fixes
* Firehose data ingest disabled by default to avoid deadlock condition if Ops Metrics installed before Elastic Runtime.
* Firehose no longer defaults to using 4443 to read data, and instead asks Elastic Runtime for the port the firehose comes from.

### Notes
* Upgrading from Ops Metrics 1.4.X to 1.6.X will leave the firehose nozzle job disabled (since it did not exist previously).
* Upgrading from Ops Metrics 1.5.X to 1.6.X will enable the firehose nozzle by default (since it was enabled before upgrading).
  * If you are upgrading to resolve an installation error with 1.5.X, immediately disable the firehose job before deploying, and enable once you have deployed Elastic Runtime.
* Stemcell for 1.6.0 is 3144

## Version 1.5.X (changes since v1.4.x)

### Known issues
For Known Issues, please see the [Ops Metrics Known Issues](./opsmetrics_ki_1_6.html) documentation.  For Ops Metrics 1.5.X (compatible with Ops Manager and Elastic Runtime 1.6.X ) there is one important install ordering dependency.

### Major Features
* Ops Metrics now supports the firehose in addition to Bosh and the Collector for data.
* This requires the Elastic Runtime tile to be deployed before Ops Metrics (see known issues)

### Bug Fixes
* In the event of a data collision, Ops Metrics now keeps the last value that arrived by timestamp.

### Notes
* Stemcell for 1.5.2 is 3130
* Stemcell for 1.5.1 is 3112
* Stemcell for 1.5.0 is 3100
