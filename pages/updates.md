---
permalink: /updates/
layout: default
title: Update schedule
---
<a name="update-schedule"></a>
Installing software updates promptly is a key security measure, and it avoids discrepancies between development and production systems.
Each application should have a defined process for communicating and deploying updates with varying levels of testing based on the importance of the update.

* Developers should design software so system administrators can safely restart it at any time using the standard operating system interface — for example, init.d, upstart, or systemd (on Unix servers) or the service manager (on Windows). This reduces the level of application-specific knowledge a system administrator must have to restart services after installing updates.
* Developers should provide well-documented health checks that automated monitoring services and system administrators can use to confirm that an application is fully operational after they restart it.
* System administrators and developers should agree on a deployment mechanism — *including a rollback process* — to reduce the risk of proactively installing system updates.
