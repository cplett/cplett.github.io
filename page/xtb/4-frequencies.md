---
layout: default
title: Frequencies
parent: "xtb"
nav_order: 6
has_children: false
permalink: page/xtb/Frequencies
---

# Frequency calculations

With **xtb**, also hessian calculations can be done which is required for thermocorrections to free energies and to compute IR and Raman spectra. To perform a Hessian computation, the `--hess` flag can be used

```bash
xtb struc.xyz --hess
```


Alternatively, the `--ohess` flag directly performs an optimization with subsequent Hessian computation.

{% include warning.html content='Computing Hessians on not fully optimized structures or transition states will have no physical meaning and should generally not be used to compute thermocontributions or spectra.'%}

At the end of the calculation, the printout will contain the frequencies, total free energy and total thermocorrection (`G(RRHO) contrib.`).
Further, a `vibspectrum` file will be written containing the IR active modes with the respective intensities.
Additionally, a gaussian output `g98.out` will be written, which can be opened with, *e.g.*, molden to directly look at the vibrational levels computed.
These can be used to identify transition states or to confirm that the geometry converged into a minimum.

Check, if the provided structure is a minimum, a reasonable transtition state or an arbitrary point on the PES. Use GFN2-xTB with ALPB(THF). How does the spectrum look change when using GFN-FF with ALPB(THF) instead?

<!-- Tab links -->
<div class="tab card">
  <button
    class="tablinks tab-id-1"
    onclick="openTabId(event, 'struc-1', 'tab-id-1')"
    id="open-1">
    {{ site.data.icons.codefile }} <code>struc.xyz</code>
  </button>
</div>
<!-- Tab content -->
<div id="struc-1" class="tabcontent tab-id-1" style="text-align:justify">
{% capture struc_file_1 %}
60

Ir 0.22444 0.14527 -0.19941
B 1.33274 -1.02240 1.19281
O 2.10728 -0.52368 2.23124
O 1.29878 -2.41761 1.23252
C 2.75593 -1.61003 2.89859
C 2.04814 -2.87405 2.36426
B 1.80738 -0.67323 -1.25750
O 1.60340 -1.37252 -2.45859
O 3.15353 -0.70050 -0.91729
C 2.83363 -1.99118 -2.85163
C 3.89810 -1.30030 -1.97774
B 1.44948 1.70801 0.27916
O 2.50688 2.19680 -0.48225
O 1.26386 2.52815 1.40609
C 3.16792 3.23950 0.23108
C 2.18823 3.61911 1.36048
C -2.30905 -0.65090 1.42723
C -2.25834 -1.68944 0.37026
N -1.30803 0.26358 1.43328
N -1.23625 -1.60021 -0.50919
C -3.32614 -0.60417 2.38997
C -3.30852 0.38423 3.36785
C -2.26730 1.30909 3.36702
C -1.28713 1.21455 2.38323
C -3.20068 -2.72376 0.27943
C -3.08457 -3.67137 -0.73143
C -2.02500 -3.56877 -1.63030
C -1.12272 -2.51872 -1.48063
C -1.14523 1.44405 -1.40055
C -1.32790 2.78803 -1.02925
C -1.99683 0.92863 -2.39248
C -2.34780 3.56470 -1.58615
C -3.01467 1.70232 -2.95766
C -3.19935 3.02499 -2.55218
H 0.37405 0.80500 -1.68399
H -0.44935 1.90106 2.33342
H -2.20575 2.09631 4.11121
H -4.09485 0.42683 4.11592
H -4.12897 -1.33084 2.37621
H -4.01648 -2.79488 0.98859
H -3.80980 -4.47600 -0.81155
H -1.89129 -4.28555 -2.43403
H -0.27298 -2.38745 -2.14226
H 1.35904 -3.30922 3.10064
H 2.74940 -3.65517 2.05006
H 2.65464 -1.48884 3.98290
H 3.82436 -1.59665 2.64805
H 1.64159 4.54652 1.14131
H 2.67739 3.72788 2.33451
H 3.38162 4.07382 -0.44625
H 4.12089 2.86119 0.62441
H 4.43772 -0.51679 -2.52565
H 4.63150 -2.00027 -1.56306
H 2.99198 -1.84055 -3.92463
H 2.77505 -3.07061 -2.65637
H -0.67931 3.23230 -0.27913
H -2.47374 4.59719 -1.26591
H -3.98804 3.63103 -2.99159
H -3.65923 1.27131 -3.72132
H -1.86324 -0.09332 -2.73789
{% endcapture %}
{% include codecell.html content=struc_file_1 style="font-size:10px" %}
</div>

Another functionality of **xtb** is the Single-Point Hessian (SPH) approach. This allows to compute reasonable Hessians on arbitrary structures.
It can be used to, *e.g.*, compute the thermocorrections of a DFT optimized structure to save the computational time of a rather expensive DFT Hessian.
To activate it, the `--bhess` flag is used as explained in the [documentation](https://xtb-docs.readthedocs.io/en/latest/hessian.html#single-point-hessian-sph-calculations). Further information on the theoretical concept can be found in the [publication](https://pubs.acs.org/doi/10.1021/acs.jctc.0c01306).
