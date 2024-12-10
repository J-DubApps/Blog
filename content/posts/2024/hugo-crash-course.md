+++
date = '2024-10-20T23:17:51-06:00'
draft = false
title = 'More On My New Blog Digs: Dodging Ensh*ttification'
type = 'post'
tags = ["blog", "tech", "code"]
+++

So, yeah.  As I <a href="http://julianwest.me/Blog/hugo-crash-course/">mentioned yesterday</a>, I moved the blog.  Again.  <br />

Wait a second, I say that like I do this often but I don't.  It's been 10 years since the last move.  It's just that I moved this blog 5 times in its 20 years and 3 incarnations. <br />

<b>As for why</b>: I've been tired of the <i><b><a href="https://en.wikipedia.org/wiki/Enshittification">enshittification</a></b></i> of <b><a href="https://www.makeuseof.com/reasons-not-medium/">Medium</a></b>.  For quite some time now. 

Up until a few weeks ago, I wasn't sure about the best replacement.  My needs are simple, and my goal was to simplify this thing.  Not depending on a 3rd party blog publishing platform was another goal. Over the years this blog has resided on a local PHP CMS, Drupal, WordPress, even SquareSpace before it landed at Medium.  For better or worse, each solution was fantastic early-on, but then time passes and that ole <i>"value-extraction cycle"</i> hits. Voila: the afforementioned <a href="https://en.wikipedia.org/wiki/Enshittification">enshittification</a> inevitably occurs.  And I start all over again, lugging my posts over to something less <i>enshittified</i>. And I've learned that, given enough time, ALL things will suck despite the good intentions of platform founders (see: Twitter). It's just a fact of life: every human endeavor eventually degrades. It's like gravity. <br /> 

So, what to do?  Where else can I put my blog that won't enshittify, or otherwise hit its suck cycle?  The <i>trick</i> is not to <i>avoid</i> <a href="https://en.wikipedia.org/wiki/Enshittification">enshittification</a> , my friends.  No: you <b><i>embrace</b></i> the enshittification cycle, and make it work for you! Get on a platform early on, and just be ready to make the hop away once that ole suck cycle kicks in.  <br />

So where were we?  Ah yes, options for new Blog move. <a href="https://en.wikipedia.org/wiki/Substack">Substack</a> looked promising and I have many friends still using it, but it's already enshitifying with tell-tale <a href="https://janefriedman.com/substack-is-both-great-and-terrible-for-authors/">signs</a>.  Substack is mostly-obsessed with <a href="https://thehypothesis.substack.com/p/heres-why-substacks-scam-worked-so">pushing your writing to newsletter subscribers</a>, anyway.<br />

So I looked at options in the self-hosted solution space.  I really don't wanna roll a Vercel instance or other high-maintenance thing for a <i>stupid personal blog</i>, and gone are the days where you could just self-host a CMS: Security ends up being THE ONLY thing you'll do, instead of blogging. Almost nobody self-hosts anymore. <br />

<b><i>But <i>then</i> it occured to me</b></i>: I <i>already</i> host <a href="https://julianwest.me">julianwest.me</a> on <b><a href="https://pages.github.com">GitHub Pages</a></b>, why not just put my blog over there too?<br />  

Turns out every decent dev already does this, via <b><a href="https://en.wikipedia.org/wiki/Static_site_generator">Static Site Generators</a></b>. Nice! So I looked into the top 3 in this space:  <a href="https://github.com/TryGhost/Ghost">Ghost</a>, <a href="https://github.com/jekyll/jekyll">Jekyll</a>, and <a href="https://github.com/gohugoio/hugo">Hugo</a>.  They are the major SSGs for GitHub hosted blogs, and each one is fast and efficient with its own pros and cons. <b>My requirements were</b>: I want the ability to write in Markdown in whatever editor I have open (vim, vscode, notepad etc.), and be able to just <a href="https://docs.github.com/en/get-started/using-git/pushing-commits-to-a-remote-repository">git-push</a> whatever <i><b>markdown-blog-post.md</i></b> file I save locally. <br />

I went with (drumroll 🥁) <b><a href="https://github.com/gohugoio/hugo">Hugo</a></b>.  I moved the blog last weekend, and if you're reading this then I was successful.  😉 <br />

What's nice is I can just throw together a blog post in text editor and git-push it up, where I have a Github Action workflow doing the site-generator magic with my new Post. No muss, no fuss. Very demure, very <b></i><a href="https://en.wikipedia.org/wiki/CI/CD">CI/CD</a></i></b>. 🤭 <br /> 


For more info on the new blog setup, click the <b>Colophon</b> link below at the footer of this article. Enjoy the new digs!<br />


Quick note here for myself, to review Jon Yocky's excellent <a href="https://www.yockyard.com/post/the-hugo-markdown-crash-course/">The Hugo Markdown Crash Course</a> so that I can back-format all of my old articles properly for Hugo.