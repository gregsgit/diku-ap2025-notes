# Notes on Advanced Programming course from DIKU, 2025

Created, I think, mostly by [Troels
Henriksen](https://hjemmesider.diku.dk/~athas/).
Seems like also [Fritz
Henglein](https://di.ku.dk/english/staff/?pure=en/persons/14770). 

* Main site: https://github.com/diku-dk/ap-e2025-pub/tree/main
  * you probably want to clone or fork that repo

## Each week

* Read that week's [course notes](https://diku-dk.github.io/ap-notes),
  which are like a concise textbook
  
* Read that week's lecture notes and work through exercises; e.g.,
  [week 1](https://github.com/diku-dk/ap-e2025-pub/tree/main/week1)
  
  * To make sure you are set up with haskell, go to,
    e.g. `week1/handout` and make sure `cabal test` works (no errors) 
  
  * The recommended strategy for the exercises is to start editing the
    starter files in the `handout` folder. Note that the final
    exercise solutions are given in the `solution` folder, but the
    goal is for you to work out the exercise solutions yourself, with
    minimal reference to the `solution` folder sources

* Work on that week's assignment; e.g., [week 1](https://github.com/diku-dk/ap-e2025-pub/tree/main/a1) 
The assignment is in, e.g. "a1.pdf".
The "handout" archive contains a project tree with starter files to
which you are supposed to add code, including a unit test suite.
For week 1, at least, the assignment starting source is just the
result of doing the exercises. 

## Notes from working through week 2

Week 2 is implementing an interpreter for mostly the same language as
for week 1, but this time in a monadic style. While I found week 1
easy, I did struggle with the monadic approach. While writing
individual `eval` functions is more concise, the monadic plumbing
takes more work. Also, I'm still vaguely uneasy that monads hide both
state and control flow. 

I did find that struggling with the monad plumbing was very helpful
for me, including implementing the monadic type checker.

## Notes from working through week 1

My goal for looking into this course was to get comfortable with a
monad-centric approach to implementing a compiler, such as is
pervasive in the [futhark compiler](https://github.com/diku-dk/futhark). 

Unfortunately, week 1 doesn't touch on monads. Nonetheless, I spent a
fair amount of time tediously implementing the exercises, in the order
given, and writing test cases. It's pretty standard stuff if you've
written an interpreter before. It served to remind me of the basics of
Haskell. The assignment for week 1 took less time than the exercises
-- I found the tasks straightforward. I didn't spend time removing
parentheses from the pretty printer.

If you want to do some work, but not spend all the time working
through the exercises, you could jump right to the assignment. 

The beginning of `Eval_Tests.hs` in the week 1 assignment has
definition of the Y combinator, which is always baffling, and then
uses that definition to implement factorial. Very pretty.

The remaining weeks introduce basic functors, etc. and then monadic
parsing. Then there's a digression into "free monads" in
week 4. Troels said to ignore the free monad stuff, so I'm not sure
what to make of it. Nothing really on stacks of monads for
compilation.

## Using Nix for Haskell

Install nix following: https://nixos.org/download/#download-nix

To enable flakes, add the following to your `~/.config/nix/nix.conf`:
```
experimental-features = nix-command flakes
```

Even though the Haskell `stack` tool has nix integration, my approach
is very basic. I just do `nix develop` at the command line, which runs
this [flake.nix](./flake.nix) script, which puts me at a shell with
haskell tools available. From there, I start up an emacs, and haskell
mode is able to find everything.

If, for example, you've cloned the `ap-e2025-pub` repo and want to use
nix, you first have to copy the `flake.nix` file to the `ap-e2025-pub`
top level folder, and then do `git add flake.nix` so that nix "sees"
the file. Then you can do `nix develop`.

## Emacs with eglot and haskell language server lsp-haskell

For some reason, I have not been able to get eglot + lsp-haskell
working well for me. I can get the server to start, but errors from
build are not reported, which is a real pain. I've even tried copying
just, e.g. week1/handout to a folder under my ~/Downloads, thinking
the issue is that there are too many separate projects (one per week),
but that brute force approach did not seem to help.
