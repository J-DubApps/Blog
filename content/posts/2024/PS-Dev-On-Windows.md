+++
date = '2024-09-10T14:14:51-06:00'
draft = false
title = 'Setting up VSCode for PowerShell Work - Windows'
type = 'post'
tags = ["tech", "powershell", "devops", "microsoft", "code", "windows", "it-fundamentals"]
+++

So I have seen some co-workers of late using the Windows built-in (and officially EOL / retired, but still bundled) <a href="https://learn.microsoft.com/en-us/powershell/scripting/windows-powershell/ise/introducing-the-windows-powershell-ise?view=powershell-7.4">PowerShell ISE</a> tool to write their scripts. 😬<br />  

In a word: ***YUCK***!  <br />

If you're a nascent PowerShell scripter, you need the best editing setup in place.  One that "gets out of the way" but also offers features for PS devevlopment.  Enter ~~vim~~, ahem, <a href="https://code.visualstudio.com">Visual Studio Code</a>. VS Code is one of the best editors for PowerShell development.  I use it every day, and as a beginner you should start with this fundamental editor for your PS script development.  **In this tutorial** I'll walk you through setting up VS Code on Windows for PS scripting/development.  And then we can explore some features VS Code offers for PowerShell, which make it such a great core scriping IDE. <br />

**First, let's start with a couple of pre-requisites:** <br /> 

You need to be running *at least* the last most-recent release of Windows 10, or (more preferred) a current version of Windows 11, to get anything out of this tutorial.  And, second, you need to have already installed <a href="https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.4">PowerShell 7</a> (or latest PS Core version, if they've moved on to 8x +) onto your machine, at some point.  For any PowerShell dev work you want both one bundled with Windows (5x) *and* PowerShell Core, so follow the link I just shared and install it if you need to.   Now, on with the show... <br />

In my work environment I package/publish VS Code into our CM Software Center and Intune Company Portal, for convenience.  But we're not at work here (well, you may be, but I'm not...) so let's do a fast walk-through of installing it onto your chosen Windows PC. First go here and download for your OS:<br />

<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/download-vs-code.jpeg" alt="Alt text" width="400" height="215">
</div>

***Note***: you can follow-along here on a Mac or Linux and I do intend to do a MacOS write-up on PS Dev on that platform, but the rest of this is pretty Windows-centric.

I didn't get into the next logical progression, where PowerShell development may take you: Git, or GitHub Repos, and creating modules (to name a few things).  But if there is any interest, I am happy to do some follow-ups to this tutoral.  I am already drafting follow-up for this post to set up VS Code ***MacOS*** for PS development. A MacBook Pro & Mac Studio are where I do 85% of my PS development these days, so I might as well give equal time there.  Maybe also a Neovim tutorial in the future.  I use it for some PS dev, though mostly I just it for python and javascript stuff.  One cool thing about vim editors and VS Code: <a href="https://marketplace.visualstudio.com/items?itemName=vscodevim.vim">you can make VSCode offer vim nav</a> as well. <br />

Happy scripting & dev journey!