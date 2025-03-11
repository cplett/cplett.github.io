---
layout: default
title: Installation
parent: "crest"
nav_order: 1
has_children: false
permalink: /page/crest/installation
---

## General Considerations

The xtb software is open-source and available under the LGPL 3.0 license on the GitHub platform. This guide provides a brief summary of the existing [guideline](https://xtb-docs.readthedocs.io/en/latest/setup.html). Some features are available only for the newer version of xtb (`=6.7.0`, [start Linux download](https://github.com/grimme-lab/xtb/releases/download/v6.7.0/xtb-6.7.0-linux-x86_64.tar.xz)).
In case of any issues, you can always refer to the full documentation for further details.
Even though xtb is cross-platform, for simplicity and stability reasons, we assume a **Linux** distribution for the rest of the workshop.

{% include warning.html content="Primary operating system (OS) for the development and application of **xtb** is Linux. While it is possible to install **xtb** on Windows and macOS, support for these platforms may be more limited." %}


## Straighforward Installation
The most straightforward way to install xtb is by downloading the [precompiled binaries](https://github.com/grimme-lab/xtb/releases). You can also get bleeding-edge version of the program.
After downloading the appropriate version, extract it, make it executable, and add it to your `PATH` variable:

```bash
tar -xvf xtb*.tar.xz
chmod +x ./xtb-dist/bin/xtb
export PATH=$PWD/xtb-dist/bin:$PATH
```

To verify that the executable is correctly linked, use:

```bash
which xtb
```
And check the installed version with:
```bash
xtb --version
```

{% include tip.html content='You can add the full path to your Bash shell configuration file (~/.bashrc) to automatically load **xtb** in new sessions.'%}


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
