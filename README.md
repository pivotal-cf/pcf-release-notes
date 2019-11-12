pcf-release-notes
===========

This repository stores the content that publishes to the Pivotal Platform versioned release notes.

All release notes are stored in version-specific branches. Do not use the MASTER branch for release note content.

**Create Release Notes**

When you create release notes, create them in the branch of this repository that corresponds to the product version number
you are updating. Release notes for versioned products publish from the branch of the same name.
For example, we publish the PCF v1.11 Release Notes using the content of the 1.11 branch of this repository.

**Publish or Update Release Notes**

Change and additions to the content in an existing branch of this repository automatically trigger the `cf-release-notes`
Concourse pipeline run by the Pivotal Platform Documentation team:
https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes

This pipeline automatically publishes release notes to a staging environment. Once published to a staging environment,
someone should review the results to verify the content and formatting. After verification, someone must manually trigger
publishing to a production site.

Contact the Pivotal Platform Documentation team to publish your release notes to a production site, either through Slack (#pcf-docs in the Pivotal organization) or by email (cf-docs@pivotal.io).

If you have access permission to the `cf-release-notes` Concourse pipeline, you can publish your release notes to a
production site without contacting the Pivotal Platform Documentation team. In general, we only recommend this for small changes.

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
    * [Pivotal Platform 2.7 staging site](http://docs-pcf-staging.cfapps.io/platform/2-7/pcf-release-notes/index.html)
    * [Pivotal Platform 2.8 staging site](http://docs-pcf-staging.cfapps.io/platform/2-8/pcf-release-notes/index.html)
    * [Pivotal Platform 2.9 staging site](http://docs-pcf-staging.cfapps.io/platform/2-9/pcf-release-notes/index.html)

3. Open the appropriate tab in Concourse, click the **production** box, then click the **+** button in the top right to start a production build.

    * [PCF 2.0 and earlier](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?group=archive)
    * [PCF 2.1](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?group=pcf-2-1)
    * [PCF 2.2](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?group=pcf-2-2)
    * [PCF 2.3](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?group=pcf-2-3)
    * [PCF 2.4](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?group=pcf-2-4)
    * [PCF 2.5](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?group=pcf-2-5)
    * [PCF 2.6](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?group=pcf-2-6)
    * [Pivotal Platform 2.7](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?group=pcf-2-7)
    * [Pivotal Platform 2.8](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?group=pcf-2-8)
    * [Pivotal Platform 2.9](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-release-notes?group=pcf-2-9)
