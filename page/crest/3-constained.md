---
layout: default
title: constraints
parent: "crest"
nav_order: 5
has_children: false
permalink: page/crest/constraints
---

For electronically more complex systems, and in case you want to preserve certain structure motifs, **CREST** provides the possibility to contrain certain bonds, dihedral, and torsion angles. For this, a file with similar format to the **xtb** input can be provided with the **--cinp** flag:

```bash
crest struc.xyz --cinp <FILE>
```

All possible contraints are listed in the [documentation](https://xtb-docs.readthedocs.io/en/latest/xcontrol.html#fixing-constraining-and-confining).

{% include note.html content='The exact fixing of atoms is currently not possible due to instabilities during the MD and MTD simulations.'%}

To easify the manual definition of constraints, **CREST** provides the possibility to automatically generate the required input file. For this, the **--constrain <atomlist>** keyword can be used, where **<atomlist>** defines the index of the atoms to be contrained, **e.g.**:

```bash
crest struc.xyz --contrain 1-5,8,12
```

This results in a **.xcontrol.sample** file that can be renamed and used as input for the **CREST** run.
Further, **CREST** provides the possibility to contrain certain interaction motifs automatically. For example, **--cmetal** contrains the bonds of a metal with all ligands to prevent unwanted behaviour during the MD and MTD simulations. Further, information can be found in the [documentation](https://crest-lab.github.io/crest-docs/page/examples/example_4.html).
