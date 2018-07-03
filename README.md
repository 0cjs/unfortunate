unfortunate: The Uncompiled Fortune Cookie Program
==================================================

This is a substitute for the standard BSD `/usr/games/fortune`
program. It's designed for a portable personal set of fortune cookies.

Unlike the standard [fortune-mod] program or [misfortune], it does not
need compiled indices for the fortune database (the `.dat` files), nor
does it even use compiiled code. Instead it's a simple Bash script
that works from the standard fortune source files sans indices.

On modern computers, and especially with a personal fortune collection
that is relatively small compared the full set distributed with most
Unix distributions, the indices now seem to be an unnecessary
optimization.


Usage
-----

This is designed to be used as a [dot-home] module:

    mkdir -p ~/.home
    cd ~/.home
    git clone https://github.com/dot-home/_dot-home.git     # Core system
    git clone https://github.com/dot-home/fortunesh.git     # This repo
    ~/.home/_dot-home/bin/dot-home-setup

However, you can also use it standalone:

1. Copy `bin/fortune` to `~/.local/bin/` or another directory in
   your path.
2. Put your fortune cookie files under `~/.local/share/fortune`.


File Format
-----------

Fortunes are stored in any number of files in `~/.local/share/fortune`.
Within a file a `%` alone on a line separates individual fortunes.


Bugs
----

* Standard fortune appears to `%` as a fortune terminator, not
  separator, as this program does. Adding `%` at the end of every
  fortune file would produce empty fortunes at this point. (Also,
  the Wikipedia entry for fortunate appears to incorrectly assert
  that `%` is a separator, not a terminator.)
* For compatibility with other fortune programs, this should ignore
  files ending in `.dat`. (These are the compiled indices for the
  fortune cookie files.)
* This should probably also look for fortune files in subdirs of the
  fortune dir, as `fortune-mod` does.
* This should be configurable to read the standard system fortune
  files (under `/usr/share/games/fortune/`) as well.
* There's currently no support for offensive fortunes (the `-o` flag).
  Files containing offensive fortunes are stored either under an `off`
  subdir or end with `-o`, and the fortunes themselves are stored in
  `rot13` format.



[dot-home]: https://github.com/dot-home/_dot-home/
[fortune-mod]: https://github.com/shlomif/fortune-mod
[misfortune]: https://github.com/mokus0/misfortune
