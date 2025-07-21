---
layout: custom-page
title: "Jai Compiler References"
permalink: /jai/
---

# Jai Compiler References

I got tired of looking up links over and over. Last update: April, 11, 2019

Jai is a computer language being developed by [Jonathan Blow](https://en.wikipedia.org/wiki/Jonathan_Blow) ([His older website](http://number-none.com/blow/) and newer [blog](http://number-none.com/blow/blog/)) and his team [Thekla](https://twitter.com/Thekla_Inc). The main goal is to replace C/C++ with a new language that will speed up the development of computer games (but it should be useful in general purpose programming.) The language's big concepts are:

* bring back the joy of programming
* putting data at the center of the design
* a syntax that respects the programmer's workflow
* controlling compiling from the language (compile-time-execution so you can write the build script in the language itself.)

## When will JAI release?

On April 10th, 2019 Abner Coimbre announced during his Twitch stream that the Jai Team decided on the final tasks need for Beta release. Coimbre didn't give a hard deadline, but it seems reasonable the team should finish before the end of 2019. (see http://www.mrphilgames.com/jai-close-to-beta/) (Note, on Jun 2018 Blow said four people were working on the compiler and a game using the language.)

## People blogging or streaming about Jai

* Abner Coimbre on Twitch: [https://www.twitch.tv/abnercoimbre](https://www.twitch.tv/abnercoimbre)
* [https://inductive.no/jai/](https://inductive.no/jai/)
* [http://www.alexisbreust.fr/2019-game-programmers-and-the-cpp-collapse.html](http://www.alexisbreust.fr/2019-game-programmers-and-the-cpp-collapse.html)
* [http://the-witness.net/news/category/engine-tech/](http://the-witness.net/news/category/engine-tech/)
* [A Jai to C converter/compiler written by a 3rd party](https://github.com/machinamentum/jai)

## Links and mentions by Jonathan Blow in his videos

* Sept'14 - the Talk that started it all (outdated at this point, see next link) [Ideas about a new programming language for games](https://www.youtube.com/watch?v=TH9VCN6UkyQ&index=1&list=PLmV5I2fxaiCKfxMBrNsU1kgKJXD3PkyxO)
* Jul'18 - Gamelab talk [Design decisions on creating Jai (or would you ever want to replace C++?!)](https://www.youtube.com/watch?v=uZgbKrDEzAs)
* Jan'18 - status update [January Progress Report](https://www.youtube.com/watch?v=rFaBs-CUX5w)
* YouTube Playlist: [A Programming Language for Games (Jonathan Blow's Videos on Jai)](https://www.youtube.com/playlist?list=PLmV5I2fxaiCKfxMBrNsU1kgKJXD3PkyxO)
* Mar'18 - Abner Coimbre in-depth blog: [Testing the Jai Compiler](http://the-witness.net/news/2018/03/testing-the-jai-compiler/)
* [Jorge Rodríguez's JAI Primer](https://sites.google.com/site/jailanguageprimer/) ([His blog post about it](http://bsvino.tumblr.com/post/109058912920/why-jai))
* [Inductive's JAI Page](https://inductive.no/jai/)
* [JAI Revolution Free (Visual Studio 2013)](https://visualstudiogallery.msdn.microsoft.com/511a3a8f-c2e8-4eb6-a5e7-ae49c2dc3553)
* Reddit:
    - Nov'14 - [First Reddit Thread](https://www.reddit.com/r/gamedev/comments/2mita3/jai_a_primer_written_by_a_fan_summarizing_the/)
    - Oct'15 - [The Second Reddit thread](https://www.reddit.com/r/programming/comments/3ou2gi/jon_blow_jai_compiler_demo_workspace_ast/)
    - Oct'15 - [Hacker News/Y Combinator Thread](https://news.ycombinator.com/item?id=10346985)
    - Jan'18 -[Jai Language Status Update](https://www.reddit.com/r/programming/comments/7okvam/jai_language_status_update/)
* Twitch [https://www.twitch.tv/naysayer88](https://www.twitch.tv/naysayer88)
* [BSVino/JaiPrimer](https://github.com/BSVino/JaiPrimer/blob/master/JaiPrimer.md)
* Jumplinks to parts about other language thoughts from the Video 1: [Ideas about a new programming language for games.](https://www.youtube.com/watch?v=TH9VCN6UkyQ&index=1&list=PLmV5I2fxaiCKfxMBrNsU1kgKJXD3PkyxO)
    - 6:19 [Go](https://golang.org/)
    - 8:35 [D](http://dlang.org/)
    - 10:02 [Rust](https://www.rust-lang.org/)
    - 14:04 [LLVM](http://llvm.org/)
* Important related topics:
    - [CppCon 2014: Mike Acton "Data-Oriented Design and C++"](https://www.youtube.com/watch?v=rX0ItVEVjHc)
    - [dyncall](http://www.dyncall.org/) - way JAI calls external C functions dynamically
    - [John Carmack on Inlined Code](http://number-none.com/blow/john_carmack_on_inlined_code.html)
    - He mentions talk on why exceptions are bad, maybe this video? [Andrei Alexandrescu - Systematic Error Handling in C++](https://channel9.msdn.com/Shows/Going+Deep/C-and-Beyond-2012-Andrei-Alexandrescu-Systematic-Error-Handling-in-C) or [Andrei Alexandrescu - Error Handling in C++](https://vimeo.com/97329153)
    - [Cfront](https://en.wikipedia.org/wiki/Cfront)

## Non Jai Links, but related to language creation

* Ginger Bill's
    + "sister" project [Odin](https://github.com/odin-lang/Odin)
    + Public Domain C/C++ Libraries in [Nothings' stb style](https://github.com/nothings/stb): [gb](https://github.com/gingerBill/gb/)
* [Should I use a parser generator or should I roll my own custom lexer and parser code?](http://programmers.stackexchange.com/questions/17824/should-i-use-a-parser-generator-or-should-i-roll-my-own-custom-lexer-and-parser)
* Dr. Dobb's [So You Want To Write Your Own Language?](http://www.drdobbs.com/architecture-and-design/so-you-want-to-write-your-own-language/240165488)
* [How To Write A Simple Lexical Analyzer or Parser](http://stlab.adobe.com/wiki/index.php/How_To_Write_A_Simple_Lexical_Analyzer_or_Parser)
* [Let's Build a Compiler, by Jack Crenshaw](http://compilers.iecc.com/crenshaw/)
* [Bret Victor - Inventing on Principle](https://vimeo.com/36579366)
* [The Next Mainstream Programming Language: A Game Developer's Perspective Tim Sweeney Epic Games (slides only)](https://www.st.cs.uni-saarland.de/edu/seminare/2005/advanced-fp/docs/sweeny.pdf)
* [Writing Your Own Toy Compiler Using Flex, Bison and LLVM](http://gnuu.org/2009/09/18/writing-your-own-toy-compiler/)
* [Building a Modern Computer from First Principles aka From NAND Gates to Tetris](http://www.nand2tetris.org/)
* [Tuukka Pensala's C or C++ for my game engine?](http://crafn.kapsi.fi/new_engine.html)
* [Building a C-based processor](http://fabiensanglard.net/fd_proxy/quake3/building_a_c_based_processor.pdf)
* Fabien Sanglard (of Black Book fame)'s [Quake Engine Code Review](http://fabiensanglard.net/quakeSource/index.php)