---
permalink: /
layout: default
title: Introduction
---
Best practices are difficult to practice without a good environment in which
to practice them. Here we enumerate the elements of a productive development
environment.

##<a name="environments"></a> Environments
When developing and maintaining software several environments will be needed. Usually at least 4 environments are needed, each servering a different purpose:

* Dev (development)
    * Where developers have free rein(Admin) to do whatever they need to for development, such as install software for evaluation, test new architecures, or test production install instructions. 
    * Code changes from Dev will most likely create new Int builds.
    * Dev should be "sandboxed" from other environments to prevent any accidents to other resources.
* Int (integration)
    * Where developers combine code from everyone and test to make sure they merged correctly, and it works as expected. 
    * Builds that pass in Int can be passed to Test for possible use in Prod.
* Test
    * Permissions and data are exact copies from Prod. 
    * The data is updated on some predefined schedule determined by communication between developers and system admins. 
    * End users and other testers verify bug fixes and new features. 
    * Any build that passes in Test is eligible for promotion to Prod.
* Prod (production)
    * Where the built software is deployed for use by all users. 
    * Actual data is entered, and software provides value. 
    * Developers to have as little admin access as needed. 
    * Prod also has a well defined process for deploying new test builds that have been promoted. See [Build Promotion] (#build-promotion) below.

It should be noted that most (if not all) environments will need the full set of developer tools, this includes but is not limited to:

* Compilier(s) / build tool(s)
* Continuous integration server(s)
* Debugger(s)

## <a name="update-schedule"></a> Update Schedule
Because updating software can affect multiple software and or systems, communication needs to agree upon for updates. It is also agree upon that critical patches to system can be done without notification before applying, and developers should design software to stop and restart at any time without reprocussions.

## <a name="build-promotion"></a> Build promotion
Every code check in creates a potentially deployable artifact due to Continuous integration server building after each code check in. Therefore a well defined and version controlled process for promoting a build from Dev(or continuous integration artifact)->Int->Test->Prod needs to exist.

## <a name="self-provisioning"></a> Self Provisioning
Developers can create and delete systems on-demand, with group alloction and quotas as needed to avoid over-commiting resources. These self-provisioned systems with documented exceptions for network configuration, autherntication, etc. All services should be developed using SSL. This requires a self-service system to issue certificates, so that applications can be developed and tested using the same configuration used in production.

## <a name="service-contract"></a> Service Contract with System Administrators
There is a defined support contract specifying a base-line level of service and software support. Admins are required to manage system configurations in version control. Defined base operating system and pre-approved software repositores (like YUM or DEB) for common components like PHP or Python.

_Note that this is a work in progress; we will be adding content
shortly._
