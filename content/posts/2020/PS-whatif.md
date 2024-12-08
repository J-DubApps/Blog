+++
date = '2020-04-20T23:17:51-06:00'
draft = false
title = 'PowerShell -WhatIf and -Confirm Switches: A Net for Newbies'
type = 'post'
tags = ["tech", "powershell", "code", "fundamentals", "best-practice"]
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

Here's one that came up at work, and I thought I would put here on the blog for co-workers and other IT friends who might just be getting into PowerShell.<br />

So I have been working to slowly encourage my collagues to develop ways to automate routine tasks, and build-up their PowerShell scripting skills. I believe PS skills are essential for any IT worker.  And PS should leveraged by everyone in any IT group from a Service Desk, to Technicians, right on up through Systems Admins and Ops teams. But these days, the most contact my colleagues seem to have with PowerShell is just basic CLI sessions to connect to our Office 365 tenant, to run one-liner commands during user-administration, etc. <br />  

In pressing my team to devlop some basic scripting experience, for automating mundane tasks, I could see they were repeatedly trying to recreate testing conditions, and struggling.  There was a bit of fear and hesitancy of "breaking something" associated with deploying their scripts. I could tell some on my team were not yet aware of the <span class="mono">-Confirm</span> and <span class="mono">-WhatIf</span> switches available to them. So I sent them this example, to introduce a little more confidence:


<div class="code-block">
Get-ChildItem -Path C:\Temp\CSV_Files\ -File *.csv -Recurse | Remove-Item -WhatIf
</div>

In the above one-liner I provided to my team, you can see that <span class="mono">-WhatIf<span> allows you to quickly see what the <span class="mono">Remove-Item</span> action would have <i>done</i>, if they hadn't provided the <span class="mono">-WhatIf</span> switch.<br /> This allowed my team to quickly build confidence in testing: you needn't feel like you are taking risks, just use <span class="mono">-WhatIf<span>.<br />  

And it's a similar story with the <span class="mono">-Confirm</span> switch: <br />
<div class="code-block">
Get-ChildItem -Path C:\Temp\CSV_Files\ -File *.csv -Recurse | Remove-Item -Confirm
</div>

It makes PowerShell pause before <i>each</i> and <i>every</i> action, interactively prompting you asking to <b>confirm</b> an action before moving to the very next line to execute. Very useful, and for the newbie it builds confidence. <br />

Hope this was helpful to anyone beginning their PowerShell scripting journey!