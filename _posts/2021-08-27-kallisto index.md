---
layout: post
title: blast locally 
date: '2021-08-27'
categories: index
tags: test
tags: transcriptome, p. generosa, index, kallisto
---
#using Roadrunner for bulding a Kallisto index

'srlab@roadrunner.fish.washington.edu'

'srlab@roadrunner:~/anaconda2$ curl -O https://github.com/trinityrnaseq/trinityrnaseq/releases/download/v2.11.0/trinityrnaseq-v2.11.0.FULL.tar.gz --insecure -O https://gannet.fish.washington.edu/Atumefaciens/20191105_swoose_pgen_v074_renaming/Panopea-generosa-v1.0.fa'

'srlab@roadrunner:~/anaconda2$ kallisto'

'srlab@roadrunner:~/anaconda2$ !curl --insecure \
curl -O https://github.com/trinityrnaseq/trinityrnaseq/releases/download/v2.11.0/trinityrnaseq-v2.11.0.FULL.tar.gz --insecure -O https://gannet.fish.washington.edu/Atumefaciens/20191105_swoose_pgen_v074_renaming/Panopea-generosa-v1.0.fa  --insecure \
> -O https://owl.fish.washington.edu/halfshell/genomic-databank/Pgenerosa_transcriptome_v5.fasta'

'srlab@roadrunner:~/anaconda2$ mv Pgenerosa_transcriptome_v5.fasta ~/anaconda2/bin/Pgenerosa_transcriptome_v5.fasta'

'srlab@roadrunner:~/anaconda2$ mv Panopea-generosa-v1.0.fa ~/anaconda2/bin/Panopea-generosa-v1.0.fa'

'srlab@roadrunner:~/anaconda2/bin$ kallisto \index -i ../transcriptome_v5.idx Pgenerosa_transcriptome_v5.fasta'
>[build] loading fasta file Pgenerosa_transcriptome_v5.fasta
>[build] k-mer length: 31
>[build] warning: clipped off poly-A tail (longer than 10)
        from 5780 target sequences
>[build] counting k-mers ... done.

'



