---
permalink: /continuous-integration/
layout: default
title: Continuous Integration 
---
<a name="continuous-integration"></a>
Continuous integration is the practice of testing each change done to your codebase automatically and as early as possible. 

### Costs and Benefits
Costs:

* Constructing automated test suites, and automating actions is considerable work. This is never considered done, as new tests are required for new functionality or to ensure found bugs do not get reintroduced.
* Much cheaper to do from the beginning then to retroactively execute.

Benefits:

* Integration bugs are detected early and are easy(or easier) to track down due to small changes. This saves both time and money over the lifespan of a project.
* If changes need to be rolled back (reverted) only a small number of changes are lost because integration happens frequently.
* Constant availability of "current" build for testing, demo, or release purposes.
* Frequent code check-in pushes developers to create modular and less complex code.
* With automated testing, immediate feedback and generated mentrics are available for each commit.

### Best practices

The longer the time spent between code integrations the greater the risk of multiple conflicts and failures.
The number and complexity also increase with the number of developers working together.
Given enough time, the code changes so much that integrating it becomes almost impossible, and is often referred to as "integration hell". 
To avoid this, we follow these best practices:

* Maintain a code repository
    * The system should be stored in a code repository that is accessible by every developer. Typically the mainline (trunk, master, etc) of the code should be the place for the working version of the software.
* Automate the build
    * Building the software should be easy, and by easy we mean with a single command. This includes not only compiling the software, but also building documentation, packaging deployable artifacts, and deploying. Depending on your language/deployment there are tools for automating and simplifying. To name a few:
        * [Gradle] (https://gradle.org/)
        * [Make] (https://www.gnu.org/software/make/)
        * [Grunt] (http://gruntjs.com/)
* Testing
    * Testing should be run as soon as the software is in a runable state to ensure it logically works as expected. Tests can also serve as requirements for functionality and thus document the behavior of the system.
    * Testing should be done in an environment identical to production, with well documented exceptions (like a smaller dataset). 
* Developers commit code changes fequently
    * A good goal to start is for each developer to commit code at least once a day. The more often a developer commits code the less of a chance there will be of a conflict. There will still be minor conflicts, but this demands that developers communicate with each other about the functionality of the system which leads to a better understanding for everyone.
    * Each commit to the baseline creates a deployable artifact. This further reduces risk by ensuring that the same binary is used in test as in production, which changes only to the configuration. </br></br>_If you compile before each deployment, you run the risk of a new service pack or library update sneaking in, leading to small differences between what is eventually deployed to each environment (drift). The more consistency that you can keep between pre-production and production deployments, the more likely the production deployment is to go smoothly. </br></br>It's important to recognise that a build process isn't just a deterministic function of "code in", "binaries out". The binaries produced don't just depend on the code going in, but also the libraries, compiler, operating system updates, and a host of other environmental aspects that can change over time._ [Octopus deploy blog post] (http://octopusdeploy.com/blog/build-your-binaries-once)
* Build fast, fail fast
    * Building and testing of any one commit should be fast to reduce/eliminate problems found during integration. The faster you can build and test, the faster the developer can recieve feedback on the changes they made.

### Typical workflow
A typical workflow for continuous integration might look something like this:

1. Developer checks out code from repository(i.e. version control)
2. Developer makes changes to code and checks in changes to repository
3. Continuous integration(CI) server detects changtes in repository
4. CI server checks out latest changes
5. CI server builds and tests latest changes
6. If changes are sucessful, deploy to test environment
7. If changes are *NOT* successful, alert developers of broken build, and possibly roll back changes. Go to step #2
