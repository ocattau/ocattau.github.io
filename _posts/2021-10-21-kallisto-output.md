---
layout: post
title: steps on how to count data from a kallisto index
date: '2021-10-21'
categories: kallisto, transcriptome, P. generosa, computation, index, QC
tags: P. generosa, index, kallisto
---

## Inspect P. generosa genome for candidate genes. First step is to extract output data: 

[link to abundance data](https://githubusercontent.com/ocattau/kallisto/main/analyses/output_01/abundance.tsv)

```{r}
abundance_data<-read.table(file="https://github.com/ocattau/kallisto/blob/main/analyses/output_01/abundance.tsv")
head(abundance_data)

```

[link to run info json file](https://github.com/ocattau/kallisto/blob/main/analyses/output_01/run_info.json) 

[link to index file](https://gannet.fish.washington.edu/gigas/data/transcriptome_v5.idx) 

### Next step is to get count data on the abundance.tsv file. Grab our Geoduck Transcriptome off of Mox

```{bash}
#login to Mox
#find file location-->
~/gscratch/srlab/blastdbs/ncbi-sp-v5_20210224/

```
