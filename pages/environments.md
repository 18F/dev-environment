---
permalink: /environments/
layout: default
title: Environments
---
<a name="environments"></a>
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
    * Prod also has a well defined process for deploying new test builds that have been promoted. See the [Build Promotion] ({{site.baseurl}}/build-promotion/) section.

It should be noted that most (if not all) environments will need the full set of developer tools. 
Also, each environment should be sandboxed from each other to prevent resources from accidents.
