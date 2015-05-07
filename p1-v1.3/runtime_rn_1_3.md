---
title: Pivotal Elastic Runtime v1.3.0.0 Release Notes
---

CF Runtime Version: 183

## Changes since v1.2.2.0:

* Work on Feature Flags completed. See supporting documentation here: http://apidocs.cloudfoundry.org/
* Environment Variable Groups are now available and support administrators setting environment variable values across all applications.
* Application containers no longer create a listing of environment variables in log/env.log.
* Changed syslog config to send all syslog logs from the VM, the previous config only sent logs tagged with vcap. Nats logs are now sent to stderr so they end up in syslog.
* Included additional support for UDP and RELP (default is TCP) as syslog transport options.
* LDAP groups mapping to scopes is now supported. Administrators can now be derived from LDAP groups.
* Space Quotas are now supported.
* Added X-Forwarded-For to access log records.
* Support for I18N in the Pivotal Cloud Foundry CLI.
* Go, NodeJS, Java, PHP, Ruby, Python and PHP buildpacks are now all installed by default. The PHP buildpack has been reduced from 400+mb down to 64mb for droplet hello world and no longer includes cached dependencies in the droplet.
* Changed CC to use HM9000's bulk app state API. This should be more efficient for spaces with lots of apps.
* Added the /v2/apps/:guid/instances/:index endpoint, against which a DELETE kills the app instance at the specified index.
* This release is the first release where CF Security Groups are fully implemented. Security groups are used in this release. However, operators should review the Security Groups documentation to determine the correct application of these groups for their specific use cases. By default in this release, Security Groups are configured to allow outbound traffic from applications. CF Security Groups can be managed via the API or CF CLI
* Many missing CC API docs have now been added and are available at http://apidocs.cloudfoundry.org/
