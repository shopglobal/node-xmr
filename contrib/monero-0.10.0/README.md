# Monero

Copyright (c) 2014-2016, The Monero Project

[![Build Status](https://travis-ci.org/monero-project/monero.svg?branch=master)](https://travis-ci.org/monero-project/monero)
[![Coverage Status](https://coveralls.io/repos/github/monero-project/monero/badge.svg?branch=master)](https://coveralls.io/github/monero-project/monero?branch=master)

## Development Resources

- Web: [getmonero.org](https://getmonero.org)
- Forum: [forum.getmonero.org](https://forum.getmonero.org)
- Mail: [dev@getmonero.org](mailto:dev@getmonero.org)
- GitHub: [https://github.com/monero-project/monero](https://github.com/monero-project/monero)
- IRC: [#monero-dev on Freenode](irc://chat.freenode.net/#monero-dev)

## Introduction

Monero is a private, secure, untraceable, decentralised digital currency. You are your bank, you control your funds, and nobody can trace your transfers unless you allow them to do so.

**Privacy:** Monero uses a cryptographically sound system to allow you to send and receive funds without your transactions being easily revealed on the blockchain (the ledger of transactions that everyone has). This ensures that your purchases, receipts, and all transfers remain absolutely private by default.

**Security:** Using the power of a distributed peer-to-peer consensus network, every transaction on the network is cryptographically secured. Individual wallets have a 24 word mnemonic seed that is only displayed once, and can be written down to backup the wallet. Wallet files are encrypted with a passphrase to ensure they are useless if stolen.

**Untraceability:** By taking advantage of ring signatures, a special property of a certain type of cryptography, Monero is able to ensure that transactions are not only untraceable, but have an optional measure of ambiguity that ensures that transactions cannot easily be tied back to an individual user or computer.

## About this Project

This is the core implementation of Monero. It is open source and completely free to use without restrictions, except for those specified in the license agreement below. There are no restrictions on anyone creating an alternative implementation of Monero that uses the protocol and network in a compatible manner.

As with many development projects, the repository on Github is considered to be the "staging" area for the latest changes. Before changes are merged into that branch on the main repository, they are tested by individual developers in their own branches, submitted as a pull request, and then subsequently tested by contributors who focus on testing and code reviews. That having been said, the repository should be carefully considered before using it in a production environment, unless there is a patch in the repository for a particular show-stopping issue you are experiencing. It is generally a better idea to use a tagged release for stability.

**Anyone is welcome to contribute to Monero's codebase!** If you have a fix or code change, feel free to submit is as a pull request directly to the "master" branch. In cases where the change is relatively small or does not affect other parts of the codebase it may be merged in immediately by any one of the collaborators. On the other hand, if the change is particularly large or complex, it is expected that it will be discussed at length either well in advance of the pull request being submitted, or even directly on the pull request.

## Supporting the Project

Monero development can be supported directly through donations.

Both Monero and Bitcoin donations can be made to donate.getmonero.org if using a client that supports the [OpenAlias](https://openalias.org) standard

The Monero donation address is: `44AFFq5kSiGBoZ4NMDwYtN18obc8AemS33DBLWs3H7otXft3XjrpDtQGv7SqSsaBYBb98uNbr2VBBEt7f2wfn3RVGQBEP3A` (viewkey: `f359631075708155cc3d92a32b75a7d02a5dcf27756707b47a2b31b21c389501`)

The Bitcoin donation address is: `1KTexdemPdxSBcG55heUuTjDRYqbC5ZL8H`

Core development funding and/or some supporting services are also graciously provided by sponsors:

[<img width="80" src="https://static.getmonero.org/images/sponsors/mymonero.png"/>](https://mymonero.com)
[<img width="150" src="https://static.getmonero.org/images/sponsors/kitware.png?1"/>](http://kitware.com)
[<img width="100" src="https://static.getmonero.org/images/sponsors/dome9.png"/>](http://dome9.com)
[<img width="150" src="https://static.getmonero.org/images/sponsors/araxis.png"/>](http://araxis.com)
[<img width="150" src="https://static.getmonero.org/images/sponsors/jetbrains.png"/>](http://www.jetbrains.com/)
[<img width="150" src="https://static.getmonero.org/images/sponsors/navicat.png"/>](http://www.navicat.com/)
[<img width="150" src="https://static.getmonero.org/images/sponsors/symas.png"/>](http://www.symas.com/)

There are also several mining pools that kindly donate a portion of their fees, [a list of them can be found on our Bitcointalk post](https://bitcointalk.org/index.php?topic=583449.0).

## License

See [LICENSE](LICENSE).

## Installing Monero from a Package

Packages are available for

* Arch Linux via AUR: [`bitmonero-git`](https://aur.archlinux.org/packages/bitmonero-git)

* OS X via [Homebrew](http://brew.sh)

        brew tap sammy007/cryptonight
        brew install monero --build-from-source

* Docker

        docker build -t monero .
     
        # either run in foreground
        docker run -it -v /monero/chain:/root/.bitmonero -v /monero/wallet:/wallet -p 18080:18080 monero

        # or in background
        docker run -it -d -v /monero/chain:/root/.bitmonero -v /monero/wallet:/wallet -p 18080:18080 monero

Packaging for your favorite distribution would be a welcome contribution!

## Compiling Monero from Source

### Dependencies

The following table summarizes the tools and libraries required to build.  A
few of the libraries are also included in this repository (marked as
"Vendored"). By default, the build uses the library installed on the system,
and ignores the vendored sources. However, if no library is found installed on
the system, then the vendored source will be built and used. The vendored
sources are also used for statically-linked builds because distribution
packages often include only shared library binaries (`.so`) but not static
library archives (`.a`).

| Dep            | Min. Version  | Vendored | Debian/Ubuntu Pkg  | Arch Pkg       | Optional | Purpose        |
| -------------- | ------------- | ---------| ------------------ | -------------- | -------- | -------------- |
| GCC            | 4.7.3         | NO       | `build-essential`  | `base-devel`   | NO       |                |
| CMake          | 3.0.0         | NO       | `cmake`            | `cmake`        | NO       |                |
| pkg-config     | any           | NO       | `pkg-config`       | `base-devel`   | NO       |                |
| Boost          | 1.58          | NO       | `libboost-all-dev` | `boost`        | NO       |                |
| BerkeleyDB     | 4.8           | NO       | `libdb{,++}-dev`   | `db`           | NO       |                |
| libevent       | 2.0           | NO       | `libevent-dev`     | `libevent`     | NO       |                |
| libunbound     | 1.4.16        | YES      | `libunbound-dev`   | `unbound`      | NO       |                |
| libminiupnpc   | 2.0           | YES      | `libminiupnpc-dev` | `miniupnpc`    | YES      | NAT punching   |
| libunwind      | any           | NO       | `libunwind8-dev`   | `libunwind`    | YES      | stack traces   |
| ldns           | 1.6.17        | NO       | `libldns-dev`      | `ldns`         | YES      | ?              |
| expat          | 1.1           | NO       | `libexpat1-dev`    | `expat`        | YES      | ?              |
| GTest          | 1.5           | YES      | `libgtest-dev`^    | `gtest`        | YES      | test suite     |
| Doxygen        | any           | NO       | `doxygen`          | `doxygen`      | YES      | documentation  |
| Graphviz       | any           | NO       | `graphviz`         | `graphviz`     | YES      | documentation  |

[^] On Debian/Ubuntu `libgtest-dev` only includes sources and headers. You must
build the library binary manually.

### Build instructions

Monero uses the CMake build system and a top-level [Makefile](Makefile) that
invokes cmake commands as needed.

#### On Linux and OS X

* Install the dependencies
* Change to the root of the source code directory and build:

        cd monero
        make

    *Optional*: If your machine has several cores and enough memory, enable
    parallel build by running `make -j<number of threads>` instead of `make`. For
    this to be worthwhile, the machine should have one core and about 2GB of RAM
    available per thread.

* The resulting executables can be found in `build/release/bin`.

* **Optional**: build and run the test suite to verify the binaries:

        make release-test

    *NOTE*: `coretests` test may take a few hours to complete.

* **Optional**: to build binaries suitable for debugging:

         make debug

* **Optional**: to build statically-linked binaries:

         make release-static

* **Optional**: build documentation in `doc/html` (omit `HAVE_DOT=YES` if `graphviz` is not installed):

        HAVE_DOT=YES doxygen Doxyfile


#### On Windows:

Binaries for Windows are built on Windows using the MinGW toolchain within
[MSYS2 environment](http://msys2.github.io). The MSYS2 environment emulates a
POSIX system. The toolchain runs within the environment and *cross-compiles*
binaries that can run outside of the environment as a regular Windows
application.

**Preparing the Build Environment**

* Download and install the [MSYS2 installer](http://msys2.github.io), either the 64-bit or the 32-bit package, depending on your system.
* Open the MSYS shell via the `MSYS2 Shell` shortcut
* Update the core packages in your MSYS2 install:

        update-core  
        
* Exit the MSYS shell using Alt+F4, then restart MSYS and update packages using pacman:  

        pacman -Syuu  

* Exit the MSYS shell using Alt+F4  
* Edit the properties for the `MSYS2 Shell` shortcut changing "msys2_shell.bat" to "msys2_shell.cmd -mingw64" for 64-bit builds or "msys2_shell.cmd -mingw32" for 32-bit builds
* Restart MSYS shell via modified shortcut and update packages again using pacman:  

        pacman -Syuu  


* Install dependencies:

    To build for 64-bit Windows:

        pacman -S mingw-w64-x86_64-toolchain make mingw-w64-x86_64-cmake mingw-w64-x86_64-boost

    To build for 32-bit Windows:
 
        pacman -S mingw-w64-i686-toolchain make mingw-w64-i686-cmake mingw-w64-i686-boost

* Open the MingW shell via `MinGW-w64-Win64 Shell` shortcut on 64-bit Windows
  or `MinGW-w64-Win64 Shell` shortcut on 32-bit Windows. Note that if you are
  running 64-bit Windows, you will have both 64-bit and 32-bit MinGW shells.

**Building**

* If you are on a 64-bit system, run:

        make release-static-win64

* If you are on a 32-bit system, run:

        make release-static-win32

* The resulting executables can be found in `build/release/bin`

### On FreeBSD:

The project can be built from scratch by following instructions for Linux above.

We expect to add Monero into the ports tree in the near future, which will aid in managing installations using ports or packages.

### On OpenBSD:

This has been tested on OpenBSD 5.8.

You will need to add a few packages to your system. `pkg_add db cmake gcc gcc-libs g++ miniupnpc gtest`.

The doxygen and graphviz packages are optional and require the xbase set.

The Boost package has a bug that will prevent librpc.a from building correctly. In order to fix this, you will have to Build boost yourself from scratch. Follow the directions here (under "Building Boost"):
https://github.com/bitcoin/bitcoin/blob/master/doc/build-openbsd.md

You will have to add the serialization, date_time, and regex modules to Boost when building as they are needed by Monero.

To build: `env CC=egcc CXX=eg++ CPP=ecpp DEVELOPER_LOCAL_TOOLS=1 BOOST_ROOT=/path/to/the/boost/you/built make release-static-64`

### Building Portable Statically Linked Binaries

By default, in either dynamically or statically linked builds, binaries target the specific host processor on which the build happens and are not portable to other processors. Portable binaries can be built using the following targets:

* ```make release-static-64``` builds binaries on Linux on x86_64 portable across POSIX systems on x86_64 processors
* ```make release-static-32``` builds binaries on Linux on x86_64 or i686 portable across POSIX systems on i686 processors
* ```make release-static-arm8``` builds binaries on Linux on armv8 portable across POSIX systems on armv8 processors
* ```make release-static-arm7``` builds binaries on Linux on armv7 portable across POSIX systems on armv7 processors
* ```make release-static-arm6``` builds binaries on Linux on armv7 or armv6 portable across POSIX systems on armv6 processors, such as the Raspberry Pi
* ```make release-static-win64``` builds binaries on 64-bit Windows portable across 64-bit Windows systems
* ```make release-static-win32``` builds binaries on 64-bit or 32-bit Windows portable across 32-bit Windows systems

## Running monerod

The build places the binary in `bin/` sub-directory within the build directory
from which cmake was invoked (repository root by default). To run in
foreground:

    ./bin/monerod

To list all available options, run `./bin/monerod --help`.  Options can be
specified either on the command line or in a configuration file passed by the
`--config-file` argument.  To specify an option in the configuration file, add
a line with the syntax `argumentname=value`, where `argumentname` is the name
of the argument without the leading dashes, for example `log-level=1`.

To run in background:

    ./bin/monerod --log-file monerod.log --detach

To run as a systemd service, copy
[monerod.service](utils/systemd/monerod.service) to `/etc/systemd/system/` and
[monerod.conf](utils/conf/monerod.conf) to `/etc/`. The [example
service](utils/systemd/monerod.service) assumes that the user `monero` exists
and its home is the data directory specified in the [example
config](utils/conf/monerod.conf).

If you're on Mac, you may need to add the `--max-concurrency 1` option to
monero-wallet-cli, and possibly monerod, if you get crashes refreshing.

## Internationalization

See README.i18n

## Using Tor

While Monero isn't made to integrate with Tor, it can be used wrapped with torsocks, if you add --p2p-bind-ip 127.0.0.1 to the monerod command line. You also want to set DNS requests to go over TCP, so they'll be routed through Tor, by setting DNS_PUBLIC=tcp. You may also disable IGD (UPnP port forwarding negotiation), which is pointless with Tor. To allow local connections from the wallet, you might have to add TORSOCKS_ALLOW_INBOUND=1, some OSes need it and some don't. Example:

`DNS_PUBLIC=tcp torsocks monerod --p2p-bind-ip 127.0.0.1 --no-igd`

or:

`DNS_PUBLIC=tcp TORSOCKS_ALLOW_INBOUND=1 torsocks monerod --p2p-bind-ip 127.0.0.1 --no-igd`

TAILS ships with a very restrictive set of firewall rules. Therefore, you need to add a rule to allow this connection too, in addition to telling torsocks to allow inbound connections. Full example:

`sudo iptables -I OUTPUT 2 -p tcp -d 127.0.0.1 -m tcp --dport 18081 -j ACCEPT`

`DNS_PUBLIC=tcp torsocks ./monerod --p2p-bind-ip 127.0.0.1 --no-igd --rpc-bind-ip 127.0.0.1 --data-dir /home/amnesia/Persistent/your/directory/to/the/blockchain`

`./monero-wallet-cli`

## Using readline

While monerod and monero-wallet-cli do not use readline directly, most of the functionality can be obtained by running them via rlwrap. This allows command recall, edit capabilities, etc. It does not give autocompletion without an extra completion file, however. To use rlwrap, simply prepend `rlwrap` to the command line, eg:

`rlwrap bin/monero-wallet-cli --wallet-file /path/to/wallet`

Note: rlwrap will save things like your seed and private keys, if you supply them on prompt. You may want to not use rlwrap when you use simplewallet to restore from seed, etc.

