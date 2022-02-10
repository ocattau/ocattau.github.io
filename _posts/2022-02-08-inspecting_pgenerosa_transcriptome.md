---
layout: post
title: Functional Annotation of P. Generosa transcriptome part 3
date: '2022-02-08'
categories: kallisto, transcriptome, P. generosa, computation, index, QC, count data
tags: P. generosa, index, kallisto
---

# First Step: take merged data from geoduck transcriptomes and upload to R
```{r}
countMatrix<-read.table(file="https://raw.githubusercontent.com/sr320/nb-2022/main/P_generosa/analyses/kallisto-0207.isoform.counts.matrix", header=TRUE, sep = '\t')
names(countMatrix)[1]<-"target_id"
head(countMatrix)
```
# Second Step: take blast data and load
```{r}
#load blast data, see blasting .sh file to see code (in GItHub)
blast_data<-read.table(file="https://gannet.fish.washington.edu/gigas/Panopea-generosa-uniprot_blastx.tab")
names(blast_data)[1]<-"target_id" #renamed to match countMATRIX data
names(blast_data)[2]<-"identifiers" #renamed to search in uniprot swiss prot 
```
# Third Step: merge blast data with geoduck transcriptome data 

```{r}
library(dplyr)
library(tidyr)
#merging target_ids to count Matrix to get identifies for swissprot
generosa_counts<-full_join(blast_data, countMatrix, by = "target_id")
generosa_counts<-generosa_counts[-c(3:12)] # not every target ID has a protein identifier...could be an issue later on....
generosa_counts[complete.cases(generosa_counts),] 
#blast_data<-read.csv(file="/Users/oliviacattau/Documents/analysis/code/generosa_counts.csv")#lost count data due to excel stupidity
generosa_counts$identifiers<-sub("\\.\\d+$", "", generosa_counts$identifiers) #removed decimal after identifiers so match Uniprot format
```
# Fourth Step: Go to Uniprot website and grab all go terms for all reviewed proteins
[Uniprot Website](https://www.uniprot.org/uniprot/?query=*&fil=reviewed%3Ayes#)

```{r}
#loaded into gannet and pulled down
uniprot_all_reviewed<-read.csv(file="https://gannet.fish.washington.edu/gigas/uniprot-reviewed_yes.tab", sep='\t', header=TRUE)
```
# Fifth Step: Left Join Tables by identifier

```{r}
names(uniprot_all_reviewed)[1]<-"identifiers" #renamed
pgenerosa_proteins<-left_join(generosa_counts, uniprot_all_reviewed, by ="identifiers")
write.csv(pgenerosa_proteins, file="/Users/oliviacattau/Documents/GitHub/code/characterize_larval_transciptome/pgenerosa_proteins_2_10_2022.tab")
```
[link to protein table](https://gannet.fish.washington.edu/gigas/data/p.generosa/#:~:text=pgenerosa_proteins_2..%3E)
