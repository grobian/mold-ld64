# mold-ld64 linker for macOS

_mold-ld64_ is a re-named fork of
[sold](https://github.com/bluewhalesystems/sold), which is in turn an
outdated fork of [mold](https://github.com/rui314/mold).  After it was
relicenced under MIT licence, _sold_ didn't receive much updates and was
basically
[abandoned](https://github.com/bluewhalesystems/sold/issues/43).

In macOS linker land not much choice is available.  Admittedly, Apple
ships a functional linker with Xcode Tools, but updating the linker on
older macOS versions, e.g. by building _lld_ requires a fair amount of
LLVM foo.  Apple's _cctools_ and _ld64_ projects are abandoned, projects
like [xtools](https://github.com/iains/darwin-xtools) are functional,
but basically old linkers, not really suitable (e.g. no support for M1).
Because there is a need for (non-LLVM) macOS linkers, _mold-ld64_ is
there to use with GCC and allow using a self-built up-to-date linker.

## How to build

```
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_CXX_COMPILER=c++ -B build
cmake --build build -j <cpus>
```

## How to use

You need to configure your compiler to use _mold-ld64_.  This likely
happens via PATH, but can also happen whilst configuring the compiler.
This is up to you.

Within Gentoo Prefix it is used behind a
[wrapper](https://gitweb.gentoo.org/repo/proj/prefix.git/tree/sys-devel/binutils-config/files/ldwrapper.c).
