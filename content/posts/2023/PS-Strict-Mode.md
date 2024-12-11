+++
date = '2023-04-15T23:14:51-06:00'
draft = false
title = 'PowerShell Strict Mode'
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

One of PowerShell’s greatest strengths is its forgiving nature when it comes to undeclared variables, out-of-scope references, and questionable coding practices. It will just let you stumble to a working script in short-order, and move on getting a coffee or whatever is on your mond.  <br />

But this flexibilty and forgiveness is also PowerShell's Achilles heel in larger, production-grade environments where the scripts *must.not.fail*. Enter *Strict Mode*, a PowerShell feature that provides a higher level of code quality assurance by enforcing stricter coding rules and surfacing potentially problematic code, long before it results in unexpected behavior in production. <br />

Strict Mode is a feature that helps enforce better coding practices and discourage certain “loose” programming habits in PowerShell. In simple terms, when Strict Mode is enabled, the PowerShell engine becomes *way*, ***way*** less forgiving. Instead of silently allowing certain risky behaviors — like using undeclared variables — it throws terminating errors, forcing you to address issues head-on.<br />

This additional scrutiny makes your code more robust and maintainable. If your PowerShell scripts are part of critical enterprise automation, or if multiple team members contribute to the same codebase, Strict Mode can help identify coding errors early and reduce technical debt over the long term.<br />

Let's play around with Strict Mode.  You can turn it on within a live PS Session or put it at the top of any script, with this command:

<span class="mono"> Set-StrictMode -Version Latest </span><br />

This enables strict mode in your script or PS session, allowing you test your code.  Notice that Strict Mode was set to "<span class="mono">-Version Latest</span>" in my first example: this is because PowerShell has two versions of Strict Mode that you can invoke. You can specify a particular version, like <span class="mono">-Version 2.0</span>, if you need to maintain compatibility or adhere to certain rules:<br />

<span class="mono"> Set-StrictMode -Version 2.0 </span><br />

You can also enable or disable Strict Mode multiple times within the same script. For instance, maybe you have a legacy function that can’t yet be fully updated, to meet Strict Mode criteria.  You could temporarily relax the rules around that specific block of code:

~~~
# Enable strict mode
Set-StrictMode -Version Latest

# Your code that must adhere to strict mode
# ...

# Temporarily disable strict mode
Set-StrictMode -Off

# Legacy code or module calls that may break strict rules
# ...

# Re-enable strict mode again if desired
Set-StrictMode -Version Latest
~~~

If you’re serious about writing resilient, enterprise-grade PowerShell scripts, give Strict Mode a try. Your future self, and your team, will thank you.  Some pointers on best-practices when using Strict Mode: <br />

### Best Practices When Using Strict Mode

1.	**Introduce Strict Mode Early**: Add Set-StrictMode at the top of your scripts to ensure you’re coding against strict rules from the start. This prevents building up technical debt.
2.	**Refactor Gradually**: For existing scripts, enabling Strict Mode may reveal numerous issues at once. Consider enabling it incrementally—start with non-critical scripts or parts of your code and systematically fix errors as they appear.
3.	**Use Consistent Versions**: For a team environment, agree on which Strict Mode version to use and stick to it. This ensures consistent coding practices across your organization’s PowerShell codebase.
4.	**Document Exceptions**: If you need to disable Strict Mode for certain legacy code sections, document the reasons and the target date or conditions under which you plan to fix that code. A comment above that code block explaining why Strict Mode is turned off goes a long way in maintaining transparency and planning future cleanup.

### When *Not* to Use Strict Mode
While Strict Mode is a best practice for production-oriented scripts, there may be scenarios where you might choose not to use it:
	• **Quick One-Liners or Ad-Hoc Queries**: In a hurry to test something in the console? Strict Mode might slow you down unnecessarily.
	• **Working with Legacy Scripts**: If you have a large codebase that hasn’t been maintained for years, enabling Strict Mode might be too disruptive initially. In these cases, fix issues incrementally before turning it on.
	• **Third-Party Modules with Questionable Practices**: Occasionally, Strict Mode may conflict with external modules that don’t adhere to strict rules. If these modules are out of your control, consider carefully applying Strict Mode only to code blocks you own.<br />

Hope this was helpful!  While there may be a learning curve and some initial cleanup when applying Strict Mode to your scripts, the long-term benefits (improved code quality, fewer runtime surprises, and a more maintainable codebase) make it well worth the effort.