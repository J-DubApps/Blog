+++
date = '2021-08-15T23:14:51-06:00'
draft = false
title = 'PowerShell ErrorAction and Error Handling'
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

Errors are inevitable when writing PowerShell scripts. Whether it’s a missing file, a failed command, or an unexpected input, handling errors effectively ensures that your script can recover gracefully or at least fail cleanly with a meaningful message.<br />

PowerShell provides built-in tools for handling errors, the most useful of which is the <span class="mono">ErrorAction</span> parameter. By mastering this parameter and a few related techniques, you can gain better control over how your scripts behave when something goes wrong.<br />

Let’s explore how ErrorAction works and how you can use it to improve your PowerShell scripts. <br />

### Understanding ErrorAction

Most PowerShell cmdlets and functions include an <span class="mono">-ErrorAction</span> parameter that determines how they respond to errors. Instead of silently failing or showing an ugly red error message, you can choose from a range of options to control their behavior. <br />

Here’s the basic syntax: <br />

~~~

<Command> -ErrorAction <Action>

~~~

The <span class="mono">Action</span> specifies what PowerShell should do when it encounters an error. Let’s look at the available options: <br />

| Action            | Behavior                                                              |
|-------------------|-----------------------------------------------------------------------|
| Continue          | Display the error (default behavior) and continue script execution.   |
| SilentlyContinue  | Suppress the error message and continue script execution.  |
| Stop              | Stop script execution and throw a terminating error.  |
| Inquire           | Prompt the user for action (e.g., continue, stop, or ignore). |
| Ignore            | Suppress the error without logging it to $Error.    |


**ErrorAction in** ***Action*** <br />
