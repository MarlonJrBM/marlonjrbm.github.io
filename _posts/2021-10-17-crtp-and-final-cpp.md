---
title: "The costs of dynamic polymorphism"
categories:
  - C++
tags:
  - C++
  - CRTP
  - Final
  - Inheritance
  - Repost
excerpt_separator: "<!--more-->"
---

Hello World !

I stumbled upon two articles this week, which I would like to share with you. The first one is about final classes in C++, and the second about CRTP (curiously recurring template pattern).

These are short readings which may have huge implications, at least for me. They may give you new ideas for your code or allow you to revisit some important C++ concepts which are not always obvious.

<!--more-->

They may seem completely unrelated but they do share one common concern: the runtime impact of traditional inheritance in C++, and what can be done to mitigate that.

The first one mentions how the use of one simple keyword (final) can help the compiler perform de-virtualization, which can lead to significant performance gains.

The second one proposes a way to get rid of dynamic polymorphism and relying exclusively on template metaprogramming, notably on the CRTP feature.

I will let you take a look at the articles as they explain it really well. Without further ado:


- [The Performance Benefits of Final Classes](https://devblogs.microsoft.com/cppblog/the-performance-benefits-of-final-classes/) 
- [CRTP Interface technique](https://www.foonathan.net/2021/10/crtp-interface/)

Thanks !