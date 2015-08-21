---
permalink: /build-promotion/
layout: default
title: Build promotion
---
<a name="build-promotion"></a>

* Every code commit to version control creates a potentially deployable artifact in the continuous integration server. This being the case, we need a well defined and version controlled process for promoting a build (a continuous integration artifact) from development to test, to staging, and, eventually, production. </br> See the [Continuous Integration] ({{site.baseurl}}/continuous-integration/) section for more info.
* These built artifacts shouldn't change when deploying to multiple environments (for example, built once), and are stored in an artifact repository for easy retrieval. This ensures that the built product is the same when testing in each environment and that only configuration changes — if any — are different between environments.
