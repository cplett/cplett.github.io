---
layout: default
title: Additional Features
parent: "CREST"
nav_order: 7
has_children: false
permalink: page/crest/addition
---

# Additional Feature

## Ensemble Sorting Tool

**crest** provides the feature to sort a given ensemble or trajectory according to the energies and to sort out duplicates. The energies taken are given in the comment line of each structure (second line right after the number of atoms per structure).
This is very helpfule for combined ensembles resulting from different **crest** runs.
It can be invoked with the `--cregen` keyword.

```bash
crest struc.xyz --cregen <ensemble file>
```

where `struc.xyz` is a random conformer of the structure and `<ensemble file>` the ensemble.
The sorted ensemble is writte on the file `<ensemble file>.sorted.
The standard **crest** sorting flags can be used as well, *e.g.*, `--ewin <REAL>`.
A complete list of keywords can be found at the [documentation](https://crest-lab.github.io/crest-docs/page/documentation/keywords.html#ensemble-sorting-options).

## Clustering
**crest** also allows the clustering of ensembles. This will leave only the most representative conformers of the ensemble.
The sorting is done with an automatic principle component analysis (PCA) and k-Means sorting clusterin algorithm.
It is invoked with the `--cluster` flag and can be combined with the `--cregen` sorting or for ensemble searches, where the clustering is performed after the default search.
The resulting reduced ensemble can be found on `crest_clustered.xyz` along the usual output files.
An optional argument after the flag can be provided to, *e.g.*, only leave a certain number of structures (`--clsuter <INT>`).
Further options can be found on the [documentation](https://crest-lab.github.io/crest-docs/page/documentation/keywords.html#pca-clustering-options).

## Ensemble File splitting

It is possible with **crest** to split an ensemble into individual conformers in different directories with the `--splitfile` flag:

```bash
crest --splitfile <ensemble file>
```
This will yield a directory called `SPLIT` containing directories called `STRUCX` where X is the number of the respective conformer. Each of those directories contain a structure file of the conformer.

## Properties for Ensembles

Computing different properties of an ensemble can also be done with **crest**.
This feature is invoked with the `--forall` flag:

```bash
crest --forall <ensemble file>
```

This can be combined with the `--prop` flag. For example, `--prop singlepoint` will compute the single-point energy of each conformer and list the respective energies as well as the ensemble average.
`--prop hess` invokes additional Hessian and thermocorrections computations, and `--prop autoIR` a vibrational spectrum of the ensemble written to `crest.vibspectrum`.

## Trajectory Optimization

With **crest**, you can also optimize the structures of an ensemble or trajectory file, *e.g.*, resulting from an **xtb** MD simulation. This can be done with different GFN methods and is invoked with:

```bash
crest --mdopt <FILE>
```

where `<FILE>` is the trajectory/ensemble file. The optimized and sorted structures will be written to the `crest_ensemble.xyz` file.
