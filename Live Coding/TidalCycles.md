# TidalCycles

## Install with neovim
* Install the libs
```
yay -S haskell-tidal
```
* Install the vim-tidal plguin: 'tidalcycles/vim-tidal'
* Set g:tidal_target to "terminal"
* Clone the git repository and run "sudo make install"

## Install dependencies
* If supercollider is not installed, install it. Run supercollider with scide.
* Install dependencies: cabal, install, jack, git, build essentials
* Run supercollider with "scide" and run the following to install SuperDirt:
```
Quarks.checkForUpdates({Quarks.install("SuperDirt", "v1.1.3");
thisProcess.recompile()})
```
* Jackd must first be running before starting SuperDirt
* Start SuperDirt in SuperCollider with:
```
include("SuperDirt");
SuperDirt.start;
```

## Run in neovim
* Make a file ending with .tidal
* Hit Ctrl+E to execute a line of code:
```
d1 $ s "bd hh bd hh"
```
