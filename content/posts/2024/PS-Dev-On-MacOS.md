+++
date = '2024-09-12T14:14:51-06:00'
draft = false
title = 'Setting up VSCode for PowerShell Work - MacOS'
type = 'post'
tags = ["tech", "powershell", "devops", "microsoft", "code", "apple", "beginner-fundamentals", "enterprise-it", "best-of", "walk-thru"]
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

Welcome back! [**In my previous post**](https://julianwest.me/Blog/ps-dev-on-windows/) I walked you through how to set up a modern **PowerShell** development environment on Windows with **VS Code**. Now we're doing again, giving [macOS](https://en.wikipedia.org/wiki/MacOS) the same treatment. If you’re a cross-platform PowerShell engineer like myself—or just curious how the setup differs on a Mac—this basic starter guide is for *you*.<br />  

Similar to my previous post, the path will be --> installing PowerShell Core, getting VS Code ready, and customizing your environment.  We'll also be tuning your Mac for a smooth PowerShell experience.  ***Buuuuut FIRST***... <br />

## *Why PowerShell on Mac*?

**PowerShell isn’t just for Windows anymore**, not for 6 years now: Microsoft open-sourced the engine awhile back, making it cross-platform. Windows, macOS, and Linux are all able to run the same [**PowerShell Core**](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell?view=powershell-7.4). For those who like to keep the same workflow across multiple OSes, this was *game-changing*.  With a uniform scripting language: you can automate tasks, manage cloud services, and more—no matter which machine you’re on (*almost* -- there *are* a tiny few PowerShell Core commands that are still Windows-only, and I'll list those at the end of this tutorial -- but they are very *few*).  ***Another reason*** to be familiar with PS scripting on Mac is that a *lot* of SEs and DevOps people are multi-platform these days, like *yours-truly*.  I live in Windows ARM *all the time now*, running on my Macbook Pro. While I am using several Wintel laptops (*and* servers) in my daily DevOps project work, **I'd wager the past three years of my scripts on [my GitHub](https://github.com/J-DubApps) were all written on Mac** (same for my blog posts, and most of my [markdown](https://en.wikipedia.org/wiki/Markdown) document editing). <br />

## Installing VS Code

**First, let's start with a couple of pre-requisites.** Before we install anything, make sure you have: <br /> 

-	macOS 10.13 or later (High Sierra and above) – You’ll want a reasonably up-to-date Mac. <br />
- [**Homebrew**](https://brew.sh) (Optional but *highly recommended*) – Homebrew is the most popular package manager for macOS. It simplifies installation of many command-line tools, including PowerShell and VS Code. <br />
- Administrator privileges on your Mac (you’ll need to enter your password for certain steps.  PS-if you're on a managed company Mac, contact your Jamf / Intune admins to help you with that). <br />

**Next, we're installing PowerShell Core**. There are several ways to install it on macOS, but ***Homebrew*** is by far the easiest (and my preferred) method. I will show you this way first, and then also share PowerShell direct-download info afterward.  <br /> 

If you don’t already have Homebrew, head to [**brew.sh**](https://brew.sh) to install it-don't worry it's a *quick* install.  You'll be launching [***macOS Terminal***](https://en.wikipedia.org/wiki/Terminal_(macOS)) (**⌘ + spacebar + "terminal" + *return***) BTW, to install **Homebrew**. <br /> 

Once installed (or to just confirm it's already installed) let's get back into the [***macOS Terminal***](https://en.wikipedia.org/wiki/Terminal_(macOS)) (steps again, in case you closed it: **⌘ + spacebar + "terminal" + *return***), and type these commands: <br />

1.  Optional - verify Homebrew by typing: <span class="mono">which brew</span> & ***return*** (or <span class="mono">brew help</span> & ***return***).  Brew should give you the nod... <br />
2.	**Install PowerShell using Homebrew**: <br />

```
brew install --cask powershell 
```

<span style="font-size:smaller">(Depending on Homebrew’s current naming conventions, you might see brew install powershell --cask. Check the [PowerShell GitHub docs](https://github.com/PowerShell/PowerShell) if you run into issues.)</span> <br />

Verify PowerShell installation by typing this in **Terminal**: <br />

```
pwsh --version
```

<span style="font-size:smaller">You should see a version number for PowerShell Core.</span> <br />

As you might guess, launching PowerShell on macOS is --> launching **Terminal** and typing <span class="mono">pwsh</span> + ***return***-which opens a new PowerShell session right there inside your **Terminal**. <br />

***The other method for installing PowerShell Core*** is to just *download* it which can be done [***here***](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-macos?view=powershell-7.4#installation-via-direct-download).

Before we move on to installing VS Code, if you got lost anywhere [**here is some backup**](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-macos?view=powershell-7.4#installation-via-direct-download) straight from the horse's mouth. <br />


**Ok *next* we're installing VS Code** and, as you may have guessed, you have the **Homebrew** option vs direct-download-we'll cover both starting with the former. In **Terminal** (you didn't close it, did you? If so no worries, just do the steps again of: **⌘ + spacebar + "terminal" + *return***) we're going to enter these commands: <br />

```
brew install --cask visual-studio-code
```

And that's it!  Check your Applications folder or Launchpad area, and you'll find VS Code has been installed by Homebrew. <br />

To download [**go here**](https://code.visualstudio.com/download) and choose your Mac's CPU type (Intel or Apple Silicon):


<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/download-vs-code.jpeg" alt="Alt text" width="400" height="215">
</div>

A .zip file download will complete, and auto-extract the actual "Visual Studio Code.app" file in your **Downloads** folder.  Just simply click-drag this file into your Applications folder:

<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/VSCode-Downloads.jpeg" alt="Alt text" width="400" height="215">
</div>

From here you can launch VS Code and pin it to your Dock:

<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/VSCode-on-macOS-Dock.jpeg" alt="Alt text" width="200" height="115">
</div>

## VS Code PowerShell Extension

With VS Code launched for the first time, it should look something like this: 

<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/vscode_launch_macos.jpeg" alt="Alt text" width="500" height="315">
</div>

At this point I want to refer you to Microsoft's well-done <a href="https://code.visualstudio.com/docs/getstarted/userinterface">VS Code UI walkthrough</a>.  Go through that before we move on, I'll be right here when you get back.  <br /> 

With VS Code installed, let’s add the official PowerShell extension:

- Click on the *Extensions* icon in the left sidebar (or press ⇧⌘X), and Search for “PowerShell”:

<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/vscode-ps-extension-macos.jpeg" alt="Alt text" width="600" height="415">
</div>

Click the blue Install button, and then Enable the extension afterward.  <br />

This extension will be your Swiss Army Knife for PowerShell development—syntax highlighting, debugging, IntelliSense, integrated console, and so on. <br />

## Recommended Additional Extensions & Add-Ons

While the core PowerShell extension might be all you strictly need, here are a few more suggestions to supercharge your environment: <br />

•	**PowerShell Preview** – Offers early access to PowerShell extension features. <br />
•	**GitLens** – If you’re working with Git source control, GitLens offers line-by-line blame, advanced diffing, and more. <br />
•	**Pester Test Adapter** – Great optional Extension if you're an intermediate or advanced scripter and your team is using Pester tests in their [CI/CD pipeline](https://en.wikipedia.org/wiki/CI/CD). <br />

One last Extension recommendation, is for any Mac or Linux users who use [vim](https://en.wikipedia.org/wiki/Vim_(text_editor)). You can have a vim-like workflow in VS Code via a [vim exension](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim)!  It lets VS Code offer vim key bindings and workflow, which is pretty slick! <br />

## macOS-Specific Configuration Tweaks

**While the Windows and Mac workflows are similar, there are a *few* macOS-specific tweaks you might find helpful**: <br />

**a) Configure the Integrated Terminal** <br />

By default, VS Code might still open bash/zsh in its integrated terminal. To open PowerShell in the integrated terminal: <br />
1.	Open the Command Palette (⇧⌘P) and type <span class="mono">“Terminal: Select Default Profile”</span>. <br />
2.	Choose PowerShell from the dropdown (if you don’t see it, make sure pwsh is on your PATH). <br />
3.	Close and re-open the integrated terminal (or reload VS Code) to confirm it’s now running PowerShell (***note***: you can easily switch this back if you also do a fair bit of ['nix](https://en.wikipedia.org/wiki/Unix-like) bash scripting). <br />

**b) Execution Policy on Mac** <br />

macOS has fewer restrictions on script execution than Windows, which can present objections from CISOs or SOCs that are not 100% familiar with how PowerShell operates on Macs. To illustrate, inside a PowerShell session issue this command:
```
Get-ExecutionPolicy -List
```
You will notice right away that everything is "*unrestricted*", which is *not* the norm on Windows.  **The thing to *know*, here, is**: on macOS and Linux you *cannot* issue the <span class="mono">"Set-ExecutionPolicy"</span> command in order change PowerShell Core's execution policy.  ***But do not despair***! You and your SOC team might be relieved to know that, when you run <span class="mono">"pwsh"</span> to launch a PowerShell session in Terminal on macOS or Linux, PowerShell already runs in a limited user-context ([user-mode](https://en.wikipedia.org/wiki/User-mode_Linux)).  Just as it does on Windows.  So you're already in a basic secure footing working with PowerShell scripts on Mac when running PowerShell the default way as the logged-in user. <br />

While you *can* run <span class="mono">"sudo pwsh"</span> as the superuser (root), take care as most IT Enterprise security tools (EDR/endpoint protection suites) will alert on this or perhaps even not allow it.  This is because you would be running pwsh with the ability to make privileged system-level changes. So in any corporate IT or DevOps environment where you're using your Mac, it's important to see what the rules of the road are, here.<br />

## Working with PowerShell in VS Code on macOS

Once PowerShell and the VS Code extension are installed, the workflow is pretty much identical to Windows:<br />

1.	Create a new file in VS Code and save it with a .ps1 extension to trigger PowerShell IntelliSense. <br />
2.	Write or paste your script. <br />
3.	Press F5 (or click on the Run/Debug icon on the left) to debug the script with breakpoints, variable watch, etc. <br />

You’ll get the same color-coding, tab completion, and debugging experience you’re used to on Windows—only you’re on macOS!  😉 <br />

**A word on testing your PowerShell scripts that target Windows OS**: on recent Mac models you can generally test *most* of your Windows scripts, by running Windows ARM [Virtual Machine](https://en.wikipedia.org/wiki/Virtual_machine).  For *that* you need to either purchase [Parallels](https://en.wikipedia.org/wiki/Parallels_Desktop_for_Mac)  (*what I use), or go with low-cost/free solutions like [UTM](https://apps.apple.com/us/app/utm-virtual-machines/id1538878817?mt=12) or [VMWare Fusion Pro](https://blogs.vmware.com/teamfusion/2024/05/fusion-pro-now-available-free-for-personal-use.html) (made *free* in late 2024 for non-commercial use). <br />

I can test 85% or more of my Windows-targeting PowerShell scripts right here on my Mac; however, if your environment has a lot of Wintel endpoints to suport-keep a PC around for basic testing as well.  It will save you additional time. 

## Tips & Gotchas for Windows VS Code Users

1.	**Path Differences** <br />
On macOS, the <span class="mono">$HOME</span> directory is typically <span class="mono">/Users/YourName</span>. In scripts that might reference Windows paths (like <span class="mono">C:\Users</span>), you’ll want to adapt them to macOS file paths.<br />

2.	**Case Sensitivity** <br />
macOS file systems can be case-sensitive (depending on your disk format). Keep that in mind for any file references in scripts or module imports.<br />

3.	**Script Signing** <br />
If your organization requires signed scripts, you’ll need to configure a signing certificate that works on macOS. Typically, that’s done via a code-signing certificate from a recognized authority or your internal PKI.<br />

4.	**Auto-Update** <br />
Using Homebrew means you can run <span class="mono">brew upgrade</span> to keep PowerShell and other tools updated. For major PowerShell updates or changes, check the official PowerShell release notes.

5. **Windows *OS-Specific* Cmdlets** <br />
Certain cmdlets aimed at Windows simply won't work withing PowerShell on macOS or Linux (see above, for Virtual Machine tip).  Commands like Get-EventLog, Get-WmiObject, and commands that manage Windows Services (or use AD PS Modules) will not run nativelyh on the cross-platform PowerShell edition. Same for any PS script code that use any Graphical or Windows Shell-specific cmdlets (really *any cmdlets* that depend on Windows‑specific APIs). So I recommend Windows VMs to run those cmdlets, or sync'ing your scripts so you can test on available Wintel PCs (see my note on Git in the next section).  <br />

You *may* be able run some Windows-specific PowerShell cmdlets from your Mac to remote Windows PCs via <span class="mono">Enter-PSSession</span>; *however*, that is a whole other write-up and outside the scope of this tutorial. 😉 <br />

PowerShell Core (the cross-platform edition) preserves a *lot* of compatibility between Windows/macOS/Linux, but some cmdlets just can never work.  Especially many commands from “classic” Windows built-in PowerShell. **So if you're doing a lot of Windows PowerShell scripting development on your Mac, just keep that in mind**! ☺️

## Version Control & Syncing

If you aren’t already, consider using Git for all your PowerShell scripts. Version control is essential for tracking changes, collaborating, and rolling back mistakes.  You don't have to be using [GitHub](https://github.com) or [Azure DevOps](https://azure.microsoft.com/en-us/products/devops), to use source control *locally**; *however*, I *highly-recommend* you (or your company IT/DevOps team) adopt something like GitHub *minimum*, if you haven't yet.  GitHub has has an [Enterprise](https://docs.github.com/en/enterprise-cloud@latest/admin/overview/about-github-for-enterprises) tier/plan and supports private company-only [Repos](https://en.wikipedia.org/wiki/Repository_(version_control).  It's a must for collaborative work, as your team needs a common source-control and Repository to work in. <br />

To install Git on macOS with Homebrew:
```
brew install git
```
...and you can also install GitHub Desktop GUI tool through HomeBrew or direct-download, too.  Here's the Homebrew way: 
```
brew install --cask github
```

**Also remember that VS Code can** [***sync settings***](https://code.visualstudio.com/docs/editor/settings-sync) (like extensions, preferences, and keybindings) across all your devices using Settings Sync. Log into your GitHub or Microsoft account from within VS Code, to enable this feature. <br />

## Wrapping Up

***And there you have it***—your Mac is now a bona fide PowerShell development workstation, powered by VS Code, complete with debugging, IntelliSense, and the convenience of a cross-platform scripting language. 😎  If you’ve followed along from my previous Windows guide, you’ll notice how similar the experience is; Microsoft has done a stellar job keeping PowerShell consistent across platforms.  You could probably follow this guide right now on a Linux machine, and the steps would be similar-except you'd be using a different package manager as Homebrew is a Mac thing *only*. <br />

**Whether you’re scripting out big automation tasks, or simply dabbling in cross-platform command-line tools**, **a Mac + PowerShell + VS Code setup will let you work confidently**. If you have any macOS-specific tweaks or customizations you love, feel free to drop me a line and share your tips, a <br />

I hope this was helpful, if it was please drop me a line to let me know. I welcome feedback, and routinely add corrections / follow-up post from it.  <br /> 

***Happy scripting***!