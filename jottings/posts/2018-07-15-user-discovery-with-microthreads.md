---
title: User Discovery with Micro.threads
date: '2018-07-15 00:00:00'
slug: user-discovery-with-microthreads
tags: dev
---
I had [recently started](https://lab.amitgawande.com/update-on-micro-threads) working on updating Micro.threads application to focus on discovery, specifically user discovery. My social interactions on the internet have never been dull or frustrated since I joined Micro.blog. And it can largely be attributed to the extremely fine community of users that exists on the platform.

However, I had also realised that there were a lot many threads, many interactions that I was missing on, because finding new users was still not easy. Discover section exists, but it helped primarily to get new, interesting posts. There was a major section of the platform which could assist me to ease this problem. And that is people I follow and their posts in my stream.

Manton had [recently updated](http://www.manton.org/2018/07/12/following-users-ui.html) the default behaviour of a user profile’s “Following” section to display only “*a list of who someone is following that you aren’t following already*”. That itself is a huge improvement in identifying new users. But, for me, that too was a bit troublesome. I wanted to focus not just on the follow status, but the interactions; not just focus on whom someone I already follow, follows, but rather whom they interact with frequently.

So it was only just to build a system, first of all for myself that will discover more amazing users that I can follow, that I can interact with and learn from. And so I did.

I have been playing around with the user discovery section of Micro.threads. And I think it will help others too. Just [head over](http://microthreads.amitg.xyz) to the Micro.threads -> Discover section and give the application a try. You may find it helpful. You may not. But I think the feedback you share would be useful for me, and hopefully to the community too.

I believe this just acts as a placeholder until such discovery features are available in the official app itself. Till then, this would be a playground to identify more ways to discover interesting profiles and threads on Micro.blog.

---

I have made some key considerations at this point while developing and rolling this out.

1. You will have to sign in with your Micro.blog user id and an app token, which is discarded the moment you log out. I have no intention to maintain any accounts or credentials. I plan to use the `/account/signin` API from micro.blog in future; for now, app token is the quickest, officially supported way to get going.
2. I haven’t optimised the performance of discover algorithm to the fullest. I plan to get that done that gradually.
3. I am inclined to keep the information shown itself improving, and also add more ways to unearth user profiles and threads.This is just a first version that I was satisfied with and could roll out. I am already working on the threads parsing and discovery which I think will get done this weekend itself.
4. I do not think I can get this perfect or can stay focused without the feedback from you all. So, any and every feedback is welcome.
