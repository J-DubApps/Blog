+++
date = '2023-06-15T23:14:51-06:00'
draft = false
title = 'Piping File Paths into a PowerShell Function'
type = 'post'
tags = ["tech", "powershell", "code", "best-practice", "devops", "walk-thru"]
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

On the heels of writing about the <span class="mono">join-path</span> cmdlet the other day, I thought I would demonstrate a real-world task that deals with the file path differently.  I saw this <a href="https://4sysops.com/archives/process-file-paths-from-the-pipeline-in-powershell-functions/">in an article on 4SysOps</a> from a few years back, where the author is <i>not</i> using <span class="mono">join-path</span> but instead he uses the <span class="mono">‑LiteralPath</span> parameter to get the same thing done.  <br />

But what's even cooler than that is he demonstrates piping file paths into a PS function, one of the essentials of writing the kinds of devops automation scripts I write on-the-daily.  This is a very handy way to have use a function loaded into your interactive PS CLI session, and point paths to it. Great article, I hope you read it! <br />

In today's example we're going take the PS function from the article (and, again, I highly recommend a read-through of it), and use it to count <i>the lines of text within each file</i> under a specific path.  <br />

Let's have a look at the code <a href="https://4sysops.com/archives/process-file-paths-from-the-pipeline-in-powershell-functions/">from the article</a>:

~~~
function Get-Lines {
    <#
    .SYNOPSIS
    Counts the number of lines in a file.
    #>
    [cmdletbinding(DefaultParameterSetName = 'Path')]
    param(
        [parameter(
            Mandatory,
            ParameterSetName  = 'Path',
            Position = 0,
            ValueFromPipeline,
            ValueFromPipelineByPropertyName
        )]
        [ValidateNotNullOrEmpty()]
        [SupportsWildcards()]
        [string[]]$Path,
        [parameter(
            Mandatory,
            ParameterSetName = 'LiteralPath',
            Position = 0,
            ValueFromPipelineByPropertyName
        )]
        [ValidateNotNullOrEmpty()]
        [Alias('PSPath')]
        [string[]]$LiteralPath
    )
    process {
        # Resolve path(s)
        if ($PSCmdlet.ParameterSetName -eq 'Path') {
            $resolvedPaths = Resolve-Path -Path $Path | Select-Object -ExpandProperty Path
        } elseif ($PSCmdlet.ParameterSetName -eq 'LiteralPath') {
            $resolvedPaths = Resolve-Path -LiteralPath $LiteralPath | Select-Object -ExpandProperty Path
        }
        # Process each item in resolved paths
        foreach ($item in $resolvedPaths) {
            $fileItem = Get-Item -LiteralPath $item
            $content = $fileItem | Get-Content
            [pscustomobject]@{
                Path  = $fileItem.Name
                Lines = $content.Count
            }
        }
    }
}
~~~

So the function has a <span class="mono">foreach</span> loop to get a line count ( <span class="mono">$content.Count</span> ) for each text file processed.  The code is place into the <i>Process</i> part of the function, because this allows you to get repeated runs for every item it receives from the <a href="https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_pipelines?view=powershell-7.4"pipeline</a>. <br />

Let's see this in action.  Say I am within a folder somewhere that has 5 files in it, all text files but with varying file types.  To pipe everything in that folder, all 5 tezt files, into the function -- I need only type:


<span class="mono">C:\Temp> Get-ChildItem | Get-Lines</span><br />

And that would get me:

~~~
Path        Lines
----        -----
[file].txt      6
codel.ps1       8
code2.ps1      48
Filel.txt       4
file2.txt       5
~~~

Let's just focus on line counts for the "File*" text files:

~~~
C:\Temp> Get-Item file* | Get-Lines

Path        Lines
----        -----
Filel.txt       4
file2.txt       5
~~~

Or maybe we can make use of <span class="mono">-LiteralPath</span> to look at one specific file:

~~~
C:\Temp> Get-Item -LiteralPath [file].txt | Get-Lines

Path        Lines
----        -----
[file].txt      5
~~~

Or just go all <i>wildcard</i> for only files ending in **txt** :

~~~
C:\Temp> '*.txt' | Get-Lines

Path        Lines
----        -----
[file] .txt     6
filel.txt       4
file2.txt       5
~~~

So I hope this clever demo of paths and pipelines inside a PowerShell function helps illustrate just how powerful your scripts and CLI sessions can be.  You can be working with data in myriad ways, and automate things to save yourself time.