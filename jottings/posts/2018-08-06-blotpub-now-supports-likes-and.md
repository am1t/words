---
title: Blotpub Now Supports Likes and Replies
date: '2018-08-06 00:00:00'
slug: blotpub-now-supports-likes-and
tags: meta
---
Since I [introduced blotpub](https://mb.amitgawande.com/micropub-endpoint-for-blot) a couple of days back, I have been continuously posting to the site from different Micropub clients. And I am happy that the system worked well. Added satisfaction was provided by the community by expressing interest and openness to try the endpoint out.

As I had mentioned in that post, handling “the creation of like and reply post types” was next on the list. I just couldn’t live with the fact that the endpoint didn’t handle these simple post types. So, it had to be addressed. And it is addressed now —  the latest version of blotpub handles replies and like posts.

The information is added as properties `in-reply-to` and `like-of` to the post metadata.

In addition,  support has been added to explicitly place the date property as part of the metadata.

Earlier, file creation date was used as the post date. The enhancement was discussed with [@jack](https://micro.blog/jack) as part of this [git issue](https://github.com/am1t/blotpub/issues/1). With this version, if the published date is provided, it would be set in the metadata. Else date-time for post creation request would be used. To enable this, just set `SET_DATE` environment variable to `true`. Additionally, you can also set the `TZ` variable to override default timezones for the server hosting your endpoint. Refer to the [`README`](https://github.com/am1t/blotpub) for more details.

I have also fixed some minor issues in handling the post creation via different clients, mainly Micro.blog iOS client.

***What’s next?*** Handling of image files.
