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

* Work on that week's assignment; e.g., 
[week 1](https://github.com/diku-dk/ap-e2025-pub/tree/main/a1) 

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
