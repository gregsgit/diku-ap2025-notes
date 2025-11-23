# Notes on Advanced Programming course from DIKU, 2025

Created, I think, mostly by [Troels
Henriksen](https://hjemmesider.diku.dk/~athas/).
Seems like also [Fritz
Henglein](https://di.ku.dk/english/staff/?pure=en/persons/14770). 

* Main page: https://github.com/diku-dk/ap-e2025-pub/tree/main

## Each week

* Read that week's [course notes](https://diku-dk.github.io/ap-notes),
  which are like a concise textbook
  
* Read that week's lecture notes and work through exercises; e.g.,
  [week 1](https://github.com/diku-dk/ap-e2025-pub/tree/main/week1)
  
* Work on that week's assignment; e.g., 
[week 1](https://github.com/diku-dk/ap-e2025-pub/tree/main/a1) 

## Nix

Install nix following: https://nixos.org/download/#download-nix

To enable flakes, add the following to your `~/.config/nix/nix.conf`:
```
experimental-features = nix-command flakes
```

Even though the Haskell `stack` tool has nix integration, my approach
is very basic. I just do `nix develop` at the command line, which runs
the [flake.nix](./flake.nix), which puts me at a shell with haskell
tools available. From there, I start up an emacs, and haskell mode is
able to find everything. 

If, for example, you've cloned the `ap-e2025-pub` repo and want to use
nix, you first have to add the `flake.nix` file to the folder, and
then do `git add flake.nix` so that nix "sees" the file.

