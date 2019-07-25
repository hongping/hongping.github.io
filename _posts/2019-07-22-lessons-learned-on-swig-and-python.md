---
tags:
- swig
- python
categories:
- misc
title: lessons learned on swig and python
---

Recently I have been trying to use [SWIG](http://www.swig.org/ "SWIG") to wrap around a shared library in python. Without prior experience and understanding, I blindly created an interface file and run, hoping everything will just magically works. Well, it didn't... And it took me two long months to realize I made some stupid mistakes. Documenting the stuff here, hopefully no silly mistakes in future.
{: style="text-align: justify;"}

The very first mistake I made is **not ignoring unimplemented prototype**. Since I am wrapping around a shared library, I will just include the header files provided. However, that doesn't mean that it will be implemented in the binary. Sometimes, the developer may just put a deprecated codes for backward compatibility, or, those are for future usages. Without realizing this, I kept on trying different method to get past the failure point. Changing the compile and link command do not help, and reordering the interface file also didn't work. By google-ing, I found the command [c++filt](https://linux.die.net/man/1/c++filt "c++filt") helped a lot. Since my error happened during python trying to load the generated shared library by throwing out some weird symbol, using c++filt, I get some hints on which method is problematic. Then, trying to ignore those in the interface file and I able to load the shared library in python. What is more hilarious, when I change my SWIG to version **4**, those errors are prompted, with clear printout which method is problematic... duh... So, the next lesson is, **always use the latest version if possible**. :sweat_smile:
{: style="text-align: justify;"}

The next failure I hit into is not realizing **SWIG will ignore all #include in source code**. I hit into a failure when I am trying to use the wrapped library where it not able recognize a **_typedef_** which mapped to std::string. Later only I know that SWIG ignored the "**#include <string>**". I need to include those in my interface file.
{: style="text-align: justify;"}

After gone past all of these, I able to use the wrapped library happily! I guess the final lesson I learned is **be perseverance**! I almost wanted to give up and forget about this... Somehow, I kept on finding solution and voila, I made this happened.
{: style="text-align: justify;"}