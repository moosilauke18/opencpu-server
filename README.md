OpenCPU Cloud Server
--------------------

This repository contains the sources for the opencpu server (aka cloud server). It consists of the following packages:

 * `opencpu-server` - rApache based opencpu API server
 * `opencpu-cache` - nginx based reverse proxy with caching (debian/ubuntu only)
 * `opencpu` - Alias for `opencpu-server` (as of 1.4.5)

## Server manual

The [server manual](http://jeroenooms.github.com/opencpu-manual/opencpu-server.pdf) is the primary reference for installing and managing the OpenCPU server.

## Prebuilt binaries

Currently, prebuilt binaries are available for recent versions of:

 - [Ubuntu](https://www.opencpu.org/download.html)
 - [Fedora](http://software.opensuse.org/download.html?project=home:jeroenooms:opencpu-1.4&package=opencpu)
 - [SUSE](http://software.opensuse.org/download.html?project=home:jeroenooms:opencpu-1.4&package=opencpu)

## Building from source

OpenCPU can be build on all major Linux distributions. However only on Ubuntu it comes standard with security policies enabled.

 - `deb` package (Debian, Ubuntu): see [debian/readme.md](debian#readme)
 - `rpm` package (Fedora, CentOS, SUSE): see [rpm/readme.md](rpm#readme)

## Issues and questions

Please post problems or suggestions on the [issues page](https://github.com/jeroenooms/opencpu/issues). For questions see the [FAQ and mailing list](https://www.opencpu.org/help.html).