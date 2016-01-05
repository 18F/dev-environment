---
permalink: /build-promotion/
title: Build promotion
---
<a name="build-promotion"></a>

Projects with complex test regimens often use the concept of “Build Promotion” to flag particular versions which have passed the entire process and are eligible to be promoted to the next level (development to testing, testing to staging, staging to production). This allows continuous integration and deployment systems to provide rapid feedback to developers while providing a more stable environment for QA testers, beta users, etc.

See the [Continuous Integration] ({{site.baseurl}}/continuous-integration/) section for more information.

## General Overview

1. Every continuous integration (CI) build generates a deployable artifact
2. Successful CI builds trigger additional testing – for example, a web application which successfully completes a core test suite might subsequently be deployed to a server for exhaustive testing with real web browsers using a tool such as Selenium. Once those additional tests pass the original build is flagged for promotion.
3. Promoted builds are stored in a durable repository which can be used for release to other environments

## Assumptions
* The application should be designed to separate system-specific configuration from the package produced by each build

## Tools
* [Jenkins Promoted Build Plugin](https://wiki.jenkins-ci.org/display/JENKINS/Promoted+Builds+Plugin)
=======
* Every code commit to version control<sup>[1](#footnote1)</sup> creates a potentially deployable artifact in the continuous integration server. This being the case, we need a well defined and version controlled process for promoting a build (a continuous integration artifact) from development to test, to staging, and, eventually, production. </br> See the [Continuous Integration] ({{site.baseurl}}/continuous-integration/) section for more info.
* These built artifacts shouldn't change when deploying to multiple environments (for example, built once), and are stored in an artifact repository for easy retrieval. This ensures that the built product is the same when testing in each environment and that only configuration changes — if any — are different between environments.

<a name="footnote1">1</a>: There are many different version control systems available today. Git is one example, we recommend [The Codebase Is in Git](http://sites.oreilly.com/odewahn/dds-field-guide/ch04.html) from O'Reily for more light reading.
