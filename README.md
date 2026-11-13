# jxrlib for Haiku

The [Haiku](https://www.haiku-os.org/) package of [jxrlib](https://github.com/4creators/jxrlib) 1.2, which
[XarQ](https://xarq.org) uses to open JPEG XR (HD Photo) images (.jxr, .wdp, .hdp). HaikuPorts doesn't have it, so we build it
and publish it in XarQ's own package repository.

## Install

Add the XarQ repository once, then install it like any other package:

```
pkgman add-repo https://xarq.org/haiku/x86_64/current
pkgman install jxrlib
```

For development, install `jxrlib_devel` too. The packages are built on Haiku R1/beta6
(x86_64) and also work on newer nightlies.

## What's here

`media-libs/jxrlib/` is a HaikuPorts recipe and its patches, in the same layout as the
[haikuports](https://github.com/haikuports/haikuports) tree. The source is the 4creators snapshot (commit 1ef17dd) with Debian's patches, which add the CMake build, shared libraries and libjxr.pc, plus a small Haiku patch: Haiku links programs as shared objects, so the tools are built with -fPIC.

To build it yourself, copy that folder into your haikuports tree and run:

```
haikuporter -S --get-dependencies jxrlib
```

Set `VENDOR="XarQ"` in `haikuports.conf` first if the package is going into the XarQ
repository: Haiku's repository tool only accepts packages whose vendor matches the
repository's.

## Releases

Each release has the built `.hpkg` files. The XarQ repository at
https://xarq.org/haiku picks them up automatically, through the workflow in
[XarQ-design/xarq](https://github.com/XarQ-design/xarq/blob/main/.github/workflows/haiku-repo.yml).

## Licence

jxrlib is under the BSD 2-clause licence; see the upstream project. The recipe is under the MIT
licence, like the HaikuPorts tree, and any patch is under jxrlib's own licence.
