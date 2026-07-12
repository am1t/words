---
title: Update on Blot Open Questions
date: '2018-07-10 00:00:00'
slug: update-on-blot-open-questions
tags: dev
---
**Update:** I had sent these questions to David, the developer behind Blot, on the support email address. And of course, given how gem of a person he is, he did address all of them quickly. I am updating the original post with his responses. This dedication of David makes me love this service even more!

---

I have some questions I need to explore and find answers for some issues in using Blot. Just jotting them down for reference. The list may continuously grow and shrink as I find the answers.

1. What’s going on with `{{Summary}}`? I do not think it generates what it says it does - “first line”. It ignores lines with links, it ignores codes in the line. So what’s outputted is something inaccurate.

> **[David]**: You can override summary in the metadata at the start of a file. If you know a little javascript, you can read the rules for how the summary property is generated automatically.

2. Can we override the behaviour of `{{title}}`? It is especially important for title-less posts as currently, the file name gets used by default. You need to explicitly set `Title:` to blank.

> **[David]**: You can also override title in the metadata. However, based on what you are trying to do, I’d make use of the property. This refers to a markdown or HTML title tag in the file itself. For example:

3. Point 2 is also important for posts via just the image files. As of now, it adds the image name as the title. I would prefer not the post to have any title at all.

> **[David]**: I think I have solved this point in #2, please let me know if not.

4. Can we override the behaviour of `{{{body}}}`? Just want to explore possibility to modify behaviour of URLs of image sources. Currently, relative URLs to `blotcdn` without scheme are added.

> **[David]**: No, it is not possible to modify body. Please can you explain what you are trying to do? Would you like Blot to stop uploading your images to blotcdn? You can disable this behaviour on the settings page under Images > Cache and optimize images

5. How can we make reference to any Post parameter in a post? If we include the parameter (for example , it gets converted to the title on build? Can we escape the `{` and `}`?

> **[David]**: This is not possible right now, it is a bug, I will fix it. Sorry!
