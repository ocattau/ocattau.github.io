---
layout: post
title: steps on how to create kalllisto index file
date: '2021-10-13'
categories: kallisto, transcriptome, P. generosa, computation, index, QC
tags: P. generosa, index, kallisto
---

[link to Patcher Lab handbook](https://pachterlab.github.io/kallisto/starting)

#Building an Index

```{bash}
#load kallisto
#cd kallisto/tests
#kallisto index -i transcripts.idx transcripts.fasta.gz
cd /home/shared/kallisto/test
 /home/shared/kallisto/kallisto \
index -i ~/data/transcriptome_v5.idx /home/olivia/x.fasta
```
#Quantification

```{bash}
kallisto quant -i transcripts.idx -o output -b 100 reads_1.fastq.gz reads_2.fastq.gz
run_info.json 
#The run_info.json file contains a summary of the run, including data on the number targets used for quantification, and the number of bootstraps performed
```

