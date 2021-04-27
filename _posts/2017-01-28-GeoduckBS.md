---
layout: post
title: Geoduck RRBS Library - First Look
date: '2017-01-28'
categories: Geoduck
tag: [geoduck, methylation, acidification, PPP]
---

Fifty RRBS Libraries were constructed by Hollie and sequenced
(Maybe? these numbers do not match nightingales).

```
EPI-230_S37_L004
EPI-229_S38_L004
EPI-227_S35_L004
EPI-215_S31_L004
EPI-214_S30_L004
EPI-209_S29_L004
EPI-208_S28_L004
EPI-206_S27_L004
EPI-205_S26_L004
EPI-200_S25_L003
EPI-199_S24_L003
EPI-194_S23_L003
EPI-193_S22_L003
EPI-188_S21_L003
EPI-187_S20_L003
EPI-185_S19_L003
EPI-184_S18_L003
EPI-182_S17_L003
EPI-181_S16_L003
EPI-176_S15_L003
EPI-175_S14_L003
EPI-170_S13_L002
EPI-169_S12_L002
EPI-168_S11_L002
EPI-167_S10_L002
EPI-162_S9_L002
EPI-161_S8_L002
EPI-160_S7_L002
EPI-159_S6_L002
EPI-154_S5_L002
EPI-153_S4_L002
EPI-152_S3_L002
EPI-151_S2_L002
EPI-135WG_S42_L005
EPI-44_S41_L005
EPI-43_S40_L005
EPI-42_S39_L005
EPI-145_S38_L005
EPI-41_S38_L005
EPI-143_S37_L005
EPI-136_S36_L005
EPI-135_S35_L005
EPI-128_S34_L005
EPI-127_S33_L005
EPI-120_S32_L005
EPI-119_S31_L005
EPI-113_S30_L005
EPI-111_S29_L005
EPI-104_S28_L005
EPI-103_S27_L005
```

--- 

Here are some details on batch 01
<img src="http://eagle.fish.washington.edu/cnidarian/skitch/project_juvenile_geoduck_OA_20161201_Library_prep_1_csv_at_master_·_hputnam_project_juvenile_geoduck_OA_1E3D5BCF.png" alt="project_juvenile_geoduck_OA_20161201_Library_prep_1_csv_at_master_·_hputnam_project_juvenile_geoduck_OA_1E3D5BCF.png"/>

---

The first batch came in late December.

```
[   ]	EPI-103_S27_L005_R1_..>	28-Dec-2016 10:33	1.2G	 
[   ]	EPI-103_S27_L005_R2_..>	28-Dec-2016 10:33	1.1G	 
[   ]	EPI-104_S28_L005_R1_..>	28-Dec-2016 10:33	1.7G	 
[   ]	EPI-104_S28_L005_R2_..>	28-Dec-2016 10:33	1.7G	 
[   ]	EPI-111_S29_L005_R1_..>	28-Dec-2016 10:33	1.5G	 
[   ]	EPI-111_S29_L005_R2_..>	28-Dec-2016 10:33	1.5G	 
[   ]	EPI-113_S30_L005_R1_..>	28-Dec-2016 10:33	1.5G	 
[   ]	EPI-113_S30_L005_R2_..>	28-Dec-2016 10:33	1.4G	 
[   ]	EPI-119_S31_L005_R1_..>	28-Dec-2016 10:33	1.6G	 
[   ]	EPI-119_S31_L005_R2_..>	28-Dec-2016 10:33	1.6G	 
[   ]	EPI-120_S32_L005_R1_..>	28-Dec-2016 10:33	1.4G	 
[   ]	EPI-120_S32_L005_R2_..>	28-Dec-2016 10:33	1.3G	 
[   ]	EPI-127_S33_L005_R1_..>	28-Dec-2016 10:33	1.3G	 
[   ]	EPI-127_S33_L005_R2_..>	28-Dec-2016 10:33	1.2G	 
[   ]	EPI-128_S34_L005_R1_..>	28-Dec-2016 10:33	1.4G	 
[   ]	EPI-128_S34_L005_R2_..>	28-Dec-2016 10:33	1.4G	 
[   ]	EPI-135_S35_L005_R1_..>	28-Dec-2016 10:33	1.6G	 
[   ]	EPI-135_S35_L005_R2_..>	28-Dec-2016 10:33	1.6G	 
[   ]	EPI-136_S36_L005_R1_..>	28-Dec-2016 10:33	1.5G	 
[   ]	EPI-136_S36_L005_R2_..>	28-Dec-2016 10:33	1.5G	 
[   ]	EPI-143_S37_L005_R1_..>	28-Dec-2016 10:33	1.2G	 
[   ]	EPI-143_S37_L005_R2_..>	28-Dec-2016 10:33	1.2G	 
[   ]	EPI-145_S38_L005_R1_..>	28-Dec-2016 10:33	1.4G	 
[   ]	EPI-145_S38_L005_R2_..>	28-Dec-2016 10:33	1.4G	 
```
 and is also in Cyverse/CoGe and analyzed
 
 <img src="http://eagle.fish.washington.edu/cnidarian/skitch/_89__Discovery_Environment_1E3D4DEB.png" alt="_89__Discovery_Environment_1E3D4DEB.png"/>
 
 
---

This first batch was aligned to Bismarck using this version of the genome.
<img src="http://eagle.fish.washington.edu/cnidarian/skitch/CoGe__GenomeInfo_and_untitled_text_3_1E3D4EF7.png" alt="CoGe__GenomeInfo_and_untitled_text_3_1E3D4EF7.png"/>


These are the files generated     

<img src="http://eagle.fish.washington.edu/cnidarian/skitch/CoGe__My_Data_1E3D4FB3.png" alt="CoGe__My_Data_1E3D4FB3.png"/>

BAM file are all in a Notebook     

<img src="http://eagle.fish.washington.edu/cnidarian/skitch/CoGe__My_Data_1E3D5818.png" alt="CoGe__My_Data_1E3D5818.png"/>


https://genomevolution.org/coge/NotebookView.pl?lid=1927

---

[Viewable in CoGe Browser](https://genomevolution.org/coge/GenomeView.pl?embed=0&gid=34160&loc=scaffold26337%3A1..154898&tracks=notebook1927%2Cexperiment9827%2Cexperiment9812%2Cexperiment9831%2Cexperiment9787&highlight=)




