---
layout: default
title: thermo submodule
parent: "xtb"
nav_order: 13
has_children: false
permalink: page/xtb/thermo
---

# Thermodynamic Corrections

With the **xtb** thermo submodule, thermodynamic properties of a structure can be evaluated based on a previously calculated Hessian. The mRRHO approximation is used for these calculations. It can be invoked with:

```bash
xtb thermo [options] struc.xyz <hessian file>
```

With [options], the type of Hessian is defined, **e.g.**, **--orca** or **--turbomole**.
The output will display a `total energy` of 0 Hartree, with the sum of thermocorrections as `total free energy`, and include different components such as `zero point energy`, `G(RRHO) w/o ZPVE`, and `G(RRHO) contrib.`.
This is generally useful, if a evaluation at different temperatures should be done. The temperature can be set with the `--temp <REAL>` flag.
For further details, refer to the [documentation](https://xtb-docs.readthedocs.io/en/latest/xtb_thermo.html).
