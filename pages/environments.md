---
permalink: /environments/
layout: default
title: Environments
---
<a name="environments"></a>
When developing and maintaining software, you'll need several environments.
Usually you'll need at least four environments, each servering a different purpose:

* Dev (development)
    * Developers have free rein (admin) to do whatever they need to for development, such as install software for evaluation, test new architecures, or test production install instructions. 
    * Code changes from development will most likely create new test builds.
* Test
    * Developers combine code from everyone and test to ensure they merged correctly and it works as expected. 
    * Builds that pass in test can be passed to staging for possible use in production.
* Staging
    * Permissions and data are exact copies from production. 
    * Data is updated on some predefined schedule determined by communication between developers and system administrators. 
    * End users and other testers verify bug fixes and new features. 
    * Any build that passes in staging is eligible for promotion to production.
* Prod (production)
    * This is where built software is deployed for use by all users. 
    * Actual data is entered, and software provides value. 
    * Developers have as little admin access as needed. 
    * Production also has a well defined process for deploying new test builds that have been promoted. See the [Build Promotion] ({{site.baseurl}}/build-promotion/) section.

Note: Most (if not all) environments will need the full set of developer tools. Also, each environment should be sandboxed from each other to prevent resources from accidents.
