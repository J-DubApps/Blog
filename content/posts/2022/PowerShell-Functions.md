+++
date = '2022-06-20T23:17:51-06:00'
draft = false
title = 'Writing Good Resusable PowerShell Code'
type = 'post'
tags = ["tech", "powershell", "code"]
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

Creating functions is among the most frequent tasks you will run int, when working with PowerShell long enough. PS Functions serve a fundamental role, as a component that helps us organize and encapsulate our code. Without them, scripts would become overly complex, cluttered with numerous <span class="mono">if/else</span> statements or loops or other repetitive code segments.<br />

By using functions, we bundle our PowerShell logic into manageable units that can be invoked as needed. They allow us to pass parameters to modify their behavior and promote code reuse. To me, code reuse is EVERYTHING in every coding lang, adhering to the DRY (Don’t Repeat Yourself) principle.<br />

<b>So here are some tips I wanna share for writing functions in PowerShell.</b>  Some are even useful when <i>not</i> writing functions!<br />

### Use PS Naming Convensions <br />

You should name your functions by what <i>action</i> they are doing + the <i>thing</i> involved, aka the <span class="mono">verb-noun</span> syntax that PowerShell commands have always used. Go ahead and issue the <span class="mono">get-verb</span> command in a PS session, to see the list of approved verbs (actions) that I am talking about.  I use this command all the time when I start banging out a quick function.<br />

Consistency is king when writing supportable scripts and functions. So use what PowerShell gives us to maintain consistency and readability.  When I see a function named <span class="mono">"Function IPAddress-Display"</span><br />

### Keep your functions Singular in purpose, and keep them Self-Contained <br />

What I mean here is: 

- A function in PowerShell should do only <i>one thing</i> (and one thing <i>only</i>) and do it well.
- A function in PS should be modular, or self-contained, so that it has well-defined input parameters, produces output, and doesn’t rely on external variables unless explicitly passed.  

Below is a code example I just threw together to illustrate:

<div class="code-block">
   
    function Get-FormattedDate {
    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [datetime]$InputDate,

        [Parameter()]
        [string]$DateFormat = "yyyy-MM-dd"
    )

    # Core logic
    try {
        $FormattedDate = $InputDate.ToString($DateFormat)
        return $FormattedDate
    } catch {
        Write-Error "Failed to format date. Error: $_"
    }
 }
 \# Example usage:
 \# Get-FormattedDate -InputDate (Get-Date) -DateFormat "MM/dd/yyyy"
</div>

This PS function is doing one single thing, formatting the date in Output, and the logic and error-handling is done completely within the function itself.<br /> 

A quick & dirty function, often might not do this is usually this instead:<br />

<div class="code-block">

    function FormatDate {
    # Relies on a global variable
    $FormattedDate = $Global:Date.ToString("yyyy-MM-dd")
    Write-Output $FormattedDate
 }

</div>

...and that's okay, but isn't necessarily testable or reads clearly for anyone coming in behind you, to support your code. 😉 <br />

### Don't sleep on -WhatIf and -Confirm

Use <span class="mono">-Confirm</span> and <span class="mono">-WhatIf</span> switches, for dry runs and testing of functions, just as you might in PowerShell CLI sessions.  For a recap let's start with <span class="mono">-WhatIf<span>.  This is you telling PowerShell to show you what your code will do, without actually <i>doing it</i>. Example:<br />

<div class="code-block">
Get-ChildItem -Path C:\Temp\CSV_Files\ -File *.csv -Recurse | Remove-Item -WhatIf
</div>

In the above one-liner, you can see what <span class="mono">Remove-Item</span> would have done if you hadn't provided the <span class="mono">-WhatIf<span> switch.<br />

And you can use the <span class="mono">-Confirm</span> switch to make PowerShell pause before <i>each</i> and <i>every</i> action, interactively prompting you asking to <b>confirm</b> an action, before moving to the very next action.<br />

<div class="code-block">
Get-ChildItem -Path C:\Temp\CSV_Files\ -File *.csv -Recurse | Remove-Item -Confirm
</div>

For PS functions, you can only use <span class="mono">-Confirm</span> and <span class="mono">-WhatIf</span> switches when writing <i><b>advanced functions</b></i> in PowerShell.  So let's talk about advanced functions next.<br />

PowerShell offers a great array of features that you can leverage in your functions, almost effortlessly if you write them as <i>advanced functions</i>.

<a href="https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-7.4&viewFallbackFrom=powershell-6">Advanced parameters in PowerShell</a>