+++
date = '2025-01-22T17:09:51-06:00'
draft = true
title = "How AT Protocol and Bluesky Work..."
description = 'A high-level walkthrough on roughly how it works and why it's kind of a big deal.'
type = 'post'
tags = ["news-link", "social-media", "tech", "networking", "devops", "deep-dive"]
+++
As a continuation of [**my post the other day about Protocols as a better design approach than Platforms**](https://julianwest.me/Blog/protocols-not-platforms/), I want to offer more details about *how* AT Proto and Bluesky ***work***. <br />




***tl;dr*** **of the above**: Each individual Bluesky user gets their *own* personal database that stores their likes, comments, and so forth (PDS).  By defaut Bluesky creates/hosts and registers that personal database with the Bluesky server, which fetches your data and merges it with everyone else’s to generate your feed.  Your able to, however, have your personal database live just about *anywhere* of Bluesky's infra: giving you total control of your "*identity*" and social media activity.