---
permalink: /build-promotion/
layout: default
title: Build Promotion
---
<a name="build-promotion"></a>
* Every code commit to version control creates a potentially deployable artifact in the Continuous integration server.
Therefore a well defined and version controlled process for promoting a build from Dev(or continuous integration artifact)->Test->Staging->Prod needs to exist.
* These built artifacts should not change when deploying to multiple environments(i.e. built once), and are stored in a artifact repository for easy retrieval. 
This ensures that the built product is the same when testing in each environment, and that only configuration changes(if any) are different between environments.
