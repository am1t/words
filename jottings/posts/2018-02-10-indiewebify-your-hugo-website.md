---
title: IndieWebify Your Hugo Website
date: '2018-02-10 17:35:00'
slug: indiewebify-your-hugo-website
tags: dev
ghost_id: 68511293eb03dc000150c810
---
For many, that’s too much jargon in the title. So, to the basics first, I would not go into the [history](https://www.amitgawande.com/things-are-changing/) or [setup](http://amitgawande.com/moving-from-squarespace-to-hugo/) of this website. `TL;DR` this site ~~is~~ was at one time built with a static site generator [Hugo](http://gohugo.io/) themed by [a custom port](https://github.com/am1t/ghostwriter) of Ghostwriter theme. In this post, I want to focus mainly on the why and how of *IndieWeb*.

Ever since I built this site, I had grown pretty determined to styling this exactly to my liking. Every section in here is thought through and has a purpose. When I was happy with what I had at the core, I started exploring how to make this my primary identity online. I had realised that thanks to all the silos of Facebook, Twitter, Medium, et al., my online presence was scattered across multiple sites. [IndieWeb](https://indieweb.org/) calls it “*sharecropping your content*”.

> Our online content and identities are becoming more important and sometimes even critical to our lives. Neither are secure in the hands of random ephemeral startups or big silos. We should be the holders of our online presence. When you post something on the web, it should belong to you, not a corporation. Too many companies have gone out of business and lost all of their users’ data. By joining the IndieWeb, your content stays yours and in your control.

Yes, absolutely. I couldn’t stop nodding my head in agreement as I read along. I want this site to be the primary place where my content exists. And I hope everyone spending time online, doing as basic a task as consuming content on social media and liking stuff there, should do so first, primarily on a place he controls. Post on your website and syndicate it everywhere else.

It doesn’t take much to enable this. The steps I mention below can be incorporated into any platform you base your site on. Here, I specifically jot down the steps I took for my site. It’s just a set of principles, many of which are already [W3C Recommendations](https://www.w3.org/wiki/Socialwg).

## Hugo Basics

Hugo allows you to completely define how your website is structured and styled, including the behaviour of the pages. Typically, a user chooses a theme from a varied selection and lets it handle everything. However, you always have access to the theme files and the code—just some Go snippets spread across HTML pages, making it fairly simple to modify the same.

1. Familiarise yourself with your theme, typically present in `/themes/`
2. Identify the customisations made
3. Make changes to the code, typically present either in `layouts` folder of your site or the theme

## Web Sign-in via IndieAuth

The first step in owning your identity online is allowing your site to be your identity online. All this needs is to declare your social network profiles openly as `rel-me` links and link those profiles back to your site. This allows you to log in to any IndieAuth-enabled websites using just your website homepage; no need to create an account or maintain more passwords.

For me, I already had links to my social network profiles in my `/layouts/partials/header.html` file. All I had to do was add a `rel-me` tag to it — a sample snippet to the Twitter profile below.

```html
<a data-hint="Twitter" title="Twitter" href="{{ . }}" target="_blank" rel="me"> 
      ... 
</a>
```

I have selected Twitter and Github as the social network profiles to be used for identification.

You must also declare the service, which will act as an `authorization endpoint` when needed. This is used by other services, mostly IndieAuth clients, to validate your identity. To configure this, add the below link to your site’s `head`.

## Identity via h-card

Of course, once you decide your site will be your identity, your profile online, you need to make sure it clearly declares your basic information, i.e. define that identity. This allows other sites and services to know more about you. This is done via an `h-card`, a part of the [microformats2](http://microformats.org/wiki/microformats2#h-card) specification.

I added an `h-card` with my name, nickname, email and photo in `/layouts/partials/footer.html`

```html
<p class="h-card vcard">
   <a style="text-decoration: none" href={{ .Site.BaseURL }} class="p-name u-url url author metatag" rel="me"> {{ .Site.Author.name }} </a> /
   <a class="p-nickname u-email email metatag" rel="me" href="mailto:{{ .Site.Author.email }}"> {{ .Site.Author.nick }} </a>
   <img class="u-photo" src="img/headshot.png" alt="" />
</p>
```

This way, your social networks do not define your identity; rather, it is you who declare and control it.

## Content definition with microformats

After defining yourself, the next step is to define your content. It is important for other sites and services not just to identify you but your content too. Just add a `h-entry` markup (again, part of microformats2 specification) to the posts template. This is possible by identifying the layouts that handle your posts and adding some markups to them.

I had to modify the `/layouts/partials/post-header.html`, `/layouts/partials/post-content.html` and `/layouts/post/single.html`. The information I declare is post title (`p-name`), post URL (`u-url`), author (`p-author`), date (`dt-published`) and, of course, the content (`e-content`). Finally, a typical post template looks as follows.

```html
<article class="h-entry"> 
    <h1 class="post-title p-name" itemprop="name headline">{{ .Title }}</h1>
    <span>Published <a class="u-url" href="{{ .Permalink }}"> 
        <time class="dt-published">{{ .Date }}</time>
    </a> </span> 
    <span>by</span> <span class="p-author">{{ .Params.author | default .Site.Author.name }}</span> 
    <div class="post-content clearfix e-content" itemprop="articleBody"> {{ .Content }} </div> 
</article>
```

## Cross-site conversations via Webmentions

All the steps done till now allow defining your and your content’s identity for external websites. However, how do you enable conservation with them? If enabled, every time you or your website is referenced online, if they are IndieWeb Level 2 enabled, you are notified by Webmentions, another W3C Recommendation.

> Webmention is a simple way to automatically notify any URL when you link to it on your site. From the receivers perspective, it’s a way to request notification when other sites link to it.

In short, it is a modern alternative to the erstwhile Pingback mechanism in prime blogging days. Of course, you must enable your site to send and receive web mentions.

To send a webmention to the page you have referenced, you can notify by

- using a form made available on the referenced page
- using curl or one of the many open-source clients

If the referenced site can receive webmentions, they would be notified that you have linked to them. But how do you enable your site to receive webmention?

Again, it involves hosting and declaring a webmention endpoint. Of course, the active community already has a solution for this - [webmention.io](https://webmention.io/) by [Pelle Wessman](https://voxpelli.com/). It is “a hosted service created to easily handle webmentions”. All you have to do is sign in with your domain (i.e. validate your identity) and let webmention.io receive all mentions to your site. Once that’s done, declare the web mention endpoint as below in your `head`.

```html
<link rel="webmention" href="https://webmention.io/username/webmention" />
```

Webmention.io also provides APIs to fetch the webmentions to your content/site. You can implement your solution for fetching and displaying these mentions along with posts. I have a simple Javascript to fetch and display them with posts — this is still a work in progress.

## Interactions from Social Media

Though references to your posts from IndieWeb sites are handled, what about the references made on Twitter or Facebook? It can be in any form of response (i.e. likes, retweets/reposts) to the syndicated post. Of course, they do not send webmentions (I wish they did).

One option is to implement your [backfeed](https://indieweb.org/backfeed) to poll for such interactions and handle them as a response. Of course, the community has ensured there is a simpler hosted option. Enter [Bridgy](https://indieweb.org/Bridgy).

> Bridgy is an open source project and proxy that implements backfeed and POSSE as a service. Bridgy sends webmentions for comments, likes, etc. on Facebook, Twitter, Google+, Instagram, and Flickr.

I was set . Now, every time there is an interaction about my post on a service, Bridgy captures that and sends a webmention to my endpoint.

## One More Thing - Micropub

At this point, I had completely IndieWebified this site. I understand it might get overwhelming if you read it as a long sequence of steps. But trust me, the changes to be made are neither too many nor too complicated. It is just setting your site with appropriate markups and endpoints. There is also a really helpful guide in [IndieWebify.me](http://indiewebify.me/) that walks you through every step, and also validates if you have everything set up correctly. But if you still do not want to go through the trouble, I have [open-sourced](https://github.com/am1t/ghostwriter) the changes I made to the theme I was using. You can use this theme, style it as you like, if needed, and get going.

For me though, there was one more thing pending. At the same time I was doing setting this up, [micro.blog](https://micro.blog/) had caught my attention. I already had [a section](https://www.amitgawande.com/journal) dedicated for the microposts. I configured a feed for these posts, the microblogs, to syndicate to my micro.blog timeline too. I was enjoying the interactions I was being part of with the community there.

There was just one issue, I could not use it to post to my site. My process to post to this site still involved text editors and git commits. I wish it was simpler  
 — at least for such microblogs. I wish I could just *post* from micro.blog and have an entry made. Enter [Micropub](https://indieweb.org/Micropub), again another W3C Recommendation.

It is the trickiest part of the puzzle. Again it involves creating an endpoint which can accept a request to post, verify that it is coming from an authorised source and finally create the post file in required structure for Hugo to build and deploy. I have enabled the support for Micropub on this site, thanks again to [Paul](https://voxpelli.com/).

I would like to detail out the solution I have running. But that would be a topic for another detailed post. In short, I hosted Paul’s open-source [micropub endpoint](https://github.com/am1t/webpage-micropub-to-github), configured it to generate the post in the format I need, configured it to commit to my website source at GitHub, declared it as my site’s micropub endpoint and then let Netlify handle the rest.

You bet I would say it was all simple. I won’t.

---

I have realised that the idea of owning your identity online is a crucial facet of protecting yourself and your content in this fragile, siloed world of internet. It may be perceived as ostentatious by many, but it is rather humble, driven by a virtuous intent. There is nothing wrong in attempting to control what you post online, to make sure it stays online till you want it to. IndieWeb project allows that.

I do also realise that it is naive to think no one getting online will find this process irksome. Even though well defined, the principles are not for all. The simplicity of using and posting on social media services will continue to attract regular users. However, here’s wishing that at least a part of these users are inspired to get their own personal domain. After all, it’s the first step in [getting started](https://indieweb.org/Getting_Started#Get_a_personal_domain) on this IndieWeb journey.

**Update (23rd September 2020):** Updated the post to clarify the site has been moved away from Hugo recently.
