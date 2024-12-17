+++
date = ‘2024-06-16T23:44:51-06:00’
draft = false
title = ‘PowerShell ErrorAction and Error Handling’
type = ‘post’
tags = [“tech”, “powershell”, “code”, “best-practice”, “devops”, “beginner-fundamentals”, “enterprise-it”, “walk-thru”]
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

Errors are inevitable when writing PowerShell scripts. Whether it’s a missing file, a failed command, or an unexpected input, handling errors effectively ensures that your script can recover gracefully or at least fail cleanly with a meaningful message.<br />

PowerShell provides built-in tools for handling errors, the most useful of which is the <span class="mono">ErrorAction</span> parameter. By mastering this parameter and a few related techniques, you can gain better control over how your scripts behave when something goes wrong.<br />

Let’s explore how ErrorAction works and how you can use it to improve your PowerShell scripts. <br />

### Understanding ErrorAction

Most PowerShell cmdlets and functions include an <span class="mono">-ErrorAction</span> parameter that determines how they respond to errors. Instead of silently failing or showing an ugly red error message, you can choose from a range of options to control their behavior. <br />

Here’s the basic syntax: <br />

~~~

<Command> -ErrorAction <Action>

~~~

The <span class="mono"><Action></span> specifies what PowerShell should do when it encounters an error. Let’s look at the available options: <br />

| Action            | Behavior                                                              |
|-------------------|-----------------------------------------------------------------------|
| Continue          | Display the error (default behavior) and continue script execution.   |
| SilentlyContinue  | Suppress the error message and continue script execution.  |
| Stop              | Stop script execution and throw a terminating error.  |
| Inquire           | Prompt the user for action (e.g., continue, stop, or ignore). |
| Ignore            | Suppress the error without logging it to $Error.    |


**ErrorAction in** ***Action*** <br />

Let’s see how <span class="mono">ErrorAction</span> works using a simple example. <br />

Imagine you’re trying to retrieve a *non-existent* file: <br />

~~~
Get-Item -Path "C:\NonExistentFile.txt"

~~~

By default, this cmdlet will throw an error, but your script will keep running. Now, let’s use ErrorAction to change this behavior:

1.	<b>Suppress** the Error (<span class="mono">SilentlyContinue</span>): <br />

~~~
Get-Item -Path "C:\NonExistentFile.txt" -ErrorAction SilentlyContinue
Write-Output "Command completed without displaying an error."

~~~

In this case, the error is ignored, and no message appears. <br />

2.	Stop the Script on Error (<span class="mono">Stop</span>): <br />

~~~
Get-Item -Path "C:\NonExistentFile.txt" -ErrorAction Stop
Write-Output "This line will not run if an error occurs."

~~~

Here, the script execution stops immediately, and the message after the command is never executed.<br />

3.	Prompt for Action (<span class="mono">Inquire</span>): <br />

~~~
Get-Item -Path "C:\NonExistentFile.txt" -ErrorAction Inquire

~~~

You’ll see a prompt asking how you’d like to proceed: </br >

~~~
Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):

~~~

**Global ErrorActionPreference**

While <span class="mono">-ErrorAction</span> controls error handling at the cmdlet level, you can also set a global preference for error handling using the <span class="mono">$ErrorActionPreference</span> variable. <br />

Here’s how you set it: <br />

~~~
$ErrorActionPreference = "Stop"

~~~

Once set, all cmdlets in the script or session will default to this error behavior unless overridden with a specific <span class="mono">-ErrorAction</span> parameter.<br />

For example: <br />

~~~
$ErrorActionPreference = "SilentlyContinue"
Get-Item -Path "C:\NonExistentFile.txt"
Write-Output "No error displayed because of global preference."

~~~

**Important**: Use this carefully in scripts, as it changes the behavior globally and can have unintended consequences.

<b>Capturing and Handling Errors with <span class="mono">Try-Catch</span></b> <br />

While <span class="mono">ErrorAction</span> is useful for basic scenarios, you often need more advanced error handling. This is where the <span class="mono">try-catch</span> block comes in. <br />

When you use <span class="mono">-ErrorAction Stop</span> with a <span class="mono">try</span> block, PowerShell converts non-terminating errors into *terminating errors* that can be caught.

Example: <br />

~~~
try {
    Get-Item -Path "C:\NonExistentFile.txt" -ErrorAction Stop
}
catch {
    Write-Warning "An error occurred: $_"
}

~~~

In this example:<br />
•	If <span class="mono">Get-Item</span> fails, the error is caught in the catch block.
•	The <span class="mono">$_</span> variable contains the error details.

**Best Practices for Error Handling**
1.	<b>Always Handle Critical Errors</b>: Use  <span class="mono">-ErrorAction Stop</span> and  <span class="mono">try-catch</span> to ensure critical errors don’t go unnoticed.
2.	<b>Be Selective with</b>  <span class="mono">SilentlyContinue</span>: Suppressing errors is fine for non-critical commands but can hide real issues.
3.	<b>Set Global Preferences Wisely</b>: Only modify  <span class="mono">$ErrorActionPreference</span> when absolutely necessary, and reset it afterward.
4.	**Log Errors**: Use catch blocks to log errors for debugging or reporting purposes.

Example with logging: <br />

~~~
try {
    Get-Item -Path "C:\NonExistentFile.txt" -ErrorAction Stop
}
catch {
    Write-Error "Error encountered: $($_.Exception.Message)"
    Add-Content -Path "C:\ErrorLog.txt" -Value "Error: $($_.Exception.Message) - $(Get-Date)"
}

~~~

**When *Not* to Use Error Handling**

While error handling is a best practice, there are cases where it may be overkill:
•	**Ad-Hoc Scripts**: For quick one-liners or tests, error handling might slow you down.
•	**Non-Critical Operations**: If an error doesn’t impact the script’s success, letting it display is fine.

### Takeaways...

By mastering <span class="mono">ErrorAction</span> and combining it with advanced error handling techniques like <span class="mono">try-catch</span>, you can write more robust and predictable PowerShell scripts. Errors are inevitable, but how you handle them can make the difference between a script that crashes and one that recovers gracefully. <br />

Start incorporating these techniques into your scripts today—your future self will appreciate the added reliability! 🚀


```  <-- starting code fence
code goes here
```  <-- ending code fence