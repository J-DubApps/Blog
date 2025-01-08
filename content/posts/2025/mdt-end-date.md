+++
date = '2025-01-08T01:17:51-06:00'
draft = false
title = 'MDT Hard-Stop In Upcoming CM Update'
type = 'post'
tags = ["tech", "devops", "enterprise-it", "ms-config-mgr", "intune"]
+++


…been seeing this around for a couple weeks: almost all of my supported Task Sequences are [**Microsoft Deployment Toolkit**](https://en.wikipedia.org/wiki/Microsoft_Deployment_Toolkit) (MDT)-dependent, and leverage it most every day.  There are PowerShell replacements to put the main MDT features into a Task Sequence, reducing the need for MDT, so that is probably the route we will take.  We just aren't 100% Autopilot-ready yet, even with [CloudOSD](https://www.osdcloud.com) being a thing...