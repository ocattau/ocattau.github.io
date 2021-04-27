---
layout: post
title: BS Mapping Oly Cats
date: '2019-06-30'
---

Working on the genetics / epigenetics paper, I decided to try to concatenate all reads and align with Bismark in order to get some basic stats.

Here is the script. 

[0620_1100.sh](https://d.pr/n/ujWPIe)

tldr
```
#SBATCH --workdir=/gscratch/scrubbed/sr320/0620

${bismark_dir}/bismark \
--path_to_bowtie ${bowtie2_dir} \
-genome /gscratch/srlab/sr320/data/olurida-genomes/v081 \
-p 14 \
--non_directional \
/gscratch/scrubbed/sr320/0620/zr1394_all_s456_trimmed.fq
```

```
Final Alignment report
======================
Sequences analysed in total:	1635584275
Number of alignments with a unique best hit from the different alignments:	507562199
Mapping efficiency:	31.0%
Sequences with no alignments under any condition:	477689355
Sequences did not map uniquely:	650332721
Sequences which were discarded because genomic sequence could not be extracted:	496024
```
