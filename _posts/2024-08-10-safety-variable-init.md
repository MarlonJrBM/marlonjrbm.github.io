---
title: "Safety variable initialization in C++, finally!"
categories:
  - C++
tags:
  - C++
excerpt_separator: "<!--more-->"
---

C++ is getting a very interesting feature. It makes the initialization of trivial types (int, float, double, etc.) safe by default. This will only be available by default on C++26, but you can use it **today** via a special compilation flag.

Let's take a closer look at how this all works. You may have seen code like this before:

    int ii;
    std::cout << ii;

<!--more-->

What is the value of ii ? No one knows. This is a classic example of undefined behavior. Reading from an unitialized variable is unsafe practice. Don't do it !

Starting from C++26, however, things change. This is no longer undefined behavior, but erroneous behavior ([the proposal explains what that is](https://www.open-std.org/jtc1/sc22/wg21/docs/papers/2024/p2795r5.html)). To make things short, the standard says for cases like this, the compiler must initialize with an "erroneous value" it knows about. In other words, it's not random bytes from memory anymore, it's a well-defined, non-null sentinel value.

Check out my godbolt example (https://godbolt.org/z/a9cdbhr49) using the compilation flag *-ftrivial-auto-var-init=pattern*. For GCC, the int value gets initialized to **0xFFFF'FFFF'FEFE'FEFE**. For chars, it gets the value **-2**. These values are predictable (albeit not necessarily the same across vendors and versions) and could be used by compilers and/or developers to handle the code appropriately.

For information, I was able to get this working with GCC as early as 12.1. Clang-wise, I got it working on version 8.0.0.

Some may ask, Why don't you just initialize to zero ? If you did that, then there would be no way to disambiguate between a 0-initialized and uninitialized value. In other words, you could be transforming one bug into another. Furthermore, this could hide the problem from sanitizers.

I think this is all pretty solid. My only question would be regarding the choice of these sentinel values by compilers. It cannot be something obvious, otherwise it may fall down the ambiguity problem. The values I saw on GCC seem to be appropriate, though.


## Conclusion
So, what do you think? I believe this is a great feature, as safety is becoming more and more critical these days. I always admire how the Standard can come up with cool ways of solving problems without breaking backward compatibility. I'm definitely adding the new compilation flag to my projects.

## Sources

- Erroneous behaviour for uninitialized reads (Thomas Koppe)  https://www.open-std.org/jtc1/sc22/wg21/docs/papers/2024/p2795r5.html

- What does it mean to initialize an int? (Herb Sutter) https://herbsutter.com/2024/08/07/reader-qa-what-does-it-mean-to-initialize-an-int/