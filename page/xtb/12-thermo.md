---
layout: default
title: thermo submodule
parent: "xtb"
nav_order: 13
has_children: false
permalink: page/xtb/thermo
---

# Thermocorrections

With the **xtb** thermo submodule, thermodynamic functions of a structure can be evaluated based on a previously calculated Hessian. The mRRHO approximation is used.
It can be invoked with 

```bash
xtb thermo [options] struc.xyz hessian
```

With [options], the type of Hessian is defined, **e.g.**, **--orca**, or **--turbomole**. Additional information can be found in the [documentation](https://xtb-docs.readthedocs.io/en/latest/xtb_thermo.html).
