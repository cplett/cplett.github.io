---
layout: default
title: Installation
nav_order: 3
permalink: /page/installation.html
summary: "This guide contains detailed step-by-step instructions for the installation of xtb software. Make sure to read it carefully."
---

# {{page.title}}
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}
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
meson compile -C build
```

## External Driver Programs
During the workshop, we will use external programs, namely *Conformer–Rotamer Ensemble Sampling Tool* (CREST) and *Command-line Energetic Sorting* (CENSO).
Note that CENSO is only required in the optional 6th exercise.
The simplest way to install CREST is by downloading the [precompiled binaries](https://github.com/crest-lab/crest/releases), similar to xtb. Full installation instructions can be found [here](https://crest-lab.github.io/crest-docs/page/installation/install_basic.html).
The installation instructions for CENSO can be found in the [official project repository](https://github.com/grimme-lab/CENSO).


## Utility Tools
During the course of the workshop, you will also need to visualize molecular structures.
The required graphical user interfaces (GUIs) include [Avogadro](https://avogadro.cc/), [Molden](https://www.theochem.ru.nl/molden/), Chimerax and others.
Additionally, you should have a text editor (e.g., vim, nano, VSCode) to edit input files and adjust calculation parameters as needed.


