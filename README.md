** Dcrtxmatcher server for join split transaction
Dcrtxmatcher refers dicemix and coinshuffle++ to perform coinjoin as in https://crypsys.mmci.uni-saarland.de/projects/FastDC/paper.pdf

Dicemix uses flint libs to solve polynomial to get roots as peer's output address.So we need to build flint libs and dependency.

There are two options to get it works.

- Build flint from scratch (suggestion)
- Download header files and pre-built libs


* Download header files and pre-built libs:

- Download libs directory in dcrtxmatcher.

There are four directories. Copy all files in each directory to equivalent directory of your linux distro.
The paths used in this document is referred to ubuntu 18.4

- usr-local-lib: copy lib files of mpir, mpfr to /usr/local/lib
- usr-local-include: copy header files of mpir, mpfr to /usr/local/include
- usr-local-flint-lib: copy libs of flint to /usr/local/flint/lib
- flint-include: copy header files of flint to dcrtxmatcher/flint/include

* Build flint from scratch

Download and build following libs. We can switch between mpir and gmp.

- mpir: http://www.mpir.org/downloads.html

$ apt-get install automake
$ ./configure && make
$ make check
$ make install

- mpfr: https://www.mpfr.org/mpfr-current/#download

$ sudo apt-get install yasm
$ make
$ make check
$ make install

- flint: http://www.flintlib.org/downloads.html

open Makefile.subdirs and replace -W,-r with -r
$ sudo ./configure --with-mpir=/usr/local/ --with-mpfr=/usr/local/ --prefix=flint
$ make
$ make check
$ make install
