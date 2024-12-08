+++
date = '2024-10-20T23:17:51-06:00'
draft = false
title = 'New Blog Digs...again: Dodging Enshittification'
type = 'post'
tags = ["blog", "tech", "code"]
+++

I've been tired of the </i></b><a href="https://en.wikipedia.org/wiki/Enshittification">enshittification</a></b></i> of <b><a href="https://medium.com">Medium</a></b> for quite some time now, so I decided to move <a href="https://julianwest.me/Blog">the blog</a> away from that site.<br />

But up until a couple days ago, I just wasn't sure what would make a good replacement.  My needs are simple, and a goal was to simplify this thing.  And depending on some 3rd party blog-publishing platform was another goal. Over the years this blog has resided on a local PHP CMS, Drupal, WordPress, even SquareSpace.  And, finally, Medium.  For better or worse, each solution was fantastic early-on, but then time passes and the <i>"value-extraction cycle"</i> hits and voila: the afforementioned <a href="https://en.wikipedia.org/wiki/Enshittification">enshittification</a> hits that blogging solution.  And I start all over again, lugging my posts over to something less <i>enshittified</i>.  Given enough time, things will suck despite the good intentions of platform founders (see: Twitter). It's just a fact: every human endeavor eventually degrades. It's like gravity. <br /> 

So, what to do?  Where else can I move this blog to that won't enshittify, or otherwise suck?  I believe the <i>trick</i> is not to <i>avoid</i> <a href="https://en.wikipedia.org/wiki/Enshittification">enshittification</a> , but simply manage it! Surf onto a platform when it works, and just <i>depart</i> it when it starts sucking.  <br />

Ok so where were we?  Oh yeah, options to move my blog away from Medium. <a href="https://en.wikipedia.org/wiki/Substack">Substack</a> looked promising and a lot of friends are still using it, but it's beginning to show subtle <a href="https://janefriedman.com/substack-is-both-great-and-terrible-for-authors/">signs</a> of the afforementioned "value-extraction" clycles.  So (say it with me...), more potential <a href="https://en.wikipedia.org/wiki/Enshittification">enshittification</a> with Substack, a platform mostly-obsessed with <a href="https://thehypothesis.substack.com/p/heres-why-substacks-scam-worked-so">gobbling your blogging efforts into paid newsletters</a>. <br />

So I looked over options that weren't soup-to-nuts <i>paid platform</i>-based, which prety much means going back to hosting the blog myself. But I really don't want to roll a Vercel instance or similar high-maintenance thing, just for a <i>dumb personal blog</i>.  Gone are the days where you could just self-host a CMS: security ends up being THE constant high-touch thing, so nobody self-hosts their personal sites much anymore. <br />

<b><i>But <i>then</i> it occured to me</b></i>: I <i>already</i> host <a href="https://julianwest.me">julianwest.me</a> on <b><a href="https://pages.github.com">GitHub Pages</a></b>, why not just host my blog over there too?<br />  

Turns out every decent dev with a GitHub presence is already been doing this, for a long time now, with <b><a href="https://en.wikipedia.org/wiki/Static_site_generator">Static Site Generators</a></b> and GitHub Pages. Nice! So I looked into the top 3 in this space:  <a href="https://github.com/TryGhost/Ghost">Ghost</a>, <a href="https://github.com/jekyll/jekyll">Jekyll</a>, and <a href="https://github.com/gohugoio/hugo">Hugo</a>.  They are the major SSGs for GitHub hosted blogs, and each one is fast and efficient. <b>My requirements were</b>: I want the ability to write in Markdown in whatever editor I have open (vim, vscode, notepad etc.), and be able to just <a href="https://docs.github.com/en/get-started/using-git/pushing-commits-to-a-remote-repository">git-push</a> whatever <i><b>markdown-blog-post.md</i></b> file I save locally. Then a GitHub Action workflow could handle content-generation after my Post / git-push event. No muss, no fuss. Very demure, very <b></i><a href="https://en.wikipedia.org/wiki/CI/CD">CI/CD</a></i></b>. 🤭 <br /> 

Simple requirements, and any of these SSGs whouldn't be too difficult to deploy in a weekend!  Then I could move all of my old Medium blog content over, and land at a low-maintenance / low-touch blog setup that I control.<br />

Ultimately I went with <a href="https://github.com/gohugoio/hugo">Hugo</a>, moved it last weekend, and if you're reading this then I was successful.  😉 <br /> <br />


Quick note for myself, to review Jon Yocky's excellent <a href="https://www.yockyard.com/post/the-hugo-markdown-crash-course/">The Hugo Markdown Crash Course</a> so that I can back-format all of my old articles properly for Hugo.