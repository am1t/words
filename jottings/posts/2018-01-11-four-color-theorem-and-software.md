---
title: Four Color Theorem and Software Complexity
date: '2018-01-11 00:00:00'
slug: four-color-theorem-and-software
tags: tech
---
> Looking at these graphs feels a lot like looking at a graph of dependencies in a codebase. If you add a node for each class, and draw and edge between the classes that communicate, you’ll end up with a graph like the ones above. My talk of “components” and “modules” was influenced by thinking about these graphs in terms of software. The last example touches on an important point - you can manage a growing codebase without growing in complexity if you manage the way modules connect to each other. A codebase composed of small interconnected modules that communicate with each other in a well-defined way will have a lower complexity than one where the modules communicate with each other haphazardly.
>
>  This is an example of how it’s better to manage interaction along a point than along an edge. By that I mean modules that present a single point of interaction will be able to maintain their own internal dynamics without polluting the complexity of the codebase. If programmers don’t think about how they connect the modules in their codebase, and they end up connecting modules along multiple points of interaction, the complexity of the codebase will grow.

This is such a fascinating read. I have recently come across the [four color theorem](https://en.m.wikipedia.org/wiki/Four_color_theorem) many times in different variants. It is a fascinating mathematical statement on graphs, specifically maps. But I could never imagine how it could also be applied to represent software complexity, or rather how one can build and manage the growing codebase of a software without adding to the complexity.

---

Of course, the theorem is concisely explained by [Dr James Grime](http://jamesgrime.com/) at [Numberphile](https://www.youtube.com/user/numberphile) channel on YouTube.
