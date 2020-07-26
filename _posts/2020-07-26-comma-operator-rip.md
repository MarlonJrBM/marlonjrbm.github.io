---
title: "Goodbye Comma Operator, Goodbye"
categories:
  - C++
tags:
  - C++
  - C++20
  - Comma Operator
excerpt_separator: "<!--more-->"
---

It's always sad to see a feature that I extensively used being deprecated of your favorite programming language. Such a sad destiny, How could the gods of C++ have done this to me?

No, actually I'm just kidding. I've never used it in the way described below, and I guess no one ever has. Have you?

On on a more serious note, it's nice to see the committee is doing some clean-up at least. Let go of the past we must, young Jedi.

<!--more-->

&nbsp; 

## The past

Until C++20, there were some funny things we could do with comma operator, such as:

    int myFunc() {
        std::vector<int> data {42,43,45,142};
        return data[2,3];
    }


I can hear some of you saying that no one has ever written such an aberration, and I will be the first to admit I've never seen a C++ code like that in production code, and I hope I never will. Still, my skeptical friend, what does the above myFunc() return?

After reflecting for a while and remembering the good old days when you were learning C, you will remember that the comma operator had this funny little property of evaluating all expressions and returning the last one. So, for the above example, the value 3 will be returned. Therefore, we will be returning data[3], which is 142.


## The future

According to the approved proposal [P1161R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1161r3.html) (Deprecate uses of the comma operator in subscripting expressions), the above use case will be deprecated starting in C++20.

Are you searching for proof? Please go talk to my friend [godbolt, he will show you](https://godbolt.org/z/P156ve). Have you met him by the way? He's really nice.

Anyway, you can see that gcc 10.1 returns the following warning:

    <source>:6:18: warning: top-level comma expression in array subscript is deprecated [-Wcomma-subscript]
        6 |     return data[2,3];

Pretty cool, isn't it?

Furthermore, the authors of the proposal suggest that deprecating this use case of the comma operator will open the door to *multidimensional subscript operators*. Imagine a world where C++ supports *multidimensional subscript operators*. I can barely do it, but I'm sure there is a hip language out there that already does it, and if the cool kids are doing it, I want to do it too... probably.  

## There will always be a comma in your heart

Attention, in spite of this post's article, I didn't mean to say that the comma operator will be gone forever and ever. If you read attentively the proposal, it will only lose the aforementioned property in subscripting expressions, such as:

    std::cout << myVec[doStuff(), returnAnInt()]; // Bad code, bad code.

However, you will still be able to use the comma operators in all other contexts, even in subscripting expressions, provided you put the expression inside parenthesis:

    void f(int *a, int b, int c) {
        a[b,c];   // deprecated
        a[(b,c)]; // OK
    }  

&nbsp;  

## Thanks

Well, this is it for the comma operator. It's not really gone, but we might change the way we see it entirely in the near future. Thanks for reading until here, I hope you have not left this post dumber than you have entered it. Have a good one!
  
_________________

Sources:

- <http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1161r3.html>
- <https://www.youtube.com/watch?v=qD1aKLux5Fw>

