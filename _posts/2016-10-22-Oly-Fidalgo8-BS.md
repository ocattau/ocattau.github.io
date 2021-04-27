---
layout: post
title: Fidalgo 8 Oly Oyster BS
date: '2016-10-22'
categories: Ostrea
tags: bs, bsmap, python, olympia, oyster, scaffold
---


Analysis of eight Fidalgo Olympia oysters. Maybe I just need a second sentence.





```python
ls analyses/2016-10-11
```

    mkfmt_M2.txt  mkfmt_M3.txt



```python
ls -lh /Volumes/caviar/wd/2016-10-11/bsmap*sam
```

    -rw-r--r--  1 sr320  staff   208M Oct 15 02:52 /Volumes/caviar/wd/2016-10-11/bsmap_out_1_ATCACG.sam
    -rw-r--r--  1 sr320  staff   254M Oct 16 04:21 /Volumes/caviar/wd/2016-10-11/bsmap_out_2_CGATGT.sam
    -rw-r--r--  1 sr320  staff   253M Oct 17 05:33 /Volumes/caviar/wd/2016-10-11/bsmap_out_3_TTAGGC.sam
    -rw-r--r--  1 sr320  staff   253M Oct 18 08:19 /Volumes/caviar/wd/2016-10-11/bsmap_out_4_TGACCA.sam
    -rw-r--r--  1 sr320  staff   264M Oct 20 15:50 /Volumes/caviar/wd/2016-10-11/bsmap_out_5_ACAGTG.sam
    -rw-rw-rw-  1 sr320  staff   263M Oct 22 02:37 /Volumes/caviar/wd/2016-10-11/bsmap_out_6_GCCAAT.sam
    -rw-rw-rw-  1 sr320  staff   225M Oct 20 18:49 /Volumes/caviar/wd/2016-10-11/bsmap_out_7_CAGATC.sam
    -rw-rw-rw-  1 sr320  staff   299M Oct 19 18:55 /Volumes/caviar/wd/2016-10-11/bsmap_out_8_ACTTGA.sam
    -rw-r--r--  1 sr320  staff   1.5G Oct 11 08:06 /Volumes/caviar/wd/2016-10-11/bsmap_out_M2.sam
    -rw-r--r--  1 sr320  staff   1.6G Oct 11 08:10 /Volumes/caviar/wd/2016-10-11/bsmap_out_M3.sam



```python

```


```python
bsmaploc="/Applications/bioinfo/BSMAP/bsmap-2.74/"

```


```python
cd /Volumes/caviar/wd/2016-10-11/
```

    /Volumes/caviar/wd/2016-10-11



