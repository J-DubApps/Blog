+++
date = '2024-11-20T23:17:51-06:00'
draft = true
title = 'New HomeLab: Dodging Enshittification'
type = 'post'
tags = ["blog", "tech", "test-dev", "homelab", "vmware", "devops"]
+++

Referring to my post from last month, about escaping the inevitable <i><b><a href="https://en.wikipedia.org/wiki/Enshittification">enshittification</a></b></i> of a platform, that effort has moved on from my blog to my HomeLab.<br />


Paired with this physical lab is a Xeon ESXi server I built a couple years ago to run pre-prod labs for work projects. It has 10 (ten!) NIC ports that I can use in-tandem with the physical lab in various configurations. Say I want to introduce a CSR1000V router, Junos VM, or Ostinato VM (traffic gen), or Wireshark to the topology. It’s pretty easy to do with this many NIC ports in ESXi. One of the NICs I sourced from leftover gear that was out of production, and the other I ordered from Amazon for $150.00. Best yet, ESXi immediately recognized both of these NICs without any need to install a driver.