---
layout: default
title: smth
parent: "QCxMS"
nav_order: 3
has_children: false
permalink: page/censo/smth
---

# {{ page.title }}

As an example application of QCxMS2, try to compute the EI spectra for the best conformer of 2-pentanone, which is provided here.
To save computation time, we compute the spectrum at the GFN2-xTB level for geometries, energies, and ionization potentials and only allow further fragmentation 
for fragments above an intensity threshold of 5 percent ("-pthr 5").

<!-- Tab links -->
<div class="tab card">
  <button class="tablinks tab-id-1" onclick="openTabId(event, 'xyz-1', 'tab-id-1')" id="open-1">
    {{ site.data.icons.codefile }} <code>in.xyz</code>
  </button>
  <button class="tablinks tab-id-2" onclick="openTabId(event, 'cmd-1', 'tab-id-2')" id="open-2">
    {{ site.data.icons.codefile }} <code>Command Line</code>
  </button>
  <button class="tablinks tab-id-3" onclick="openTabId(event, 'csv-1', 'tab-id-3')" id="open-3">
    {{ site.data.icons.codefile }} <code>exp.csv</code>
  </button>
</div>

<!-- Tab content for in.xyz -->
<div id="xyz-1" class="tabcontent tab-id-1" style="text-align:justify">
  {% capture xyz_file_1 %}
  <pre>
  16
  energy: -19.369243382271 gnorm: 0.000059854200 xtb: 6.7.1 (b14f90e)
  C    -2.2940556  -0.2725986  -0.0453133
  C    -0.8595415   0.1327712   0.0314810
  H     2.2442557   0.5348094   1.2371323
  H     2.9632725   0.8303553  -0.3817743
  H     1.3138758   1.3508751  -0.0106671
  H    -2.9329297   0.5920872   0.1263702
  H    -2.4811111  -0.6473139  -1.0542316
  H    -2.5205893  -1.0706288   0.6575871
  C     0.1012081  -1.0348426   0.2620038
  H     1.4041016  -0.7281018  -1.4388475
  O    -0.4785022   1.2621103  -0.0658222
  C     1.4592878  -0.7296276  -0.3461410
  H     0.1627662  -1.1203002   1.3532907
  H    -0.3239036  -1.9583427  -0.1296494
  C     2.0670866   0.5410099   0.1623242
  H     2.1176359  -1.5722792  -0.0812496
  </pre>
  {% endcapture %}
  {% include codecell.html content=xyz_file_1 style="font-size:10px" %}
</div>

<!-- Tab content for Command Line -->
<div id="cmd-1" class="tabcontent tab-id-2" style="text-align:justify">
  <pre>
  ```bash
  qcxms2 in.xyz -T 8 -pthr 5
  ```
  </pre>
</div>

<!-- Tab content for exp.csv -->
<div id="csv-1" class="tabcontent tab-id-3" style="text-align:justify">
  {% capture csv_file_1 %}
  <pre>
  14,20
  15,170
  25,10
  26,120
  27,770
  28,40
  29,160
  30,10
  31,20
  37,60
  38,130
  39,780
  40,110
  41,1380
  42,600
  43,9999
  44,290
  45,70
  49,10
  50,50
  51,40
  52,10
  53,80
  54,10
  55,90
  56,20
  57,60
  58,980
  59,30
  60,10
  61,10
  62,10
  63,10
  65,10
  67,20
  68,10
  69,20
  71,970
  72,40
  85,10
  86,1970
  87,120
  88,10
  </pre>
  {% endcapture %}
  {% include codecell.html content=csv_file_1 style="font-size:10px" %}
</div>


The result will be written to the `peaks.csv` file and can be visualized with any suitable plotting tool. You can use the experimental [plotQCxMS2](https://github.com/gorges97/plotQCxMS2) Python script for this. Copy the given experimental spectrum for 2-pentanone `exp.csv` in the directory and execute the `plotqcxms2.py` script to visualize the spectrum including the fragmentation pathways.




