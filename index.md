---
permalink: /
layout: default
title: Introduction
---
Best practices are difficult to practice without a good environment in which to practice them. 
Here we enumerate the elements of a productive development environment.

##<a name="people"></a> People not Systems
Technology use should be from the perspective of the person, not the system(s). 
Put another way, this is giving developers what they need to do their job and selecting hardware and software to support this. 
By allowing developers to work the way they want, they are more productive and consistent, which leads to a better product.
If done well, these systems become largely invisible while still allowing personal customization by the developer that is applied across work devices.

## <a name="self-provisioning"></a> Self Provisioning
Developers can create and delete systems on-demand, with group alloction and quotas as needed to avoid over-commiting resources. 
These self-provisioned systems are identical with documented exceptions for network configuration, autherntication, etc. 
All services should be developed using SSL for proper testing. 
This requires a self-service system to issue certificates, so that applications can be developed and tested using the same configuration used in production.

##<a name="automation"></a> Automation
Automation brings several key advantages to your development environment, and should be used wherever possible.
Some of these are: 

* It increases speed and reduces the likelyhood of an error.
* Automated processes can be tested, just like the code that is written by developers.
* It can be version controlled. Each change is recorded in the version control along with comments as to why that change needed to happen; with manual steps there is no such history.
* It lets testers and developers spend more time on adding or fixing functionality instead of monotonous tasks.
* Something that is automated can be verified, and thus can be trusted.

####Tasks that are great for automation:

* Build of the system under design
* Deployment of the system under design
* Execution and report generation of
    * Unit tests
    * Code coverage
    * Functional testing
    * Load testing
    * Code quality metrics and conventions
* Health check of systems

##<a name="environments"></a> Environments
When developing and maintaining software several environments will be needed.
Usually at least 4 environments are needed, each servering a different purpose:

* Dev (development)
    * Where developers have free rein(Admin) to do whatever they need to for development, such as install software for evaluation, test new architecures, or test production install instructions. 
    * Code changes from Dev will most likely create new Test builds.
* Test
    * Where developers combine code from everyone and test to make sure they merged correctly, and it works as expected. 
    * Builds that pass in Test can be passed to Staging for possible use in Prod.
* Staging
    * Permissions and data are exact copies from Prod. 
    * The data is updated on some predefined schedule determined by communication between developers and system admins. 
    * End users and other testers verify bug fixes and new features. 
    * Any build that passes in Staging is eligible for promotion to Prod.
* Prod (production)
    * Where the built software is deployed for use by all users. 
    * Actual data is entered, and software provides value. 
    * Developers to have as little admin access as needed. 
    * Prod also has a well defined process for deploying new test builds that have been promoted. See [Build Promotion] (#build-promotion) below.

It should be noted that most (if not all) environments will need the full set of developer tools. 
Also, each environment should be sandboxed from each other to prevent resources from accidents.

## <a name="update-schedule"></a> Update Schedule
Installing software updates promptly is a key security measure and avoids discrepancies between development and production systems.
Each application should have a defined process for communicating and deploying updates with varying levels of testing based on the importance of the update.

* Developers should design software to be safely restarted at any time using the standard operating system interface (e.g. init.d, upstart or systemd on Unix servers or the service manager on Windows) to reduce the level of application-specific knowledge required for a system administrator to restart services after installing updates
* Developers should provide well-documented health checks which automated monitoring services and system administrators can use to confirm that an application is fully operational after being restarted
* System administrators and developers should agree on a deployment mechanism including a rollback process to reduce the risk of proactively installing system updates

## <a name="build-promotion"></a> Build promotion
* Every code commit to version control creates a potentially deployable artifact in the Continuous integration server.
Therefore a well defined and version controlled process for promoting a build from Dev(or continuous integration artifact)->Test->Staging->Prod needs to exist.
* These built artifacts should not change when deploying to multiple environments(i.e. built once), and are stored in a artifact repository for easy retrieval. 
This ensures that the built product is the same when testing in each environment, and that only configuration changes(if any) are different between environments.

## <a name="service-contract"></a> Service Contract with System Administrators
There is a defined support contract specifying a base-line level of service and software support.
This should include but is not limited to:

* System configuration is managed in a version control system and should be automatically applied for consistency
* Defined base operating system and pre-approved software repositores (like YUM or DEB) for common components like PHP or Python.

_Note that this is a work in progress; we will be adding more content
shortly._
