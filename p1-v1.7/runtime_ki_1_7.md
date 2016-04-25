---
title: Pivotal Elastic Runtime&reg; v1.7 Known Issues
owner: Release Engineering
---

#### New Issues

* The Apps Manager console URL has changed from **console**._YourSystemDomainL_ to **apps**._YourSystemDomain_.

* When you upgrade Ops Manager from 1.6 to 1.7 on vSphere or vCloud, you may notice that several of your Elastic Runtime VMs will automatically resize to have more CPU, memory, and/or disk. This is because the new Ops Manager defines specific instance types instead of custom sizings, and the each instance will adopt an instance type that is the closest match to the previous custom size. For instance, you may see the Diego Cells will increase their CPU to 4 and their disk to 130 GB per Cell if you kept the default size of Cell instances from Elastic Runtime 1.6.x.


#### Existing Issues

* Existing issues here
