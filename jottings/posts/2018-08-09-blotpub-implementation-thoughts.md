---
title: Blotpub implementation thoughts
date: '2018-08-09 00:00:00'
slug: blotpub-implementation-thoughts
tags: dev
---
This is a running list of things I need to implement in Blotpub. I intend to pour my thoughts and prioritise. This may also go to github on things to come once finalised.

1. [Low] Support like and reply with data pulled [xray](xray.p3k.io). I am not sure what I plan to achieve out of this. It is primarily when I like a twitter post or an [image posts](https://xray.p3k.io/parse?url=http%3A%2F%2Fxkcd.com%2F2030%2F), xray gives data in [nice format](https://xray.p3k.io/parse?url=https%3A%2F%2Fblog.amitgawande.com%2Ffake-news-false-information-online). I would want to use that.
2. Media upload as multipart. I thing this should address the need for photo upload, mainly from quill. It is simpler as I have a reference of voxpelli’s project.
3. Media endpoint(?q=config). This is a big ask. First need to implement one without any reference. Second use it for photo upload.
4. [Syndication](https://quill.p3k.io/docs/syndication) (?q=syndicate-to). This should be simpler. Need to support sending posts to twitter. Again, I have the reference from voxpelli’s project.
5. Support for update/delete posts
6. Handle authentication issues reported by micropub.rocks
