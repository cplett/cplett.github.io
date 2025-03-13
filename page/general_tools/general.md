---
layout: default
title: General
parent: "general tools"
nav_order: 1
has_children: false
permalink: /page/general
---

# General tools of the Grimme Lab

## PubGrep

PubGrep is a command line tool that can automatically get random conformer structure data (.sdf files) from the PubChem database, if it is available. This tool is very useful to quickly get a 3D structure of a compound. It comes either as a bash script or a Python implementation, both found on [GitHub](https://github.com/grimme-lab/PubGrep). The bashscipt can directly be used after making it executable, *e.g.*

```bash
chmod u+x PubGrep
```

The Python implementation can be installed with pip into the current environment:

```bash
pip install -e .
```

A complete list of functions is shown by executing

```bash
PubGrep --help
```

The usage is fairly simple. You can get a 3D structure by using, for example, the compound name or the PubGrep ID:

```bash
PubGrep <Name>
PubGrep <ID> --input cid
``` 

The result is per default an *.sdf* file named after the CID. If there is no 3D structure on PubChem, a 2D to 3D converter is used to generate a random conformer which must not be the energetically favored one.


## Structure converter

The MCTC library provides access to many commonly required routines like structure handling. Further, it provides a stand-alone for structure converstion, namely the `mctc-convert`.
The library is available on [github](https://github.com/grimme-lab/mctc-lib) and can be compiled with meson, cmake, or fpm with standard fortran compiler.
A precompiled `mctc-convert` binary is also available at [github](https://github.com/grimme-lab/mctc-lib/releases/tag/v0.3.1). After extracting the `mctc-convert-0.3.1.tar.xz` archive, you can find the binary in the *bin* directory. It can be copied to a place of your liking, *e.g.*, your bin.
The mctc-convert only requires an input coordinate file and a name for the output file:

```bash
mctc-convert <input> <output>
```

Determining the file format of the input and desired output file is done automatically according to the respective file extension. For example, *.xyz* is recognized as Xmol file, while *.coord* defines the Turbomole format. Supported formats are:

| Format                                   | Suffix                           |
|------------------------------------------|----------------------------------|
| Xmol/xyz files                          | xyz, log                        |
| Turbomole’s coord, riper’s periodic coord | tmol, coord                     |
| DFTB+ genFormat geometry inputs          | gen                              |
| VASP’s POSCAR/CONTCAR input files        | vasp, poscar, contcar           |
| Protein Database files (single files)    | pdb                              |
| Connection table files (molfile, SDF)    | mol, sdf                         |
| Gaussian’s external program input        | ein                              |
| JSON input with qcschema structure       | json                             |
| Chemical JSON input                      | cjson                            |
| FHI-AIMS' input files                    | geometry.in                      |
| Q-Chem molecule block inputs             | qchem                            |


Further information are shown by using the *--help* command (`mctc-convert --help`)


## RMSD tools

The MCTC rmsd tool is a efficient tool for calculating the Root mean square deviation (RMSD) of two structures. This is useful qunatifying structural differences, *e.g.*, to identify similar structures. It is available on [github](https://github.com/grimme-lab/rmsd-tool) including [precompiled binaries] (https://github.com/grimme-lab/rmsd-tool/releases). After extracting the `mctc-rmsd-0.1.1.tar.xz` archive, the `mctc-binary` can be found in the *bin* directory. It is called with

```bash
mctc-rmsd struc1.xyz struc2.xyz
```

Additional filters can be applied, *e.g.*, excluding hydrogen atoms by using the *--filter heavy*. Further information can be found with the *--help* flag (`mctc-rmsd --help`).