```python
for i in ("1_ATCACG","2_CGATGT","3_TTAGGC","4_TGACCA","5_ACAGTG","6_GCCAAT","7_CAGATC","8_ACTTGA"):
    !python {bsmaploc}methratio.py \
-d ../data/Ostrea_lurida.scafSeq \
-u -z -g \
-o methratio_out_{i}.txt \
-s {bsmaploc}samtools \
bsmap_out_{i}.sam \
```

    @ Sat Oct 22 09:46:37 2016: reading reference ../data/Ostrea_lurida.scafSeq ...
    @ Sat Oct 22 09:47:26 2016: reading bsmap_out_1_ATCACG.sam ...
    [samopen] SAM header is present: 765755 sequences.
    @ Sat Oct 22 09:47:53 2016: combining CpG methylation from both strands ...
    @ Sat Oct 22 09:49:11 2016: writing methratio_out_1_ATCACG.txt ...
    @ Sat Oct 22 09:54:10 2016: done.
    total 467574 valid mappings, 618824 covered cytosines, average coverage: 2.02 fold.
    @ Sat Oct 22 09:54:15 2016: reading reference ../data/Ostrea_lurida.scafSeq ...
    @ Sat Oct 22 09:55:04 2016: reading bsmap_out_2_CGATGT.sam ...
    [samopen] SAM header is present: 765755 sequences.
    @ Sat Oct 22 09:55:37 2016: combining CpG methylation from both strands ...
    @ Sat Oct 22 09:56:55 2016: writing methratio_out_2_CGATGT.txt ...
    @ Sat Oct 22 10:01:55 2016: done.
    total 579365 valid mappings, 689492 covered cytosines, average coverage: 2.19 fold.
    @ Sat Oct 22 10:02:00 2016: reading reference ../data/Ostrea_lurida.scafSeq ...
    @ Sat Oct 22 10:02:49 2016: reading bsmap_out_3_TTAGGC.sam ...
    [samopen] SAM header is present: 765755 sequences.
    @ Sat Oct 22 10:03:21 2016: combining CpG methylation from both strands ...
    @ Sat Oct 22 10:04:39 2016: writing methratio_out_3_TTAGGC.txt ...
    @ Sat Oct 22 10:09:37 2016: done.
    total 579579 valid mappings, 678634 covered cytosines, average coverage: 2.24 fold.
    @ Sat Oct 22 10:09:42 2016: reading reference ../data/Ostrea_lurida.scafSeq ...
    @ Sat Oct 22 10:10:31 2016: reading bsmap_out_4_TGACCA.sam ...
    [samopen] SAM header is present: 765755 sequences.
    @ Sat Oct 22 10:11:04 2016: combining CpG methylation from both strands ...
    @ Sat Oct 22 10:12:21 2016: writing methratio_out_4_TGACCA.txt ...
    @ Sat Oct 22 10:17:20 2016: done.
    total 577435 valid mappings, 690889 covered cytosines, average coverage: 2.18 fold.
    @ Sat Oct 22 10:17:25 2016: reading reference ../data/Ostrea_lurida.scafSeq ...
    @ Sat Oct 22 10:18:14 2016: reading bsmap_out_5_ACAGTG.sam ...
    [samopen] SAM header is present: 765755 sequences.
    @ Sat Oct 22 10:18:47 2016: combining CpG methylation from both strands ...
    @ Sat Oct 22 10:20:04 2016: writing methratio_out_5_ACAGTG.txt ...
    @ Sat Oct 22 10:25:04 2016: done.
    total 608092 valid mappings, 691864 covered cytosines, average coverage: 2.27 fold.
    @ Sat Oct 22 10:25:09 2016: reading reference ../data/Ostrea_lurida.scafSeq ...
    @ Sat Oct 22 10:25:58 2016: reading bsmap_out_6_GCCAAT.sam ...
    [samopen] SAM header is present: 765755 sequences.
    @ Sat Oct 22 10:26:32 2016: combining CpG methylation from both strands ...
    @ Sat Oct 22 10:27:51 2016: writing methratio_out_6_GCCAAT.txt ...
    @ Sat Oct 22 10:32:57 2016: done.
    total 604365 valid mappings, 689831 covered cytosines, average coverage: 2.27 fold.
    @ Sat Oct 22 10:33:02 2016: reading reference ../data/Ostrea_lurida.scafSeq ...
    @ Sat Oct 22 10:33:51 2016: reading bsmap_out_7_CAGATC.sam ...
    [samopen] SAM header is present: 765755 sequences.
    @ Sat Oct 22 10:34:20 2016: combining CpG methylation from both strands ...
    @ Sat Oct 22 10:35:33 2016: writing methratio_out_7_CAGATC.txt ...
    @ Sat Oct 22 10:40:32 2016: done.
    total 507109 valid mappings, 646374 covered cytosines, average coverage: 2.09 fold.
    @ Sat Oct 22 10:40:38 2016: reading reference ../data/Ostrea_lurida.scafSeq ...
    @ Sat Oct 22 10:41:27 2016: reading bsmap_out_8_ACTTGA.sam ...
    [samopen] SAM header is present: 765755 sequences.
    @ Sat Oct 22 10:42:05 2016: combining CpG methylation from both strands ...
    @ Sat Oct 22 10:43:22 2016: writing methratio_out_8_ACTTGA.txt ...
    @ Sat Oct 22 10:48:21 2016: done.
    total 689625 valid mappings, 732123 covered cytosines, average coverage: 2.42 fold.



