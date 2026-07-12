---
title: Displaying images from Blot on Micro.blog
date: '2018-10-10 00:00:00'
slug: displaying-images-from-blot-on
tags: dev, writing, meta
---
**Update:** David has added a [new function](https://github.com/davidmerfield/Blot/commit/0eb301b8c64a48843c54f1401d8ce0c61f2c6143) “to step around the issues micro.blog was having with images in Blot’s RSS feeds”. This change should allow using the Blot’s caching feature.

For all the defaults templates, David has already deployed the fix. So you should have the issue sorted without any update. If you have a custom template, to enable this change, wrap the html component around with the function `absoluteURLs` in your RSS file. For example, if you use `html`, use the below block in your description feed of your rss file (typically `feed.rss`).

```
{ {#absoluteURLs}} { { {html}}} { {/absoluteURLs}}
```

---

When you publish a micro post (one without title) on Blot which has images in it, Blot uses a CDN by default to store for these images. Though it may be helpful overall in blog performance, it causes some issues while interoperating with micro.blog. You will find that these images are not visible on its timeline.

It’s a known issue where micro.blog is unable to parse these images. To enable the images posted on Blot to appear on micro.blog timeline, make following changes with the configuration.

1. You can disable the blot cdn. This option is available on the Blot [settings](https://blot.im/settings/services) page under Settings > Services > Cache And Optimize Images. This makes the images be served directly under your blog’s domain. This change does not take much time to propagate, you will see the change reflect in the `url` for the images.
2. In addition, by default (in most themes), images may have relative urls. For example, you might just put `_images\<IMAGE_NAME>` while adding the image to the post. However,these relative paths are again not parsed by micro.blog well (though most feed readers do it well). Anyway, to overcome this problem just include the complete url of the image while adding it (for example, `http://<BLOGNAME>/<PATH>`).

These changes should be enough to allow your images to be visible at m.b timeline.
