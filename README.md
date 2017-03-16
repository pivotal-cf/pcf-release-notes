pcf-release
===========

A repo that stores the release notes that publish to the PCF versioned release notes.

All release notes are stored in a version-specific branch. Do not use the MASTER branch for release note content.

**To author release notes:**

Use the branch for the product version number you are updating. Release notes for versioned products publish from the branch of the same name, such as the PCF 1.7 release notes yield from the `1.7` branch of this repo.

**To publish updates to your release notes (if the docs team is unavailable):**

Requirement: If you cannot reach the Docs team to Publish your release notes, you need to have access permission to the CI/CD pipelines that publish `production` release notes. 

The procedure to bump production notes:
  1. Update, commit and push your content to this repo.
  2. Check that your updates publish to the staging site correctly (it normally takes about 10-15 minutes).
    * [PCF 1-6 Staging](http://docs-pcf-staging.cfapps.io/pivotalcf/1-6/pcf-release-notes/index.html)
    * [PCF 1-7 Staging](http://docs-pcf-staging.cfapps.io/pivotalcf/1-7/pcf-release-notes/index.html)
    * [PCF 1-8 Staging](http://docs-pcf-staging.cfapps.io/pivotalcf/1-8/pcf-release-notes/index.html)
    * [PCF 1-9 Staging](http://docs-pcf-staging.cfapps.io/pivotalcf/1-9/pcf-release-notes/index.html)
    * [PCF 1-10 Staging](http://docs-pcf-staging.cfapps.io/pivotalcf/1-10/pcf-release-notes/index.html)
    * NOTE: **If not, do you need to hard refresh your page? (CNTL-SHIFT-R)**
  3. For **1-6**: From the [PCF 1-6 concourse group](https://p-concourse.wings.cf-app.com/teams/system-team-docs-docs-1-88aa/pipelines/cf-previous-versions?groups=pcf-1-6), click to the **production** job and then click the **+** button (top right) to start a production build.
  4. For **1-7**: From the [PCF 1-7 concourse group](https://p-concourse.wings.cf-app.com/teams/system-team-docs-docs-1-88aa/pipelines/cf-previous-versions?groups=pcf-1-7), click to the **production** job and then click the **+** button (top right) to start a production build. 
  5. For **1-8**: From the [PCF 1-8 concourse group](https://p-concourse.wings.cf-app.com/teams/system-team-docs-docs-1-88aa/pipelines/cf-previous-versions?groups=pcf-1-8), click to the **production** job and then click the **+** button (top right) to start a production build.
  6. For **1-9**: From the [PCF 1-9 concourse group](https://p-concourse.wings.cf-app.com/teams/system-team-docs-docs-1-88aa/pipelines/cf-previous-versions?groups=pcf-1-9), click to the **production** job and then click the **+** button (top right) to start a production build.
  7. For **1-10**: From the [PCF 1-10 concourse group](https://p-concourse.wings.cf-app.com/teams/system-team-docs-docs-1-88aa/pipelines/cf-current?groups=pcf-1-10), click to the **production** job and then click the **+** button (top right) to start a production build.

