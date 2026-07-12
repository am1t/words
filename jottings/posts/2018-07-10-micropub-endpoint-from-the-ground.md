---
title: Micropub endpoint from the ground up
date: '2018-07-10 00:00:00'
slug: micropub-endpoint-from-the-ground
tags: dev
---
The [recent](https://mb.amitgawande.com/update-on-blot-experiment) [experiments](https://lab.amitgawande.com/2018-07-09-2002) with blot.im has given the perfect opportunity to explore if I can get a Micropub endpoint created specifically for my needs. Till now, I have been using [a custom fork](https://github.com/am1t/webpage-micropub-to-github/tree/musings) of a endpoint from [Pelle Wessman](https://github.com/voxpelli) for my Hugo site. It has served me well.

However, I always wished if I could get one written specifically for my simple needs. One that I know and understand every part of. Given that I have no endpoint yet for the blot site, this is clear opportunity to create one geared for making this site micropub enabled. Hugo site will address my *third-party-posting* needs till then. So here’s the start. I will capture this journey, of course, here and will keep this updated with progress (*I hope*). Below are the things at this point that I need to get started.

- [https://indieweb.org/Micropub#How*to*implement](https://indieweb.org/Micropub#How_to_implement)
- <https://devcenter.heroku.com/articles/getting-started-with-python#introduction>
- <http://dropbox-sdk-python.readthedocs.io/en/latest/moduledoc.html#module-dropbox.dropbox>

I want to explore python first as an option to get this implemented. I have come to realise that I do not like Javascript as a language. I can get work with it, but at times the inconsistencies and the constructs get in my hair.
