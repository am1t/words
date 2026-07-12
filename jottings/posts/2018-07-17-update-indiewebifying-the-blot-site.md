---
title: Update - IndieWebifying the Blot site
date: '2018-07-17 00:00:00'
slug: update-indiewebifying-the-blot-site
tags: meta
---
Given the recent focus on the [working on Micro.threads](https://mb.amitgawande.com/user-discovery-with-microthreads/), I hardly had any spare time for working on exploring Blot. [Micropub](https://mb.amitgawande.com/micropub-endpoint-from-the-ground-up) remains a distant dream. In line with [the first update](https://lab.amitgawande.com/update-on-blot-experiment), I thought the best way to get going would be to IndieWebify the site first.

So I took some time out today and started with incorporating the basic principles. Some were addressed without much hiccup. Some have left me with some questions.

1. Web Sign In is enabled. However, it did throw a curveball. Given that I already have my primary site active, how can I include `rel=me` links point to any of the Twitter/Github services? Concern is primary as I cannot link my Twitter/Github profiles to multiple homepage. May have to identify a different unused profile?
2. `h-card` microformat is incorporated; so the site provides information on me now.
3. `h-entry` microformat is added to all the post entries. There is one issue though. I could not find any way to format the published date that gets displayed on the posts. The post properties exposes just , which gets the default format of `MMM DD, YYYY`. And I do not think it’s a valid ISO-8601 as expected by the microformats2.

 **Update**: I did sort out the way to [format the published date](https://mb.amitgawande.com/changing-date-format-blot).

**Stuff to sort out next**

- Webmentions, both send and receive. I think I may keep this for later. I do not think I want to bring in the interactions at this point
- Support for different posts types - replies, likes and reposts. I need to be able to add these posts type. However, more I think about it, I come to realise biggest benefit is going to be once Micropub is setup and site is able to send the Webmentions at the least. So even this might take some time.
