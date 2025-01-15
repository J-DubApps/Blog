+++
date = '2024-12-20T01:14:51-06:00'
draft = false
title = 'A New Windows ADK is out'
type = 'post'
tags = ["tech", "microsoft", "windows", "enterprise-it", "ms-config-mgr", "endpoint-mgmt"]
+++

[ADK 10.1.26100.2454 is out](https://learn.microsoft.com/en-us/windows-hardware/get-started/what-s-new-in-kits-and-tools#whats-new-in-the-adk-101261002454-december-2024) and it deprecates the "ADK nobody bothered with, if they didn't have to" - 10.1.26100.1 released in May 2024.  The May ADK removed VBScript support -- which every MDT-integrated Config Manager shop had to patch, if they wanted to continue using OSD Task Sequences.  <br />

Microsoft ADK and WinPE add-on installers are now current and secure - without sacrificing compatibility that a lot of IT shops still depend on. <br />

As always check those backups and *test-test-test* before updating any of your production OSD boot images.