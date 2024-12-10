+++
date = '2024-11-20T23:17:51-06:00'
draft = false
title = 'New HomeLab: Dodging Ensh*ttification'
type = 'post'
tags = ["blog", "tech", "test-dev", "homelab", "vmware", "devops"]
+++

Taking a cue from my post from last month about escaping the inevitable <i><b><a href="https://en.wikipedia.org/wiki/Enshittification">enshittification</a></b></i> of <a href="http://julianwest.me/Blog/hugo-crash-course/">blog platform</a>, that effort has shifted over to my aging HomeLab setup.<br />

With exception of a few Cloud sandboxes I run in AWS and Azure, I still run the bulk of my personal learning / test-dev setups here at home, on a couple of beefy mini HomeLab servers.  My HomeLab actually resides in my garden shed which has cooling, advanced smoke detection, and ethernet. But the main benefit is no noise in the house. A big no-no for the Mrs. 😬 <br />

So while I am using Cloud instances more and more, I do still often need to spin-up the odd Docker instance or VM to quickly prototype or put something through its paces.  But developments with my HomeLab Hypervsor's new owner has me facing the afforementioned challenge of <a href="https://en.wikipedia.org/wiki/Enshittification">enshittification</a>.  Here's why that is: <br />

VMWare was acquired by <a href="https://www.glassdoor.com/Reviews/Employee-Review-Broadcom-E6926-RVW75069965.htm">Broadcom</a> who promptly retired educational licenses, shuttered VMWare IT Academy licensing, and erased ESXi standalone licenses. <br />

Broadcom's acquisition has been a <a href="https://www.itbrew.com/stories/2024/04/03/broadcom-ceo-admits-vmware-takeover-has-resulted-in-some-unease-among-our-customers">gouging of epic proportions</a>, and painful to experience with prod environments I support. I won't belabor it, let me just say this... <br />

VMware under Broadcom is like seeing your favorite restaurant getting bought by a guy who only serves reheated leftovers at triple the price.  Unsurprisingly, everyone’s looking for a new place to eat. <br />

When it comes to pricing I feel like Broadcom is a kings of <a href="https://en.wikipedia.org/wiki/Enshittification">enshittification</a> of platforms and products. <br />

To be somewhat generous, Broadcom apparently did have a change-of-heart with VMWare Workstation and Fusion. Not a fit for most HomeLab folks with 256gb ESXi hosts doing test-dev or SDWAN prototyping. <br />

So I am looking <a href="https://www.proxmox.com/en/proxmox-virtual-environment/overview">Proxmox VE</a> or <a href="https://learn.microsoft.com/en-us/virtualization/hyper-v-on-windows/about/">Hyper-V</a> to flee VMware.  A sad day, being as I have run VMware professionally and personally, in some form, since 2006.<br />

I'm going to be trying both out in my HomeLab and will report what I end up doing. If anyone has any other suggestions on a good HomeLab platform beyond the above two options, <a href="http://julianwest.me/Blog/contact/contacting/">I'm all ears</a>. 