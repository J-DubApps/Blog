+++
date = '2025-01-22T17:09:51-06:00'
draft = false
title = "How AT Protocol and Bluesky Work..."
description = "A very basic walkthrough on roughly how ATProto and Bluesky work together, and why it&#39;s kind of a big deal"
type = 'post'
tags = ["news-link", "social-media", "tech", "networking", "devops", "deep-dive"]
+++
As a continuation of [**my post the other day about Protocols as a better design approach than Platforms**](https://julianwest.me/Blog/protocols-not-platforms/), I want to offer more details about ***how*** [***ATProto***](https://atproto.com) **and** [**Bluesky**](https://bsky.app) ***work***. <br />

So Bluesky is this *decentralized* social network that distributes control across multiple servers, built on the open-source ATProto framework. Bluesky uses a federated architecture render the familiar client-server model of traditional social media. But Bluesky is *anything but* "traditional". <br />

Bluesky defines distinct data schemas and API endpoints for ATProto apps, storing *each user’s* published data in a dedicated repository backed by SQLite. Every user action (such as likes or comments etc) lives in that repository(*database*).  Each *individual user* user also has their own *personal database* that stores primary data (who they follow etc), separate from their *actions*.  Multiple repositories reside on a **data server**, exposting the data to the index server and clients via http access (and users can store their *personal respository* on *their own* ***personal data server***-we will circle back to that in a bit). <br />

Bluesky then uses a crawler service which collects data from each repository, and forwards it data in streams over WebSockets to an **index server**.  The **index server** then processes the data stream, hunting for total likes and comments on posts (and the total counts of likes / comments). <br />

Bluesky stores Media files (e.g., images) on the **data server** where they get referenced in the repositories. On user requests, the **index server** fetches these media files *from* the **data server**.  These fetches get cache on a [CDN](https://en.wikipedia.org/wiki/Content_delivery_network).

### *tl;dr* of all of the above: 

**Each individual Bluesky user gets their *own* personal database that stores their likes, comments, and so forth (PDS).  By defaut Bluesky creates/hosts and registers that personal database with the Bluesky server, which fetches your data and merges it with everyone else’s to generate your feed.  Your able to, however, have your personal database live just about *anywhere* of Bluesky's infra: giving you total control of your "*identity*" and social media activity**. <br />

Here's a handy visual flow of what I describe above, from Bluesky's handy [October 2024 Whitepaper](https://arxiv.org/pdf/2402.03239) on how all this works: 

<div class="image-row">
  <img src="https://julianwest.me/Blog/posts/images/Bluesky-Flow.jpeg" alt="Alt text" width="600" height="415">
</div>
<smaller>The main services involved in providing Bluesky, and data flows between them.</smaller> <br />

So each user repository(*database*) stores primary data, while the **index server** stores data derived from repositories.  A user updates only *their repository* when they follow someone. Other  The index server must keep up with all this, and so consequently it is the most ***resource-intensive*** part of the overall Bluesky service.  Thus, the **index server** is big on caching results.  Results get cached in [Redis](https://github.com/redis/redis), via in-memory database, to optimize performance.

Based on this flow, here is what is happening posts are displayed on your timeline:

1. A user’s request is routed via their data server to the index server.
2. The data server finds the people a user follows by looking at their repository.
3. The index server creates a list of post IDs in reverse chronological order.
4. The index server expands the list of post IDs to full posts with content.
5. The index server then responds to the client. <br />

The user’s timeline is rendered during this request, and shows posts to the user in reverse chronological order. Since a user's personal repository doesn’t contain information about likes / comments on a post, the index server is is queried for this-and it returns this data during the timeline render, with aggregated data. <br />

This represents *the basics* of how Bluesky functions, yet it is practically revolutionary compared to Twitter(X) and other legacy social media: because all this happens in a decentralized manner, where the user ratains a lot of standaridized-controls.  For instance, beause of this design users are granted a ton of feed and content customization capabilities that the other services just cannot scale to provide.  Nor do many of those older social media services *want to* offer a framework of deep customization, when it comes to algorithsm and influencing *your attention*.  There are the competing interests of Ad-buyers and feckless owners of these services, who would prefer you not be able to deeply-curate your timeline feed.  <br />

I may go deeper on this in the coming weeks, as the result of this fundamental design shift means that Bluesky supports feeds with custom logic (and there are nearly 60K custom feeds available) as well as a number of moderation features the *individual users* get to control and manage if they want.  The result means a user can have *multiple* focused, targeted timelines that are not directed by any *single algorithm* owned by the social media platform.  This results in a feed that is "less noisy", and quite a bit less troll-happy. <br />

In a word, Bluesky's approach lets you have a timeline that can balance having positive experence with FOMO (e.g. you won't miss stuff, but you need not see stuff you don't wanna see, either...). <br />

**Here are some helpful articles, and video, used in creating this post**. <br />

https://arxiv.org/pdf/2402.03239

https://docs.bsky.app/docs/advanced-guides/federation-architecture

https://www.cl.cam.ac.uk/research/security/seminars/archive/video/2024-11-22-t224767.html