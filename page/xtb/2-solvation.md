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

Parameterized solvent and method combinations are:

| Solvent         | GFN1(ALPB) | GFN1(GBSA) | GFN2(ALPB) | GFN2(GBSA) | GFN-FF |
|----------------|-----------|-----------|-----------|-----------|--------|
| Acetone       | x         | x         | x         | x         | x      |
| Acetonitrile  | x         | x         | x         | x         | x      |
| Aniline       | x         |           | x         |           | x      |
| Benzaldehyde  | x         |           | x         |           | x      |
| Benzene       | x         | x         | x         | x         | x      |
| CH₂Cl₂        | x         | x         | x         | x         | x      |
| CHCl₃        | x         | x         | x         | x         | x      |
| CS₂          | x         | x         | x         | x         | x      |
| Dioxane      | x         |           | x         |           | x      |
| DMF          | x         |           | x         | x         | x      |
| DMSO         | x         | x         | x         | x         | x      |
| Ether        | x         | x         | x         | x         | x      |
| Ethylacetate | x         |           | x         |           | x      |
| Furane       | x         |           | x         |           | x      |
| Hexadecane   | x         |           | x         |           | x      |
| Hexane       | x         |           | x         | x         | x      |
| Methanol     | x         | x         | x         | x         | x      |
| Nitromethane | x         |           | x         |           | x      |
| Octanol      | x         |           | x         |           | x      |
| Octanol (wet)| x         |           | x         |           | x      |
| Phenol       | x         |           | x         |           | x      |
| Toluene      | x         | x         | x         | x         | x      |
| THF          | x         | x         | x         | x         | x      |
| Water (H₂O)  | x         | x         | x         | x         | x      |


An up-to-date list can also be found at the [documentation](https://xtb-docs.readthedocs.io/en/latest/gbsa.html).

In principle, both solvent models perform similar, but do not reach the performance of more costly solvent models like COSMO-RS or SMD.
GBSA and ALPB model an electrostatic continuum that is relaxed self-consistently during the SCC directly affecting the wavefunction. Non-electrostatic parts are added after the SCC convergence. 
More information on the theoretical foundation and quality of ALPB and GBSA can be found in the [publication](https://pubs.acs.org/doi/abs/10.1021/acs.jctc.1c00471).

{% include note.html content='Using a solvent model can help to converge SCC or geometry optimization steps in case no convergence is achieved in gas phase. The resulting wavefunction or structure can be used to get a good starting point for the gas-phase calculation.'%}
