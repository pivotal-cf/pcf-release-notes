---
title: Pivotal Elastic Runtime v1.4.0.0 Release Notes
---

## Changes since v1.3.3.0:

## Elastic Runtime

### New Features 

##### New Stack: Trusty 14.04
<p>
There is a new stack based on Ubuntu Trusty 14.04 LTS.  
<p>The lucid64 stack that has been part of PCF ER for several years as the root file system for containers will reach end of support for security fixes on April 29th, 2015 by Canonical. Developers or Operators will need to take action to ensure existing applications migrate to using the new stack.
<p>In PCF ER 1.4 support has been added for the new stack called cflinuxfs2 derived from Ubuntu Trusty 14.04. 
<p>
##### What do you need to do? 
<li>
1. If you have an application or app as a service running on Pivotal Cloud Foundry, ensure that your application works when run with the new stack and the corresponding new buildpacks.  We recommend using a blue/green deployment strategy to ensure there is no down time for the app.  Simply running the following command will result in a small amount of down time as old instances are stopped and the app is restaged with the new stack.
</li>
	cf push app-name -s cflinuxfs2

2. If you have custom buildpacks, you need to ensure that your buildpacks work when run with the new stack.

###### List of buildpacks that now support cflinuxfs2:

* Java buildpack
* NodeJS buildpack
* PHP buildpack
* Go buildpack
* Python buildpack
* Ruby buildpack
* Operator process for rolling out the new stack

To stay current with security fixes, operators should configure the default stack for new apps to cflinuxfs2 in the Elastic Runtime configuration tab. This means all new applications will get the new default stack:

[insert image here]

Applications that were created prior to cflinuxfs2 being the default stack will have the lucid64 stack set and therefore developers or operators need to take action.

Operators should decide when to notify users that they’ll be vulnerable to not getting new security patches once lucid64 reaches end of support.
Operators should send notice that lucid64 is close to end of life, and developers should migrate to the new cflinuxfs2 stack.
Larger deployments should manage carefully forcing restaging of apps onto the new stack.

###### lucid64 reaches end of support for security fixes on April 29th, 2015

The lucid64 stack will be removed from the Elastic Runtime tile in the next minor release.

When an Elastic Runtime release without lucid64 is deployed, apps that have not yet switched to cflinuxfs2 will not start because their stack will no longer be available. 

Operators will need to force the change to the cflinuxfs2 stack and 
restart the applications. There is a cf CLI plugin [stack-changer](https://github.com/simonleung8/cli-stack-changer) available that can be used by administrators to help determine what applications have not migrated.  It can then also be used to move apps to the new stack in batches. 

Once the migration is complete, to remove lucid64 from the list of stacks that cloud controller returns, an admin will need to delete the stack via the cc api.

	cf curl /v2/stacks/:lucid64_stack_guid -X DELETE

<b>Known issue: For apps that use native compiled binaries, when the stack is changed, the app may fail to start.  If this occurs, the current work around is to delete the app and then push the app again.</b> 






