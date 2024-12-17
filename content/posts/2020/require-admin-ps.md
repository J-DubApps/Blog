+++
date = '2020-10-05T23:13:51-06:00'
draft = false
title = 'Requires -RunAsAdministrator in PS'
type = 'post'
tags = ["tech", "powershell", "code", "best-practice", "devops", "walk-thru", "beginner-fundamentals"]
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

When writing PowerShell scripts, whether automating a common task or just sending a colleague a script -- it is easy to forget if your script required Admin mode or not.  The person at the other end will figure it out pretty quickly; however, people new to PowerShell might not.  Here's a way to save yourself that trouble at the onset, when sending a <span class="mono">.ps1</span> script over to somebody to run.   <br />

At the very top of your script, simply use the <span class="mono">#Requires -RunAsAdministrator</span> directive:
 
~~~
#Requires -RunAsAdministrator
 
# rest of script here

~~~

Now when your friend runs your helpful script in their default PS window they'll get a helpful and immediate message that they need an elevated PS session, instead of the run-of-the-mill "access is denied" red output.  🙂 <br />

But you may be wondering, "***hey Julian, can't I just have the script self-elevate into a new Admin PS session window, and prompt me?***" <br />

And I would tell you, "yes!"*

##### * interactive self-elevating scripts are not raelly a best-practice in most environments, and really is for Intermediate and crazy scripters using their own sandbox environment, not in prod!  What I am about to show you can sometimes trigger any IPS or XDR suite running on your PC, such as Palo Alto Cortex or CrowdStrike. If you don't have a clear line-of-comms to your CISO or SOC team, maybe ***don't*** play around running this code on your work PC.  😉  <br />

So assuming you're not running some IPS/XDR stuff on your PC, or you're running it on a sandbox to play around, or if you've gotten clearance from your local neighborhood SOC or CISCO -- here's a quick & dirty script that self-elevates: <br />

~~~
# Check if running as Administrator
if (-not ([Security.Principal.WindowsPrincipal] [Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole] "Administrator")) {
    # Not running as Administrator
    Write-Host "This script needs to be run as Administrator. Restarting with elevated privileges..." -ForegroundColor Yellow

    # Get the current script's file path
    $scriptPath = $MyInvocation.MyCommand.Path

    # Create a new process to start PowerShell with Administrator privileges
    Start-Process -FilePath "powershell.exe" -ArgumentList "-NoProfile -ExecutionPolicy Bypass -File `"$scriptPath`"" -Verb RunAs

    # Exit the current script
    exit
}

# Place the rest of your script here
Write-Host "Running with Administrator privileges." -ForegroundColor Green

~~~

This script code uses the [.NET Windows Security Principal class](https://learn.microsoft.com/en-us/dotnet/api/system.security.principal.windowsidentity?view=net-9.0) to check if running as admin, and launches an elevated PS session if needed. <br />

The thing about this snippet I threw together is: it's common and far better examples exist on every other PowerShell GitHub Repo. And, again, if you operate in an environment with good security hygiene on your endpoints - you'll need SOC or CISCO (and probably Change Mgmt) buy-in to ever be running scripts that interactively self-elevate. Always ask: "I'm I putting training wheels on a script...when I should just be automating something?"  With things like the new [Terminal for Windows](https://learn.microsoft.com/en-us/windows/terminal/) allowing for quick-elevation to a new PS admin session, there's less and less need for this little maneuver these days. So I would just stick with <span class="mono">#Requires -RunAsAdministrator</span>.   <br />

And don't annoy your SOC and/or CISO: 

<img src="https://julianwest.me/Blog/posts/images/gonna-cost-us.jpg" alt="Alt text">


Happy scripting...