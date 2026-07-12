---
title: 'Own your blog: With Ghost and Digital Ocean'
date: '2014-09-06 00:00:00'
slug: own-your-blog-with-ghost
tags: tech, writing, meta
---
![](https://images.amitgawande.com/2014/5fb6555cd2.jpg)

Image Credit: [Dave](https://www.flickr.com/photos/30093796@N07/10793050886)

Ever since I decided to own and host my site, i.e. basically ever since this place has existed, I was planning to write down my reasons and choices for the engines that run this site. Couple of feedbacks finally made me jot down the thoughts.

One thing I was sure about was I did not want to not control any of the knobs of my blog. So I had to go all in.

- Own the domain first
- Run and customise the blogging engine
- Host the engine

## Domain

Deciding on domain name was simpler part; that is once I had given up on all the crazy *pseudo-names* I wished my blog would have. So I went ahead with my real name. Simple.

To register a domain, there were a lot of options out there. Some were way cheaper but were sucky and known to follow shady-practises. Then there few that were comparatively costly, but simple.

I had heard so much about one such simple, no-nonsense domain registration service, [Hover](https://hover.com/Dpb5EhLf). Few visits to Hover and I decided Hover was the one that fit my *high-horse* attitude the most. I usually tend to support the service providers with principles. And it always comes at a cost.

So I registered my domain via Hover. The experience was simple and positively uncluttered. I recommend the service. Give it a go. You will be impressed.

## Blogging engine

I have been blogging for quite some time now and have owned the free blogs at Wordpress.com, blogger, tumblr and even posterous. I even hosted a blog with Wordpress.org. Each had their own benefits and shortcomings.

- Posterous was simple. But it was way too simple.
- Blogger allows heavy customisation, and even monetization via Google AdWords. But it is way too childish. It does not have a professional, or a *'mature'* look to it.
- Tumblr has nice social sharing features. But that is what it is. It is more of a social network for bloggers rather than a blogging engine. Plus majority of the themes are not good for text heavy posts, which mine always are. It's perfect for images, especially gifs.
- Wordpress.com/.org is the biggie in the space. It has everything possible under the sun. Customisation, extensibility, theming. But it is way too heavy. And far too common. I never like *common*.

So I was on a look-out for an option that is simple, lite & powerful and gives me a lot of control with what I can do. Enter [Ghost](https://ghost.org/).

Ghost is a simple open source blogging platform that you can completely own. It provides simple writing tools. I have already detailed what I like about Ghost in the [first post here](https://mb.amitgawande.com/heres-to-another-start/). Even the community has accepted it, so there are a lot of customisation options available too.

Plus if you like coding even a bit, there is nothing better. I had my Ghost blog running on my local machine and I was satisfied, only after some customisation i.e. I adopted and adapted the [Vapor theme](https://github.com/sethlilly/Vapor) from [Seth Lilly](http://sethlilly.com/).

All that remained was to make it available on the internet.

## Hosting

Final call I had to make was about how to host the blog I had running on my local machine. One thing I did not want to do was go with a PaaS solution; basically the solutions that provide you just the platform where you can upload the blog and you are up.

In a way, Ghost made my decision to go against PaaS easier. There are hardly such services that support node.js, javascript based platform, on which Ghost is built.

I had decided to either go all in, i.e. get a virtual server (VPS) or simply not worry about hosting myself.

Ghost allows you both the options. You can either go [pro](https://ghost.org/pricing/) with Ghost and let the team handle the hosting for you, like wordpress.com. Second options is to go free and host it yourself. I knew I wanted to go with the second option. And I did.

For getting VPS, I just had two options shortlisted, [Linode](https://www.linode.com/) or [Digital Ocean](https://www.digitalocean.com/). Linode was costlier. A more pro-dev friendly. Not something I was ready to sign up for with such simple requirements as mine.

On the other hand I had earlier experience, mostly positive, with Digital Ocean. Plus it had [Ghost application pre-built](https://www.digitalocean.com/community/tutorials/how-to-use-the-digitalocean-ghost-application).

So it was really as simple as creating a droplet and I had my blog up. Finally, I also wanted to secure up the Linux node, and an amazing [article](http://feross.org/how-to-setup-your-linode/) from Feross Aboukhadijeh got me rolling. It is written for a Linode node; but it can very well work for any Linux server out there. Do not forget to follow these steps. They are must if you are to keep the node running even for short time.

---

So a day in and I had a secure Linux VPS node running my blog which was completely customised by me, as per my needs. And it was satisfactory experience and a fruitful journey.
