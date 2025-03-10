---
layout: default
title: periodic calculations
parent: "xtb"
nav_order: 12
has_children: false
permalink: page/xtb/periodic
---

With **xtb** version 6.7.0, the GFN-FF method supports periodic calculations via periodic boundary conditions. 
Additionally, a special run mode (mcGFN-FF) with scaled non-covalent interactions (NCI), was introduced and is recommended for periodic systems.
It can be used for a fast optimization of periodic systems, optionally without optimizating the cell parameters (**--nocellopt**.
A periodic GFN-FF calculation is invoked similarly to a normal GFN-FF calculation, except for the structure file that contains information on the lattice and is in Turbomole format. 
As an example, optimize...
