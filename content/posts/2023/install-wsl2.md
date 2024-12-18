+++
date = '2023-11-28T23:14:51-06:00'
draft = false
title = 'Installing WSL2 on Windows 11'
type = 'post'
tags = ["tech", "devops", "enterprise-it", "windows", "linux", "powershell"]
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


**Select *Start menu***
Type <span class="mono">cmd.exe</span> in Search
Right-click & select "**Run as *Administrator***"

>``` wsl.exe --install ```

Installs the Ubuntu distribution and WSL on the device. <br />

Remember you must also install Hyper-V Service (WSL.exe doesn't do it) <br />

In the same elevated (as Administrator) Cmd prompt:

>```DISM /Online /Enable-Feature /All /FeatureName:Microsoft-Hyper-V```

Or the same can be done in an Elevated PowerShell session:

>```Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All```

REMINDER: You must also have the following enabled in your computer's BIOS: <br />

*	Enable Hardware Virtualization.
*	Enable Nested Virtualization.
*	Turn on Virtual Machine Platform

Once all of the above is down, we're ready to proceed! <br />

Now it is time to install a Linux Distro (WSL2 tries to install Ubuntu default)

>```wsl --list --online ```

lists all available Linux distributions that you may install using the wsl command. Currently, these are: <br />

|Syntax 	| Description |
|:----------|:------------|
| Ubuntu	| Ubuntu
| Debian	| Debian GNU/Linux
|kali-linux | Kali Linux Rollin
|openSUSE-42| openSUSE Leap 42
|SLES-12 SUSE| Linux Enterprise Server v12
|Ubuntu-16.04| Ubuntu 16.04 LTS
|Ubuntu-18.04| Ubuntu 18.04 LTS
|Ubuntu-20.04| Ubuntu 20.04 LTS

>```wsl --install -d <DistroName>```

installs the selected distribution. Replace <DistroName> with the name of the distribution. Can be used to install additional distributions as well.

>```wsl --update```

updates the WSL Linux kernel manually.

>```wsl --update rollback```

Rolls back to the previous WSL kernel version.

>```wsl --status```

Displays general information about the status of the Windows Subsystem for Linux installation.

>```wsl --help```

Displays the list of command parameters.

**List installed Distros:**

>```wsl -l -v```

Type the following command to set a distro as the new default and press *Enter*:

>```wsl --unregister DISTRO-NAME```

>```wsl --unregister Ubuntu```

***Remove* a Distro**

>```winget uninstall --id "DISTRO-ID-NAME"```

For example, this command *removes* the Ubuntu distro:

>```winget uninstall --id Canonical.Ubuntu```
