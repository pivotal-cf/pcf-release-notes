---
title: Pivotal Cloud Foundry Ops Metrics v1.5.0 Release Notes
---

## Version 1.5.0 (changes since v1.4.x)

### Major Features
* Ops Metrics now supports the firehose in addition to Bosh and the Collector for data.
* This requires the Elastic Runtime tile to be deployed before Ops Metrics (see known issues)

### Bug Fixes
* In the event of a data collision, Ops Metrics now keeps the last value that arrived by timestamp.

### Notes
Stemcell for 1.5.0 is 3100
