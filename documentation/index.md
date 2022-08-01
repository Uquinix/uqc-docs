---
layout: page
title: Seva Documentation
---

<div class="warning" markdown="1">
The Seva Kernel is currently under heavy development, meaning this page will be heavily modified as time goes on. [Visit the Seva Repository](https://github.com/Uquinix/Seva).
</div>

### About
The kernel is the core of the Enso operating system. It is responsible for managing memory, enforcing security controls, networking, disk access, and much more.

<strong>All of the commands listed in the examples in this chapter should be executed as root.</strong>

### Perparing to Build
The output of the build goes to /usr/obj/source path/machine architecture - e.g. /usr/obj/Users/you/seva/amd64.amd64. 

If you don't want to build as root, you need to create the path ahead of time or give yourself ownership of /usr/obj with chown.

### Building the Kernel
Kernel source lives mainly in sys/ and can be built by doing 

~~~ shell
make -jX buildkernel
~~~

Where X is the number of CPUs you can devote to the build. 

Append ``WITHOUT_CLEAN=1`` to the buildkernel command if you want to do incremental builds. 

You can install your kernel and modules with:

~~~ shell
make installkernel
~~~

### Building the "World"
The 'world' is the FreeBSD user parts including C library, compiler toolchain, commands, etc. You can build this by running:

~~~ shell
make -jX buildworld MK_LIB32=no
~~~

Append WITHOUT_CLEAN=1 to the buildworld command to do incremental builds, which are much faster. 

Install it over your running system with make installworld MK_LIB32=no

### Packaging the Kernel & World
After building kernel and world, you can run 

~~~ shell
make -C release packagesystem MK_LIB32=no COMPILER_TYPE=clang
~~~

To create base.txz and kernel.txz, which are needed to build the ISO. These will end up in /usr/obj/source path/[machine architecture here]/release/.