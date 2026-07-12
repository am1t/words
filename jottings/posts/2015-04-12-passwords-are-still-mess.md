---
title: Passwords are, still, mess
date: '2015-04-12 00:00:00'
slug: passwords-are-still-mess
tags: writing
---
Some time back, I read this interesting [post](http://xkcd.com/936/) at xkcd, a usual for these guys.

![](https://images.amitgawande.com/2015/26d8ea36c5.jpg)

It made me realise, for the zillionth time, passwords are mess. This medium of authenticating a valid, and a human, user has overstayed its welcome. The way it is [being](http://web.archive.org/web/20160304020352/http://www.slate.com/blogs/future_tense/2014/01/22/_25_worst_passwords_what_your_terrible_common_password_says_about_you.html) [used](http://gizmodo.com/the-25-most-popular-passwords-of-2013-god-help-us-1504852434) is not secure. Well, can you blame the poor souls who are made to remember the crazy letters every time they want to get something done online? Moreover, they are forced, as a security policy, to change and then remember the new passwords every some time. Sigh! Indeed, passwords are mess.

You need more proof? Try searching for the phrase [“passwords should die”](http://www.bing.com/search?q=passwords+should+die). This farce has to be one of the most cursed phenomenon out there.

### But then what are the options?

1. Make browsers/OS’es handle the **password generation and management**: This is one of the oldest and most recommended solution for this issue. The problem is such machine generated passwords are usually random Strings; hence they are extremely hard to memorise. Good password managers [can negate](https://diogomonica.com/posts/password-security-why-the-horse-battery-staple-is-not-correct/) that need. However, they become a hinderance in an environment where there are multiple machines involved (for example, work vs home environment). Moreover, the security aspect of these are [hotly debated topics](http://www.theverge.com/2013/8/7/4597018/google-chrome-saved-browser-passwords).
2. Recommend ways for **easy to remember, difficult to break** passwords: An option that is evaluated a lot these days. The xkcd post linked above recommended one such way. It also opened a lot of threads [discussing](http://security.stackexchange.com/questions/6095/xkcd-936-short-complex-password-or-long-dictionary-passphrase) and [analysing](http://www.explainxkcd.com/wiki/index.php/936:_Password_Strength) the accuracy and feasibility of the same. There were [articles](http://www.popularmechanics.com/technology/security/how-to/a8650/solving-the-password-problem-14993917/) and [papers](http://www.isi.edu/natural-language/mt/memorize-random-60.pdf) written on understanding and improving on the suggested way. The problem is, eventually, it is a human, the lazy ass, who will decide what the password would be. What would end up happening is instead of *”password1”* being a common password, it would be *”mypasswodiscommon”*.
3. Go **Biometric**: Apple introduced a working and, debatably, secure implementation of biometric authentication in [TouchId](http://en.wikipedia.org/wiki/Touch_ID). By bundling it as a core feature of iPhone, Apple made it reach to the masses. [Tons](http://arstechnica.com/security/2013/09/fingerprints-as-passwords-new-iphone-touch-id-gets-mixed-security-verdict/) of [articles](http://nymag.com/daily/intelligencer/2013/09/will-apples-touch-id-make-fingerprints-happen.html) were written detailing how it can solve the password problem altogether. Though possible, issue remains this would not happen until biometric authentication comes bundled across all technology devices, *even the low-end mobile phones*. Passwords remain the standard, and only acceptable authentication method till then.
4. Make **passwords die**, altogether: Finally, we come to the most interesting option that can be driven by the application developers themselves and not the users of the application. I feel, this will eventually become a reality.

### Password-less Authentication

A lot has been said on this front too. There are [articles](https://medium.com/@ninjudd/passwords-are-obsolete-9ed56d483eb) and even open source frameworks, like [Passwordless](https://passwordless.net/) that want to target this by providing application developers ways to replace their login forms with password-less access. At high-level, key steps involved to achieve this are

- Make a user just mention his userid/email address
- Generate a one-time token for him
- Deliver it to him
- Authenticate him with the generated token

These are pretty standard and well accepted steps. However the issue remains in the 3rd step, *how should these tokens be delivered*. Whichever mechanism one selects will become *the single point of threat* to the whole system going haywire, be it then email (*what’s the password for email account then?*) or SMS (*phone is lost, what now?*). The [hacker news thread](https://news.ycombinator.com/item?id=4308190) on [one such suggested system](http://notes.xoxco.com/post/27999787765/is-it-time-for-password-less-login) is nice rundown for the probable issues.

Now that thread is more than a couple of years old. Today, the best option would be to deliver the token to the device which has biometric authentication enabled. As an example, I really like the way Apple has enabled the [two-factor authentication](https://support.apple.com/en-us/HT204152) on Apple Id. It displays possible devices where the token can be delivered and asks the user to select one. Once delivered to, say, an iPhone, *only the user who owns the iPhone* can access it by authenticating himself with TouchId. This same mechanism can be applied for delivering the secure tokens of web/mobile applications too. There, the delivery problem is solved.

However, given that majority of the users do not own an iPhone or a similar biometric authentication enabled device, this method cannot become the primary way of authenticating users.

So even though I believe that, in [John Siracusa’](http://hypercritical.co/) words, *on an infinite timescale*, all applications will have password-less logins, we are some years away from realising that dream.

---

Ok, so what till then? This is what I would like the applications developers to do to make this password mess a bit less itchy for me. Decide first, do you really need me to secure my profile via a password? User forums/discussion groups, I am looking at you. I will give leeway to banks/financial apps to make me remember and enter the password. For all others, please make this process simple.

1. When a user visits the first time, ask for his email id/mobile number. Next, make him choose a word, an image or, preferably, a set of words/images to remember as *“password”*.
2. For every subsequent visit, just ask him for the email id or mobile number. Even better, *just do not ask him anything*. Maintain his profile information in cookie with expiration set for a longer timeframe.
3. Give him the options amongst which lies his password and make him *“select”*, not enter, that as the password. He gets a couple of chances, else make him fall back to one-time token.
4. If he does not remember the *chosen* password, *or chooses not to*, a click on a link sends him a token on email/mobile which he used while registering.

I believe this will ease the burden from majority of the people of maintaining the passwords without making them any less secure. Passwords can’t die yet, but at least *they would be a little less painful*.
