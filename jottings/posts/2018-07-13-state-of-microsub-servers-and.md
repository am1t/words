---
title: State of Microsub Servers and Client
date: '2018-07-13 00:00:00'
slug: state-of-microsub-servers-and
tags: writing, meta
---
I had recently [expressed](https://mb.amitgawande.com/journal/39619/) an excited opinion on Microsub, the “new” Indieweb spec. I could then see the potential of the standard and also the available solutions, the server and the clients, around it.

> I have seen Monocle in action now and realise the power of Microsub standard. I do not think I can read feeds in any other manner now. This is fantastic!

The fact that there exists a hosted Microsub server in Aperture is a great start, it has given a chance to many to get started knowing the standard early. And I know people like Aaron Parecki [are hard at work](https://aaronparecki.com/2018/03/12/17/building-an-indieweb-reader) to continue improving the clients like Monocle. However, I think my excitement was premature.

No doubt, the core technology behind Microsub is solid and it can eventually redefine the way feeds are subscribed to and consumed. And bundled with Micropub to post actions of the type *like*, *reply*, *repost* directly to your website right from your reading view makes it absolutely magical.

So I don’t blame myself that I got excited about the standard seeing the potential of what can be achieved when all these Indieweb standards work seamlessly together. *Seamless* is the key though. For the last few days, I have been trying to use Monocle as my primary feed reader. Unfortunately, the whole system has some way to go before I actually can. I am just noting down the frustrations I encountered using the system.

1. Keeping the read status of the posts in sync is flaky. Many of the posts I have read already are shown again. Some of the posts that should have already popped up are not available for some time. When they finally are, they are available in bulk. If I understand the standard correctly, it is the server at fault here. And it is only a single client involved at this point.
2. Subscribing to feeds with the server is not easy. Not user experience wise, but again in terms of the unreliability of the posts appearing in the stream. At times, there are 0 posts fetched; at other times, there is a bulk of hundreds of posts. It poses a challenge for the client.
3. And to the client. I think we can learn from the available feed readers and focus on the must-have features - which are primarily around showing available posts. Monocle currently cannot be configured to show only the new posts. Filter options are limited. Sorting options are limited. Marking read/unread is unavailable. Subscribing to new feeds is not possible (even though spec has a `follow` API which I hope Aperture exposes). Few of these might be nitpicking, but they are important when the reference for most new users would be existing feed readers.
4. The concept of Microsub server and client, former for maintaining the feeds and the later for displaying them, sounds great. However, to get people on board, we will need at least one application that does the job of both. Wish Monocle and Aperture were two components of a single application.

I know the standard is still a work in progress, especially the server and client applications. So no doubt there would be some kinks in the working. The intention of this post is in no way to demean the people involved or pinpoint at the failures. My intention is to capture my thoughts on why, even though I want to, I cannot yet use the current applications in place. The standard is making significant headway and I hope I would soon be able to benefit from the system. As Aaron says in his introductory post I referenced above -

> My goal with this is to use this as my primary online dashboard to follow all kinds of content, as well as being able to interact with the content without leaving the interface.

Amen to that. Unfortunately, now is not the right time. So I [am back](https://mb.amitgawande.com/journal/40523/) to my search for that perfect feed reading service.
