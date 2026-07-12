---
title: Creating a new view on Blot
date: '2018-08-20 00:00:00'
slug: creating-a-new-view-on
tags: dev
---
I recently wanted to create a new view (a page) for all my [social posts](https://mb.amitgawande.com/social). Apparently, even if you create the page there are still few additional configurations to be done for the template to make it available at a particular link.

Configuration to be done is to define a route which will serve that particular page. This can be done on the web editor at Blot dashboard in the template section.

 As of now, this is only possible when local editing is disabled. So if you have the local editing enabled, you can disable it to access the below mentioned sections.

You can create a new ‘view’ on the web editor in the view section of the templates (available at `https://blot.im/template/<theme-name>/view`).

Once you create a new view, go to settings page for the newly created view and specify its route. For example, the route (or URL) for `archives.html` is set to `/archives`. This enables the Blot engine to render the given template view at the configured URL. You can explore the `archives` view for more options.
