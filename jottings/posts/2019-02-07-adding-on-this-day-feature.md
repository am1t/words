---
title: Adding On This Day feature to Blot
date: '2019-02-07 00:00:00'
slug: adding-on-this-day-feature
tags: dev, meta
---
Recently David Merfield, the developer behind Blot, documented the steps to expose a JSON feed on a Blot site. I [have been running a JSON feed](https://mb.amitgawande.com/on-this-day-a-year-ago) for my blog for quite some time now, with some valuable help from David of course. It is this feed that drives the [On This Day](https://mb.amitgawande.com/on-this-day) page on this blog. I thought I will share my approach so that others with a blog running on Blot can create such a page.

To begin with, follow [the guide](https://blot.im/developers/guides/json-feed) to get a working JSON feed for your blog. Validate you have a properly formed and accessible feed being served using the [JSON feed validator](http://validator.jsonfeed.org/).

One key thing to understand here is how to create a view in Blot. It would be important to be aware of this step to proceed further. A view can be created in Blot by accessing the [editing template](https://blot.im/settings/theme) section (**Settings** > **Template**) in Blot dashboard. Click on **Edit** against your currently installed theme and search for an option “**Create new view**”.

Once the JSON feed is available, create a view in Blot for a javascript file. Copy the complete content of the [javascript available as a gist](https://gist.github.com/am1t/5bcbc5366491c2b010adfe1358877899) and add them to this new view. Modify the `json_feed_url` and `tz` variables appropriately to reflect the URL for the JSON feed and the timezone for your blog, you can refer to the formats in [TZ database time zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones). This script does the following.

1. **Fetches** all the posts as JSON objects from the JSON feed
2. **Identifies** the posts that share the same date and month as the current date (but not the year to avoid loading today’s posts)
3. **Renders** the posts (or *no posts* message) in the predefined section detailed below. This also includes some styling via the `.className` definition, you can remove/modify that as per your liking in fuction `renderPost`.

Make sure the above created view is accessible at a URL. If not, define a route in the **Settings** section of the view.

Next, create another view for a page to display these posts; a reference html page is available [as a gist](https://gist.github.com/am1t/472499285986345f34c61274edd22cdc). Modify the `src` in `<script src="/flashback.js"></script>` to reflects the URL for the javascript created above. The script adds and renders the posts made on this day in earlier years in the `div` element with `id` `on-this-day`.

Do give this a try, it is fascinating to see your thoughts change, or at times stay exactly the same, over the year. Reach out to me if you face any issues or find any step missing.

**TL;DR:** Expose a JSON feed on your site. Create two views in Blot using the gist [flashback.js](https://gist.github.com/am1t/5bcbc5366491c2b010adfe1358877899) and [on-this-day.html](https://gist.github.com/am1t/472499285986345f34c61274edd22cdc). You should have two additional pages, you can use the same file names. If you do, you can access your On This Day page at `/on-this-day`.

---

This javascript is inspired by and based on the wonderful project [Micro Memories](https://github.com/cleverdevil/micromemories) by [Jonathan LaCour](https://cleverdevil.io/) for the micro.blog hosted blogs. I have customized and simplified it as per my needs.
