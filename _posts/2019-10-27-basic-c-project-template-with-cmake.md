---
tags:
- cpp
- programming
- template
title: Basic C++ Project Template with CMake
categories:
- cpp

---
It has been awhile since I last coded in C++. The last compiler I used was Borland Turbo C++. Ever since then, I shifted away from C++ to other interpreted languages like Perl and Python, and also bits of Javascript for web based works.
{: style="text-align: justify;"}

I am ramping up on C++ again as I am creating executable which performance is what I am craving for. I was looking at the tools for C++, and am pretty amazed with all the new (and open source!) technologies available today.
{: style="text-align: justify;"}

After hunting for a week or two (yes, I am a indecisive programmer, with a bit of procrastination as well), I settled down with [clang](https://clang.llvm.org) as my compiler, [CMake](https://cmake.org) as the build files generator, and [ninja](https://ninja-build.org) as the build system. Also, not to forget about unit testing, I used [Google Test](https://github.com/google/googletest).
{: style="text-align: justify;"}

The criteria of tool selection is largely based on cross OS compatibility. For e.g., I choose clang over MSVC or gcc mostly due to clang can easily be used in either Windows or Linux. Same as CMake. Using CMake, I don't need to worried about which build tool to be selected later. I opt for ninja as in Windows, that's the most sensible option for me since I am not using Visual Studio.
{: style="text-align: justify;"}

While setting up a C++ project of mine, I noticed that there will be a fixed structure of directory I could reuse, hence, I created this repository in Github, served as the basic template for my future project. It is known as [hongping/cpp_template](https://github.com/hongping/cpp_template) in Github.
{: style="text-align: justify;"}

The template comes with Google Test version 1.10.0 source code in the `external` directory, and the CMake files will build a basic test in `tests` directory which is to test the aliveness of the project. Once done build and execute `tests\runUnitTests`, you should be able to see the following
{: style="text-align: justify;"}

```
Running main() from ../external/googletest-release-1.10.0/googletest/src/gtest_main.cc
[==========] Running 1 test from 1 test suite.
[----------] Global test environment set-up.
[----------] 1 test from DOA
[ RUN      ] DOA.gtestAlive
[       OK ] DOA.gtestAlive (0 ms)
[----------] 1 test from DOA (0 ms total)
[----------] Global test environment tear-down
[==========] 1 test from 1 test suite ran. (4 ms total)
[  PASSED  ] 1 test.
```

Feel free to clone [hongping/cpp_template](https://github.com/hongping/cpp_template) and use this for your future project!
{: style="text-align: justify;"}

_This post was originally posted at [dev.to](https://dev.to/hongping/basic-c-project-template-with-cmake-49p8)_ 