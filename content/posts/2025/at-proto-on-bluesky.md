+++
date = '2025-01-22T17:09:51-06:00'
draft = true
title = "How AT Protocol and Bluesky Work..."
description = "A high-level walkthrough on roughly how it works and why it&#39;s kind of a big deal"
type = 'post'
tags = ["news-link", "social-media", "tech", "networking", "devops", "deep-dive"]
+++
As a continuation of [**my post the other day about Protocols as a better design approach than Platforms**](https://julianwest.me/Blog/protocols-not-platforms/), I want to offer more details about ***how*** [***ATProto***](https://atproto.com) **and** [**Bluesky**](https://bsky.app) ***work***. <br />

So Bluesky is this *decentralized* social network that distributes control across multiple servers. It’s built on the open-source ATProto framework and uses a federated architecture for a familiar client-server model.

It defines distinct data schemas and API endpoints for ATProto apps, storing each user’s published data in a dedicated repository backed by SQLite. Every user action—such as likes or comments—lives in that repository. Multiple repositories then reside on a data server that exposes HTTP to clients.

A crawler service collects data from each repository and streams it over WebSockets, though it doesn’t include total like or comment counts. An index server processes the stream to compute these totals and handle reposts.

Media files (e.g., images) are kept in the data server and referenced in the repositories. On user requests, the index server fetches these media files from the data server and caches them on a CDN.

***tl;dr*** **of the above**: Each individual Bluesky user gets their *own* personal database that stores their likes, comments, and so forth (PDS).  By defaut Bluesky creates/hosts and registers that personal database with the Bluesky server, which fetches your data and merges it with everyone else’s to generate your feed.  Your able to, however, have your personal database live just about *anywhere* of Bluesky's infra: giving you total control of your "*identity*" and social media activity.