```python
#first methratio files are converted to filter for CG context, 3x coverage (mr3x.awk), and reformatting (mr_gg.awk.sh).
#due to issue passing variable to awk, simple scripts were used (included in repository)
for i in ("1_ATCACG","2_CGATGT","3_TTAGGC","4_TGACCA","5_ACAGTG","6_GCCAAT","7_CAGATC","8_ACTTGA"):
    !echo {i}
    !grep "[A-Z][A-Z]CG[A-Z]" <methratio_out_{i}.txt> methratio_out_{i}CG.txt
    !awk -f /Users/sr320/git-repos/sr320.github.io/jupyter/scripts/mr3x.awk methratio_out_{i}CG.txt \
    > mr3x.{i}.txt
    !awk -f /Users/sr320/git-repos/sr320.github.io/jupyter/scripts/mr_gg.awk.sh \
    mr3x.{i}.txt > mkfmt_{i}.txt
```

    1_ATCACG
    2_CGATGT
    3_TTAGGC
    4_TGACCA
    5_ACAGTG
    6_GCCAAT
    7_CAGATC
    8_ACTTGA



```python
#maybe we need to ignore case
```


```python
!md5 mkfmt_M2.txt mkfmti_M2.txt | head
```

    MD5 (mkfmt_M2.txt) = df67fde9e87ec165618d384374074057
    MD5 (mkfmti_M2.txt) = df67fde9e87ec165618d384374074057



```python
#nope
```


```python
!head -5  mkfmt*
```

    ==> mkfmt_1_ATCACG.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.33	scaffold1	33	F	3	0.00	100.00
    scaffold1.143	scaffold1	143	F	4	0.00	100.00
    scaffold1.244	scaffold1	244	F	3	66.67	33.33
    scaffold1.265	scaffold1	265	F	7	14.29	85.71
    
    ==> mkfmt_2_CGATGT.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.33	scaffold1	33	F	11	0.00	100.00
    scaffold1.143	scaffold1	143	F	9	0.00	100.00
    scaffold1.566	scaffold1	566	F	8	0.00	100.00
    scaffold1.572	scaffold1	572	F	3	0.00	100.00
    
    ==> mkfmt_3_TTAGGC.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.12	scaffold1	12	F	4	25.00	75.00
    scaffold1.33	scaffold1	33	F	3	0.00	100.00
    scaffold1.109	scaffold1	109	F	5	0.00	100.00
    scaffold1.143	scaffold1	143	F	9	0.00	100.00
    
    ==> mkfmt_4_TGACCA.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.109	scaffold1	109	F	9	11.11	88.89
    scaffold1.143	scaffold1	143	F	11	9.09	90.91
    scaffold1.244	scaffold1	244	F	3	0.00	100.00
    scaffold1.265	scaffold1	265	F	4	25.00	75.00
    
    ==> mkfmt_5_ACAGTG.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.33	scaffold1	33	F	8	0.00	100.00
    scaffold1.109	scaffold1	109	F	5	0.00	100.00
    scaffold1.143	scaffold1	143	F	5	0.00	100.00
    scaffold1.244	scaffold1	244	F	6	33.33	66.67
    
    ==> mkfmt_6_GCCAAT.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.12	scaffold1	12	F	3	0.00	100.00
    scaffold1.33	scaffold1	33	F	11	9.09	90.91
    scaffold1.109	scaffold1	109	F	7	0.00	100.00
    scaffold1.143	scaffold1	143	F	11	0.00	100.00
    
    ==> mkfmt_7_CAGATC.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.33	scaffold1	33	F	10	0.00	100.00
    scaffold1.109	scaffold1	109	F	6	0.00	100.00
    scaffold1.143	scaffold1	143	F	16	0.00	100.00
    scaffold1.244	scaffold1	244	F	3	0.00	100.00
    
    ==> mkfmt_8_ACTTGA.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.33	scaffold1	33	F	7	0.00	100.00
    scaffold1.109	scaffold1	109	F	4	0.00	100.00
    scaffold1.143	scaffold1	143	F	10	10.00	90.00
    scaffold1.244	scaffold1	244	F	6	0.00	100.00
    
    ==> mkfmt_M2.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.14274	scaffold1	14274	F	4	0.00	100.00
    scaffold1.14305	scaffold1	14305	F	4	0.00	100.00
    scaffold1.15309	scaffold1	15309	F	4	0.00	100.00
    scaffold1.15315	scaffold1	15315	F	4	0.00	100.00
    
    ==> mkfmt_M3.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.259	scaffold1	259	F	4	100.00	0.00
    scaffold1.263	scaffold1	263	F	4	100.00	0.00
    scaffold1.267	scaffold1	267	F	4	100.00	0.00
    scaffold1.271	scaffold1	271	F	4	100.00	0.00
    
    ==> mkfmti_M2.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.14274	scaffold1	14274	F	4	0.00	100.00
    scaffold1.14305	scaffold1	14305	F	4	0.00	100.00
    scaffold1.15309	scaffold1	15309	F	4	0.00	100.00
    scaffold1.15315	scaffold1	15315	F	4	0.00	100.00
    
    ==> mkfmti_M3.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.259	scaffold1	259	F	4	100.00	0.00
    scaffold1.263	scaffold1	263	F	4	100.00	0.00
    scaffold1.267	scaffold1	267	F	4	100.00	0.00
    scaffold1.271	scaffold1	271	F	4	100.00	0.00


