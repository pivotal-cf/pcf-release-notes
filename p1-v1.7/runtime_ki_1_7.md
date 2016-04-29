---
title: Pivotal Elastic Runtime&reg; v1.7 Known Issues
owner: Release Engineering
---

## New Issues

* The Single Sign-On service tile operates in lockstep with Pivotal Elastic Runtime. If you are a customer upgrading from PCF 1.6 to PCF 1.7 and you are using SSO v1.0.x, you must upgrade to the SSO v1.1.0 service tile when you upgrade the Elastic Runtime Tile to 1.7.

* The Apps Manager console URL has changed from **console**._YourSystemDomain_ to **apps**._YourSystemDomain_.

* When you upgrade Ops Manager from 1.6 to 1.7 on vSphere or vCloud, you may notice that several of your Elastic Runtime VMs will automatically resize to have more CPU, memory, and/or disk. This is because the new Ops Manager defines specific instance types instead of custom sizings, and each instance will adopt an instance type that is the closest match to the previous custom size. For instance, you may see the Diego Cells will increase their CPU to 4 and their disk to 130 GB per Cell if you kept the default size of Cell instances from Elastic Runtime 1.6.x. If you disagree with the instance size automatically selected, you may select a different type anytime.

* No metrics from any jobs in Elastic Runtime 1.7.0 will be emitted to the firehose, so none of these metrics will appear in the JMX bridge. This is being addressed in 1.7.1.

* Java apps can take advantage of the custom certificate authority feature of PCF 1.7, but it requires using a more recent Java buildpack version than the one included with Elastic Runtime 1.7.0. The buildpack version is 3.7, and it requires that you also enable the Container Certificate Trust Store feature. The feature is turned off by default, because it can impact staging performance of Java apps, adding an extra 45 seconds or so.

* The cross-container traffic checkbox is removed from Elastic Runtime, because since the migration from the DEA architecture to Diego this feature setting is now actually controlled by your CF application security groups.

## Existing Issues

* Existing issues here
