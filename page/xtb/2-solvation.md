---
layout: default
title: Solvation
parent: "xtb"
nav_order: 4
has_children: false
permalink: page/xtb/Solvation
---

# Implicit Solvent Models

When modeling processes in solvation it is crucial to include solvent effects in any calculation. This has an important effect on energies, but also on geometries.
In **xtb**, there exist two implicit solvent models, the GBSA and ALPB, that can easily be used in every calculation. They can be invoked by

```bash
xtb struc.xyz --alpb <solvent>
xtb struc.xyz --gbsa <solvent>
```

A list of usable solvents can be found at the [documentation](https://xtb-docs.readthedocs.io/en/latest/gbsa.html).
In principle, the solvent models perform similar, but do not reach the performance of more costly solvent models like COSMO-RS or SMD.
They model an electrostatic continuum that is relaxed self-consistently during the SCC directly affecting its energyi. Non-electrostatic parts are added after the SCC convergence. 
{% include note.html content='This can help to converge SCC or geometry optimization steps and can be used to get a good startinf point if gas-phase calculations fail to converge.'%}
More information can be found in the [publication](https://pubs.acs.org/doi/abs/10.1021/acs.jctc.1c00471).
