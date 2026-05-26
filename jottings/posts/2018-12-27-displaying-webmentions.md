---
title: Displaying Webmentions with Posts
date: '2018-12-27 11:05:00'
slug: displaying-webmentions
tags: dev
ghost_id: 68511293eb03dc000150c80c
---
I have been using [**Blot**](https://blot.im/), a simple blogging platform with no interface, for quite some time now for running my blog. I am not alone when I say this, but am mighty impressed with how simple it is to post things on blot and maintain the overall site. They are just some files in Dropbox - that’s about it. So, it was pretty straightforward to customise the theme to my liking and to enable the support for IndieWeb principles.

One thing I have noticed, though, is that most of the IndieWeb principles are not visible. They enable a more open web, providing sites a grammar they can talk to one another with. But for someone who owns the website or even someone who reads the posts on a website, whatever changes go in just aren’t apparent. Except, of course, for webmentions.

I have already detailed [the steps to Indiewebify one’s website](https://amitgawande.com/blog/2018/indiewebify-your-hugo-website) (specifically one built with Hugo). I did not go into the details of setting up webmentions. And that is exactly what I get asked the most about - how does one display mentions along with the posts.

The need is more evident with microblogging - and especially so with [micro.blog](https://micro.blog/). The platform fosters a very active and pleasant community focused more on the interactions (replies) than meaningless reactions (likes, reposts). It also sends webmentions for every reply to a post to the sites that can receive them. So the desire to display the interactions along with the posts, microposts more so, is understandable.

In this post, I will (finally!) document the steps that can help one receive, fetch and display the webmentions along with the posts. The steps are documented from a reference of a blot website. However, the steps below can be altered at appropriate places, primarily formats, to implement the support for any other platform.

## Essential Indieweb

Before you can start receiving the webmentions at your site, there is an essential step from IndieWeb to be achieved - to make your website your identity online. It involves declaring openly your social network profiles as `rel-me` links and link those profiles back to your site. This allows you to login to any IndieAuth enabled services using your website’s homepage - no need to create an account or maintain passwords.

To achieve this, modify the `head.html` of the site’s theme to add such links to your other online profiles in `<head>` element. These profiles can be on Twitter, Github, Facebook, or even email - anything where you can link back to your website from. Some reference links are shown below.

```html
<link rel="me" href="https://twitter.com/abcxyz" />
<link rel="me" href="http://github.com/abcxyz" />
<link rel="me" href="mailto:abcxyz@example.com" />
```

After you declare your website with either Twitter or Github, they can authenticate your identity. With email, a link is sent to the configured email address to do the same, very much like any email-based two-factor authentication.

You also need to declare the service which will act as an authorization endpoint when needed. This is used by other services, mostly IndieAuth clients, to validate your identity. To configure this, just add the below link to your site’s head.

```html
<link rel="authorization_endpoint" href="https://indieauth.com/auth">
```

Once you have this enabled, you can test your setup using [Indiewebify.Me](https://indiewebify.me/). Test the “Set up Web Sign In” section.

You are now ready to receive the webmentions from other sites, including Micro.blog.

## Receive Webmentions

This primarily involves hosting and declaring a webmention endpoint. Of course, the active IndieWeb community already has a ready solution for this - [webmention.io](https://webmention.io/) by [Aaron Parecki](https://aaronparecki.com/). It is “a hosted service created to easily handle webmentions”. All you have to do is sign-in with your domain (i.e. validate your identity) and let Webmention.io receive all mentions to your site. Once that’s done, just declare the webmention endpoint as below in your site’s `head`.

```html
<link rel="webmention" href="https://webmention.io/username/webmention" />
```

The `username` is typically the url of your site (you can also find these details on the [settings](https://webmention.io/settings) page). To test this setup, login to [webmentions.io dashboard](https://webmention.io/dashboard) and you should start seeing the mentions sent to your site (which includes the replies on Micro.blog.

## Display Webmentions

Webmention.io also [provides APIs](https://github.com/aaronpk/webmention.io#api) for you to fetch the webmentions to your posts/site. You can implement a custom solution using Javascript for fetching and displaying these mentions along with posts. Below is one of the ways this can be achieved. It specifically pulls the likes, reposts and replies and puts them below the posts. The code might look a bit untidy, but it would be easier to follow what’s going on. You can improve over this eventually.

To start with, declare a placeholder for the webmentions. Place the below `div` element in your `entry.html` file between `{{#entry}}` and `{{/entry}}` - preferably towards the end of the file, just above `{{/entry}}`.

```html
<div class="post-mentions" id="post-mentions" style="display:none">
  <ul class="mentions-list" id="mentions-list">
  </ul>
</div>
```

Of course, you could replace the unordered list `ul` element with anything else. This is just one of the ways you can do it.

Next, you need to fill this `div` element with the mentions the entry has received. You can use the javascript snippet available at [this gist](https://gist.github.com/am1t/7295b4eaf101372ea71c877cfd8be694) to fetch and display the webmentions along with the post. Just place the complete code available there at the end of `script.js` file of your blot’s theme. So it would look something like below (note that this is an incomplete snapshot).

```javascript
{{{appJS}}} 
var post_url = window.location.href; 
$(document).ready(function()
{ 
    $("ul#mentions-list").empty(); 
    $.getJSON("https://webmention.io/api/mentions?jsonp=?", { target: post_url }, 
    function(data){ ... ...
```

Make sure the first `{{{appJS}}}` line is not removed. This import makes sure the additional javascripts necessary for some specific features provided by Blot - for example jQuery for image zoom, Google Analytics etc. - are imported.

The above javascript snippet does below.

1. Gets the current post url and fetches the webmentions for that url from Webmention.io.
2. Divides and groups the mentions by the activity type (like, repost, link, reply). This is so that you can control how each activity-type is styled.
3. Finally, populates these mentions into the above-created placeholder `div` element.

At this point, you should start seeing the webmentions along with the posts once the above-mentioned steps are carried out.

In case, the webmentions are available on the webmentions.io dashboard, but aren’t getting loaded on the post, one possible root cause is failure of jQuery import. Declare a jQuery import explicitly in head.html by adding below statement within the head tags.

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"> </script>
```

You will also note that all the html elements in the javascript code are tagged with `class` attribute. This allows you to control the style of the elements as per your liking. Just modify the main css file for your theme (typically `style.css`) to add styling for these classes.

For reference, find below a sample styling for the main `post-mention` class.

```css
.post-mentions {
  padding-top: 15px; 
  margin-top: 10px; 
  border-top: 1px solid #AEADAD; 
  border-bottom: 1px solid #AEADAD; 
  font-size: 16px; 
} 

.post-mentions ul { 
  list-style:none; 
  padding:0; 
  margin-left: 0; 
}
```

Similarly, you can also style the `mention`, `mention-author`, `mention-social` and `mention-text` classes.

## Interactions from Social Media

Though references to your posts from IndieWeb sites are handled, what about the references made on Twitter or Facebook? It can be in any form of response (i.e. likes/retweets/reposts) to the syndicated post. Of course, they do not send webmentions (wish they did).

One option is to implement your own [backfeed](https://indieweb.org/backfeed) to poll for such interactions and handle them as response. Well, the community has made sure there is a simpler hosted option. Enter [Bridgy](https://brid.gy/).

> Bridgy is an open source project and proxy that implements backfeed and POSSE as a service. Bridgy sends webmentions for comments, likes, etc. on Facebook, Twitter, Google+, Instagram, and Flickr.

Just connect your social accounts with your website at Bridgy and every time there is an interaction about your post on a service, Bridgy captures that and sends a webmention to your endpoint configured earlier.
