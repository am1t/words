---
title: Micro.Threads Update
date: '2018-08-04 00:00:00'
slug: microthreads-update
tags: dev
---
**Update [04-08 17:40]: Discovery of threads**

- Discover new threads from timeline
- Refresh explore threads if not refreshed for 2 hours
- Minor styling changes

---

**Update [04-08 17:40]: Possible options to unearth in Dashboard**

1. ~~People I do not follow, but are in my stream (via interactions) - with a easy follow button~~ - Done
2. ~~Find original posts in the stream - with option to respond~~
3. ~~People recommendation from Discover~~ - Done
4. People recommendation by emojitag
5. ~~Longest threads~~
6. Recommendations from threads — add to recommendations thread
7. ~~Post reply-of~~ - API seems to not expose this information

---

**Update [20-07 23:43]: User information display**

- Added user information for recommended users
- Follow directly from app, with an option to open profile at Micro.blog
- Thread recommendations purging of old items on refresh
- Upgraded packages to latest - npm-check

---

**Update [17-07 00:50]: Refresh to the Micro.threads**

- Added performance improvements by rewriting using Promises.
- Added content around user recommendations
- Security improvements around using and storing tokens
- Security improvements around using config
- Fixes for unhanded promise rejection errors

---

**Update [15-07 11:00]: Tentative Authentication flow**

*Implemented using Passport. Passport handles maintaining os user object in session. DB temporarily stores the token information — deleted on logout.*

1. Get the app token (user provided or from Micro.blog login API)
2. Make an entry in db with token and a primary key [some thing unique and encrypted]
3. Store the key as cookie on client side, sent with every API call
4. On API call, fetch the key from cookie and query DB using the key to get app token.
5. Use token to fetch data from M.b

---

I need to improve [micro.threads](http://www.amitg.xyz/micro). Noting down the current limitation with the implementation.

- Threads concept itself is limited. Currently it takes a post id, fetches the conversation (thread) and then pull out all the links and only show these links as a thread.
- Creating thread is a mess and so is updating it.
- No way to provide access to external users. Only I can create/update threads at this point

**What I want to introduce now**

I think it would be important to change the whole direction itself. I feel the goal needs to be **discovery**. Help users discover interesting posts and people on micro.blog. To achieve this, below *has* to be handled.

1. Authentication against micro.blog. Pull individual stream.
2. Dashboard against individual stream. Summarise. Most active posts, links, micro monday recommendations, likes, books etc - similar to nuzzle etc.
3. Simple way to build threads, including ones with just posts and no links - similar to twitter moments.
4. Updating existing threads with contents from different topic id
5. Auto refreshed public threads - built from discover section of micro.blog (this is close to available).
