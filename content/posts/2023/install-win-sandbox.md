+++
date = '2023-11-30T23:14:51-06:00'
draft = false
title = 'Enabling Windows Sandbox on Windows 10/11'
type = 'post'
tags = ["tech", "devops", "enterprise-it", "windows", "linux", "powershell", "secops"]
+++

<style>
/* Base style for code blocks */
.code-block {
    padding: 15px;                    /* Padding around the code */
    font-family: 'Courier New', Courier, monospace; /* Monospace font */
    white-space: pre-wrap;            /* Preserve whitespace and wrap lines */
    border-radius: 5px;               /* Rounded corners */
    overflow-x: auto;                 /* Horizontal scroll if needed */
    margin: 20px 0;                   /* Vertical spacing */
    /* Default colors (light mode) */
    background-color: #f5f5f5;        /* Light gray background */
    border: 1px solid #ddd;           /* Light border */
    color: #333;                      /* Dark text for readability */
}

/* Style for inline monospace text */
.mono {
    font-family: 'Courier New', Courier, monospace; /* Monospace font */
    background-color: #f0f0f0;        /* Light background to highlight */
    padding: 2px 4px;                  /* Padding around text */
    border-radius: 3px;                /* Rounded corners */
}

/* Dark mode overrides for code blocks */
@media (prefers-color-scheme: dark) {
    .code-block {
        background-color: #2d2d2d;    /* Dark background */
        border: 1px solid #555;        /* Darker border */
        color: #f8f8f2;                /* Light text for readability */
    }

    .mono {
        background-color: #3c3c3c;     /* Darker background for inline code */
        color: #f8f8f2;                /* Light text */
    }
}

/* Optional: Light mode overrides (for explicitness) */
@media (prefers-color-scheme: light) {
    .code-block {
        background-color: #f5f5f5;     /* Light gray background */
        border: 1px solid #ddd;        /* Light border */
        color: #333;                   /* Dark text */
    }

    .mono {
        background-color: #f0f0f0;     /* Light background */
        color: #333;                   /* Dark text */
    }
}
</style>

A feature a lot of SecOps teams use, and many Enterprise IT org teams *ignore*, is the [***Windows Sandbox***](https://learn.microsoft.com/en-us/windows/security/application-security/application-isolation/windows-sandbox/windows-sandbox-overview).  It has been around for many years now, but you don't hear a lot about it.  It can really help in a pinch with work ranging from bonafide DFIR situations, to just getting some low-risk code isolated for a quick review using [Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon) and other tools. <br />

Windows Sandbox provides a lightweight desktop environment to safely run applications in isolation. Software installed inside the Windows Sandbox environment remains "sandboxed" and runs separately from the host machine.  And becausae it uses hardware-based virtualization for kernel isolation, it's very secure. <br />

Since Windows Sandbox is like a virtual machine, the "machine" inside Windows Sandbox does not need to be activated btw; however, I do believe you need to be running E3 or E5 Enterprise Edition for your Windows activation. <br />

### Ok here are the steps to get *sandboxing*:

Launch PowerShell as Administrator and run the following (you should reboot right away) <br />

>``` Enable-WindowsOptionalFeature -Online -FeatureName "Containers-DisposableClientVM" -NoRestart -All ```
>``` Restart-Computer -Force ```

More on Windows Sandbox [**here**](https://learn.microsoft.com/en-us/windows/security/application-security/application-isolation/windows-sandbox/windows-sandbox-overview.)

**A Quick Word Of Caution & Advice**: Some Enterprise IT orgs' flat-out won't allow you to install this, even when running Enterprise Edition Windows 10/11.  This is because some XDR/IDS systems may grumble, or stop an attempt to enable Windows Sandbox. Check with your friendly IT sysadmin or Ops team, as it may turn out some massaging of your SOC or CISO is all that's needed to enable Windows Sandbox.  <br />

I usually just cheefully send this to my friendly neighborhood SecOps team, and they usually work with me: 

![Alt text](https://julianwest.me/Blog/posts/images/IT-admin-ops-oath.jpeg)