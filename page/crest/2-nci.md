---
layout: default
title: NCI
parent: "crest"
nav_order: 4
has_children: false
permalink: page/crest/nci
---

For systems with non-covalently interacting molecules, **CREST** provides a special runtype invoked with the **--nci** flag:

```bash
crest struc.xyz --nci
```

This will apply a wall potential to prevent dissociation of the molecules upon the MTD and MD simulations.
