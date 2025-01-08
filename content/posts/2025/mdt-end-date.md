+++
date = '2025-01-08T01:17:51-06:00'
draft = false
title = 'MDT Hard-Stop In Upcoming CM Update'
type = 'post'
tags = ["tech", "devops", "enterprise-it", "ms-config-mgr", "intune"]
+++
<img src="https://julianwest.me/Blog/posts/images/mdt-cm-jan-25.jpeg" alt="Alt text">

…been seeing this around for a couple weeks: almost all of my supported Task Sequences are [**Microsoft Deployment Toolkit**](https://en.wikipedia.org/wiki/Microsoft_Deployment_Toolkit) (MDT)-dependent, and leverage it most every day.  There are PowerShell replacements for MDT features that can be used in a Task Sequence, eliminating the need for MDT for most shops, so that is probably the route we will take.  We just aren't 100% Autopilot-ready yet, even with [CloudOSD](https://www.osdcloud.com) being a thing...