# Products


```python
cd git-repos/sr320.github.io/jupyter/ 
```

    /Users/sr320/git-repos/sr320.github.io/jupyter



```python
ls
```

    [34mCgigas[m[m/   [34mOlurida[m[m/  [34manalyses[m[m/ [34mscripts[m[m/



```python
mkdir analyses/$(date +%F)
```


```python
for i in ("1_ATCACG","2_CGATGT","3_TTAGGC","4_TGACCA","5_ACAGTG","6_GCCAAT","7_CAGATC","8_ACTTGA"):
    !cp /Volumes/caviar/wd/2016-10-11/mkfmt_{i}.txt analyses/$(date +%F)/mkfmt_{i}.txt
```


```python
!head analyses/$(date +%F)/*
```

    ==> analyses/2016-10-22/mkfmt_1_ATCACG.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.33	scaffold1	33	F	3	0.00	100.00
    scaffold1.143	scaffold1	143	F	4	0.00	100.00
    scaffold1.244	scaffold1	244	F	3	66.67	33.33
    scaffold1.265	scaffold1	265	F	7	14.29	85.71
    scaffold1.579	scaffold1	579	F	4	0.00	100.00
    scaffold1.591	scaffold1	591	F	4	0.00	100.00
    scaffold1.622	scaffold1	622	F	4	0.00	100.00
    scaffold1.641	scaffold1	641	F	3	66.67	33.33
    scaffold1.723	scaffold1	723	F	3	0.00	100.00
    
    ==> analyses/2016-10-22/mkfmt_2_CGATGT.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.33	scaffold1	33	F	11	0.00	100.00
    scaffold1.143	scaffold1	143	F	9	0.00	100.00
    scaffold1.566	scaffold1	566	F	8	0.00	100.00
    scaffold1.572	scaffold1	572	F	3	0.00	100.00
    scaffold1.576	scaffold1	576	F	9	0.00	100.00
    scaffold1.579	scaffold1	579	F	8	0.00	100.00
    scaffold1.582	scaffold1	582	F	6	83.33	16.67
    scaffold1.591	scaffold1	591	F	6	0.00	100.00
    scaffold1.602	scaffold1	602	F	5	0.00	100.00
    
    ==> analyses/2016-10-22/mkfmt_3_TTAGGC.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.12	scaffold1	12	F	4	25.00	75.00
    scaffold1.33	scaffold1	33	F	3	0.00	100.00
    scaffold1.109	scaffold1	109	F	5	0.00	100.00
    scaffold1.143	scaffold1	143	F	9	0.00	100.00
    scaffold1.244	scaffold1	244	F	4	0.00	100.00
    scaffold1.265	scaffold1	265	F	11	0.00	100.00
    scaffold1.566	scaffold1	566	F	5	0.00	100.00
    scaffold1.576	scaffold1	576	F	5	0.00	100.00
    scaffold1.579	scaffold1	579	F	6	0.00	100.00
    
    ==> analyses/2016-10-22/mkfmt_4_TGACCA.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.109	scaffold1	109	F	9	11.11	88.89
    scaffold1.143	scaffold1	143	F	11	9.09	90.91
    scaffold1.244	scaffold1	244	F	3	0.00	100.00
    scaffold1.265	scaffold1	265	F	4	25.00	75.00
    scaffold1.566	scaffold1	566	F	4	0.00	100.00
    scaffold1.572	scaffold1	572	F	3	0.00	100.00
    scaffold1.576	scaffold1	576	F	7	0.00	100.00
    scaffold1.579	scaffold1	579	F	5	0.00	100.00
    scaffold1.582	scaffold1	582	F	4	50.00	50.00
    
    ==> analyses/2016-10-22/mkfmt_5_ACAGTG.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.33	scaffold1	33	F	8	0.00	100.00
    scaffold1.109	scaffold1	109	F	5	0.00	100.00
    scaffold1.143	scaffold1	143	F	5	0.00	100.00
    scaffold1.244	scaffold1	244	F	6	33.33	66.67
    scaffold1.265	scaffold1	265	F	6	0.00	100.00
    scaffold1.566	scaffold1	566	F	3	0.00	100.00
    scaffold1.572	scaffold1	572	F	3	0.00	100.00
    scaffold1.576	scaffold1	576	F	4	0.00	100.00
    scaffold1.579	scaffold1	579	F	5	0.00	100.00
    
    ==> analyses/2016-10-22/mkfmt_6_GCCAAT.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.12	scaffold1	12	F	3	0.00	100.00
    scaffold1.33	scaffold1	33	F	11	9.09	90.91
    scaffold1.109	scaffold1	109	F	7	0.00	100.00
    scaffold1.143	scaffold1	143	F	11	0.00	100.00
    scaffold1.244	scaffold1	244	F	9	11.11	88.89
    scaffold1.265	scaffold1	265	F	11	0.00	100.00
    scaffold1.566	scaffold1	566	F	10	0.00	100.00
    scaffold1.572	scaffold1	572	F	4	0.00	100.00
    scaffold1.576	scaffold1	576	F	11	0.00	100.00
    
    ==> analyses/2016-10-22/mkfmt_7_CAGATC.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.33	scaffold1	33	F	10	0.00	100.00
    scaffold1.109	scaffold1	109	F	6	0.00	100.00
    scaffold1.143	scaffold1	143	F	16	0.00	100.00
    scaffold1.244	scaffold1	244	F	3	0.00	100.00
    scaffold1.265	scaffold1	265	F	9	0.00	100.00
    scaffold1.566	scaffold1	566	F	6	0.00	100.00
    scaffold1.576	scaffold1	576	F	5	0.00	100.00
    scaffold1.579	scaffold1	579	F	6	16.67	83.33
    scaffold1.582	scaffold1	582	F	5	80.00	20.00
    
    ==> analyses/2016-10-22/mkfmt_8_ACTTGA.txt <==
    chr.Base	chr	base	strand	coverage	freqC	freqT
    scaffold1.33	scaffold1	33	F	7	0.00	100.00
    scaffold1.109	scaffold1	109	F	4	0.00	100.00
    scaffold1.143	scaffold1	143	F	10	10.00	90.00
    scaffold1.244	scaffold1	244	F	6	0.00	100.00
    scaffold1.265	scaffold1	265	F	7	14.29	85.71
    scaffold1.566	scaffold1	566	F	7	0.00	100.00
    scaffold1.576	scaffold1	576	F	6	0.00	100.00
    scaffold1.579	scaffold1	579	F	7	14.29	85.71
    scaffold1.582	scaffold1	582	F	7	42.86	57.14


url for 8 tables..

```
https://github.com/sr320/sr320.github.io/tree/master/jupyter/analyses/2016-10-22
```


```python

```
