+++
date = '2026-03-26T16:17:00-05:00'
draft = false
title = 'Using Obsidian Notes and Claude to Publish to My Blog'
type = 'post'
tags = ["tech", "blog", "devops"]
+++

I've tried a lot of blogging setups over the years. Dedicated CMS platforms, standalone Markdown editors, even just raw vim sessions committed straight to a repo. They all worked, technically. But all of them had the usual friction, weren't easily automated, and none of them felt like home.

Then I started using Obsidian for everything else in my life, notes, projects, daily journaling, research, and a thought hit me: why am I leaving this app to go write blog posts somewhere else?

## One Place for Everything

Obsidian is already where I think. It's where I capture ideas at 2am, process meeting notes, and maintain a personal knowledge base that links everything together with internal wikilinks. The Markdown is clean, the editor is fast, and the vault syncs across all my devices.

Hugo, the static site generator that powers my blog, also runs on Markdown. The connection almost makes itself. Other than frontmatter tweaks (e.g. Obsidian fronmatter is yaml while Hugo uses toml), it's nothing at all to just have my blog posting process and pipeline be right there in Obsidian.

So I configured Obsidian as my primary blogging editor. My blog's content lives inside my Obsidian vault as a symlinked folder pointing to the Hugo site's Git repo.  The symlink to the repo is not indexed or modified by any Plugins (avoids frontmatter corruption), and I keep a separate "`Blog-Posts`"  folder in Obsidian where I can keep a copy (and backup) of blog content -- while live posts just get saved direct to my blog's Git repo.  

So I write, I edit, I organize, all without leaving the app where I already spend most of my working hours. The context switching is reduced, but that lead me to another thought.

## Claude Cowork & Claude Code Assisting

Claude Cowork & Code can help me further reduce friction, by helping me automate a pipeline on each phase of my writing.   I still want to be the one doing most of the writing (though I have used Claude to do research/iterate on draft revision ideas), but there's no reason why Claude can't do a quick check on my final drafts for voice/tone issues or misspellings etc.  Then after that, Claude can push the content right into my blog's Git repo and even perform the Git commit. 

## From Obsidian to the Web

Here's how the publishing pipeline works. My blog is a Git repository hosted on GitHub. When I'm ready to publish, the post gets committed and pushed to the repo, and a GitHub Action takes over from there. Hugo builds the site in a few seconds, and the post goes live. No manual FTP uploads, no logging into a web dashboard, no copy-pasting between apps.  No database to manage, either, since my blog is just text files.  It's literally just me writing Markdown files in Obsidian...then having a process that optimizes them Hugo Markdown frontmatter.  In the end, it's just simple and elegant text files driving this blog -- via Claude workflows and Git -- right from my Obsidian app.  No "dashboard" or WordPress security nightmares, or Squarespace CMS challenges.

I kinow this isn't for everyone, **but for me the beauty of this setup is its simplicity**. Obsidian handles the writing. Git handles the versioning. GitHub Actions handle the deployment.  And Claude bridges the Obsidian-to-Git stage in between.  Each tool does what it's best at, and I stay focused and spend less time with publuishing minutiae. 

## What's Coming Next

I've been building something on top of this workflow that will add to *ideation* and *content-generation* in the future.  Again, **I'm the writer**, it's my voice, but I'm kind of toying with using Claude to help me iterate and refine my ideas into posts.  So not just research and editing assistance, but also having jr co-writer around to to handle the tedious parts in my automated blogging pipeline.   Claude has demonstrated it can help me stay in Obsidian, and stay ***in-flow***, and "just do" the boring parts of pushing to my site when I'm done.   Now I'm going to push further and see how it might help for me to get a post from rough idea to published article. I think of it as having a capable assistant that understands my Obsidian vault, my voice, and my process.

I'll detail that setup in a follow-up post. For now, if you're already using Obsidian and you blog with something like Hugo or Quartz (or any Markdown-based SSG), consider bringing those worlds together. The less friction between your thinking and your publishing, the more you'll actually want to draft and refine -- it leaves more time for just writing.

Kind of really the whole point, right?