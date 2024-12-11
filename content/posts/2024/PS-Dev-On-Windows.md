+++
date = '2024-09-10T14:14:51-06:00'
draft = false
title = 'Setting up VSCode for PowerShell Work - Windows'
type = 'post'
tags = ["tech", "powershell", "devops", "microsoft", "code", "windows", "it-fundamentals"]
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

So I have recently seen some co-workers running the Windows built-in (and officially EOL / retired) <a href="https://learn.microsoft.com/en-us/powershell/scripting/windows-powershell/ise/introducing-the-windows-powershell-ise?view=powershell-7.4">PowerShell ISE</a> tool to write their PowerShell scripts. 😬<br />  

In a word: ***YUCK***! Please close that, and let's get you something better... <br />

If you're a nascent PowerShell scripter, you need the best editing setup in place.  One that "gets out of the way" but also offers features for PS devevlopment.  Enter ~~vim~~, ahem, <a href="https://code.visualstudio.com">Visual Studio Code</a>. VS Code is one of the best editors for PowerShell development.  I use it every day, and as a beginner you should start with this fundamental editor for your PS script development.  **In this tutorial** I'll walk you through setting up VS Code on Windows for PS scripting/development.  And then we can explore some features VS Code offers for PowerShell, which make it such a great core scriping IDE. <br />

# Installing VS Code

**First, let's start with a couple of pre-requisites:** <br /> 

You need to be running *at least* the last most-recent release of Windows 10, or (more preferred) a current version of Windows 11, to get anything out of this tutorial.  And, second, you need to have already installed <a href="https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.4">PowerShell 7</a> (or latest PS Core version, if they've moved on to 8x +) onto your machine, at some point.  For any PowerShell dev work you want both one bundled with Windows (5x) *and* PowerShell Core, so follow the link I just shared and install it if you need to.   Now, on with the show... <br />

In my work environment I package/publish VS Code into our CM Software Center and Intune Company Portal, for convenience.  But we're not at work here (well, you may be, but I'm not...) so let's do a fast walk-through of installing it onto your chosen Windows PC. First go here and download for your OS:<br />

<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/download-vs-code.jpeg" alt="Alt text" width="400" height="215">
</div>

Once you download the install bits to your Downloads folder, start the installation and take the defaults: <br />

<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/install-vscode.jpeg" alt="Alt text" width="300" height="165">
</div>

***Note***: if you're on another OS you can follow-along (and I do intend to do a MacOS write-up for PS Dev on that platform, soon) but the rest of this is pretty Windows-centric.

# Tweaking VS Code and Adding PowerShell Extension

Once installation is complete, launch VS Code:

<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/VSCode.jpeg" alt="Alt text" width="400" height="215">
</div>

At this point I want to refer you to Microsoft's well-done <a href="https://code.visualstudio.com/docs/getstarted/userinterface">VS Code UI walkthrough</a>.  Go through that before we move on, I'll be right here when you get back.  <br /> 

Hit <span class="mono">Ctrl+N</span> to start a new tab, and VS Code immediate starts a new window for coding -- notice it wants you to select the language you'll be working with.  I almost *never* do that, as VS Code can 99% of the time autodetect whatever language you're working with once you get going.  But in the empty window here, feel free to select PowerShell in advance, if you want. <br />

The first VS Code tip I always share, at this piint, is remember <span class="mono">Ctrl+=<</span> and <span class="mono">Ctrl+-</span> commands for zooming in and out your active window.  Depending on the size of your screen, zooming in and out becomes your "*go-to*" for efficiently srolling through readable window content, making screen contents larger/smaller when diving into PS code.  <br />

I didn't get into the next logical progression, where PowerShell development may take you: Git, or GitHub Repos, and creating modules (to name a few things).  But if there is any interest, I am happy to do some follow-ups to this tutoral.  I am already drafting follow-up for this post to set up VS Code ***MacOS*** for PS development. A MacBook Pro & Mac Studio are where I do 85% of my PS development these days, so I might as well give equal time there.  Maybe also a Neovim tutorial in the future.  I use it for some PS dev, though mostly I just it for python and javascript stuff.  One cool thing about vim editors and VS Code: <a href="https://marketplace.visualstudio.com/items?itemName=vscodevim.vim">you can make VSCode offer vim nav</a> as well. <br />

Happy scripting & dev journey!