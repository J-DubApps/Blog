+++
date = '2022-06-20T23:17:51-06:00'
draft = false
title = 'Writing Resusable Code: PS Function Tips'
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

Creating functions is among the most frequent tasks you will run into when working in PowerShell long enough. PS functions serve a fundamental role, as a component to help us organize and encapsulate our code, and reuse it. Without functions scripts would become overly complex, cluttered with numerous <span class="mono">if/else</span> statements or loops and repetitive code segments.<br />

By using functions, we bundle our PowerShell logic into manageable units that can be invoked as needed. They allow us to pass parameters to modify their behavior and promote code reuse. To me, code reuse is EVERYTHING in every coding lang, adhering to the DRY (<a href="https://en.wikipedia.org/wiki/Don%27t_repeat_yourself">Don’t Repeat Yourself) principle</a>.<br />

<b>So here are a couple of tips I want to share for writing functions in PowerShell.</b>  <br />

### Use PS Naming Convensions <br />

You should name your functions by what <i>action</i> they are doing + the <i>thing</i> involved, aka the <span class="mono">verb-noun</span> syntax that PowerShell commands have always used. Go ahead and issue the <span class="mono">get-verb</span> command in a PS session, to see the list of approved verbs (actions) that I am talking about.  I use this command all the time when I start banging out a quick function.<br />

Consistency is king when writing supportable scripts and functions. So use what PowerShell gives us to maintain consistency and readability.  When I see a function named <span class="mono">Function IPAddress-Display</span>I cringe.  To display or report something, I would tell that person to immediate rewrite it using the <span class="mono">Get-</span> verb. <br />

Equally important, are if the verb's action is reading/writing something.  Use <span class="mono">Get-</span> for reading something in to Display, or later act on.  And use <span class="mono">Set-</span> when <i>changing</i> data or <i>writing</i>making any kind of change.  Especially if your function is making some kind of system change. <br /> 

If you remember nothing else from this blogpost, just remember using PowerShell's <span class="mono">verb-noun</span> naming standard for your functions (and script names, too) will save yourself and your colleagues problems in the future.  <br />

### Keep your functions Singular in purpose, and Self-Contained <br />

What I mean here is:

- A function in PowerShell should do only <i>one thing</i> (and one thing <i>only</i>) and do it well.
- A function in PS should be modular, or self-contained.<br> 
A good self-contained function will have: well-defined input parameters, produces output, and doesn’t rely on external variables to work.<br /> 

Below is a an example I threw together, to illustrate:

~~~  
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
 
 # Example usage:
 # Get-FormattedDate -InputDate (Get-Date) -DateFormat "MM/dd/yyyy"
~~~

This PS function is doing <i>one single thing</i>, formatting the date in Output, and the logic and error-handling is done completely within the function itself.<br /> 

A quick & dirty function, often might not do this is, instead:

~~~
    function FormatDate {
    # Relies on a global variable
    $FormattedDate = $Global:Date.ToString("yyyy-MM-dd")
    Write-Output $FormattedDate
 }
~~~

...and that is technically <i>okay</i>, but isn't necessarily testable and relies on external state to populate a variable.  Again, nothing wrong with that but it may not scale for reuse or future needs, being written that way. Also, it's harder to know what a basic function like this is needed for or reads clearly for anyone else maintaining your code. 😉

### Don't sleep on -WhatIf and -Confirm

Did you know that you can use <span class="mono">-Confirm</span> and <span class="mono">-WhatIf</span> switches, for dry runs and testing of your functions? Just as you might in a one-liner in a PowerShell session, you can use -WhatIf to see what your function might <i>do</i>, without actually <i>doing it</i>.

Note: using <span class="mono">-Confirm</span> and <span class="mono">-WhatIf</span> switches only works when writing <i><b>advanced functions</b></i> that use <span class="mono">-WhatIfSupportsShouldProcess</span> argument.  So let's talk about advanced functions next.

### Advanced functions

PowerShell offers a great array of features that you can leverage in your functions, almost effortlessly if you write them as <i>advanced functions</i>. <br /> 

One advanced function I like to use is if I am doing something destructive to data within an interactive script. As I mentioned above, I can use the <span class="mono">SupportsShouldProcess</span> and <span class="mono">ConfirmImpact</span> params, so that I can then use <span class="mono">-WhatIf</span> or <span class="mono">-Confirm</span> switches when calling a function:

~~~
function Remove-SampleFile {
    [CmdletBinding(SupportsShouldProcess = $true, ConfirmImpact = 'High')]
    param (
        [Parameter(Mandatory)]
        [string]$Path
    )

    process {
        if (-Not (Test-Path -Path $Path)) {
            Write-Warning "The file '$Path' does not exist."
            return
        }

        # SupportsShouldProcess enables the use of -Confirm
        if ($PSCmdlet.ShouldProcess($Path, "Delete the file")) {
            try {
                Remove-Item -Path $Path -Force
                Write-Host "File '$Path' deleted successfully." -ForegroundColor Green
            } catch {
                Write-Error "Failed to delete the file. Error: $_"
            }
        }
    }
  }

# Example usage:
# Remove-SampleFile -Path "C:\Temp\example.txt" -Confirm
~~~

In addition to parameters and using arguments like <span class="mono">SupportsShouldProcess</span> to enable <span class="mono">-WhatIf</span> capabilities in functions, you can also another one-liner tool in functions: <a href="https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_pipelines?view=powershell-7.4">Piplines</a> are another tool and technique you can use in advanced PS functions.<br />

Pipelines in PowerShell advanced functions enable seamless chaining of commands in your scripts, much like they do in interactive PS Sessions. This allows a cmdlet's output to feed directly into a function, without the need for intermediate variables or complex data handling. This approach simplifies scripts by promoting modularity, reducing code clutter, and making complex tasks more readable and maintainable.  Here's an example:

~~~
function Get-Example {
    [CmdletBinding()]
    param(
        [Parameter(ValueFromPipeline=$true)]
        [string]$Name
    )

    Begin {
        # Set up any required resources before processing
    }

    Process {
        # Process each pipeline input object (in this case, each $Name)
        "Hello, $Name!"
    }

    End {
        # Cleanup or finalize any processing if needed
    }
}

# Usage:
"Server1","Server2" | Get-Example
~~~

In the example above, each input string (Server1 and Server2) is passed directly to <span class="mono">Get-Example</span> function through the pipeline. The Process block runs once for each item, simplifying how you handle individual objects. This approach enables your advanced functions to integrate smoothly into larger scripts, toolchains, and DevOps workflows.<br />

Here's a good link you can refer to on <a href="https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-7.4&viewFallbackFrom=powershell-6">Advanced parameters in PowerShell</a>, but there are a ton of write-ups out to help.<br />

I hope this helped you consider ways to simplify your code, even if PS function writing is still an advanced topic for you.  Essentially observing the <a href="https://en.wikipedia.org/wiki/Don%27t_repeat_yourself">DRY principle</a> will lead you to want to get better at writing functions, and having clean readable code.  Happy coding!  
