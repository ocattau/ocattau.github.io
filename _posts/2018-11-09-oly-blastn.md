---
layout: post
title: A simple Oly Gene Track
date: '2018-11-19'
---

To get a crude gene track for the Oly genome the big transcriptome was compared to genome.

```
#SBATCH --workdir=/gscratch/srlab/sr320/analyses/1119

/gscratch/srlab/programs/ncbi-blast-2.6.0+/bin/blastn \
-task blastn \
-query /gscratch/srlab/sr320/data/oly/Trinity.fasta \
-db /gscratch/srlab/sr320/data/oly/Olurida_v081 \
-out /gscratch/srlab/sr320/analyses/1119/ks-trinity-v081.tab \
-evalue 1e-20 \
-max_target_seqs 1 \
-outfmt 6 \
-num_threads 28
```

then

```
!perl ../scripts/2_Blast2Gff.pl \
-i data/ks-trinity-v081.tab \
-s "something" \
-o analyses/ks-blastn-Olurida_v081-01.gff \
-p "gene-blast" -d "Olurida_v081"
```

Output: `http://owl.fish.washington.edu/halfshell/genomic-databank/Olurida_v081-ks-blastn.gff`

