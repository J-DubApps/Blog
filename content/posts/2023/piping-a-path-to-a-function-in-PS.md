+++
date = '2023-06-15T23:14:51-06:00'
draft = false
title = 'Piping A File Path to a Function in PSl'
type = 'post'
tags = ["tech", "powershell", "code", "best-practice", "devops"]
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

