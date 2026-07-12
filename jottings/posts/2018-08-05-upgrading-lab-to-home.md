---
title: Upgrading Lab to Home
date: '2018-08-05 00:00:00'
slug: upgrading-lab-to-home
tags: writing, life, meta
---
**Updated: 05-Aug 15:15**

I am seriously considering the option to make this blot blog as my primary site. I do not want to take decision in haste. So here I am jotting down the things I will have to sort out before the switch. This would be a rolling list.

1. Moving all the old posts to Blot. This should primarily involve handling of metadata. Hugo frontmatter needs to be converted to something that Blot can parse. Tricky part is going to be around dates and tags.
2. Handling of redirecting journal posts. Currently they are available at `/journal/<postname>`. This will have to redirected to `/<postname>`.
3. Handling of redirecting `lab.` urls. All the current blot posts will move to `www` subdomain.
4. Handling of Blot images redirect or modification of the posts.
5. Moving of the `/now` and `/about` pages to blot.

As I jot this down, there is another option that looks simpler (and so more probable).

Blot becomes my blog, replaces journal on the current site. Hugo site remains my main site. I will not move any posts, journals or pages. Everything in the old site remains in the old site. All the formatting rework is avoided.

I can move the complete journal section to an archive link in the footer. Blot will be serving `/blog`. `/lab` will be redirected.

Main site navigations will be Home | Arcticles | Blog | Now | About

That means the current site will keep serving my long form posts, the articles. Ones for which I spend significant time, I have a machine available to write over the days. And I can control the publish process. The blot blog will sever my thoughts, ones that I need to quickly put out, may be mostly while mobile.
