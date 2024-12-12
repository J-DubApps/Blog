+++
date = '2021-05-22T23:17:51-06:00'
draft = false
title = 'Log Your Scripts! Pt 2 - Live Use-Case'
type = 'post'
tags = ["tech", "devops", "endpoint-mgmt", "powershell", "code", "beginner-fundamentals", "best-practice"]
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

The other day <a href="http://julianwest.me/Blog/logyourps-scripts/">I posted a quick primer</a> on logging in our PS scripts.  Here I will expand on that, with a use-case example I just wrote code for yesterday. Here is a registry-reading function I bashed together, as but one example of something I needed to accomplish in reading in a setting and logging it.  Thus allowing me to keep a thorough, auditable record of registry changes during an automation task.

## Reading Registry Values and Logging Them

For many automation tasks, you’ll need to retrieve configurations from the Windows Registry. The Get-RegistryValue function allows you to read a specific property from the Registry without cluttering your code. Errors are cleanly handled (returning $false if a value can’t be found), making it easy to integrate error-checking and logging.
~~~
Function Get-RegistryValue($RegPath, $Property) {
    Try {
        $Item = Get-ItemProperty -Path $RegPath -Name $Property -ErrorAction Stop
        $ItemProperty = $Item | Select -ExpandProperty $Property
        Return $ItemProperty
    }
    Catch {
        Return $false
    }
}
 ~~~

And here's a recap of the Writelog function <a href="http://julianwest.me/Blog/logyourps-scripts/">I wrote about the other day</a>:
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

**Example Usage**:

~~~
$SomeValue = Get-RegistryValue 'HKLM:\SOFTWARE\MyApp' 'InstallPath'

If ($SomeValue) {
    WriteLog "Successfully retrieved InstallPath value: $SomeValue"
} Else {
    WriteLog "Failed to retrieve InstallPath from registry."
}
~~~

You should log <i>everything</i> you're reading-in, or changes you're making (files written, etc) during any scheduled or automated run of your PS scripts.  This example shows a combination of <span class="mono">Get-RegistryValue</span> and <i>WriteLog function</i> to demonstrate a use-case, and the benefit becomes obvious once you make this a coding practice: you can retrieve configurations, make decisions based on those values, and log both the successes and failures in a neatly timestamped manner. <br />

Happy scripting...