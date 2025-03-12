---
layout: default
title: General
parent: "xtb"
nav_order: 2
has_children: false
permalink: /page/xtb/overview
---

## Getting Help
To get help and an overview over different flags usable with **xtb**, you can either use the [documentation](https://xtb-docs.readthedocs.io/en/latest/index.html) or call the help function of xtb:

```bash
xtb --help
```

## Input File

**xtb** supports various input file formats:

| Format                  | Basename           | Suffix               | Molecular | Periodic |
|-------------------------|--------------------|----------------------|-----------|----------|
| Turbomole              | coord              | coord, tmol         | x         | 3D       |
| xyz file              |                    | xyz                  | x         |          |
| mol file              |                    | mol                  | x         |          |
| Structure-Data file    |                    | sdf                  | x         |          |
| Protein Database file  |                    | pdb                  | x         |          |
| Vasp’s POSCAR/CONTCAR  | poscar, contcar    | vasp, poscar, contcar |          | 3D       |
| genFormat             |                    | gen                  | x         | 3D       |
| Gaussian external     |                    | ein                  | x         |          |

For periodic calculations, only the Turbomole, Vasp’s POSCAR/CONTCAR, and the genFormat format can be used.
Further information on the file formats can be found in the [documentation](https://xtb-docs.readthedocs.io/en/latest/geometry.html).

## Calling xtb
The most simple call to start a **xtb** calculation requires only a structure file in one of the above mentioned formats,**e.g.**:

```bash
xtb struc.xyz
```

To invoke different kinds of calculations and to call different functionalities, generelly flags are provided when calling the **xtb** program. They will be introduced in the following excercises. Most of these flags can also be combined, **e.g.**, to perform a geometry optimization with an implicit solvent model.

## Additional inputs
**xtb** comes with robust defaults, but sometimes detailed settings have to adjusted. Therefore, an additional input file can be provided with:

```bash
xtb struc.xyz --input <xtb.inp>
```

These input files can contain multiple blocks, always starting with a keyword like `$constrain`, followed by different settings and the `$end` line. For example, constraining all carbon atoms for a **xtb** calculation can be done with the following input file:

```bash
$constrain
   elements: C
$end
```

More about constraining and fixing atoms is explained in the [geometry optimization excercise](#page/xtb/GeoOpt). It is also possible to combine multiple blocks in one file.


## Charges and number of unpaired electrons
**xtb** can also handle charged molecules as well as molecules with unpaired electrons. Charges and the number of unpaired electrons can either be set via the command line (**--chrg <INT>** and **--uhf <INT>**) flag or with a **.CHRG** and **.UHF** file in the working directory that contain just the respective number.
