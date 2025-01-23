+++
date = '2024-09-12T14:14:51-06:00'
draft = true
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

Welcome back! [**In my previous post**](https://julianwest.me/Blog/ps-dev-on-windows/), I walked you through how to set up a modern **PowerShell** development environment on Windows with **VS Code**. Now we're going to give [macOS](https://en.wikipedia.org/wiki/MacOS) the same treatment. If you’re a cross-platform PowerShell engineer like myself—or just curious how the setup differs on a Mac—this basic starter guide is for *you*.<br />  

Similar to my previous post, the path will be --> installing PowerShell Core, getting VS Code ready, and customizing your environment.  We'll also be tuning your Mac for a smooth PowerShell experience.  ***Buuuuut FIRST***... <br />

## Why PowerShell on Mac?

**PowerShell isn’t just for Windows anymore**, not for 6 years now: Microsoft open-sourced the engine awhile back, making it cross-platform: Windows, macOS, and yes Linux are all able to run the same [**PowerShell Core**](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell?view=powershell-7.4). For those who like to keep the same workflow across multiple OSes, this was *game-changing*.  With a uniform scripting language: you can automate tasks, manage cloud services, and more—no matter which machine you’re on (*almost* -- there *are* a tiny few PowerShell Core commands that are still Windows-only, and I'll list those at the end of this tutorial -- but they are very *few*).  ***Another reason*** to be familiar with PS scripting on Mac is that a *lot* of SEs and DevOps people are multi-platform these days, like *yours-truly*.  I live in Windows ARM *all the time now*, running on my Macbook Pro. While I am using several Wintel laptops (*and* servers) in my daily DevOps project work, **I'd wager the past three years of my scripts on [my GitHub](https://github.com/J-DubApps) were all written on Mac** (same for my blog posts, and most of my [markdown](https://en.wikipedia.org/wiki/Markdown) document editing). <br />

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

A .zip file download will complete, and extract the actual "Visual Studio Code.app" file.  You will then simply click-drag this file into your Applications folder:

<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/VSCode-Downloads.jpeg" alt="Alt text" width="400" height="215">
</div>

From here you can launch VS Code and pin it to your Dock:

<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/VSCode-on-macOS-Dock.jpeg" alt="Alt text" width="400" height="215">
</div>

## VS Code PowerShell Extension / Tweaking macOS Config

With VS Code launched for the first time, it should look something like this: 

<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/vscode_launch_macos.jpeg" alt="Alt text" width="400" height="215">
</div>

At this point I want to refer you to Microsoft's well-done <a href="https://code.visualstudio.com/docs/getstarted/userinterface">VS Code UI walkthrough</a>.  Go through that before we move on, I'll be right here when you get back.  <br /> 

With VS Code installed, let’s add the official PowerShell extension:

- Click on the *Extensions* icon in the left sidebar (or press ⇧⌘X), and Search for “PowerShell”:

<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/vscode-ps-extension-macos.jpeg" alt="Alt text" width="600" height="415">
</div>

Click the blue Install button, and then Enable the extension afterward.  <br />

This extension will be your Swiss Army Knife for PowerShell development—syntax highlighting, debugging, IntelliSense, integrated console, and so on. <br />

**While the Windows and Mac workflows are similar, there are a *few* macOS-specific tweaks you might find helpful**:

a) Configure the Integrated Terminal

By default, VS Code might still open bash/zsh in its integrated terminal. To open PowerShell in the integrated terminal:
	1.	Open the Command Palette (⇧⌘P) and type “Terminal: Select Default Profile”.
	2.	Choose PowerShell from the dropdown (if you don’t see it, make sure pwsh is on your PATH).
	3.	Close and re-open the integrated terminal (or reload VS Code) to confirm it’s now running PowerShell.

b) Execution Policy on Mac

macOS has fewer restrictions on script execution than Windows, but you may still want to tweak the execution policy to match your security requirements.

7. Working with PowerShell on macOS
<br />

```
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```>



Hit <span class="mono">Ctrl+N</span> to start a new tab, and VS Code immediate starts a new window for coding -- notice it wants you to select the language you'll be working with.  I almost *never* do that, as VS Code can 99% of the time autodetect whatever language you're working with once you get going.  But in the empty window here, feel free to select PowerShell in advance, if you want. <br />

The first VS Code tip I always share, at this piint, is remember <span class="mono">Ctrl+=</span> and <span class="mono">Ctrl+-</span> commands for zooming in and out your active window.  Depending on the size of your screen, zooming in and out becomes your "*go-to*" for efficiently srolling through readable window content, making screen contents larger/smaller when diving into PS code.  <br />

Ok next we need to install <a href="https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell">the PowerShell VS Code Extension</a>, which you can do easily by clicking on the lowest item in the left horizontal menu, circled in the screen shot below.  Then search powershell, and click the Install button to add the PowerShell extension.  <br />

<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/vscode-ps-extension.jpeg" alt="Alt text" width="600" height="415">
</div>

Now that the VS Code PS Extension is installed, let's toss an old go-to PS cmd into your new and empty tab which you created a minute ago: <br />

<span class="mono">Get-Process</span> <br />

Assuming you installed PowerShell 7 earlier, with the PS extension installed you're seeing two things: 

1. the text colors in your new tab have changec, as VS Code now can highlight and color the PS command in the active tab.
2. A PowerShell terminal window is opened in VS Code.

<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/vs-code-ps-terminal.jpeg" alt="Alt text" width="500" height="315">
</div>

This integrated PS shell in VS Code is a Godsend because you never have to leave the editor to test snippets and scripts. <br />

Save your open tab somewhere, call the file "**get-process-test.ps1**".  Now come back to your tab, now named ***get-process-test.ps1***.  Hit the <b><span class="mono">F5</span></b> key.  <br />

***BOOM!*** you just executed and tested your first PS script in VS Code! 

<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/vs-code-ps-terminal.jpeg" alt="Alt text" width="500" height="315">
</div>

And that's it for a basic new PowerShell Dev setup for a Windows PC.  You'll never need to run PowerShell ISE (*Yuck*!) ever again.  <br /> 

There is lots more to discover and tweak, and I didn't get into the next logical progression: additionl extension, leveraging Git /GitHub Repos, and creating modules (to name a few things that you may progress into, in time...).  But if there is any interest in more advanced tutorials, I am happy to do some follow-ups building upon this one.   In fact, I am already drafting a follow-up for running VS Code on ***MacOS*** for PS development.  I do 85% of my PS development on a MacBook Pro & Mac Studio with PowerShell 7 installed on them (and I test my Windows-specific scripts in a Parallels Windows ARM Virtual Machine, on both of them).  So I will give equal time here, soon, for Mac admins who manage Windows servers and endpoints on-the-daily.  <br /> 

Maybe I will do a Neovim tutorial in the near future, too.  I use it for some PS dev, but mostly for collaborative python and javascript stuff on GitHub.  One cool thing about vim editors and VS Code: <a href="https://marketplace.visualstudio.com/items?itemName=vscodevim.vim">you can make VSCode offer vim nav</a> as well. <br />

I hope this was helpful, if it was drop me a line to let me know.  Happy scripting!