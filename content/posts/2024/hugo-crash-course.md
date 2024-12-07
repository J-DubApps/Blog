+++
date = '2024-10-20T23:17:51-06:00'
draft = false
title = 'New Blog CMS / Skin / Look'
type = 'post'
tags = ["blog", "tech", "code"]
+++

I've been tired of the </i></b><a href="https://en.wikipedia.org/wiki/Enshittification">enshittification</a></b></i> of <b><a href="https://medium.com">Medium</a></b> for quite some time now, so I decided to move away from it <br />

But I just wasn't sure what would be a good enough replacement.  My goals were to simplify this thing, and not be depending on some 3rd party blog-publishing platform anymore. Over the years this blog has resided on a local PHP solution, WordPress, SquareSpace, and finally Medium.  For better or worse, each solution was fantastic early-on, but then time passes and "value-extraction" causes the afforementioned <a href="https://en.wikipedia.org/wiki/Enshittification">enshittification</a>.  Every 3rd party solution, given enough time, will suck.  It's just gravity, which ignores the good intentions of blog platform founders.  So, what to do?  Where else can I move this blog to? <br />

<a href="https://en.wikipedia.org/wiki/Substack">Substack</a> looked promising a couple years ago, but it is beginning to show hints and signs of the afforementioned signs of "value-extraction" and (say it with me...) <a href="https://en.wikipedia.org/wiki/Enshittification">enshittification</a>. So I decided I'd much rather just go back to hosting myself, rather than depend on another platform that I might need to exit from when it gets mediocre, yet again.  But I really don't want to roll a Vercel instance or similar high-maintenance thing just for some <i>dumb personal blog</i>, either.  Gone are the days where you could just throw a host or VM onto the Internet running a blog CMS, either: security would be a constant high-touch thing. Not worth it for a blog or almost any kind of personal site! <br />

<b><i>Then it occured to me</b></i>: I already host <a href="https://julianwest.me">julianwest.me</a> on <b><a href="https://pages.github.com">GitHub Pages</a></b>, why not just host my blog over there too?<br />  

Turns out every decent dev with a GitHub presence is already been doing this, for a long time now, with <b><a href="https://en.wikipedia.org/wiki/Static_site_generator">Static Site Generators</a></b> and GitHub Pages. Nice! So I looked into the top 3 in this space:  <a href="https://github.com/TryGhost/Ghost">Ghost</a>, <a href="https://github.com/jekyll/jekyll">Jekyll</a>, and <a href="https://github.com/gohugoio/hugo">Hugo</a>.  They are the major SSGs for GitHub hosted blogs, and each one is fast and efficient. <b>My requirements were</b>: I want the ability to write in Markdown in whatever editor I have open (vim, vscode, notepad etc.), and be able to just <a href="https://docs.github.com/en/get-started/using-git/pushing-commits-to-a-remote-repository">git-push</a> whatever <i><b>markdown-blog-post.md</i></b> file I save locally. Then a GitHub Action workflow could handle content-generation after my Post / git-push event. No muss, no fuss. Very demure, very <b></i><a href="https://en.wikipedia.org/wiki/CI/CD">CI/CD</a></i></b>. 🤭 <br /> 

Simple requirements, and any of these SSGs whouldn't be too difficult to deploy in a weekend!  Then I could move all of my old Medium blog content over, and land at a low-maintenance / low-touch blog setup that I control.<br />

Ultimately I went with <a href="https://github.com/gohugoio/hugo">Hugo</a>, moved it last weekend, and if you're reading this then I was successful.  😉 <br /> <br />


Quick note for myself, to review Jon Yocky's excellent <a href="https://www.yockyard.com/post/the-hugo-markdown-crash-course/">The Hugo Markdown Crash Course</a> so that I can back-format all of my old articles properly for Hugo.