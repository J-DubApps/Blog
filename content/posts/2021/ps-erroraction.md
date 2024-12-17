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
