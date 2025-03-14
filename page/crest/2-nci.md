---
layout: default
title: NCI
parent: "CREST"
nav_order: 4
has_children: false
permalink: page/crest/nci
---

# NCI Mode

For systems with non-covalently interacting molecules, **CREST** provides a special runtype invoked with the **--nci** flag:

```bash
crest struc.xyz --nci
```

This will apply a wall potential to prevent dissociation of the molecules upon the MTD and MD simulations.

{% include warning.html content='Especially for systems containing non-bonded molecules, the conformer generation is complicated and the results of a single **crest** run is likely not sufficient to find the best conformer'%}

For systems containing multiple molecules, it is highly recommended to do multiple **crest** runs on the same system and to combine the results. Sorting the combined ensemble can also be done with **crest** as explained in the [additional features chapter](page/crest/addition). Further, it can be beneficial to try different settings, *e.g.*, to adjust the temperature of the MD runs (`--tnmd <INT>) or increase the number of searching cycles (`--mrest <INT>). Further possibilities to tune the sampling behaviour are listed in the [documentation](https://crest-lab.github.io/crest-docs/page/documentation/keywords.html#conformational-search-settings).
