pcf-release-notes
===========

This repository stores the content that publishes to the PCF versioned release notes. Versioned release notes for Pivotal Platform v2.7, Pivotal Platform v2.8, and Ops Manager and Tanzu Application Service v2.9 and later have been moved to their respective product repositories:
* [docs-ops-manager](https://github.com/pivotal-cf/docs-ops-manager)
* [docs-pas](https://github.com/pivotal-cf/docs-pas)
* [docs-pcf-windows](https://github.com/pivotal-cf/docs-pcf-windows/tree/master/docs-content)

All release notes are stored in version-specific branches. Do not use the `main` branch for release note content.

**Branch Information**

| Branch | Use |
| ------ | --- |
| main | Do not use. |


**Create Release Notes**

When you create release notes, create them in the branch of this repository that corresponds to the product version number 
you are updating. Release notes for versioned products publish from the branch of the same name. 
For example, we publish the PCF 2.5 release notes using the content of the `2.5` branch of this repository.

**Publish or Update Release Notes**

Change and additions to the content in an existing branch of this repository automatically trigger the `cf-release-notes` 
Concourse pipeline run by the VMware Tanzu Documention team: 
https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes

This pipeline automatically publishes release notes to a staging environment. Once published to a staging environment, 
someone should review the results to verify the content and formatting. After verification, someone must manually trigger 
publishing to a production site.

Contact the VMware Tanzu Documentation team to publish your release notes to a production site, either through Slack (#tanzu-docs in the VMware or Pivotal organization) or by email (cf-docs@pivotal.io).

If you have access permission to the `cf-release-notes` Concourse pipeline, you can publish your release notes to a 
production site without contacting the VMware Tanzu Documentation team. In general, we only recommend this for small changes.

If you have access permission to the `cf-release-notes` Concourse pipeline, follow the steps below to update release notes on a production site:

1. Update, commit, and changes to a branch of this repository.

2. Verify that your updates publish to the appropriate staging site correctly. You may need to refresh the site in your browser to see the changes.

    * [PCF 1.10 staging site](http://docs-pcf-staging.cfapps.io/pivotalcf/1-10/pcf-release-notes/index.html)
    * [PCF 1.11 staging site](http://docs-pcf-staging.cfapps.io/pivotalcf/1-11/pcf-release-notes/index.html)
    * [PCF 1.12 staging site](http://docs-pcf-staging.cfapps.io/pivotalcf/1-12/pcf-release-notes/index.html)
    * [PCF 2.0 staging site](http://docs-pcf-staging.cfapps.io/pivotalcf/2-0/pcf-release-notes/index.html)
    * [PCF 2.1 staging site](http://docs-pcf-staging.cfapps.io/pivotalcf/2-1/pcf-release-notes/index.html)
    * [PCF 2.2 staging site](http://docs-pcf-staging.cfapps.io/pivotalcf/2-2/pcf-release-notes/index.html)
    * [PCF 2.3 staging site](http://docs-pcf-staging.cfapps.io/pivotalcf/2-3/pcf-release-notes/index.html)
    * [PCF 2.4 staging site](http://docs-pcf-staging.cfapps.io/pivotalcf/2-4/pcf-release-notes/index.html)
    * [PCF 2.5 staging site](http://docs-pcf-staging.cfapps.io/pivotalcf/2-5/pcf-release-notes/index.html)
    * [PCF 2.6 staging site](http://docs-pcf-staging.cfapps.io/pivotalcf/2-6/pcf-release-notes/index.html)
    
    I think these staging sites are wrong. Try https://docs-pcf-staging.sc2-04-pcf1-apps.oc.vmware.com/pivotalcf/2-6/pcf-release-notes/index.html instead.

3. Open the appropriate tab in Concourse, click the **production** box, then click the **+** button in the top right to start a production build.

    * [PCF 1.10](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?groups=pcf-1-10)
    * [PCF 1.11](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?groups=pcf-1-11)
    * [PCF 1.12](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?groups=pcf-1-12)
    * [PCF 2.0](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?groups=pcf-2-0)
    * [PCF 2.1](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?groups=pcf-2-1)
    * [PCF 2.2](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?groups=pcf-2-2)
    * [PCF 2.3](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?groups=pcf-2-3)
    * [PCF 2.4](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?groups=pcf-2-4)
    * [PCF 2.5](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?groups=pcf-2-5)
    * [PCF 2.6](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?groups=pcf-2-6)

    Look on concourse: https://runway-ci.eng.vmware.com/teams/mapbu-docs/pipelines/cf-release-notes
