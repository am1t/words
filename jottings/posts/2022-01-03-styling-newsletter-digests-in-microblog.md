---
title: Styling Newsletter Digests in Micro.blog
date: '2022-01-03 00:00:00'
slug: styling-newsletter-digests-in-microblog
tags: tech, writing, meta
---
I recently changed the newsletter to a weekly digest instead of every long-form posts with Micro.blog. A fixed schedule is better for me than thinking about whether to include as part of the newsletter every time I post a post with a title. Until there is a better control (via categories) on what posts I can schedule for delivery, I want to avoid risking this particular setting.

That said, I didn’t really like the way the first digest looked. It was… mhmm … messy. Maybe a bit more control over the elements, like title etc. would be good. Without that, to make the digest look slightly better, here’s the custom CSS that I have added currently.

You can apply this to your digest by including this CSS block to your custom CSS (‘Design’ ⇾ ‘Edit CSS’).

```
/* Set the font display */
.microblog_email {
    font-family: "Avenir Next", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
    font-size: 16px;
    line-height: 1.7em;
    max-width: 600px;
    margin: auto;
}

/* Assign area and display for the blockquote */
.microblog_email blockquote {
    display: block;
    margin: 0;
    margin-bottom: 14px;
    padding: 0 20px;
    border-color: #E0E4E8;
    border-left: 2px solid #E0E4E8;
    line-height: inherit;
}

/* Assign area and display for the images */
.microblog_email img {
    display: block;
    max-width: 100%;
    height: auto;
    margin: 0 auto 0.5rem;
    vertical-align: middle;
    border-radius: 5px;
}

/* Style links */
.microblog_email a {
    color: #4F8BCA;
}

/* Hide the profile image and header */
.microblog_email .microblog_header, .microblog_email p:first-child img {
    display: none;
}

/* Style the footer links */
.microblog_email .microblog_footer {
    margin-top: 20px;
    text-align: center;
    font-size: 13px;
    padding-top: 10px;
    padding-left: 30px;
    padding-right: 30px;
    line-height: 1.5em;
}

/* Styling for the separator */
.microblog_email hr {
  margin: 12px 0;
  border: 0;
  text-align: center;
}

.microblog_email hr:before {
    content: "\2022 \2022 \2022 \2022";
    font-size: 20px;
    color: #4F8BCA;
}

/* Styling the links */
.microblog_email .microblog_permalink {
    color: #4F8BCA;
}
```

I would like to avoid these `:nth-of-type` and `:first-child` blocks. But until the elements across the body are assigned classes, I will have to stay with this. Anyway, hope this helps. Or if there’s a better, simpler way to achieve this, I would love to hear.

---

**Update [24 April 2022]**: Fixed the issue with blockquotes being hidden due to the selection for headers being mistakenly applied to the blockquotes too. This uses the recently added CSS selectors for `.microblog_header` and `.microblog_footer`.
