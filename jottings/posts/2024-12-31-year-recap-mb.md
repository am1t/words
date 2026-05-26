---
title: Year Recap in Post Stats Plugin
date: '2024-12-31 06:00:00'
slug: year-recap-mb
tags: dev
ghost_id: 68511293eb03dc000150c7dc
---
Today, I released a new version of the [Posts Stats plugin](https://micro.blog/account/plugins/view/22) for Micro.blog that adds a year recap section on the stats page. This section includes a summary of your posts in the year. Here's a snapshot of how [the section](https://mb.amitgawande.com/stats/) looks.

![](/images/year-recap-section.png)

I did not want to add too many details, crowding the overall page. Neither did I want a repeat of the whole section on overall stats, just from this year's perspective. Instead, I wanted to include key insights on the posting pattern.

I have also made the year recap available as a shortcode so you can include it on any other page ***(not post)***. **Do not include the shortcode in any post, as it will cause the blog refresh to fail.** To add the recap to any page, go to the `Pages` section on Micro.blog and create a new page or update the existing one. Include the shortcode below in the body.

```text
{{< poststats/yearrecap >}}
```

This should include a similar year recap section on the page.

The upgrade should now be available in your plugins section. Please upgrade and let me know if you encounter any issues. Also, let me know if you want me to include something else in the section. I have tried to include as many aspects as possible from [the original discussion](https://micro.blog/jthingelstad/52635531).

Wish you all a very happy new year! 🎉
