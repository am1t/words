---
title: Add Edit Post Link with Kirby CMS
date: '2024-12-09 17:35:00'
slug: edit-post-link-kirby
tags: dev
ghost_id: 68511293eb03dc000150c7e0
---
I recently added a button on my website that allows me to edit the current post when logged in to the Kirby CMS panel. This change is part of [my general effort](https://www.amitgawande.com/blog/2024/20241205-2228) to reduce friction between my intention to write and *the editor*. Here's how I implemented this - something much more straightforward than anticipated.

A [built-in function](https://getkirby.com/docs/reference/objects/panel/panel/url) links to the appropriate panel page. So, you only need to include a link somewhere in the post template to add the panel URL. Use the below snippet in your `post.php` or an appropriate template code.

```php
<?php if(kirby()->user()): ?>
    <a href="<?php echo $page->panel()->url(); ?>">Edit Post</a>
<?php endif; ?>
```

The navigation bar at the bottom was the best place for me to add the button. You can decide where to add this link and how to style it based on your overall site theme. Once this is done, the link should be visible on the site when you are logged in to the Kirby CMS panel.

![](/images/edit-post-button.png)
