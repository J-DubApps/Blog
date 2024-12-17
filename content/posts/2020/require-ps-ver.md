+++
date = '2020-10-15T23:14:51-06:00'
draft = false
title = 'More on the PowerShell Requires Statement...'
type = 'post'
tags = ["tech", "powershell", "code", "best-practice", "devops", "beginner-fundamentals", "enterprise-it", "walk-thru"]
+++

<style>

/* Style for inline monospace text */
.mono {
    font-family: 'Courier New', Courier, monospace; /* Monospace font */
    background-color: #f0f0f0;        /* Light background to highlight */
    padding: 2px 4px;                  /* Padding around text */
    border-radius: 3px;                /* Rounded corners */
}

/* Dark mode overrides */

    .mono {
        background-color: #3c3c3c;     /* Darker background for inline code */
        color: #f8f8f2;                /* Light text */
    }
}

/* Optional: Light mode overrides (for explicitness) */

    .mono {
        background-color: #f0f0f0;     /* Light background */
        color: #333;                   /* Dark text */
    }
}
</style>

PowerShell has a robust scripting environment that allows for quick and flexible code creation. But what happens when a script that relies on PowerShell 7 or specific modules gets executed on PowerShell 5.1? It fails, often with confusing errors.  Enter the <span class="mono">#requires</span> statement—a feature that allows you to preemptively enforce prerequisites for your scripts. <br />

If you remember, we actually talked about it [earlier this month](https://julianwest.me/Blog/require-admin-ps/) on how to use the <span class="mono">#requires -RunAsAdministrator</span> statement to make a script require being executed in an Admin PS session. But <span class="mono">#requires</span> can do a lot more!

The <span class="mono">#requires</span> statement ensures that your script will only execute under the proper conditions, such as the right PowerShell version, required modules, or user privileges. If these prerequisites aren’t met, PowerShell immediately throws an error and stops the script—saving you time and unnecessary troubleshooting. <br />

Let’s dive into how to use the <span class="mono">#requires</span> statement effectively. <br />

As we covered a couple weeks ago, the <span class="mono">#requires</span> statement must be placed at the *very top* of your script. It is processed before any other code executes. If the conditions defined in the <span class="mono">#requires</span> line aren’t met, the script bails and halts immediately. <br />

Here’s a basic example that enforces a PowerShell version: <br />

~~~
#requires -Version 7.0

# rest of script here

~~~

So if someone tries to run this script in PowerShell 5.1, they’ll see an immediate error like this: <br />

<span class="mono">The script is not supported on this system. PowerShell version 7.0 or greater is required.</span> <br />

<b>Key Options for <span class="mono">#requires</span></b> <br />

The #requires statement has several options that allow you to define exactly what your script needs. Here are the most common:
1.	-Version: Enforces a minimum PowerShell version.
2.	-Modules: Ensures required modules are available.
3.	-RunAsAdministrator: Requires the script to run with elevated privileges (covered [a couple weeksback](https://julianwest.me/Blog/require-admin-ps/))
4.	-PSSnapin (legacy): Ensures a specific snap-in is available (mostly for older scripts). 

Leaving out <span class="mono">#Requires -RunAsAdministrator</span> that we already covered, and the old legacy <span class="mono">-PSSnapin</span>, let’s look at the <span class="mono">#requires -Modules</span> option in more detail: <br />

**Requiring Modules** <br />

Sometimes your script depends on certain modules to function correctly. Instead of manually checking for their existence, use <span class="mono">#requires</span> to enforce them: </br>

~~~
#requires -Modules ActiveDirectory, Az

# rest of script here

~~~

This line ensures the ActiveDirectory and Az modules are available. If they’re missing, PowerShell stops execution and throws an error. <br />

**Combining Multiple Requirements**

You can combine multiple #requires statements to enforce complex conditions. For example: <br />

~~~
#requires -Version 7.0
#requires -Modules ActiveDirectory
#requires -RunAsAdministrator

# rest of script here

~~~

So this script will *only* execute if:
1.	PowerShell 7.0 (or higher) is running.
2.	The ActiveDirectory module is available.
3.	The user has administrative privileges.

<b>How <span class="mono">#requires</span> Improves Script Resilience</b> <br />

By using <span class="mono">#requires</span>, you avoid runtime errors caused by missing prerequisites. Instead of a cryptic failure halfway through the script, the user gets an immediate and clear error message—saving both time and frustration. <br />

For example, instead of doing this manually: <br />

~~~
if ($PSVersionTable.PSVersion.Major -lt 7) {
    Write-Error "This script requires PowerShell 7.0 or greater!"
    exit
}

~~~

You can simply write: <br />

~~~
#requires -Version 7.0

~~~

It’s cleaner, more elegant, and follows best practices. <br />

Best Practices for #requires
1.	<b>Always Place <span class="mono">#requires</span> at the Top</b>: It must be the very first executable line in your script.
2.	<b>Be Specific</b>: Use <span class="mono">-Version</span> and <span class="mono">-Modules</span> to communicate clear requirements.
3.	Combine Requirements: Use multiple <span class="mono">#requires</span> lines if your script has multiple dependencies.
4.	Document Prerequisites: Even with <span class="mono">#requires</span>, include comments explaining why certain conditions are needed.

**Example Script** <br />

Here’s an example of a script that requires PowerShell 7, the Az module, and administrative privileges: <br />

~~~
#requires -Version 7.0
#requires -Modules Az
#requires -RunAsAdministrator

# Sample Script: Retrieve Azure Resource Groups
Write-Output "Checking Azure Resource Groups..."

# Connect to Azure
Connect-AzAccount

# List Resource Groups
Get-AzResourceGroup | Select-Object ResourceGroupName, Location

~~~

If someone runs this script without PowerShell 7, the Az module, or admin rights, they’ll get an immediate and clear error. <br />

<b>When <i>Not</i> to Use <span class="mono">#requires</span></b> <br />

While <span class="mono">#requires</span> is extremely helpful, there are a few situations where it might not be appropriate:
1.	**Ad-Hoc One-Liners**: For quick testing or one-off scripts, enforcing prerequisites may be overkill.
2.	**Non-Critical Scripts**: For scripts that won’t cause harm if prerequisites are missing, manual checks may suffice.
3.	**Legacy Environments**: If you’re working in environments with older PowerShell versions, consider backward compatibility carefully.

### Takeaways...

The <span class="mono">#requires</span> statement is a simple yet powerful way to enforce pre-reqs in your PowerShell scripts. By using it, you can ensure your code runs under the correct conditions, reducing errors and making your scripts more reliable.

Give <span class="mono">#requires</span> a spin in your next script, your future self will thank you! 🚀