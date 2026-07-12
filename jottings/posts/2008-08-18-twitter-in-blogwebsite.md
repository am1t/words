---
title: Twitter in Blog/Website..
date: '2008-08-18 00:00:00'
slug: twitter-in-blogwebsite
tags: writing, meta
---
I always wanted to add my tweets to my blog, to pen in the sudden and randomly generated vibes in me. I use to do that at twitter. But i wanted to pull in the thoughts at one place. As i owned the place now, i thought of a dedicated section for the purpose and hence came into existence the “[Blabber Land](http://www.elatedamit.com/blabber/ "Blabber Land")”.

If you follow the link, you can find the live demonstration of twitter in blog under the first section named “*Abrupt Blabberings*”. The procedure is pretty not-so-complex sorts. And with a simple but informative article like [this](http://remysharp.com/2007/05/18/add-twitter-to-your-blog-step-by-step/) your work is greatly reduced. Thanks Remy …

But still it would need a bit of a scripting and customizing on your part, for better results that is. Few points to remember (basically the ones i didn’t :P)


1. Make sure you add the *<div id=”twitter”>* section at a proper place. Before pulling the tweets, book the place holder and test the looks with the dummy data. Customize the *div* section.

2. Add the pre-fetch message at the blog. Let user know something is about to happen in the section. A progress indicator would be a plus.

3. Now add the scipt that fills in the place holder booked earier i.e. the *<div>* section. Make sure you rename the *tweet* in *getTwitters('tweet',* to the id you have mentioned in the *<div>* section above. So in this case, it should be renamed as “getTwitters(’*twitter*’,”

4. Adding the script section towards the *</body>* tag of your page would always be favorable. The simple reason being the browsers don’t start any parallel downloads i.e. of images etc as long as they don’t download the scripts. It is always recommended that scripts, wherever possible, should always come right at the end, after most of the page is completely loaded.
