---
layout: default
title: NMR
parent: "CENSO"
nav_order: 3
has_children: false
permalink: page/censo/nmr
---

# {{ page.title }}

**CENSO** is not only capable of ensemble refinement, but also allows the automated computation of NMR spectra for an entire ensemble. Since NMR is a structure-sensitive property, this is a prime example of the importance of ensemble quality.

As an example, use **CENSO** to refine the ensemble you computed for histidine in the [respective CREST ensemble](page/crest/ensemble).

{% include image.html file="l-histidine.png" alt="hist" max-width=400 %}

{% include important.html content='This task requires some time to compute, approximately 2.5 hours on 4 cores (Intel(R) Xeon(R) CPU E3-1270 v5 @ 3.60GHz, not the fastest). Most of the time will be spent on geometry optimizations, so if you expect this to take too long, consider skipping the geometry optimization step in CENSO (set run = False in the **optimization** section in censo2rc histidine)' %}

## Ensemble Refinement and Spectral Parameter Calculation

{% include important.html content='For the next steps, the ORCA software is required.' %}

Next, you will refine the ensemble using DFT calculations.  
**CREST** uses GFN2-xTB as the default method, which produces ensemble rankings that are not accurate enough for NMR calculations. Therefore, it is necessary to refine the initial ensemble.  
You can do this using **CENSO**, which automates the process of ensemble refinement and property calculation.

**Before starting your calculations, please configure the program paths in the provided configuration file.**  
You can define the number of cores for **CENSO** with **--maxcores**.

 <!-- Tab links -->
<div class="tab card">
  <button class="tablinks tab-id-2" onclick="openTabId(event, 'tab-2-1', 'tab-id-2')" id="open-2">{{ site.data.icons.code }} <code>command</code></button>
  <button class="tablinks tab-id-2" onclick="openTabId(event, 'tab-2-2', 'tab-id-2')">{{ site.data.icons.codefile }} <code>conso2rc_histidine</code></button>
</div>
<!-- Tab content -->
<div id="tab-2-1" class="tabcontent tab-id-2" style="text-align:justify">
{% include command.html cmd="censo  <span class='nt'>-i</span> crest_conformers.xyz <span class='nt'>--inprc</span> censo2rc_histidine > censo.out &" %}
    </div>
<div id="tab-2-2" class="tabcontent tab-id-2" style="text-align:justify">
{% capture struc_file %}
[prescreening]
threshold = 4.0
func = pbe-d4
basis = def2-SV(P)
prog = tm
gfnv = gfn2
run = False
template = False

[screening]
threshold = 3.5
func = r2scan-3c
basis = def2-TZVP
prog = orca
sm = smd
gfnv = gfn2
run = True
implicit = True
template = False

[optimization]
optcycles = 8
maxcyc = 200
threshold = 2.0
hlow = 0.01
gradthr = 0.01
func = r2scan-3c
basis = def2-TZVP
prog = orca
sm = smd
gfnv = gfn2
optlevel = loose
run = False
macrocycles = True
crestcheck = False
template = False
constrain = False
xtb_opt = True

[refinement]
threshold = 0.95
func = wb97x-v
basis = def2-TZVP
prog = tm
sm = cosmors
gfnv = gfn2
run = False
implicit = False
template = False

[nmr]
resonance_frequency = 600.0
ss_cutoff = 8.0
prog = orca
func_j = r2scan-d4
basis_j = def2-TZVP
sm_j = smd
func_s = r2scan-d4
basis_s = def2-TZVP
sm_s = smd
gfnv = gfn2
run = True
template = False
couplings = True
fc_only = True
shieldings = True
h_active = True
c_active = False
f_active = False
si_active = False
p_active = False

[uvvis]
prog = orca
func = wb97x-d4
basis = def2-TZVP
sm = smd
gfnv = gfn2
nroots = 20
run = False
template = False

[general]
imagthr = -100.0
sthr = 0.0
scale = 1.0
temperature = 298.15
solvent = h2o
sm_rrho = alpb
multitemp = True
evaluate_rrho = True
consider_sym = True
bhess = True
rmsdbias = False
balance = True
gas-phase = False
copy_mo = True
retry_failed = True
trange = [273.15, 373.15, 5]

[paths]
orcapath = /path/to/orca/binary
xtbpath = /path/to/xtb/binary
mpshiftpath = 
escfpath = 
orcaversion = 
{% endcapture %}
{% include codecell.html content=struc_file style="font-size:10px" %}
</div>

{% include defaulttab.html id="open-2" %}

CENSO will write output for all parts in text format, as well as in JSON format (`.out` and `.json` files). You will also find ensembles in XYZ format, along with all files generated during the run, organized by section in your working directory.  
\\  
In the program's printout and in the `4_NMR.out` file, you will find the ensemble-averaged NMR parameters. Sodium trimethylsilylpropanesulfonate (DSS) is used as the NMR standard, and the spectrum is recorded at a frequency of 600 MHz in aqueous solution.  
Compare the ensemble-averaged values and the values for the lowest conformer only to the provided experimental reference values below.

| δ (ppm) | Integral | Multiplet type | J (Hz) | Atom No. |
| :---:   | :---:    | :---:          | :---:  | :---:    |
| 3.16    | 1        | dd             | 15.55, 7.7 | 6    |
| 3.23    | 1        | dd             | 16.10, 4.9 | 6    |
| 3.98    | 1        | dd             | 7.73, 4.98 | 7    |
| 7.09    | 1        | d              | 0.58       | 5    |
| 7.9     | 1        | d              | 1.13       | 2    |

{% include image.html file="l-histidine-atoms.png" alt="histidine" max-width=300 %}
