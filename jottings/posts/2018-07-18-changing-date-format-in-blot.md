---
title: Changing Date Format in Blot
date: '2018-07-18 00:00:00'
slug: changing-date-format-in-blot
tags: meta
---
So, in one of the [recent posts](https://mb.amitgawande.com/indiewebify-blot-site) on indiewebifying the blot.im site, I was faced with a roadblock.

> I could not find any way to format the published date that gets displayed on the posts. The post properties exposes just , which gets the default format of MMM DD, YYYY. And I do not think it’s a valid ISO-8601 as expected by the microformats2.

Well, I had reached out to David and apparently there is a *yet-to-be-documented* way.

As per the [official document](https://blot.im/developers/reference) for developers, the standard way to get the post’s publish date is with property `{ { date } }`[1](#footnote-1HH2). However, if so inserted, it inserts the date in a default format - `MMMM DD, YYYY`. Even though it is a format that displays well, it does not provide the complete information on date, up to time level. For the microformats2 `dt-published` `time` tag, it is important that the post publish date is inserted as valid ISO-8601. So to do that, just use the below code snippet instead of `{ { date } }`.

```
{ { # entry } } { { # formatDate } } MM YYYY DD { { /formatDate } } ... { { / entry } }
```

Make sure you remove spaces in between the curly brackets (*refer footnote 1*). Wherever the snippet `{ { # | / formatDate } }` is added, it would be replaced by post’s publish date in the format defined in between the tags.

In David’s own words, “any of [Moment.js’ date formatting tokens](https://momentjs.com/docs/#/displaying/) work (formatDate is basically [Moment.js](https://momentjs.com/docs) behind the scenes)”. So you should be able to customise it completely as per your need.

---

1. As clarified by David in an earlier [open queries post](https://mb.amitgawande.com/blot-open-questions-update), there is at this point no way to escape the parsing of the code references for properties that Blot uses. It ends up replacing them with the value. So adding spaces is my way to work around that limitation at this point.[↩](#ref-1HH2)
