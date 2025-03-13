---
layout: default
title: Installation
parent: "xtb"
nav_order: 1
has_children: false
permalink: /page/xtb/installation
---

# Installation

## General Considerations

The xtb software is open-source and available under the LGPL 3.0 license on the GitHub platform. This guide provides a brief summary of the existing [guideline](https://xtb-docs.readthedocs.io/en/latest/setup.html). Some features are available only for the newer version of xtb (`6.7.0`).
In case of any issues, you can always refer to the full documentation for further details or open an issue on GitHub.

{% include warning.html content="Primary operating system (OS) for the development and application of **xtb** is Linux. While it is possible to install **xtb** on Windows and macOS, support for these platforms may be more limited." %}


## Straighforward Installation
The most straightforward way to install xtb is by downloading the [precompiled binaries](https://github.com/grimme-lab/xtb/releases). You can also get a bleeding-edge version of the program.
After downloading the appropriate version, extract it, make it executable, and add it to your `PATH` variable for easy use:

```bash
tar -xvf xtb*.tar.xz
chmod +x ./xtb-dist/bin/xtb
export PATH=$PWD/xtb-dist/bin:$PATH
```

Alternatively, you can copy the **xtb** binary to a directory of your liking, **e.g.**, your bin.
To verify that the executable is correctly linked, use:

```bash
which xtb
```
And check the installed version with:
```bash
xtb --version
```

{% include tip.html content='You can add the full path to your **xtb** executable to the Bash shell configuration file (~/.bashrc) to automatically load **xtb** in new sessions.'%}


## Compilation 
A more advanced approach is to compile xtb from the source code. Native compilation has certain advantages over precompiled binaries, such as producing a system-tailored binary and allowing modifications to the software in place.

Here, we follow a minimalistic build using our default toolchain: the `meson` build system and the `ifort`/`icc` compilers.

First step is to clone the official GitHub repository via:
```bash
git clone https://github.com/grimme-lab/xtb.git
```

Then, define the Fortran and C compilers, which can be installed via Intel's [Developer Toolkit](https://www.intel.com/content/www/us/en/developer/tools/oneapi/toolkits.html#base-kit):
```bash
export FC=ifort CC=icc
```

Finally, you can build the project with [Meson](https://mesonbuild.com/):
```bash
meson setup build --buildtype=release
meson compile -C build
```

Alternatively, `gfortran`/`gcc` compilers are also supported. For a complete list of supported compilers and backends, please see the [github page](https://github.com/grimme-lab/xtb?tab=readme-ov-file#semiempirical-extended-tight-binding-program-package).


## Important settings
To work properly also for large systems, it is recommended to unlimit the system stack size, **e.g.**, with bash by:

```bash
ulimit -s unlimited
```

This can also be included in the **.bashrc** file.

Further, to allow parallelisation, a reasonable large number of OMP stacksize must be provided, **e.g.**:

```bash
export OMP_STACKSIZE=4G
```

and the number of cores to be used by **xtb** are set with

```bash
export OMP_NUM_THREADS=<ncores>,1
```
