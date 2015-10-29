---
title: Pivotal Cloud Foundry Ops Metrics v1.5.0 Known Issues
---

## New Issues

Some of these issues may be fixed in subsequent patch releases to 1.5. Consult the Ops Metrics 1.5 [Release Notes](opsmetrics_rn_1_5.html) for more information.

* Ops Metrics 1.5.0 may fail to install with a "500 error" if the Elastic Runtime tile is not present.  To avoid this issue, you must remove the Ops Metrics tile completely before deploying Elastic Runtime.
