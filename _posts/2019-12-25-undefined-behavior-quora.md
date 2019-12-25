---
title: "An example of Undefined Behavior in C"
categories:
  - C++
  - Undefined Behavior
tags:
  - C
  - Undefined Behavior
excerpt_separator: "<!--more-->"
---
(This post is a republish of a Quora answer I gave 2 years ago: <https://www.quora.com/What-is-wrong-with-this-C-code-8/answer/Marlon-Marques>).

## Question

What is wrong with this C code?

<!--more-->

    int main() {
	    char *a = malloc(5);
	    a[5] = '\0';
	    size_t i = 0;
	    while (i < 5) a[i++] = ' ';
	    printf("'%s'\n", a);
	    free(a);
	    return 0;
    }


## My answer

Oh, my dear fellow Quoran, you are looking at the bogeyman of C programming: the **undefined behavior.**

You see, your code (I’m assuming that’s all you wrote), actually runs on my computer without any errors. But that’s the thing about undefined behavior: it can produce any result, even a successful one. It can even work sometimes, and crash at others. The bottom line is that undefined behavior is something you want to avoid at all costs (refer to recommended reading below).

Let’s go through your code line by line and I’ll show you where the bogeyman lies:

    char *a = malloc(5);

Here you’re essentially doing two things:

1. Allocating memory dynamically with malloc: since you’re passing 5 as parameter, you allocate 5 bytes of memory.
2. You’re declaring a char pointer named a, and you’re making it point to the recently allocated memory.

Now, moving on to: 

    a[5] = '\0';

Oh, oh, **undefined behavior alert!** Remember that you allocated **5 bytes** of memory? Well, my friend, you need to remember that computers always count from 0. That means when you write **a[5]**, you’re actually referring to the **6th element** of the array. In other words, **you are messing with memory which you did not allocate**.** That’s a classic **undefined behavior!** You don’t wanna do that, ever. However, that’s easy to fix: allocate an extra byte for that null character. Do **malloc(6)** in the previous line and you’ll be fine. =)

    size_t i = 0;
    while (i < 5) a[i++] = ' ';
    printf("'%s'\n", a);

You’re using the postincrement operator (i++) here very nicely! The effect of this chunk of code is to set your array of chars (a[0] to a[4]) to the whitespace character (‘ ’). Then, it will print 5 whitespace characters, followed by a newline. This is all correct.

    free(a);

This is also correct. You need to pass a pointer to the free function, which points to a previously allocated chunk of memory, and your **a** variable fits the criteria. =)

I hope this answer will help you somehow, and that you steer clear of undefined behaviors as much as you can. Finally, I would just like to add one comment to this statement of yours:

> or it would take memory on your computer until you restart it.

Once your program finishes running, **all program memory (even the part you did not unallocate with free) will be freed by the operating system.** Fortunately, operating systems are smarter than you’d think. Having said that, we programmers should not get sloppy: let’s always free the memory we allocate! For small programs memory leakage is not a problem, but when it comes to programs that are huge and very important, memory leaks can be a real nightmare.

**EDIT (Feb 9th)**: As my very clever friend Thiago Martins pointed out, the below line could also be problematic:

    printf("'%s'\n", a);

Over here you’re using the string format specifier (%s), which is good. But remember that C-strings are null terminated. Considering that your NULL character is situated in memory you did not allocate (a[5]), this piece of code will end up reading **unallocated memory (undefined behavior).**

Boy, tracking undefined behavior can be a hard task! But at the end, I guess it’s one of the joys of being a C programmer. =)

_________________

Recommended reading:

- <https://blog.regehr.org/archives/213>
- <https://www.programiz.com/c-programming/c-dynamic-memory-allocation>
- <http://www.geeksforgeeks.org/storage-for-strings-in-c/>

