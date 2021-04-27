---
layout: post
title: Bowtie for Oly Genome Expression
date: '2016-11-11'
categories: snippet
---


```
!/Applications/bioinfo/bowtie2-2.2.4/bowtie2 \
-x ../data/Ostrea_lurida-Scaff-10k-bowtie-index \
-1 /Volumes/web/nightingales/O_lurida/filtered_106A_Male_Mix_TAGCTT_L004_R1.fastq.gz \
-2 /Volumes/web/nightingales/O_lurida/filtered_106A_Male_Mix_TAGCTT_L004_R2.fastq.gz \
-p 6 \
--very-fast \
-S /Volumes/caviar/wd/2016-11-11/bw-106A_Male_Mix_TAGCTT_L004.sam
!samtools view -bS /Volumes/caviar/wd/2016-11-11/bw-106A_Male_Mix_TAGCTT_L004.sam \
| samtools sort -o /Volumes/caviar/wd/2016-11-11/bw-106A_Male_Mix_TAGCTT_L004.bam
!samtools index /Volumes/caviar/wd/2016-11-11/bw-106A_Male_Mix_TAGCTT_L004.bam
```

![igv](http://eagle.fish.washington.edu/cnidarian/skitch/IGV_1DD6523A.png)

