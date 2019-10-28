---
title: "My experience as a Software Developer in the EDA Industry"
categories:
  - EDA
tags:
  - EDA
  - programming
  - software development
excerpt_separator: "<!--more-->"
---

Here’s a typical conversation I often find myself having:

> Person : So Marlon, what do you work with?
>
> Marlon: I make programs. =D
<!--more-->
>
> Person: Cool! What kind of programs?
>
> Awkward silence…
>
> Marlon: Hmmm… Sorry, but I really need to go now…



My usual answer is not very descriptive, I know. Sometimes I say “I work in the EDA Industry” but that doesn’t seem to be any more helpful. There are even some people who work with software development and don’t have the slightest clue, but I don’t blame them. Software Development for EDA is definitely not as popular these days as Web Development or Mobile Development. Yet the EDA industry will hardly go extinct before humankind does. Why, you ask? Well, that’s what I hope to show in this post. =)

![](/assets/images/waveform.jpg)

## So what is EDA?
EDA stands for Electronic Design Automation, and is sometimes referred to ECAD (Electronic Computer-Aided Design). In a nutshell, this industry builds software solutions that aid the design of hardware components or electronic systems, such as integrated circuits and printed circuit boards. Since these electronic systems can be huge nowadays (have over billions of components), software tools are essential for their creation. These tools can come in many different flavors, as the EDA field can be divided into several subareas, like logic simulation, hardware emulation, formal verification, among many, many others.

It’s actually kind of overwhelming the amount of techniques that were developed over the years and how they greatly influenced the growth of the industry (commercial EDA started in 1981). Like many areas in Computer Science, it truly inspires me awe to see the amount of knowledge we have accumulate so far. Gotta thank all those brilliant computer scientist and engineers!

But why is EDA important? Considering the enormous complexity of microprocessors we have today, I’d like to invite you for a brief thought experiment. Imagine a world in which companies could only validate their chips after they were manufactured. Do you think they would get everything right in just one try? Or would it take them multiple attempts? In my opinion, this scenario would be a real dystopia, in which the personal computer was never invented (maybe that would be a good thing, but then again, no… I’d totally be unemployed, haha).



## What do I actually do?
One of the many flavors of the EDA industry is called hardware emulation: the ability to imitate the behavior of a certain piece of hardware by using another special piece of hardware, such as FPGAs. This approach is commonly used to test complex microprocessors and SoC (System on Chips) before they are manufactured. Fortunately, the EDA Industry currently provides emulators with highly advanced debugging capabilities, which saves designers a considerable amount of time, and also keep me employed. =)

So, to answer the question in the subtitle, as a software developer in the EDA Industry, I mostly work in developing debugging tools that are built on top of these highly sophisticated hardware emulation platforms. The language I mostly code in is C++, but I also occasionally write code in TCL, Verilog and Python. My daily routine also involves activities that are common to any developer: code review, version control, testing, etc.

Having said that, I believe that developing in C++ (and working in this industry in general) gives me a slightly different perspective on programming compared to other software development domains. The applications I build need to have a deeper awareness of the underlying hardware (remember that’s what EDA is all about), as well as a critical demand on performance. This forces the developer to stay in constant touch with “lower-level affairs”, like memory management, undefined behaviors and portability across different architectures. Other domains, like web development, simply don’t have these requirements (but they indeed face other kinds of challenges), which allows them to save time by working at higher levels of abstraction.

Finally, most of the programs I write are CLI-based (command line interface) — which kind of makes sense, considering the users of said programs are highly talented computer engineers. Still, there is space for some hybrid and GUI-based applications: these can be very convenient at times, even for the most talented user.



## Companies
Although EDA is not the most popular field at the moment, there are a plethora of companies that work in the area. The main ones that come to my mind are:

- Synopsys, Inc.;
- Cadence Design Systems;
- Mentor Graphics;
- Altera;
- Xilink;

For a complete list, check Wikipedia’s article: <https://en.wikipedia.org/wiki/List_of_EDA_companies>


## Final Thoughts
Please leave your feedback. Do you have any questions about EDA? Did I make any errors in my descriptions? What is YOUR experience as a software developer? Feel free to comment whatever is on your mind, I’d really appreciate it. =)
