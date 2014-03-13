---
title: Pivotal CF Elastic Runtime 1.1.0.0 Known Issues
---

* It's possible for the auth token to expire right before a request to Loggregator, which means that users will be unable to see logs for their app. They will also see an "Error: Invalid authorization" message in Loggregator. Log in again to fix the issue.

* The `system` org is reserved for the Developer Console. Spaces cannot be created in the `system` org.

* After installing the “Pivotal Metrics” product (currently in Beta), operators must increase the collector VM instance count to 1 and re-push Elastic Runtime to have the setting take effect.

* Deleting a service product deployment (e.g. HD, MySQL) leaves orphan rows in the Cloud Controller DB. Before you can deploy the same service product again, you must delete and re-deploy Elastic Runtime.

* Quotas are not configurable for the plan offered by MySQL Dev.

* If upgrading from 1.0 to 1.1, change the following values in **Pivotal Elastic Runtime > Settings > Resource Sizes**:
	* RAM (MB) for Cloud Controller must be 4096 or greater
	* Ephemeral Disk (MB) for Compilation must be 6144 or greater

* SSO integration is only supported for Pivotal CF on vSphere 5.5. SSO integration is a beta feature with the 1.1.0.0 release.

* Binding a service to an app will cause an error when requesting status from the app until the app is restarted.

* Deleting products in Ops Manager must be done separately from applying changes or installing other products to avoid unexpected errors.

* Upgrading 1.0.0.1 to 1.1.0.0 by exporting/importing will not provide users with an upgraded Dev Console. See the Pivotal Operations Manager [Release Notes](./opsmanager_rn.html) for instructions on how to inject the 1.1 Dev Console when upgrading.

* If logging data comes in at a high rate, the DEA logging agent may split
log messages on non-line-endings.
The DEA logging agent does not drop any bytes when this happens.
Instead, the agent simply splits one log line into two.
If this occurs, it should only happen once per 4KB of log messages.
This behavior is 'as designed' in the current implementation of the DEA logging
agent.

* Custom Orgs and domains created in PCF 1.0 cannot be deleted after an upgrade to PCF 1.1:

__Example Failure:__

<pre class='terminal'>
$ cf delete-org example-org

Really delete org example-org and everything associated with it?> yes
Deleting org example-org as admin...
FAILED
Internal Server Error
</pre>

__Workaround:__
Login to the ccdb and run `TRUNCATE TABLE ONLY domain_organizations;`. If you would like assistance with this process, please contact Pivotal support.

1. Verify domain organizations table is populated:

    ```
    ccdb=> select * from domains_organizations;
     domain_id | organization_id
    -----------+-----------------
             1 |               3
             1 |               6
             1 |               8
    (3 rows)
    ```

1. Truncate this table:

    ```
    ccdb=> truncate table only domains_organizations;
    TRUNCATE TABLE
    ```

1. This table should no longer be populated:

    ```
    ccdb=> select * from domains_organizations;
     domain_id | organization_id
    -----------+-----------------
    (0 rows)
    ```

1. Upon successful truncation, it will be possible to delete domains and organizations created before the upgrade.

    <pre class='terminal'>
    $ cf delete-org example-org

    Really delete org example-org and everything associated with it?> y
    Deleting org example-org as admin...
    OK
    </pre>