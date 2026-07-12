---
title: Directory of Microbloggers
date: '2018-08-29 00:00:00'
slug: directory-of-microbloggers
tags: tech, writing, meta
---
We need a directory of microbloggers. This fact is clear from the sheer number of discussions that happen on the [Micro.blog](https://micro.blog) platform asking for recommendations on users by interests, or geography or something else.

I just wanted to put down my thoughts on what such a directory would need to have for it to be helpful and not polluted with mess.

1. Directory needs to have a vouch mechanism. A user mentions some information about himself, his followers vouch for that. And the vouch’s what matters. Without such a mechanism, the system is prone to abuse, where people can pollute it with catchy tags without nothing to back it up with. We know how such systems are gamed. SEO. App Store tag words.
2. Other users should be able to associate more information about a person, an extension of vouch. They only get shown if the concerned person accepts.
3. Group types need to be limited. Possible options for groups need to be predefined. So geography - possibly timezones or countries, interests - sports or tech or writing etc, current events followed. Without this, it’s again prone to abuse. This may also make aggregation/interface easier to manage. Tagmoji is already a good example.
4. As [Brad Enslen](https://micro.blog/bradenslen/839473) opined, may be it should not be limited to micro.blog platform. One should be able to provide other details too. May be via IndieAuth signin?
5. An option to add to directory directly from a post would be handy. It may also allow building metadata for the vouch system, if needed.
6. A person’s interests, geography, isn’t it an extension of one’s identity? Can it not be captured as part of one’s `h-card`?

Can such a directory exist outside of Micro.blog? Sure (I even had basic one running on [Micro.threads](http://microthreads.amitg.xyz/micro) dev). But for it to be helpful it would need a significant number of users adding their information to such a service. I believe it fits best with the platform, as the list of users is already available. With some metadata added, a directory page, just like there are Tagmoji pages for posts, can be enabled for users. This will avoid creating a parallel user list, which will always be lesser than what would exists with the platform.

Directory can be made as tricky as it can get. But it is sure one is required as the number of microbloggers grow. Blogrolls, personal directories on individual blogs are good starts. We need a place where that can be brought all together. And displayed easily on demand.
