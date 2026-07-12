---
title: Posting Liked Articles from Web
date: '2018-07-29 00:00:00'
slug: posting-liked-articles-from-web
tags: tech, writing, meta
---
I recently received a great feedback and a query from [@cygnoir](https://micro.blog/cygnoir) at Micro.blog.

> The links you share are so interesting! I especially love that you give a bit of an excerpt. Are you auto-posting these somehow? If so, would you be willing to teach me (or point me in the right direction to learn)?

Yes, I do read a lot of articles on web and share each one I like. And the reason I share them is I want others to read them too. I think it is difficult to convince people just with a title. So I also include an excerpt from the post that may give the readers an idea what the post is about ([sample](https://mb.amitgawande.com/journal/40488/))

For me this usually happens while am on mobile and so it is just isn’t simple to copy and paste. So I have a system worked out on iOS with iA Writer and Workflow apps that allows me to easily post the links with excerpt.

It starts with a template in iA Writer with placeholders for all the relevant sections - date, title, link and content that is to be shared.

```
--- title : “” date : {date} --- ★ Liked "<a href="{link}" class="u-like-of" rel="like-of">{title}</a>" > {content}
```

I then have a Workflow which prepares the actual file with this template. I trigger this Workflow from Safari as Action Extension, which runs through the below process.

1. Gets the current URL and puts it into a variable `link`.
2. Gets the title of the current page and puts it into a variable `title`.
3. Gets the contents of clipboard and sets it variable `content`.
4. Gets the current `date` in required format.
5. Picks up the above template and replaces appropriate placeholders with the actual values fetched earlier.
6. Creates a new markdown file with this content and opens it in iA Writer for further processing. And publish.

This system, though not perfect, works for me currently. I want to simplify it further - mainly using Micropub endpoint. But haven’t got a chance to implement that yet. Till then, I am going to use this one.

I have similar template and Workflow combinations for reply, image, link posts.
