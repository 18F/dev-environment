---
permalink: /updates/
layout: default
title: Update Schedule
---
<a name="update-schedule"></a>
Installing software updates promptly is a key security measure and avoids discrepancies between development and production systems.
Each application should have a defined process for communicating and deploying updates with varying levels of testing based on the importance of the update.

* Developers should design software to be safely restarted at any time using the standard operating system interface (e.g. init.d, upstart or systemd on Unix servers or the service manager on Windows) to reduce the level of application-specific knowledge required for a system administrator to restart services after installing updates
* Developers should provide well-documented health checks which automated monitoring services and system administrators can use to confirm that an application is fully operational after being restarted
* System administrators and developers should agree on a deployment mechanism including a rollback process to reduce the risk of proactively installing system updates
