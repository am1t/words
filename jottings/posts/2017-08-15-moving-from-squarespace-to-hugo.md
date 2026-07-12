---
title: Moving from Squarespace to Hugo
date: '2017-08-15 00:00:00'
slug: moving-from-squarespace-to-hugo
tags: tech, life
---
This is my personal place, a destination where one can find every thought I ever post on the web, anywhere. At times it originates, and so just exists, here. There are also times when it’s [published](https://medium.com) at [some](https://theweeklyknob.com/) [other](https://medium.com/misplaced-identities) [places](https://crossingenres.com/) first, but is also made available here. It has been in existence since 2008 and just like every year, this time too I wanted another fresh start for this place.

I have already documented all the [history behind](https://mb.amitgawande.com/things-are-changing/#simplicity-vs-customisation) and the [context for](https://mb.amitgawande.com/things-are-changing/#enter-hugo) the existence of this site and this page. Here, I intend to document all there’s to know about this site.

Before I get to the details, this is what I set to achieve when I began.

1. A website designed, in and out, to my liking, with every knob controlled by me.
2. A landing page with a brief about me and the site. One that clearly links to the key content.
3. Clean and simple experience, while reading a post or navigating the site.
4. Consistent writing experience, preferably offline, across mobile and desktop.
5. Source control for the whole place. No fallouts from brain freezes.

I do not believe what I sought out was that complex. So I was confident I could get this working.

**Here’s the `TL;DR` version of what I have achieved.**
**1.** ~~This~~ My old site was built with Hugo — it is extremely simple, highly customisable, well documented and has an active community. It’s difficult to beat all of that. [∞](#core-engine-hugo)
**2.** The look and layout of this site is themed by an extremely personalised port of the original ‘ghostwriter’ theme. I intend to open-source the same soon. [∞](#personalising-the-look-layout)
**3.** The source for the complete website along with all the posts, as markdown files, resides in GitHub. Every change to this setup is driven as it would be in a standard git project. [∞](#cushioning-against-brain-freeze)
**4.** Contents from Squarespace were exported into a Wordpress package first. They were converted into markdown files using ExitWP. Followed by cleanup. And deploy. [∞](#migrating-the-content)
**5.** This site is deployed by Netlify. With continuous deployment and one-click SSL for custom domains possible with minimum configuration, the choice was pretty simple. [∞](#deploying-with-netlify)

## Core Engine - Hugo

I had always wanted to attempt a site creation from scratch, but I failed miserably every single time. Given I had ample time before my Squarespace subscription expired, I attempted it again this time. I believe I did not fail. This is a static site, built with [Hugo](http://gohugo.io/). It was the ease with which I could get a site running on my dev environment via Hugo that convinced me about the viability of this whole project. If you do not believe, just head over to the Hugo docs for a *[quick start](http://gohugo.io/getting-started/quick-start/)* and begin. You will have a site running by step two. It is that easy.

You would have also realised how well document the whole framework is from your visit to the quick start guide. There is nothing that you want to achieve that isn’t documented. In addition, given that Hugo is written in [GoLang](https://golang.org/), it gave me an opportunity to learn a new language. Post that, every need of mine to get the things just right was just a code snippet away.

For example, find below a snippet for fetching a list of random five articles. Yes, it is easy. And a lot powerful.

```
{{ $pag := where .Data.Pages "type" "post" } } {{ range (shuffle $pag | first 5) } } {{ ....custom.... } } {{ end } }
```

And if it does turn out that there is some tricky edge case that you just can’t get your head around (or you are being plain, simple lazy), there is a [thriving community](https://discourse.gohugo.io) of fellow users which is extremely active and a lot helpful.

**TL;DR**: Hugo is simple, highly customisable, well documented and has an active community. It’s difficult to beat that.

## Personalising the look & layout

Once I had the core finalised, I shifted my attention to personalising the site. And again Hugo comes with a lot of good looking [themes](http://themes.gohugo.io/) — extremely minimalistic to fully loaded. You will always find the one for your liking there.

If you, like me, do not find one that ticks all the boxes for you, you can select any that is closest and get to personalising. All the themes come with the source code. So if it suits you, let the developer in you go wild.

I began with a theme “[Ghostwriter](https://themes.gohugo.io/ghostwriter/)”. It was simple and I could see how it can be extended to enable every aspect that I wanted to achieve. So I began working. After a week of customisation, I could finally see the site shaping up just the way I imagined.

~~I intend to soon open source the changes I have made to the original theme. I am working on cleaning up the source and committing.~~ All the enhancements and personalisations added to the theme are available at Github. If you like the theme that you see and if you are using Hugo for building your Static website, you can download and use the theme from [here](https://github.com/am1t/ghostwriter).

**TL;DR**: The look and layout of this site is themed with an extremely [personalised and open-sourced port](https://github.com/am1t/ghostwriter) of the original ‘ghostwriter’ theme. ~~I intend to open-source the same soon.~~

## Cushioning against brain freeze

Yes. Commits and port. I am not letting another of my brain freeze moments to spoil all the efforts the put in over the years. Refer the history section I mentioned in my introduction above.

So whole website is a git project. It is currently maintained as a private repository at [GitHub](https://github.com/am1t/). Every change, major or minor is committed. Every milestone is tagged as release. And every major enhancement is pull request. No, I am not taking any risk with myself this time. Here is a snapshot for the effort that has gone in to bring the v1 of this site.

![](https://images.amitgawande.com/2017/5586b98e43.jpg)

Do I intend to make the source of this website public? Well, initially I wanted to do just that. However, I do want to keep my messy drafts, be it to the posts or the website, just to myself. I could not find a public way to achieve that. So as of now, the source stays private.

**TL;DR**: The source for the complete website along with all the posts, as markdown files, [resides in GitHub](https://github.com/am1t/). Every change to this setup is driven as it would be in a standard git project.

## Migrating the content

Talking about the posts, I had to bring the old entries along from Squarespace. After all, this is also a place for my writings. I would not want to loose any of my old ones[1](#footnote-1DXK).

This time, though, I did not have the luxury of the out-of-box imports. I had to do it on my own. Well, I did have a couple of points playing on my side.

- I have been writing all my posts in [markdown](https://daringfireball.net/projects/markdown/) format and exporting them as required.
- Current setup with Hugo is all markdown driven, where every content exists as a `.md` file.

So, all I had to do was find a way to export the content from Squarespace as markdown files. I wish it was that simple; it wasn’t. The only option that Squarespace supports for export is as a Wordpress package. However, anyone who has been blogging for even a slightest of time would know Wordpress package should be fine. Because there is nothing to be done with a Wordpress package that no one else has already tried. Just getting markdown files out of that must be a cakewalk. Markdown, after all, is a geek’s solution.

And as I thought, it already is handled. [ExitWP](https://github.com/thomasf/exitwp) is a great tool to migrate a Wordpress blog to a static site. It is introduced as a tool to convert to “*the [jekyll](https://github.com/mojombo/jekyll/) blog engine*”. But that should be fine. Both Jekyll and Hugo use markdown files as content.

After going through the steps as documented at the git repo for ExitWP, I had all the content available as markdown files[2](#footnote-2DXK). It did need the below minor cleanup.

- Images had to be handled separately. All references were to the Squarespace domain. Thankfully, I maintain a credit link with every image to the original one. So I just had to re-download, compress and deploy them.
- Front matter needed porting to the Hugo standard. I did weigh in the option to write a script to do that. But then ended up siding on doing it manually.
- Post content did need some minor fixing. ExitWP has some issue handling and regenerating the emphasis, especially around symbols (for example, quotation marks, dashes etc).

Deploy the post, test each one from the post link on dev and I had all my content back. Thanks to this effort, I believe I never have to worry about porting out my content ever. Every published copy of a post stays as a raw file with me.

**TL;DR**: Export contents from Squarespace to Wordpress package. Use ExitWP to convert it into markdown files. Cleanup. Deploy.

## Deploying with Netlify

Once I had a site running on dev and tested multiple times to bring it to my liking, I had to start thinking on a place to deploy it. And of course, Hugo has all the possible options [well documented](https://gohugo.io/hosting-and-deployment/).

As my code was in GitHub, the first option I tried was to [deploy it](https://gohugo.io/hosting-and-deployment/hosting-on-github/) on GitHub Pages. I configured Hugo to generate the static pages in a defined directory (configured as submodule for the GitHub pages repository). I built my site, pushed the changes and deployed, and it all looked fine. However, there was just one problem — the deployment workflow was a bit messy. In addition there were few more niggles[3](#footnote-3DXK).

- There is no provision for SSL with custom domains. So they cannot yet be delivered over secure `http`.
- Auto-triggering for build and deploy had to be configured as web hooks.
- Given the deployment workflow, publishing from mobile was just out of question.

On reading some more, I found a far simpler option in [Netlify](https://www.netlify.com/). Again I will let the official document explain itself.

> Netlify builds, deploys and hosts your front end. It provides continuous deployment services, global CDN, ultra-fast DNS, atomic deploys, instant cache invalidation, one-click SSL, a browser-based interface, a CLI, and many other features for managing your Hugo website.

One might say jargon, but there are key needs I had which GitHub pages just didn’t handle — a couple being continuous deployment and one-click SSL. So I did [another deployment](https://gohugo.io/hosting-and-deployment/hosting-on-netlify/) with Netlify and again fell for the simplicity of the things involved. No configuration head-ache. No custom workflow to handle the built site separately.

> Write Frontend Code. Push it. We handle the rest.

Yes it, indeed, is that easy. It doesn’t matter then where you push to the repository from, mobile or desktop.

There is one issue with the Hugo documentation though. One does not need to trigger a build command with Hugo version number appended in it. Just configure a parameter in the build for the version of your Hugo environment.

![](https://images.amitgawande.com/2017/bdc49e6024.jpg)

Once the Netlify account was created and the continuous deployment for the site setup, I just followed the documentation for using custom domain and setting up SSL. The site was live.

**TL;DR**: The deployment of this site is handled by Netlify. With continuous deployment and one-click SSL for custom domains possible with minimum configuration, the choice was pretty simple.

## Change log

So to summarise, I have first releasable version of this website ready. Built with Hugo. Themed with Ghostwriter. Run with Netlify. And of course, it is just v1.

**Musings Et Al. v1:** First version of the website with all the clogs designed and working as planned. It hosts below custom features.

- Support for write-up section on homepage driven by config.toml
- Support for headshot on the homepage
- Support for displaying the latest featured post on homepage
- Support for link posts (via refs param in front matter)
- Support for related post along below the content of a post
- Link to the image credit (via imgsrc param in front matter)

---

1. As a side note, all my old posts still exist on Wordpress. You can read them [here](https://snoozyrealm.wordpress.com).[↩](#ref-1DXK)
2. I did face some difficulties while installing the dependencies. In case you hit them too, just download them from the official sites and have them available in the `classpath`. It doesn’t matter the approach is crude, it should get the work done.[↩](#ref-2DXK)
3. In case you do want to go a
   head with GitHub Pages, I would suggest you go ahead with the option of [deploying](https://gohugo.io/hosting-and-deployment/hosting-on-github/#deployment-from-your-master-branch) from the master branch itself. Hugo documents this as the last option. But I feel this is simpler and a viable option.[↩](#ref-3DXK)
