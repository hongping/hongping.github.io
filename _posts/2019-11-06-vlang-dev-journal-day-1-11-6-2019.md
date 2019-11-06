---
tags: []
title: vlang dev journal - day 1 (11/6/2019)
categories:
- journal
- vlang

---
This will be the first development journal for [vlang](https://github.com/hongping/vlang). Wanted to record down the work as a way to keep myself motivated to complete a project, as well as making sure the knowledge is not lost else where. The journal will be in bullet notes format, as that's how I keep track of the things as well as my thought stream.

Let's the development begin... On day 1, there is nothing much, but mostly doing research...

* need to create a parser for system verilog, which is the most important part of the project.
* generally there are two ways of constructing parser
  1. using parser generator tool like antlr4, flex/bison, lex/yacc, etc.
  2. handcrafted the parser, like clang
* there are many existing parser framework for system verilog
|repo|language|
|---|---|
|https://github.com/Nic30/hdlConvertor|antlr4 c++ runtime|
|https://github.com/veriktig/ieee1800_2017|antlr4 java runtime|
|https://github.com/MikePopoloski/slang|handcraft c++|
|https://github.com/dalance/sv-parser|handcraft rust|
|verilator|flex/bison c++|
|icarus verilog|flex/bison c++|
* not planning to use parser generator
  * not wanting to have extra tool dependency during build
  * not wanting to have dependency on runtime
* will be referencing [slang](https://github.com/MikePopoloski/slang) for the parser creation while also learn more about parsing and c++
* not planning to fork the project, although the license is MIT. I wanted to learn from scratch as well 😁

And that's conclude day 1. Day 2 will begin some works on basic repository setup and deep dive into slang.