# InspIRCd Wiki &raquo; System Requirements

To compile and run InspIRCd, the following software and hardware is required:  

## Hardware

* 750MHz CPU
* 300MB RAM
* 50MB free disk space (more may be needed if building in debug mode)

It is possible to get InspIRCd running on lower spec systems than listed here, however this is
unsupported. If you are running on an ancient system, we will not be able to assist you if you have
problems.

## Required Software

* A modern UNIX-like or Windows operating system.
* [GCC](http://gcc.gnu.org/) 3.0 or [Clang](http://clang.llvm.org/) 3.0
* [Perl](http://www.perl.com/) 5.8 or above for `./configure` and `./inspircd` scripts.

## Optional Software

Modules in the `src/modules/extra/` directory require extra software to be properly compiled and
run. The software can be found in the following subsections. 

## SSL

InspIRCd offers two types of SSL implementations: GnuTLS (recommended) and OpenSSL.

To compile either of these modules for InspIRCd, you must have the binaries and development package
for your selected type of SSL.

**NOTE** If you are using FreeBSD and you would like to use OpenSSL, you MUST install OpenSSL from
the ports tree as the OpenSSL that comes built-in to the system does not use `pkg-config` which is
required for InspIRCd.

Debian/Ubuntu users, install the following packages:

### GnuTLS

* libgnutls-dev
* gnutls-bin
* pkg-config 

### OpenSSL

* libssl1.0.0
* libssl-dev
* pkg-config 

Fedora/CentOS/etc users, install the following package:

### GnuTLS

- gnutls
- gnutls-devel
- gnutls-utils
- pkgconfig 

### OpenSSL

- openssl
- openssl-devel
- pkgconfig

## Regex

InspIRCd offers various types of Regex engines to be used. Each engine has dependencies on certain
software.

The GLOB regex engine is available on all platforms and has no dependencies.

The POSIX regex engine is not available to Windows platforms, and has no other dependencies.

The PCRE engine requires the source libraries to build against. Debian/Ubuntu users can install
libpcre3-dev and it's dependencies with Apt. Fedora/CentOS/etc users can install pcre and pcre-devel
packages with Yum.

The TRE engine requires the source libraries to build against. Debian/Ubuntu users can install
libtre4 and libtre4-dev with Apt. Fedora/CentOS/etc users can install tre and tre-devel with Yum.
