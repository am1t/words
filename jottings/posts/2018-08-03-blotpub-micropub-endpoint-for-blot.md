---
title: Blotpub - Micropub Endpoint for Blot
date: '2018-08-03 00:00:00'
slug: blotpub-micropub-endpoint-for-blot
tags: meta
---
Continuing [my experiments](https://mb.amitgawande.com/tagged/blot) with Blot, and as [a next step](https://mb.amitgawande.com/indiewebify-blot-site) in Indiewebifying it, I had recently sorted out the webmentions setup and display.

There was one final piece of puzzle missing, one that I had posted in a [recent update](https://mb.amitgawande.com/theme-refresh) on the theme refresh.

> Why not make this the primary homepage? Well, I am still on the journey of indiewebifying this place. I still post to my site using other apps, mainly Quill and Micro.blog. Until I get the micropub endpoint that I am working on done, I will keep this place booked for my excursions, my experiments.

Well, I finally managed to get a basic version of one worked out. Basic, but a workable version. Introducing [Blotpub](https://github.com/am1t/blotpub).

It is a self-hosteable Micropub endpoint for blot.im and Dropbox. It accepts Micropub requests, creates a simple Blot posts and saves them to a configured Dropbox folder. This enables updating a Blot blog through a Micropub client.

I have tested creation of both long and short posts via [Quill](https://quill.p3k.io/). It supports creation of posts with or without titles. For me, the former are my micro posts while later are more of the long form articles.

It also supports metadata creation for tags and slugs as part of the post documents.

With this, I have my basic needs covered. Most of the time, I am posting text posts; the current version should be able to handle that.

Next, I need to handle the creation of like and reply post types and also handle the image files. It may so happen that I end up getting these done soon. However, I wanted to put the bare bones version out there.

### How do I use this?

Well, as I said earlier the [source is open](https://github.com/am1t/blotpub). It is a Node application which you can self-host as your own micropub endpoint. I have covered some of the details as part of the project [readme](https://github.com/am1t/blotpub/blob/master/README.md).

However, before you use blotpub, there is one essential step from IndieWeb that needs to be addressed - to make your website your identity online. It involves declaring openly your social network profiles as rel-me links and link those profiles back to your site. This allows you to login to any IndieAuth enabled services using your website’s homepage - no need to create an account or maintain passwords.

You can refer to the “Essential IndiWeb” section in [this post on how to display webmentions](https://mb.amitgawande.com/display-webmentions/#essential-indieweb) on your site. That step applies to using a micropub too.

This is an **early alpha release** of the application. Things may be a bit unstable. Please use it with caution. Also, I will continue to work on this and improve it, so, you may have to refresh your deployment regularly. However, I would be happy if you choose to join me on this bumpy ride - this will only get better with more people using it.

1. **Install**: Just install this as a normal Node.js application. A better way would be to [deploy directly to Heroku](https://heroku.com/deploy?template=https://github.com/am1t/blotpub).
2. **Grant Dropbox Access**: Generate a [Dropbox access token](https://blogs.dropbox.com/developers/2014/05/generate-an-access-token-for-your-own-account/) from the Dropbox [App Console](https://www.dropbox.com/developers/apps) to grant the application access to your Dropbox folder. Just create a new app in the console, chose API as Dropbox API, select the type of access as “Full Dropbox” and finally, name your application. You will need this generated token while configuring your application.  Just to reiterate the point, the “Permission type” for the app that you create for blotpub in dropbox needs to be set to “Full Dropbox”
3. **Configure**: Add the required configuration values via environment variables or the Heroku app deploy dashboard. You will need the token generated above.
4. **Endpoint Discovery**: Once you have deployed the application, your Micropub endpoint will be available at `/micropub` (e.g. `https://deployed-blotpub-app.com/micropub`).  Note that the endpoint url is different from your website url. It would be the url for the blotpub application that your installed in the 1st step.

   For Heroku deployment, it would be something like `https://*****.herokuapp.com/micropub` (exact url will be available at Heroku dashboard). To enable automatic discovery for your [Micropub endpoint](https://indieweb.org/micropub#Endpoint_Discovery) and [token endpoint](https://indieweb.org/obtaining-an-access-token#Discovery), you will need to add the following values to your Blot site’s `<head>` - usually available in the `head.html` file in your theme/template.

```
<link rel="micropub" href="https://deployed-blotpub-app.com/micropub"> <link rel="tokenendpoint" href="https://tokens.indieauth.com/token">
```

5. **Media Endpoint:** Most of the micropub clients, like quill, can send the media files as `multipart` data. So, you can attach image while creating a new post. However, some clients like Micro.blog require a [Media Endpoint](https://indieweb.org/micropub_media_endpoint) to handle the media files (primarily the image files). Blotpub comes with an inbuilt media endpoint. To use it, just configure the `MEDIAENDPOINT` variable in your blotpub deployment to `https://deployed-blotpub-app.com/micropub/media` (for Heroku, something like `https://*****.herokuapp.com/micropub/media`). This will allow you to post image from such clients too.
6. Note that file uploads via blotpub media endpoint will only add the image file at the location configured at `PHOTO_PATH` and the URL to the image will be added to the post metadata as `photo: <url-to-image>`. To render this in the post, you can add the below code block in `entries.html` and `entry.html` in your Blot theme either before or after `{{{html}}}` as per your preference.

```
{{#metadata.photo} } <img src="{{metadata.photo} }"> {{/metadata.photo} }
```

You should now be able to post to your Blot site from external Micropub clients (like Micro.blog iOS App, Quill etc). If you do use this, ping me. All your feedback is welcome.
