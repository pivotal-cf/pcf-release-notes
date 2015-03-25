---
title: Pivotal HD for PCF v1.2.0.0 Release Notes
---

## Changes since v1.0.0.0:
* On Demand Clusters
  * Each service creation request now results in the deployment of a new Pivotal HD 1.1 cluster on demand from the cloud foundry cli or developer console
  * Previously a single multi-tenant Pivotal HD cluster was deployed for use within Pivotal Cloud Foundry

* Administrator Defined Service Plans
  * The PCF Administrator can now configure the metadata and Pivotal HD components they wish to offer as a PCF service plan.
  * Previously the service plan was hard coded
  * Administrators can now define the vSphere network the service will deploy Pivotal HD clusters to, independent of the network used in the deployment of PCF. If different, these networks must be able to route traffic to one another.
  *vSphere resources continue to be configurable per component

* GemFire XD Beta
  * This release enables the beta testing of GemFire XD 1.0 as a PCF Service
  * Hive, HBase, and the Pivotal HD Client VM have been removed as components of a PHD deployment

* Binding to a service instance now provisions and returns user credentials and API endpoints for all components of the PHD cluster that was created.
