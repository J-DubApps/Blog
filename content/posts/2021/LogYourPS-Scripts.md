+++
date = '2021-05-20T23:17:51-06:00'
draft = false
title = 'Log Your Scripts'
type = 'post'
tags = ["tech", "devops", "powershell", "code", "fundamentals", "best-practice"]
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

We're automating so much these days, post-Covid.  It's how we survived, and thrived, as the small IT shop we are. <br />

Automation scripting is a cornerstone of effective IT systems management. Whether you’re applying bulk config changes, querying status or config values across your environment, or simply experimenting with new cmdlets, proper logging ensures that you have a clear record of what happene and when it happened.  Logging is learning.  Logging is life. 😉 <br />

One challenge my team experienced was seeing what their scripts were <i>doing</i>. I was surprised at how none of my colleages' scripts were creating any logging data.  So I threw this together a primer to help them out, and decided to also post this info here. <br />

PowerShell makes it straightforward to keep track of your work by leveraging built-in transcript capabilities and custom logging functions. In this post I will briefly review how to use PowerShell’s <span class="mono">Start-Transcript</span> feature to capture entire console sessions, and then we’ll explore a custom <b>WriteLog</b> function to document scripted processes more granularly. Here we go!<br />

## Why Log?

Before diving into code, it’s worth understanding the importance of logging. Logging provides:<br />
	•	Traceability: Know exactly which commands were executed and when.<br />
	•	Accountability: Provide an audit trail for compliance and troubleshooting.<br />
	•	Debugging Aid: Easily identify what went wrong when a script doesn’t behave as expected.<br />
	•	Documenting Changes: Keep a historical record of environment modifications for reference. <br />

Especially in enterprise environments, maintaining robust logs can save countless hours of guesswork and improve your operational integrity.

## Primer on Start-Transcript

PowerShell’s built-in Start-Transcript and Stop-Transcript cmdlets offer a simple way to record everything that happens in the console. When you run Start-Transcript, PowerShell begins capturing all input and output during your session. When you’re done, Stop-Transcript finalizes the logging and saves the output to the file you specified.<br />

<b>Example</b>: <br />

~~~
# Start transcript with a specified output file
Start-Transcript -Path "C:\Logs\MyPSSession.log"

\# ... run various commands here ...

Stop-Transcript
~~~

Once stopped, you have a neat record of every command entered and response returned during that session. This approach is perfect for one-off sessions or documenting the execution of a large script that you run interactively. <br />

___However___, when creating highly automated, unattended scripts, you may want more structured control over what gets logged. That’s where a custom logging function can be invaluable.<br />

~~~
Function WriteLog($LogString) {
    ##########################################################################
    ## Writes a timestamped entry to a log file defined by $LogFile variable
    ##########################################################################

    $Stamp = (Get-Date).ToString("yyyy/MM/dd HH:mm:ss")
    $LogMessage = "$Stamp $LogString"
    Add-Content $LogFile -Value $LogMessage
}
~~~

**How It Works**: <br />

1.  Timestamping: The function prefixes each message with a date/time stamp for clear sequencing.<br />
2.  Custom Messages: You have fine control over what gets logged. You can log progress, error messages, or summary statements at key points.<br />
3.  Predefined Log File Variable: By setting $LogFile before you call WriteLog, you control the output location without modifying the function itself each time.

**Example Usage**: <br />

~~~
# Define where you want your log
$LogFile = "C:\Logs\MyScriptActions.log"

WriteLog "Starting configuration tasks..."
\# Run some complex script actions here
WriteLog "Configuration tasks completed successfully."
~~~

When you inspect MyScriptActions.log, you’ll see entries like: <br />

~~~
2024/12/09 09:15:00 Starting configuration tasks...
2024/12/09 09:16:10 Configuration tasks completed successfully. 
~~~

This selective approach to logging is particularly useful in automation scripts, where every executed step can be logged methodically. <br />

## Best Practices for Logging in Your Scripts

1. Use Consistent, Centralized Logs:<br />
Keep logs in a known, consistent directory structure. Consider naming logs by date or by the script that generated them for quick reference.<br />
2. Log Important Steps and Results:<br />
Don’t flood your logs with every tiny detail—log the big steps, decision points, errors, and completion states. Your logs should tell a story of what your script did, not overwhelm you with noise.<br />
3. Secure Your Logs:<br />
Logs can contain sensitive information. Ensure that the directories storing them have appropriate file system permissions. In some cases, consider encrypting or obfuscating sensitive data.<br />
4. Periodically Review and Rotate Logs:<br />
Large logs become unmanageable. Consider archiving old logs and rotating them monthly or after a certain size threshold.<br />

## Putting It All Together

A robust logging approach might look like this:<br /><br />
	1.	Begin Transcript for Full Visibility:<br />
Use <span class="mono">Start-Transcript</span> at the start of an interactive session or a run-once script to capture a full record.<br />
	2.	Use WriteLog in Your Script Logic:<br />
Throughout your script, insert calls to WriteLog to highlight key steps, confirm registry values read, and record errors or decisions.<br />
	3.	Stop Transcript at the End (If Applicable):<br />
When the script is done, run <span class="mono">Stop-Transcript</span> to finalize your console-based logging.<br />

By combining these techniques, you get both broad-stroke session logging and fine-grained, contextual logging of critical actions. Whether you’re troubleshooting an issue or proving compliance with your organization’s policies, these logs become invaluable assets.<br />

Effective logging is a fundamental practice for anyone running scripts in a production environment. With PowerShell’s native transcript tools and the flexible WriteLog function I share above, you can create robust and meaningful logs that help you maintain control, compliance, and peace of mind in your automated operations. Have fun building transparent, well-documented workflows in PowerShell!