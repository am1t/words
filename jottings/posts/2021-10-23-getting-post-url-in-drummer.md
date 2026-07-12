---
title: Getting Post URL in Drummer
date: '2021-10-23 00:00:00'
slug: getting-post-url-in-drummer
tags: dev, writing
---
I enjoy writing posts in Drummer. One of the [many reasons](https://ol.amitgawande.com/2021/10/21/163615.html?title=BenefitsofWritingwithDrummer) for that is I can see all my posts in the same editing space. It is so easy to scroll through all your posts and find reference to just that one old post.

One thing that missing, though, was there was no easy way to get the `url` for that post right in Drummer. So, I got scripting. I have [created a script](https://gist.github.com/am1t/c1a1d37af7cd33aedc9e1263888a70e0) which does just that. Select any node, run the script, and it will present the URL for that post in a dialog box. Here’s how you enable it.

- Copy the below Drummer script and paste it in your special `opml` file for [Scripts menu](http://docserver.scripting.com/drummer/scripting.opml) (File ⇾ Special files ⇾ Scripts menu…)
- You will see a new entry in Scripts menu
- Select any node, even the headline (a titled post), and select the newly added script menu item

You will get the URL for the selected node.

```
Get Post URL
    var created = op.attributes.getOne("created");
    var baseurl = opml.getHeaders().urlBlogWebsite;
    if(typeof(baseurl) == "undefined"){
        baseurl = "http://oldschool.scripting.com/" + opml.getHeaders().ownerTwitterScreenName + "/";
    }
    var dt = new Date(created)
    var day = (dt.getUTCDate() < 10 ? '0' : '') + dt.getUTCDate();
    var month = ((dt.getUTCMonth() +1) < 10 ? '0' : '') + (dt.getUTCMonth() + 1);
    var year = dt.getUTCFullYear();
    var hour = (dt.getUTCHours() < 10 ? '0' : '') + dt.getUTCHours();
    var minutes = (dt.getUTCMinutes() < 10 ? '0' : '') + dt.getUTCMinutes()
    var seconds = (dt.getUTCSeconds() < 10 ? '0' : '') + dt.getUTCSeconds()
    var post = opml.parse(op.getCursorOpml());
    var isTitledPost = typeof(post.opml.body.subs[0].subs) != "undefined";
    var postUrl = "";
    if(isTitledPost) {
        postUrl = baseurl + year + "/" + month + "/" + day + "/" +  hour + minutes + seconds + ".html";
        postUrl = postUrl + "?title=" + op.getLineText();
    } else
    {
        postUrl = baseurl + year + "/" + month + "/" + day + ".html#a" +  hour + minutes + seconds;
    }
    dialog.ask("This is the URL for the selected post:",  postUrl);
```
