+++
date = '2023-11-30T23:14:51-06:00'
draft = false
title = 'Enable Windows Sandbox on Windows 10/11'
type = 'post'
tags = ["tech", "devops", "enterprise-it", "windows", "linux", "powershell", "secops"]
+++
A feature a lot of SecOps teams use, but Enterprise IT org teams *ignore*, is the [***Windows Sandbox***](https://learn.microsoft.com/en-us/windows/security/application-security/application-isolation/windows-sandbox/windows-sandbox-overview).  It has been around for many years now, but you don't hear a lot about it.  It can really help in a pinch with work ranging from bonafide DFIR situations, to just getting some low-risk code isolated for a quick review using [Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon) and other tools. <br />

Windows Sandbox provides a lightweight desktop environment to safely run applications in isolation. Software installed inside the Windows Sandbox environment remains "sandboxed" and runs separately from the host machine.  And becausae it uses hardware-based virtualization for kernel isolation, it's very secure. <br />

It's not the same as Hyper-V but Windows Sandbox *is* a lot like a virtual machine, and what's awesome is Windows Sandbox does not need to be activated; however, I do believe you need to be running E3 or E5 Enterprise Edition for your Windows activation. <br />

### Ok here are the steps to get *sandboxing*:

Launch PowerShell as Administrator and run the following (you should reboot right away) <br />

>``` Enable-WindowsOptionalFeature -Online -FeatureName "Containers-DisposableClientVM" -NoRestart -All ``` <br />
>``` Restart-Computer -Force ```

**A Quick Word Of Caution & Advice**: Some Enterprise IT orgs' flat-out won't allow you to enable Windows Sandbox, even when running Enterprise Edition activation, because some XDR/IDS suites may grumble or even *stop* an attempt to enable it. So check with your friendly IT sysadmin or Ops team if you're going to run this on your work machine, it may turn out some simple massaging of your SOC or CISO is all that's needed.  <br />

And be prepared to take this friendly oath if your friendly neighborhood SecOps team gives you the go-ahead: 

![Alt text](https://julianwest.me/Blog/posts/images/IT-admin-ops-oath.jpeg)