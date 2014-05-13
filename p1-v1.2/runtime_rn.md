---
title: Pivotal Elastic Runtime v1.2.0.0 Release Notes
---

## Changes since v1.1.0.0:

* Go-router now supports sending `X-Vcap-Request-Id` to all routes to give both CF users and CF components the ability to trace the lifecycle of a request.
* Space attributes such as id and name are now included in `VCAP_APPLICATION`.
* You can now find Cloud Controller API docs at [http://apidocs.cloudfoundry.org](http://apidocs.cloudfoundry.org).
* Over 50 community submitted PRs have been pulled into this release.
* All CC jobs are now co-locatable.
* NATS now runs in a clustered mode using gnatsd.
* Cloud Controller now supports no-downtime deploys.
* Operators can now install buildpacks in CF from the CLI and manage their detect order.
* CF now supports 1GB applications.
* Cloud Controller read/write scopes are now implemented per endpoint.
* Large buildpacks are now supported (~1GB).
