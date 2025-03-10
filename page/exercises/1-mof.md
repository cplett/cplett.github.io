---
layout: default
title: MOM
full_title: Metal 
parent: "Exercises"
nav_order: 1
has_children: false
permalink: page/exercises/mof
---
# Metal-Organic Materials

To demonstrate possible applications of **xtb**, we want to start with metal-organic frameworks (MOFs, 3D) and cages (MOCs, 0D). Due to their diverse elemental composition, consisting of organic linkers and complexed metal atoms, and their usually large size of hundreds of atoms, they can be challenging to treat computationally. The broad parameterization of all elements up to at least Z=86 combined with the computational costs that are much cheaper than usual DFT or WFT methods make the GFN methods a valuable tool for treating such systems.
In the following, we present an excerpt from a workflow-like compilation of experiments with the HUMJIL MOC (CCDC nomenclature).

## Geometry Optimization
Perform a geometry optimization for `humjil.xyz` in the gas phase and with THF as a solvent (via an implicit solvation model, ALPB - Analytically Linearized Poisson Boltzmann Model) at the *GFN2-xTB* and *GFN-FF* levels of theory.
Compare the 4 geometries by visually overlaying within e.g. [Chimera](https://www.cgl.ucsf.edu/chimera/) or with a (commandline) RMSD tool.


<div class="tab card">
  <button class="tablinks tab-1-1" onclick="openTabId(event, 'command', 'tab-1-1')" id="defaultOpen">{{ site.data.icons.code }} <code>commands</code></button>
  <button class="tablinks tab-1-1" onclick="openTabId(event, 'struc', 'tab-1-1')">{{ site.data.icons.codefile }}  <code>humjil.xyz</code></button>
</div>
<!-- Tab content -->
<div id="command" class="tabcontent tab-1-1" style="text-align:justify">
{% include command.html cmd="xtb humjil.xyz <span class='nt'>--opt --gfn 2 --alpb thf</span> > opt.out &" %}
{% include command.html cmd="xtb humjil.xyz <span class='nt'>--opt --gff --alpb thf</span> > opt.out &" %}
{% include command.html cmd="xtb humjil.xyz <span class='nt'>--opt --gfn 2</span> > opt.out &" %}
{% include command.html cmd="xtb humjil.xyz <span class='nt'>--opt --gff</span> > opt.out &" %}
</div>

<div id="struc" class="tabcontent tab-1-1" style="font-size:10px">
{% capture struc_xyz %}
270
Energy =
Pd    0.0000000   -0.0000000   -9.3798511 
N    -1.3354224   -0.5674368   -7.8625033 
C    -1.2764300   -1.7910299   -7.3066982 
H    -0.5696081   -2.4832666   -7.7376007 
C    -2.0841670   -2.1621617   -6.2461927 
H    -2.0012811   -3.1569726   -5.8406101 
C    -2.9976205   -1.2508124   -5.7156836 
C    -3.8300020   -1.5896796   -4.5281567 
N    -4.6170320   -0.6330408   -4.0213480 
C    -5.3146620   -0.9673456   -2.9289736 
C    -6.1665561    0.0786934   -2.2984962 
C    -6.9112742   -0.1849734   -1.1484659 
H    -6.9315650   -1.1735558   -0.7202096 
C    -7.6384137    0.8293590   -0.5503892 
H    -8.2294635    0.6447898    0.3335154 
N    -7.6601257    2.0830703   -1.0381398 
C    -6.9783362    2.3389052   -2.1692700 
H    -7.0502987    3.3423151   -2.5598749 
Pd   -8.6656352    3.6201240   -0.0228356 
N    -9.7389978    5.0783740    0.8896466 
C    -9.2788257    5.9114056    1.8347371 
H    -8.2515049    5.7930855    2.1323057 
C   -10.0783495    6.8816614    2.4080625 
H    -9.6689237    7.5312355    3.1660863 
C   -11.3963152    6.9997045    1.9943720 
H   -12.0468695    7.7480618    2.4227445 
C   -11.8711153    6.1394692    1.0181582 
H   -12.8941718    6.2213890    0.6882777 
C   -11.0328811    5.1784913    0.4698386 
C   -11.4264608    4.2281294   -0.5549908 
C   -12.6924008    4.1571177   -1.1199336 
H   -13.4678358    4.8366298   -0.8047396 
C   -12.9662894    3.2109716   -2.0935812 
H   -13.9506150    3.1541725   -2.5348556 
C   -11.9586056    2.3442347   -2.4876506 
C   -10.7129958    2.4501151   -1.8989897 
H    -9.9088703    1.7935085   -2.1823282 
H   -12.1299920    1.5926167   -3.2425626 
N    -6.8738894    3.9822651    1.0085774 
C    -6.5994280    3.3459561    2.1617906 
H    -7.3776777    2.7143489    2.5616291 
C    -5.3909927    3.4946365    2.8195921 
H    -5.2232193    2.9663498    3.7436702 
C    -4.4073466    4.3280932    2.2862148 
C    -3.0685241    4.4559181    2.9255083 
N    -2.1733114    5.2675612    2.3497260 
C    -0.9711032    5.3213206    2.9355092 
C     0.0749749    6.1730150    2.3050245 
C    -0.1895719    6.9198634    1.1566198 
H    -1.1788191    6.9424831    0.7300211 
C     0.8250569    7.6458117    0.5577917 
H     0.6405173    8.2380863   -0.3252551 
N     2.0796000    7.6645599    1.0435061 
C     2.3362599    6.9812641    2.1735583 
H     3.3404300    7.0510823    2.5625613 
Pd    3.6152242    8.6664942    0.0241441 
N     3.3615457   10.4523390    0.9512402 
C     4.2226793   11.4295410    0.5458256 
C     4.1510129   12.6979107    1.1053085 
C     3.2047536   12.9754995    2.0779332 
C     2.3384396   11.9690555    2.4763261 
H     1.5866689   12.1432771    3.2303716 
H     3.1476985   13.9615659    2.5152620 
H     4.8300800   13.4724937    0.7869000 
C     5.1730734   11.0319911   -0.4777617 
C     6.1341972   11.8678789   -1.0294255 
H     6.2168904   12.8919583   -0.7030208 
C     6.9940783   11.3894738   -2.0042581 
C     6.8754788   10.0701263   -2.4133624 
H     7.5245408    9.6578250   -3.1702471 
C     5.9051647    9.2729696   -1.8368538 
H     5.7866105    8.2446265   -2.1307425 
H     7.7427438   12.0382143   -2.4349336 
C     2.4447857   10.7209432    1.8928576 
H     1.7882839    9.9179410    2.1796554 
N     3.9757621    6.8713412   -1.0029936 
C     4.8140842    5.9464257   -0.5013019 
H     5.3438074    6.2132013    0.4002682 
C     5.0081670    4.7172035   -1.1064086 
H     5.6942850    4.0128578   -0.6658077 
C     4.3202863    4.4033585   -2.2789230 
C     4.4484021    3.0644926   -2.9183365 
N     5.2601788    2.1693359   -2.3426616 
C     5.3146620    0.9673456   -2.9289736 
C     6.1665561   -0.0786934   -2.2984962 
C     6.2308167   -1.3720128   -2.8177975 
C     6.9783362   -2.3389052   -2.1692700 
H     7.0502987   -3.3423151   -2.5598749 
N     7.6601257   -2.0830703   -1.0381398 
C     7.6384137   -0.8293590   -0.5503892 
H     8.2294635   -0.6447898    0.3335154 
Pd    8.6656352   -3.6201240   -0.0228356 
N     9.7389978   -5.0783740    0.8896466 
C     9.2788257   -5.9114056    1.8347371 
H     8.2515049   -5.7930855    2.1323057 
C    10.0783495   -6.8816614    2.4080625 
H     9.6689237   -7.5312355    3.1660863 
C    11.3963152   -6.9997045    1.9943720 
H    12.0468695   -7.7480618    2.4227445 
C    11.8711153   -6.1394692    1.0181582 
H    12.8941718   -6.2213890    0.6882777 
C    11.0328811   -5.1784913    0.4698386 
C    11.4264608   -4.2281294   -0.5549908 
C    12.6924008   -4.1571177   -1.1199336 
H    13.4678358   -4.8366298   -0.8047396 
C    12.9662894   -3.2109716   -2.0935812 
H    13.9506150   -3.1541725   -2.5348556 
C    11.9586056   -2.3442347   -2.4876506 
C    10.7129958   -2.4501151   -1.8989897 
H     9.9088703   -1.7935085   -2.1823282 
H    12.1299920   -1.5926167   -3.2425626 
N     6.8738894   -3.9822651    1.0085774 
C     6.5994280   -3.3459561    2.1617906 
H     7.3776777   -2.7143489    2.5616291 
C     5.3909927   -3.4946365    2.8195921 
H     5.2232193   -2.9663498    3.7436702 
C     4.4073466   -4.3280932    2.2862148 
C     3.0685241   -4.4559181    2.9255083 
N     2.1733114   -5.2675612    2.3497260 
C     0.9711032   -5.3213206    2.9355092 
C    -0.0749749   -6.1730150    2.3050245 
C     0.1895719   -6.9198634    1.1566198 
C    -0.8250569   -7.6458117    0.5577917 
H    -0.6405173   -8.2380863   -0.3252551 
N    -2.0796000   -7.6645599    1.0435061 
C    -2.3362599   -6.9812641    2.1735583 
H    -3.3404300   -7.0510823    2.5625613 
Pd   -3.6152242   -8.6664942    0.0241441 
N    -3.3615457  -10.4523390    0.9512402 
C    -2.4447857  -10.7209432    1.8928576 
H    -1.7882839   -9.9179410    2.1796554 
C    -2.3384396  -11.9690555    2.4763261 
H    -1.5866689  -12.1432771    3.2303716 
C    -3.2047536  -12.9754995    2.0779332 
H    -3.1476985  -13.9615659    2.5152620 
C    -4.1510129  -12.6979107    1.1053085 
H    -4.8300800  -13.4724937    0.7869000 
C    -4.2226793  -11.4295410    0.5458256 
C    -5.1730734  -11.0319911   -0.4777617 
C    -6.1341972  -11.8678789   -1.0294255 
H    -6.2168904  -12.8919583   -0.7030208 
C    -6.9940783  -11.3894738   -2.0042581 
H    -7.7427438  -12.0382143   -2.4349336 
C    -6.8754788  -10.0701263   -2.4133624 
C    -5.9051647   -9.2729696   -1.8368538 
H    -5.7866105   -8.2446265   -2.1307425 
H    -7.5245408   -9.6578250   -3.1702471 
N    -5.0725592   -9.7366665   -0.8930907 
N    -3.9757621   -6.8713412   -1.0029936 
C    -4.8140842   -5.9464257   -0.5013019 
H    -5.3438074   -6.2132013    0.4002682 
C    -5.0081670   -4.7172035   -1.1064086 
H    -5.6942850   -4.0128578   -0.6658077 
C    -4.3202863   -4.4033585   -2.2789230 
C    -4.4484021   -3.0644926   -2.9183365 
C    -3.4860022   -5.3865083   -2.8119413 
H    -2.9564644   -5.2177099   -3.7350489 
C    -3.3380182   -6.5955279   -2.1551077 
H    -2.7056723   -7.3732675   -2.5549008 
H     1.1788191   -6.9424831    0.7300211 
C    -1.3691318   -6.2344812    2.8225426 
H    -1.6255439   -5.7080812    3.7270802 
N     0.6364106   -4.6228885    4.0271963 
C     1.5930887   -3.8360611    4.5340651 
C     1.2535958   -3.0024172    5.7203347 
C     0.0019851   -3.0828416    6.3315166 
C    -0.3037111   -2.2445696    7.3892863 
H    -1.2612698   -2.2985820    7.8840285 
N     0.5684861   -1.3360543    7.8630959 
C     1.7923601   -1.2777475    7.3078634 
H     2.4840975   -0.5697951    7.7376313 
Pd   -0.0000000    0.0000000    9.3790567 
N     0.5430832   -1.1894033   10.9288782 
C     0.3070136   -0.6577260   12.1624934 
C     0.6523556   -1.3661518   13.3050255 
H     0.4691120   -0.9471030   14.2813657 
C     1.2376001   -2.6166789   13.1960775 
H     1.5079827   -3.1694234   14.0837333 
C     1.4694338   -3.1401658   11.9334328 
H     1.9238786   -4.1101228   11.8043495 
C    -0.3070136    0.6577260   12.1624934 
C    -0.6523556    1.3661518   13.3050255 
H    -0.4691120    0.9471030   14.2813657 
C    -1.2376001    2.6166789   13.1960775 
H    -1.5079827    3.1694234   14.0837333 
C    -1.4694338    3.1401658   11.9334328 
H    -1.9238786    4.1101228   11.8043495 
C    -1.1103515    2.4002125   10.8230239 
H    -1.2775969    2.7762196    9.8288037 
C     1.1103515   -2.4002125   10.8230239 
H     1.2775969   -2.7762196    9.8288037 
N    -0.5430832    1.1894033   10.9288782 
N    -0.5684861    1.3360543    7.8630959 
C    -1.7923601    1.2777475    7.3078634 
H    -2.4840975    0.5697951    7.7376313 
C    -2.1642924    2.0874592    6.2492125 
H    -3.1591016    2.0048759    5.8435728 
C    -1.2535958    3.0024172    5.7203347 
C    -0.0019851    3.0828416    6.3315166 
H     0.7316469    3.7957848    5.9929975 
C    -1.5930887    3.8360611    4.5340651 
C     0.3037111    2.2445696    7.3892863 
H     1.2612698    2.2985820    7.8840285 
H    -0.7316469   -3.7957848    5.9929975 
C     2.1642924   -2.0874592    6.2492125 
H     3.1591016   -2.0048759    5.8435728 
N     2.8213392   -3.7187883    4.0151154 
C     4.7203104   -5.0152270    1.1130627 
H     4.0156767   -5.7011808    0.6725395 
C     5.9488811   -4.8205665    0.5070309 
H     6.2151987   -5.3495556   -0.3950890 
N    10.4479301   -3.3666895   -0.9563373 
H     5.7064551   -1.6279445   -3.7236404 
C     6.9112742    0.1849734   -1.1484659 
H     6.9315650    1.1735558   -0.7202096 
N     4.6170320    0.6330408   -4.0213480 
C     3.8300020    1.5896796   -4.5281567 
C     2.9976205    1.2508124   -5.7156836 
C     2.0841670    2.1621617   -6.2461927 
H     2.0012811    3.1569726   -5.8406101 
C     1.2764300    1.7910299   -7.3066982 
H     0.5696081    2.4832666   -7.7376007 
C     3.0782890   -0.0007394   -6.3269784 
H     3.7899449   -0.7349724   -5.9870696 
C     2.2423030   -0.3054806   -7.3868810 
H     2.2971622   -1.2627864   -7.8820269 
N     3.7118021    2.8174997   -4.0083532 
C     3.4860022    5.3865083   -2.8119413 
H     2.9564644    5.2177099   -3.7350489 
C     3.3380182    6.5955279   -2.1551077 
H     2.7056723    7.3732675   -2.5549008 
N     5.0725592    9.7366665   -0.8930907 
C     1.3691318    6.2344812    2.8225426 
H     1.6255439    5.7080812    3.7270802 
N    -0.6364106    4.6228885    4.0271963 
N    -2.8213392    3.7187883    4.0151154 
C    -4.7203104    5.0152270    1.1130627 
H    -4.0156767    5.7011808    0.6725395 
C    -5.9488811    4.8205665    0.5070309 
H    -6.2151987    5.3495556   -0.3950890 
N   -10.4479301    3.3666895   -0.9563373 
C    -6.2308167    1.3720128   -2.8177975 
H    -5.7064551    1.6279445   -3.7236404 
N    -5.2601788   -2.1693359   -2.3426616 
N    -3.7118021   -2.8174997   -4.0083532 
C    -3.0782890    0.0007394   -6.3269784 
H    -3.7899449    0.7349724   -5.9870696 
C    -2.2423030    0.3054806   -7.3868810 
H    -2.2971622    1.2627864   -7.8820269 
N     1.3354224    0.5674368   -7.8625033 
N     1.1902163    0.5416441  -10.9298751 
C     2.4018344    1.1073285  -10.8241635 
H     2.7780627    1.2745780   -9.8299210 
C     3.1424714    1.4648923  -11.9345913 
H     4.1130954    1.9180941  -11.8056847 
C     2.6188939    1.2331385  -13.1972060 
H     3.1721798    1.5023782  -14.0849403 
C     1.3675233    0.6497181  -13.3060998 
H     0.9484020    0.4668439  -14.2824633 
C     0.6582706    0.3059091  -12.1635150 
C    -0.6582706   -0.3059091  -12.1635150 
C    -1.3675233   -0.6497181  -13.3060998 
C    -2.6188939   -1.2331385  -13.1972060 
C    -3.1424714   -1.4648923  -11.9345913 
C    -2.4018344   -1.1073285  -10.8241635 
H    -2.7780627   -1.2745780   -9.8299210 
H    -4.1130954   -1.9180941  -11.8056847 
H    -3.1721798   -1.5023782  -14.0849403 
H    -0.9484020   -0.4668439  -14.2824633 
N    -1.1902163   -0.5416441  -10.9298751 
{% endcapture %}
{% include codecell.html content=struc_xyz %}
</div>
{% include defaulttab.html %}

Perform *GFN2-xTB* single-point gas-phase calculations on both structures optimized with *GFN2-xTB* and check their energy difference.

{% include note.html content=
'To perform single-point calculations, replace **--opt** by **--sp**. The total energies are given in Hartree. To have more meaningful values, convert them to kcal/mol with 1 Eh = 627.5 kcal/mol.'%}

## Docking 

Use the optimized structure from the previous exercise at the *GFN2-xTB* (gas) level of theory and perform a docking with a CO<sub>2</sub> molecule at the same level of theory. The **aISS** docking module can be called as follows:

 <!-- Tab links -->
<div class="tab card">
  <button class="tablinks tab-id-1" onclick="openTabId(event, 'tab-1-1', 'tab-id-1')" id="open-1">{{ site.data.icons.code }} <code>command</code></button>
  <button class="tablinks tab-id-1" onclick="openTabId(event, 'tab-1-2', 'tab-id-1')">{{ site.data.icons.codefile }} <code>co2.xyz</code></button>
</div>
<!-- Tab content -->
<div id="tab-1-1" class="tabcontent tab-id-1" style="text-align:justify">
{% include command.html cmd="xtb dock humjil_opt.xyz co2.xyz <span class='nt'>--gfn 2</span> <span class='nt'>--nfinal 2</span> > aiss.out &" %}
</div>
<div id="tab-1-2" class="tabcontent tab-id-1" style="text-align:justify">
{% capture struc_file %}
3

C          0.00765        0.03540        0.00000
O         -1.17431       -0.14918        0.00000
O          1.18955        0.22040        0.00000
{% endcapture %}
{% include codecell.html content=struc_file style="font-size:10px" %}
</div>

{% include defaulttab.html id="open-1" %}

The energetically best structure can be found in the `best.xyz` file.
For the docking, most flags possible for a geometry optimization can also be used. For example, implicit solvation can also be employed by providing the *--alpb* flag.

{% include note.html content=
'To save computational time for this workshop, the number of final structures optimized with *GFN2-xTB* was limited to 2 with the **--nfinal** flag. Per default, 15 structures are produced.'%}


## Molecular Dynamics

Use the docked structure from the previous exercise to perform a molecular dynamics (MD) simulation at the *GFN-FF* (gas) level of theory. You'll need a second input file `md.inp` besides the coordinate file:

 <!-- Tab links -->
<div class="tab card">
  <button class="tablinks tab-id-2" onclick="openTabId(event, 'tab-2-1', 'tab-id-2')" id="open-2">{{ site.data.icons.code }} <code>command</code></button>
  <button class="tablinks tab-id-2" onclick="openTabId(event, 'tab-2-2', 'tab-id-2')">{{ site.data.icons.codefile }} <code>md.inp</code></button>
</div>
<!-- Tab content -->
<div id="tab-2-1" class="tabcontent tab-id-2" style="text-align:justify">
{% include command.html cmd="xtb docked_coord.xyz <span class='nt'>--md</span> <span class='nt'>--gfnff</span> <span class='nt'>-I</span> md.inp > md.out &" %}
</div>
<div id="tab-2-2" class="tabcontent tab-id-2" style="text-align:justify">
{% capture struc_file %}
$md
   temp=298     # temperature in K
   time=20.0    # duration in ps
   dump=300.0   # coordinate dump interval in fs
   step=2.0     # stepsize in fs
   velo=false   # scale velocities
   nvt=true     # uses NVT ensemble
   hmass=4      # increased hydrogen mass for FF stability
   shake=2      # constrain all bonds from breaking
   sccacc=2.0   # SCC accuracy
$end

{% endcapture %}
{% include codecell.html content=struc_file style="font-size:10px" %}
</div>

{% include defaulttab.html id="open-2" %}



{% include note.html content= 'This calculation can take about 10 minutes. To speed up this exercise you may reduce the length of the MD by modifying the `time` keyword in `md.inp`.'%}

Before you list any content of this directory when the calculation has finished, remove all `scoord` files:
```bash
rm scoord*
```
Have a look at the simulation by opening the `xtb.trj` file with, e. g., [Molden](https://www.theochem.ru.nl/molden/).
You can do this already during the calculation.


{% include note.html content=
'If the MD takes too long, you might cancel it. The trajectory up to this point will still be available in the `xtb.trj` file. Alternatively, you can start a shorter MD by adjusting the `time` keyword of the `md.inp` file as mentioned before.'%}

## Optional
**xtb** can also be helpful in generating structures relevant to reaction mechanism exploration. For example, the Buchwald Hartwig amination of bromobenzene and (S)-3-amino-2-methylpropan-1-ol with a Pd(BINAP) catalyst involves the complexation of the intermediate catalyst by the amine. Try to generate this complex with the following input

 <!-- Tab links -->
<div class="tab card">
  <button class="tablinks tab-id-3" onclick="openTabId(event, 'tab-3-1', 'tab-id-3')" id="open-3">{{ site.data.icons.code }} <code>command</code></button>
  <button class="tablinks tab-id-3" onclick="openTabId(event, 'tab-3-2', 'tab-id-3')">{{ site.data.icons.codefile }} <code>amine.xyz</code></button>
  <button class="tablinks tab-id-3" onclick="openTabId(event, 'tab-3-3', 'tab-id-3')">{{ site.data.icons.codefile }} <code>cat.xyz</code></button>
</div>
<!-- Tab content -->
<div id="tab-3-1" class="tabcontent tab-id-3" style="text-align:justify">
{% include command.html cmd="xtb dock amine.xyz cat.xyz <span class='nt'>--alpb dmso --fast</span> > aiss.out &" %}
</div>
<div id="tab-3-2" class="tabcontent tab-id-3" style="text-align:justify">
{% capture struc_file %}
17

C         -3.83142        2.84076       -0.12858
C         -2.71271        3.80734        0.30971
H         -3.71462        1.86884        0.40191
H         -3.75622        2.64976       -1.22212
N         -5.15092        3.38956        0.17246
C         -1.33694        3.16769        0.04220
H         -1.25577        2.18168        0.55506
O         -0.29754        4.00686        0.46991
H         -1.20946        2.97517       -1.04499
C         -2.83420        5.15491       -0.42082
H         -2.80779        3.98502        1.40408
H         -3.81369        5.63034       -0.20316
H         -2.74149        5.01454       -1.51927
H         -2.04024        5.85352       -0.08200
H         -0.26205        3.93413        1.45941
H         -5.25016        3.49470        1.20852
H         -5.87559        2.70758       -0.14876
{% endcapture %}
{% include codecell.html content=struc_file style="font-size:10px" %}
</div>
<div id="tab-3-3" class="tabcontent tab-id-3" style="text-align:justify">
{% capture struc_file %}
91

C         1.93043500098766    1.88705038720360    1.27636508509218
C         1.97459955939123    0.74829779266863    0.44541875684329
C         1.02990478561238   -0.25192813715073    0.61271403691281
C         0.01601735664743   -0.12897843953165    1.59684329718372
C         0.00486602136491    1.01110036222777    2.44153841945833
C         0.97835673662409    2.01174361389064    2.24665778060226
C        -0.97905754314325    1.11228749020351    3.44591237208907
C        -1.91732132645756    0.13258429215518    3.60623449046156
C        -1.91580023210662   -0.98853603691249    2.76273320705236
C        -0.97388551841309   -1.11865256011331    1.78244381763454
H         2.65978989329656    2.67284509679964    1.13525202046656
P         3.40713569692185    0.45063598133824   -0.66730537531161
H         0.96019342902486    2.88618786841156    2.88182270064755
H        -0.97520803758161    1.98254339068831    4.08664095236231
H        -2.66738870368542    0.21483103956499    4.37886209692111
H        -2.66684386400195   -1.75316672163424    2.89574895976153
H        -0.97655866734491   -1.98426023003818    1.13659299566919
C         0.14526976821989   -1.59943917510233   -1.31351060703041
C         1.07251821082195   -1.45287954419223   -0.25056729192353
C         2.01675163349715   -2.43347387046616   -0.00496289247722
P         3.16338763564251   -2.18383389437502    1.40106621266299
C         2.09382972162840   -3.55943079098827   -0.84871958824212
H         2.83641281317833   -4.31953291581165   -0.65217511543419
C         1.24280991573976   -3.69290879737754   -1.90717437340130
H         1.31553262831252   -4.55229356826996   -2.55820916660748
C        -0.87091005687256   -0.65166269717626   -1.56151193975196
H        -0.95748963139948    0.20553325193108   -0.91031863064544
C        -1.73979297136593   -0.81645211711138   -2.60279427063404
H        -2.51734053271247   -0.08796162352007   -2.77956466580218
C        -1.62876259469206   -1.92603748517661   -3.45412086454612
H        -2.31889204202597   -2.03459993938128   -4.27768220744122
C        -0.65665910714600   -2.86135403786885   -3.23917435001203
H        -0.56554282455158   -3.72146199672846   -3.88685605699420
C         0.24636505357355   -2.72958028321865   -2.16482109262523
H         5.04053258549462    1.95308963427405    1.04874130293099
C         4.89299905597580    2.58285906489136    0.16680216541704
C         4.10488718080303    2.11753771222348   -0.88819970805292
C         3.97295738904971    2.88967645799337   -2.03513257239657
H         3.39723484500199    2.52608137901539   -2.87409316269410
C         4.59842473761614    4.12259113716083   -2.10916621820447
H         4.49632983073021    4.71832348999157   -3.00459307720805
C         5.36052464719349    4.58801603121167   -1.05134179967215
H         5.85161053486878    5.54723300913738   -1.12057939847728
C         5.51132642475435    3.81457877063409    0.08906544598702
H         6.12430221283919    4.16423408293853    0.90645144171876
H         4.02235854811705   -1.50514117966998   -2.62568631546343
C         3.17171560446993   -0.95856763004698   -3.01734431858295
C         2.63287562149439    0.08153169594252   -2.26955458530146
C         1.54867283380819    0.80195882229825   -2.75892383744741
H         1.12910258822322    1.60673248403452   -2.16984850528478
C         1.01257926858250    0.47853247540941   -3.99057124693866
H         0.17235393384064    1.03814430156328   -4.37523265288449
C         1.54560532773241   -0.56581734842844   -4.72987768534842
H         1.11691409607470   -0.81711771999023   -5.68872690644839
C         2.62541313998850   -1.28431754891050   -4.24489077872467
H         3.04105424986400   -2.09553801038726   -4.82408759676300
H         1.33583677784850   -0.82873466427346    5.74959205741078
C         1.26250407321549   -1.53427439323018    4.93563022334869
C         0.29685622096144   -2.52577568384178    4.96085114639427
H        -0.38313849657341   -2.59518745232414    5.79689008875041
C         0.19668480503760   -3.42844758612526    3.91363117399716
H        -0.55933008558367   -4.19984014517295    3.93572836724455
C         1.05679203332485   -3.33904298939608    2.83622868708840
H         0.97445240569863   -4.03019593470187    2.00770835752968
C         2.03445785679514   -2.34902776756531    2.81406458864911
C         2.13344773754576   -1.44693938519777    3.86489629972164
H         2.89614915297169   -0.67987095722238    3.83313387572892
H         3.25921334801924   -4.71335584827297    3.07226012100153
C         4.00261823026728   -4.76527466002177    2.28923954719084
C         4.13222360890273   -3.72488308629829    1.37980089608449
C         5.12501838704103   -3.78362597909007    0.39615117544011
H         5.25174418682844   -2.94381011451806   -0.29798750601985
C         5.94979789753754   -4.88747721429718    0.30547426182948
H         6.71495850178344   -4.92841143016068   -0.45555496637095
C         5.80628422003005   -5.93092016593784    1.20919590786652
H         6.45742194745829   -6.79014207166281    1.14714340803080
C         4.84174527360330   -5.86441400163025    2.19959273526782
H         4.74234127515449   -6.67004520297639    2.91238124196596
Pd        4.78192197941655   -0.66933638538210    0.85762028033921
Br        6.90486545126967   -0.17867263571098   -0.18326172511155
H         7.37446354631147   -1.04019934049166    6.04329576704061
C         6.91663995455383   -1.04349587877704    5.06457569303456
C         6.05508853955129   -0.02279064401079    4.70077220142163
H         5.83860591747490    0.78008768332450    5.39255355348365
C         5.47218706806705   -0.03062310789953    3.44297757635991
H         4.79334920330727    0.78885028511248    3.17067260451879
C         5.74792721423441   -1.05736492435150    2.54875260346842
C         6.62248653363798   -2.06747078693591    2.90806661030017
H         6.87538232643100   -2.85581054435732    2.20921648721850
C         7.20078991262123   -2.05881341616422    4.16869328286306
H         7.88469613172747   -2.84885038665529    4.44540467384734
{% endcapture %}
{% include codecell.html content=struc_file style="font-size:10px" %}
</div>
{% include defaulttab.html id="open-3" %}

The outcome shows a structure in which the amine functional group does not coordinates to the metal center, but rather a hydrogen bond is formed between the bromine and the OH group.
However, this is not the desired complex required for the reaction. For such cases, the program can be told to search for an amine coordination by defining a preferred interaction site by providing an input file that specifies the atom numbers relevant for complexation:

 <!-- Tab links -->
<div class="tab card">
  <button class="tablinks tab-id-4" onclick="openTabId(event, 'tab-4-1', 'tab-id-4')" id="open-4">{{ site.data.icons.code }} <code>command</code></button>
  <button class="tablinks tab-id-4" onclick="openTabId(event, 'tab-4-2', 'tab-id-4')">{{ site.data.icons.codefile }} <code>xtb.inp</code></button>
</div>
<!-- Tab content -->
<div id="tab-4-1" class="tabcontent tab-id-4" style="text-align:justify">
{% include command.html cmd="xtb dock amine.xyz cat.xyz <span class='nt'>--alpb dmso --fast </span> <span class='nt'>-I xtb.inp</span> > aiss.out &" %}
</div>
<div id="tab-4-2" class="tabcontent tab-id-4" style="text-align:justify">
{% capture struc_file %}
$directed
   scaling factor= 1.0
   atoms: 5,16,17
$end
{% endcapture %}
{% include codecell.html content=struc_file style="font-size:10px" %}
</div>
{% include defaulttab.html id="open-4" %}
