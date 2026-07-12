---
title: Getting Started Blogging with Drummer
date: '2021-10-16 00:00:00'
slug: getting-started-blogging-with-drummer
tags: dev, writing, life, meta
---
I recently [started blogging with Drummer](https://mb.amitgawande.com/2021/10/12/of-course-i.html), a new Outliner made public by Dave Winer. It has been a wonderful experience. I don’t know what it is about a single outline as a base for your blog, but it feels natural. I have been enjoying writing and playing around with [my Drummer blog](https://ol.amitgawande.com). However, it is not easy to fathom the simplicity of the whole system just through words — only trying it out will make you appreciate the ease. I wanted to capture what it is and how to quickly get started with it for myself and others to follow.

Drummer documentation captures most of this information. But for someone, like me, who’s new to the concept of outliner, the whole stuff can be pretty overwhelming. So, here I capture what I learned and liked so that it helps other newbies like me.

## What’s an Outliner?

An outliner is basically an editor that can edit an outline. What is an outline, you ask? Well, outline is text items represented in a hierarchy, with each item having a parent (typically a title) or multiple sub-items (typically related points). There’s a lot more to know, but I am more focused on drawing a parallel with regular blogging terminologies.

You can think of a first parent item as a title of your post. Each sub-item that follows is like a new paragraph. You can further divide the items into sub-items, that’s grouping related points into a subtitle for example. The only difference is instead of it being represented as a header and list of paragraphs, it is a tree-structure of points, closely related and unrelated.

If a post doesn’t have any child, it’s a titleless post, a micro-post — something like a tweet.

Dave Winer is the strongest proponent of using the outlines as the base for the blogs, he uses them for his blog, [Scripting News](http://scripting.com). The basic hierarchical structure of an outline, makes using outliner for blogging powerful. Both the types of posts, long-form and micro, sit well together. After all, it’s just one long list of text items one after another. Whether they have a sub-item or not define how they get represented. Or that’s how Dave likes them represented.

Drummer is one such outliner that benefits from the years of Dave’s experience. He has understood all the nitty-gritty of blogging through this form. So, once you overcome the initial struggle of unknown, the experience is pretty smooth.

## Is it a Blogging CMS?

Not really, Drummer is just a web application that can edit outlines. These outlines are typically represented as an `OPML` file. Basically, all you do with Drummer is edit `OPML` files of different forms. It wraps a few special `OPML` files — mainly `blog.opml` — to give them specific meaning while using them as base for blogging.

But, all we do is edit these `OPML` files then, what builds the blog?

Well, the software that runs Dave’s blog does that job. It is called [Old School](https://github.com/scripting/oldSchoolBlog) (because Dave believes this is the old school way of blogging) and is hosted by Dave. In a way, Old School is the blogging CMS and not Drummer.

So, from my understanding, the way the thing connect is as below.

1. You sign in with your Twitter account and that creates the necessary backend — basically a S3 store for your OPML files — based on your Twitter username.
2. You create, view, edit the `OPML` files using Drummer. The special files like `blog.opml` and `about.opml` hold special meaning for Old School. (**Update:** In fact, `about.opml` is just used for representation. You can name it anything.) So, you update them and through a command in Drummer (Build my blog), you communicate to Old School server to refresh your blog.
3. Old School receives the communication and based on provided inputs, it identifies the files to use for building the blog. It reads the `OPML` files from the backend store for the files and converts them to static files that get served as your blog.
4. Old School also serves you blog at the `http://oldschool.scripting.com/<your-user-name>` URL. So in a way, you don’t need to host any additional software.

In a way, then, Drummer and Old School together act as your blogging engine. Drummer is your editor where you write your posts. Old School acts as a CMS to build and serve your blog.

## How do I get started?

Dave has a got a handy documentation in place that you can follow. I will point to the relevant parts in the documentation so that you can follow along and get started.

1. **Main blog:** Follow the [getting started guide](http://docserver.scripting.com/drummer/blogging.opml#1628692121000) to get a blog up and running with Drummer. In short, create a `blog.opml` outline file. Make the outline public. And finally, build the blog using `Tools > Build my blog...`. This should open a new tab with your blog rendered with Old School. You can customise your title and description of your blog and a few head-level attributes.
2. **Title and Description:** Modify/add the head-level attributes `title` and `description` and rebuild your blog.
3. **Header Image:** Add a head-level attribute `urlHeaderImage` pointing to the header image of your choice and rebuild your blog.
4. **Copyright:** Add a head-level attribute `copyright` with the text you want to appear in the footer and rebuild your blog.
5. **About Page:** If you want to create a new tab in your blog for [your About page](http://docserver.scripting.com/drummer/blogging.opml#1633177951000), create a new `about.opml` outline file using Drummer, make the outline public, add a head-level attribute `urlAboutOpml` pointing to this public outline and build your blog again. (**Update:** In fact, `about.opml` is just used for representation. You can name it anything, as long as you configure the value for `urlAboutOpml` accordingly.)
6. **Link Blog:** If the concept of linkblog excites you, you [can use another software](http://docserver.scripting.com/drummer/blogging.opml#1633177803000) by Dave, [Radio3](http://radio3.io/). Just add a new head-level attribute `urlLinkblogJson` pointing to your linkblog JSON file, which would look something like `http://radio3.io/users/<your-user-name>/linkblog.json`.
7. **TimeZone:** To make sure the dates are rendered correctly on your blog, add a head-level attribute `timeZoneOffset` for the place where you would be blogging from. The value should be the offset from UTC — for example, `+5:30` for India or `-4` for New York.
8. **Creating Post:** Head over to your `blog.opml` file in Drummer and click on the **+** icon (for New Note), write what you want to write and rebuild your blog. Your post should be up.
9. **Adding Links:** Select the text to which you want to add a link, click on the “Link” icon (the second icon from top in the icon bar that sits on the left of the editing area) and insert the URL.
10. **Adding Images:** This one’s slightly tricky. First, have your image hosted on some place where it would be accessible publicly. Get the URL to your image. While on the item you want to associate the image with, click on the “Edit attributes” icon (the third icon from top in the icon bar that sits on the left of the editing area). Now you can either create an inline image (with attribute `inlineImage`), right-margin image (with attribute `image`), title image (with attribute `metaImage`). I wish this work was simpler.

At this point, you should have a well-configured blog up and running. Keep Drummer interface open in tab and keep adding entries. This method of updating your blog will soon grow on you.

## What else can I customise?

Even though you have all the basics covered till now, there is still a lot that you can and should do. But I would recommend get comfortable working Drummer and check for yourself if the workflow fits your routine and liking. If it doesn’t, these additional configurations are just a distraction.

Anyway, if you find out that you are enjoying this system of blogging, here are links to a few additional configurations that you can perform.

- Customise the styling using the custom templates [1](http://docserver.scripting.com/drummer/blogging.opml#1628776805000), [2](http://ol.amitgawande.com/2021/10/13/170912.html?title=customTemplateWithDrummer)
- Build your blog [with one-click](http://docserver.scripting.com/drummer/blogging.opml#1628861390000) using dedicated icon
- Using Custom Domain for your blog. [PagePark](%20%20https://rudimentarylathe.wiki/#Using%20a%20custom%20domain%20with%20Drummer), [NGINX](https://rudimentarylathe.wiki/#Using%20a%20custom%20domain%20with%20Drummer)
- [Create a Glossary](http://docserver.scripting.com/drummer/blogging.opml#1629212543000) — a text replacement/substitution/expansion list
- [Embed Tweet](http://docserver.scripting.com/drummer/blogging.opml#1628781021000). [Embed YouTube video](http://docserver.scripting.com/drummer/blogging.opml#1628781065000). [Emoji Short Codes](http://docserver.scripting.com/drummer/blogging.opml#1628781273000).
- Enabling [HTTPS for Drummer Blog](http://scripting.com/drummer/blog/2021/10/15/203642.html?title=https) (evolving)

## A Few Additional Notes

1. There’s a Mac app (electron based) called [Electric Drummer](http://docserver.scripting.com/drummer/electricDrummer.opml) that can act as an outliner. However, you should avoid using it for blogging if you intend to blog from multiple systems. Changes made through the app can overwrite ones as done on the web Drummer. So thread carefully.
2. Drummer is evolving. Dave is working hard to make sure all serious reported issues are resolved. Early adopters are trying out a hundred things independently. If that sounds fun, the [Drummer support issues page](https://github.com/scripting/drummerSupport/issues) is the place to go.
3. You can stay-to-date with all things Drummer by following [this official blog](http://scripting.com/drummer/blog/).
4. How does Drummer cost zero? [Dave answers](http://scripting.com/2021/10/12.html#a114128).
5. Why is Drummer, and other software from Dave, so tightly coupled with Twitter? [Dave answers](http://scripting.com/2021/10/13/140500.html?title=whyWeUseTwitterIdentity).

—

I intend to use Drummer as a place where I form my thoughts over the time. The ease of the updating process makes posting unformed thoughts a breeze. So, in a way, this space represents the most raw me. You can follow this me as he experiments with [my Drummer blog](https://ol.amitgawande.com). And of course, there’s an [RSS feed](http://ol.amitgawande.com/rss.xml).
