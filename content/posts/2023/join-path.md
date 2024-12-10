+++
date = '2023-06-10T23:14:51-06:00'
draft = false
title = 'Using Join-Path in PowerShell'
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

In PowerShell, it’s quite common to be working with file paths when you’re reading from (or writing <i>to</i>) files. For many automation scenarios involving PowerShell scripts, that means building / constructing a complete path to whatever file(s) your script will work with. There are several approaches to constructing file paths in a PowerShell script or CLI session, and I want to go over a couple here.<br />

## Using a Hard-Coded String

One of the most straightforward common approaches is to explicitly define the entire file path as a string:

~~~
$filepath = 'C:\pathtofile\mydata.txt'
~~~

However, relying on a fully hard-coded path is not a best practice, and has several drawbacks.  First, notice that this example uses <span class="mono">C:</span> as the starting point, which locks your command or script to Windows. With PowerShell Core 6 and later, we're cross-platform so we should consider how our scripts would behave on macOS or Linux. Presuming your scripts will <b><i>only ever</i></b> run on Windows immediately limits your scripts, and makes it harder to share them with others.

Another big drawback is the use of backslashes <span class="mono">  \ </span> in the path. While backslashes are the standard directory separators on Windows, everything else typically uses forward slashes <span class="mono"> / </span>. Every Unix-like systems out there (macOS and Linux distros) could run your fancy script if you take this into account.  PowerShell often normalizes these separators internally, and Windows itself actually supports the forward slash in some scenarios, but this won’t always hold true.  So for maximum portability, it’s a good habit to use <span class="mono">/</span> when manually building a folder or file path.

Moreover, if you need use a path like <span class="mono">E:\pathtofile\mydata.txt</span> on Windows or similar on other operating systems, consider using environment variables or built-in PowerShell variables.  They offer the greatest flexibility, and in PS Core 6 and onward you get <span class="mono">$IsWindows</span>, <span class="mono">$IsLinux</span>, and <span class="mono">$IsMacOS</span> to tell your code which operating system it's running in. On Windows, <span class="mono">$env:SYSTEMDRIVE</span> returns the system drive (often <span class="mono">C:</span>, but not necessarily). On Unix-like systems, you can default to root <span class="mono">  / </span>. Using PS env variables allows your script to adapt to the operating system dynamically:

~~~
if ($IsWindows) {
    $filepath = "$env:SYSTEMDRIVE/pathtofile/mydata.txt"
} else {
    $filepath = '/pathtofile/mydata.txt'
}
~~~

## Enter: Join-Path

PowerShell provides the <span class="mono">Join-Path</span> cmdlet, which combines multiple path segments into one fully qualified path. This approach is way more robust because <span class="mono">Join-Path</span> automatically picks the appropriate path separator based on the environment. 

For example, the following returns <span class="mono">C:\myfolder</span> on Windows:

~~~
$path = Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'myfolder'
~~~

## Joining Multiple Paths

Sometimes you’ll need to combine more than two path segments. A simplistic way might be:

~~~
$filepath = "$folder1/$folder2/$folder3"
~~~

<b><i>Or</b></i>:

~~~
$filepath = Join-Path -Path $folder11 -ChildPath "$folder2/$folder3"
~~~

<b><i>Or</b></i>, getting really wild and convoluted:

~~~
$filepath = Join-Path -Path $folder1 -ChildPath (Join-Path -Path $folder2 -ChildPath $folder3)
~~~

Yuck! None of these options are particularly clean or easy-to-read. <br />

So let's leverage PS Core capabilities, where the <span class="mono">Join-Path</span> cmdlet offers a parameter called <span class="mono">-AdditionalChildPaths</span>. This parameter accepts an array of string values, allowing you to join multiple path segments in one go:

~~~
$filepath = Join-Path -Path $folder1 -ChildPath $folder2 -AdditionalChildPaths ($folder3, $folder4)
~~~

Cool, huh? This way easier when dealing with multiple paths that you need to join. These parameters also work in a positional manner, so you’re not required to specify parameter names if you prefer a more concise style. While skipping parameter names isn’t typically recommended in PowerShell’s style guidelines, it’s often considered acceptable for commonly used cmdlets like <span class="mono">Join-Path</span>.<br />

## And Now For Some PS & .NET Path-Joining Kung-Fu

One of PowerShell’s strengths is its integration with the .NET framework. Whenever you need more advanced capabilities with file i/o stuff, .NET comes in clutch for PowerShell scripting. Especially if you are needing to do some fancy path building in PS 5.  <br /> 

The method I’ve recently taken to using, for building complex file paths, is using the <span class="mono">[System.IO.Path]</span> class along with its <span class="mono">Combine()</span> method. By leveraging <span class="mono">Combine()</span>, you can feed it multiple path segments at once, eliminating the need for tedious string concatenation. <br />

Using .NET for path building mirrors the behavior of PowerShell Core’s <span class="mono">Join-Path</span> and its <span class="mono">-AdditionalChildPaths</span> parameter, yet it’s still compatible with earlier versions of PowerShell! This method ensures that your script or module remains adaptable and widely portable.

~~~
$filepath = [IO.Path]::Combine($folder1, $folder2, $folder3, $folder4)
~~~

See you along the path... 😉