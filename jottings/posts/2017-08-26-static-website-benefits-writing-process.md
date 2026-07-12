---
title: 'Static Website: Benefits & Writing Process'
date: '2017-08-26 00:00:00'
slug: static-website-benefits-writing-process
tags: tech, writing, meta
---
I have [recently converted](https://mb.amitgawande.com/things-are-changing/) my blog to a website and, as I [have already documented](https://mb.amitgawande.com/page/setup), I serve it as a static website. I have preferred this approach over a dynamic one that gets driven by a full-fledged [blogging software](https://Wordpress.org) or a [publishing platform](https://ghost.org/). Of course, these were not the only possible options. As is so [well captured](https://www.thesitewizard.com/gettingstarted/difference-cms-site-builder.shtml) by Christopher Heng at his website[1](#footnote-18IH), the options are just too many.

It wasn’t an easy call to select one, it never is. Every option one chooses has its own advantages and disadvantages. And, of course, going with a standalone website builder and serving the content as *pure* HTML had its own too. For me, though, benefits really outweighed the challenges.

![writing setup](https://images.amitgawande.com/2017/writing-setup.jpg)

## Why choose a static website for blogs?

A static website is nothing but a string of HTML pages served by a hosted web server. Every document, blog post or update is a plain HTML page. Given this simplicity of existence, it has some key benefits that attracted me.

1. It’s quick and cheap to develop
2. It’s easy and cheap to host
3. It’s fast to be served

Again, Hugo [captures](https://gohugo.io/about/benefits/) them the best.

> Improved performance, security and ease of use are just a few of the reasons static site generators are so appealing.
>
>  The most noticeable is performance. HTTP servers are very good at sending files—so good, in fact, that you can effectively serve the same number of pages with a fraction of the memory and CPU needed for a dynamic site.

I have already seen this benefit realised with the performance of my website too.

> Static website has really helped the overall performance — avg response time has gone down from 1300ms to 300ms. 👊🏽😊 <https://t.co/pPoQNMXCsM> [pic.twitter.com/udsTKM0RpO](https://t.co/udsTKM0RpO)
>
> — Amit Gawande (@\_am1t) [August 18, 2017](https://twitter.com/_am1t/status/898586698895904768?ref_src=twsrc%5Etfw)

These benefits should attract every blogger out there looking for a simple manageable solution for their blogs. *Then why aren’t all blogs served as static website?* The answer is, of course, nothing’s perfect and static websites are not for all. They bring with themselves a list of challenges.

Creating static pages needs a bit of programming skill, and a lot of interest to slog it out over web design and development. In the longer run, maintaining these pages can become cumbersome if they are to be updated even so slightly, every now and then. Especially, if all you care about is the text you write, what gets placed around it is really not of much an interest to you. All you want to do is write and publish. You don’t want to awaken the web dev in you every time you want your footer to be updated or a page to be added.

Ironically, a rush to dynamic websites to solve this challenge is totally counter to what you really care about, the text. The text is light, the page carrying them needs to be the same. To have these generated every time someone requests for them[2](#footnote-28IH) is just too costly. And to have them stored as database entries is just too messy. **It is text, it needs to be stored as text.**

Hugo (and [the likes](https://www.smashingmagazine.com/2015/11/static-website-generators-jekyll-middleman-roots-hugo-review/)) provides a nice middle ground. Smashing Magazine summarizes it well.

> Each generator takes a repository with plain-text files, runs one or more compilation phases, and spits out a folder with a static website that can be hosted anywhere. No PHP or database needed.
>
>  Hugo takes caching a step further and all HTML files are rendered on your computer. You can review the files locally before copying them to the computer hosting the HTTP server.

Isn’t it, after all, better to make the whole user-facing part of your website into a cache of servable HTML pages and have it generated and deployed locally — without loading the server with a programming runtime or a database? This is exactly what Hugo enables.

This helps to design, build, test and maintain the website without much of a hassle. And with Hugo, I have already hit all the benefits of a static website I mentioned above, bypassing the challenges it presents. A one-time effort to design and build the website is handled with little pain; now I can focus on writing.

## Workflow to write, especially on mobile

There is another challenge with such websites that are built locally and served statically - all they contain is the final product, the HTMLs. Any change needs to be followed by a rebuild and redeploy. There is no online CMS to handle your content from a browser, especially no WYSIWYG[3](#footnote-38IH) web editor to create or modify your posts. Of course, one way to handle this is to deploy a [separate light-weight CMS](https://webmasters.stackexchange.com/questions/1325/allowing-customers-to-edit-static-website-via-wysiwyg#1438).

But for blogging, there is a simple way. All you need is a continuous deployment setup and a couple of applications to handle writing and publishing your posts. I have [already explained](https://mb.amitgawande.com/page/setup/#deploying-with-netlify) how Netlify has helped me achieve the first part. Below is how I circumvent the second challenge[4](#footnote-48IH).

1. **Write**: It is important you can write from multiple places, especially your mobile devices. Web editors of the blogging platforms allow you just that, keeping your drafts ready for you to pick up from where you left earlier. A static website lacks this and so calls for some other alternatives.

   I use [iA Writer](https://ia.net/writer/) to write all my posts. It has apps for all the platforms I own, iOS and macOS. It allows me to focus mainly on writing, automatically saving all the words as I write them. It also keeps all the posts synced up across all the devices, granting me the convenience of cross-device writing that web editors enable. I find it goes even a step further as it provides me a consistent experience across all the platforms, as compared to the messy state of online writing — more on this later.
2. **Deploy**: Doing this from desktop was always trivial; handling this from mobile was what puzzled me. However I managed to get a workable solution. Once I have the post ready, I use [Git2Go](https://git2go.com/) to push the final Markdown (.md) files to my Git repository. Net
   lify does the rest, making the post available at the website. Any minor modifications, it is just an update with iA Writer to these .md files and a push via Git2Go.
3. **Workflow**: Though it is easy to say just write at one place and push to repository, it would be a significant effort to get a file, as per Hugo-defined format, ready for writing. Any generator needs some added metadata, *front matter* in Hugo land, embedded along with the content to create a serve-ready HTML. Adding this to every post I write would have been a downer; especially with my intention of writing different types of posts - fiction, non-fiction and links.

   It needed [Workflow](https://www.workflow.is/), I mean literally. The Workflow app is a boon for anyone who wants to automate common tasks on iOS. It is a powerful tool with hundreds of actions that can be easily stitched together to create a workflow — one that can handle complex tasks with a single click. For example, here’s my workflow to get a link post ready.

- Once I find a link I want to share and add some comment on, I open it in Safari and just copy the content I want to comment on
- I trigger the relevant workflow from the share sheet
- Workflow then
  - fetches the template for the link post
  - adds the link to the metadata as the source URL
  - adds the current date and time as the post date
  - adds the title I provide (or the title of original post if none provided)
  - takes the content from clipboard, adds to the content body
  - saves the file and opens it in iA Writer to be edited further
- Once the post is ready to be published, I just export the post as Markdown from iA Writer and import it to Git2Go in the content section.
- Commit & Push, and the link post is ready on the website.

This is just one such workflow. I have managed to create one each for every type of posts I write. Workflow does the routine heavy lifting for me, allowing me to focus on writing.

I know just this effort might be overwhelming for many. The act of building, managing and updating the static websites is not everybody’s cup of tea. However, for me, I have found that this triplet of enablers - iA Writer, Git2Go and Workflow - serves me well. I have never been so satisfied with either the website or the process involved in publishing to it. I am pretty confident this setup, with minor modifications, will last long.

---

1. Heng’s website “[theSiteWizard](https://www.netlify.com/blog/2016/05/02/top-ten-static-website-generators/)” is really a great resource for anyone interested in building or maintaining their own websites. It doesn’t matter the scale — be it for an individual blog or a full fletched website for your group.[↩](#ref-18IH)
2. Of course, the dynamic generators, especially the CMSes like Wordpress and other, do handle this well now-a-days by caching the HTML pages to avoid the unnecessary delays of generating and delivering the pages to the end users.[↩](#ref-28IH)
3. What You See Is What You Get[↩](#ref-38IH)
4. I focus mainly on the platforms I own i.e. iOS and macOS. Of course, if you have a different set of devices, your solution may vary, or may not exists at all (chances are slim for that though).[↩](#ref-48IH)
