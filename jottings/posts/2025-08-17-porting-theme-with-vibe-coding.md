---
title: Porting Theme with Vibe Coding
date: '2025-08-17 17:26:00'
slug: porting-theme-with-vibe-coding
tags: dev
excerpt: Yesterday, I ported my original theme from the last live version on Kirby
  to Ghost. I did this through vibe coding with Claude on Cursor.
ghost_id: 68a1ab3f15e50700012c8917
---
TL;DR - Yesterday, I ported my original theme from the last live version on Kirby to Ghost. *I did this through vibe coding with Claude on Cursor.* Sure, I had to iterate to resolve a few issues, but the overall experience was pretty effortless. Even this post, except for the introduction and this section, is a result of the vibe coding session.

---

![black flat screen computer monitor turned on beside black laptop computer](https://images.unsplash.com/photo-1590658093848-f6f0df47b853?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3wxMTc3M3wwfDF8c2VhcmNofDU4fHx2aWJlJTIwY29kaW5nfGVufDB8fHx8MTc1NTM1NTYwNXww&ixlib=rb-4.1.0&q=80&w=2000)

Here's the longer version of the story. I have had a version of this theme running on my blog for some time, [first created](https://mb.amitgawande.com/2023/04/21/a-blog-no-more/) for Hugo on Micro.blog. When I moved to Kirby, I ported my theme to make the switch seamless. I wanted to attempt the same with Ghost, too. The only thing holding me back was my lack of clarity on moving each aspect of the carefully crafted theme. *Could I recreate it exactly?*

This question led to an unexpectedly enjoyable coding session with Claude, where we embarked on a complete theme migration that turned into something like pair programming with an AI.

## Starting with "How Hard Could It Be?"

When I first asked about porting my Kirby theme to Ghost, I expected a straightforward template conversion. Kirby uses PHP, Ghost uses Handlebars—how different could they be? Well, it turns out quite different.

My theme wasn't just a simple blog template. Over the years, it had evolved into something quite specific: a homepage with curated "Start Here" posts, support for both long-form blog posts and microblog "notes," IndieWeb microformats throughout, and a custom newsletter integration for my Square 101 series. Oh, and a navigation system where previous/next buttons appeared on every page but only worked on post pages.

The first challenge came immediately. *Ghost doesn't have Kirby's flexible content structure*, so we needed to think creatively about how to maintain the distinction between blog posts and notes while working within Ghost's framework.

## The Dance of Debugging

What followed was a delightful back-and-forth debugging session. Claude would examine my Kirby templates, suggest Ghost equivalents, and inevitably, something would break. "Missing helper: feature\_image" became a running theme as we discovered that Ghost's template system had its own opinions about how things should work.

Each error led to a deeper understanding. When the homepage lost its intro content, we realised Ghost's context system works differently from Kirby's page structure. When dates showed up as "July 0" instead of proper dates, we dove into Ghost's date formatting. When the navigation buttons disappeared entirely, we learned about Ghost's template inheritance.

There's something satisfying about this kind of methodical problem-solving. Each fix revealed another layer of how Ghost thinks about content, *and gradually, the theme began to take shape.*

## The Moments of Discovery

The best part of the session was those small victories. When we finally got the two-column layout working perfectly, matching the original pixel for pixel. When the microformats are appropriately validated, preserving the IndieWeb compatibility I'd worked hard to maintain. When the newsletter integration callouts appeared exactly where they should.

One particularly satisfying moment came when we implemented the navigation system. In Kirby, I had previous/next buttons that appeared on every page but were only functional on post pages. In Ghost, this required understanding the difference between global and post-specific contexts. The solution—checking for post context and showing active or inactive states accordingly—felt elegant once we figured it out. Though this is not a solved problem yet, *I got the necessary understanding of why it breaks,*

## The Art of Preservation

Throughout the process, the goal wasn't just to make something that worked, but to preserve the exact character of the original. This meant paying attention to details that might seem trivial: the precise spacing between elements, the way tags are displayed, the subtle colour variations in different modes.

Claude was remarkably good at this kind of detail work. When I mentioned that the post structure looked different, it immediately went back to the original Kirby templates to understand what was missing. When I pointed out that dates were wrong, it didn't just fix the format—it examined the original to match it exactly.

## What Emerged

After several hours of this iterative refinement, we had something remarkable: a Ghost theme that was virtually indistinguishable from the original Kirby site. Every visual element, every interaction, every piece of functionality had been preserved.

But more than that, the Ghost version was actually better in some ways. Featured images now work seamlessly with Open Graph tags. The template organisation is cleaner with reusable partials. Ghost's built-in SEO handling is more robust than what I had cobbled together in Kirby.

## The Unexpected Joy of AI Pair Programming

What struck me most about this experience was how much it felt like collaborating with a thoughtful colleague. Claude understood not just the technical requirements but the aesthetic goals. It caught details I might have missed and suggested improvements I hadn't considered.

There's something uniquely satisfying about this kind of work—*the methodical process of understanding how something works, translating it to a new system, and refining until it's exactly right.* Having an AI partner who could instantly examine templates, spot patterns, and suggest solutions made the whole process feel more like exploration than tedious porting.

The migration proved that **switching platforms doesn't require sacrificing your site's character.** With patience and attention to detail, you can maintain exactly what makes your site unique while gaining the benefits of modern tools. Sometimes the best way to appreciate what you've built is to rebuild it entirely.

---

*The complete Ghost theme emerged from this session, ready to deploy. It maintains every aspect of the original while embracing Ghost's modern publishing platform—proof that good design transcends the tools used to create it.*
