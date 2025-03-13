---
layout: default
title: General
parent: "xtb"
nav_order: 2
has_children: false
permalink: /page/xtb/general
---

# Using **xtb**

## Getting Help
To get help and an overview over different flags usable with **xtb**, you can either use the [documentation](https://xtb-docs.readthedocs.io/en/latest/index.html) or call the help function of xtb:

```bash
xtb --help
```

## Input File

**xtb** supports various input file formats for molecular structures:

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
The most simple call to start a **xtb** calculation requires only a structure file in one of the above mentioned formats,*e.g.*

```bash
xtb struc.xyz
```

To perform certain calculations and to call different functionalities, generelly flags are provided when calling the **xtb** program. They will be introduced in the following excercises. Most of these flags can also be combined to, *e.g.*, perform a geometry optimization with an implicit solvent model.

## Charges and number of unpaired electrons
**xtb** can also handle charged molecules as well as molecules with unpaired electrons. Charges and the number of unpaired electrons can either be set via the command line (`--chrg <INT>` and `--uhf <INT>`) flag or with a *.CHRG* and *.UHF* file in the working directory that contain just the respective number.

## Available methods
With **xtb**, the GFN2-xTB, GFN1-xTB, and GFN-FF methods are applicable. While GFN2-xTB is the default, the use of each method can be requested with a respective flag:

```bash
xtb struc.xyz --gfn2
xtb struc.xyz --gfn1
xtb struc.xyz --gfnff
```

## Additional inputs
**xtb** comes with robust defaults, but sometimes detailed settings must be adjusted. Therefore, an additional input file can be provided with:

```bash
xtb struc.xyz --input <xtb.inp>
```

These input files can contain multiple blocks, always starting with a keyword like `$md`, followed by different settings and the `$end` line. For example, setting the time and the temperature of an MD simulation can be done with the following input file:

```bash
$md
   time=10 #ps
   temp=200 #K
$end
```

Some of the detailed settings will be explained during the respective exercises.

## Constraining and Fixing
With the aditional input file, also certain bonds and angles can be constrained. This is very helpful if bonding motifs should remain intact during optimization or MD simulations. Such a constrain could look like this:

```bash
$constrain
   distance: 1, 2, 1.4
   angle: 5, 7, 8, auto
   dihedral: 3, 4, 1, 7, 180
$end
```

Here, the distance of atoms 1 and 2 in the input file is constrained to 1.4 Angsröm, the angle between atom 5,7, and 8 is constrained to the current angle (due to the `auto` keyword), and the dihedral angle between the atoms 1, 3, 4, and 7 is constrained to 180°. It is also possible to constrain atoms relative to each other by using the `atoms:` keyword specifying the index of the atom or all elements of a certain kind with the `elements:` keyword. An example might look like this:

```bash
$constrain
   atoms: 11,12,1-3
   elements: C,N
$end
```

Here, the atoms 1, 2, 3, 11 and 12 are constrained relative to each other, as well as all carbon and nitrogen atoms.
If a constrain is not enough, also exact fixing in Cartesian space can be done with the `$fix` block. This, however, does only work for geometry optimizations, but not for MD simulations. Detailed information can be found in the [documentation](https://xtb-docs.readthedocs.io/en/latest/xcontrol.html).
