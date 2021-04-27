---
layout: post
title: Geoduck alignments to v74
date: '2019-08-15'
---

Taking the trimmed files @ `/gscratch/srlab/strigg/data/Pgenr/FASTQS`
and aligning to version 74 of the genome.


specifically
```
[sr320@mox2 FASTQS]$ ls *.gz
EPI-103_S27_L005_R1_001_val_1.fq.gz  EPI-181_S16_L003_R1_001_val_1.fq.gz
EPI-103_S27_L005_R2_001_val_2.fq.gz  EPI-181_S16_L003_R2_001_val_2.fq.gz
EPI-104_S28_L005_R1_001_val_1.fq.gz  EPI-182_S17_L003_R1_001_val_1.fq.gz
EPI-104_S28_L005_R2_001_val_2.fq.gz  EPI-182_S17_L003_R2_001_val_2.fq.gz
EPI-111_S29_L005_R1_001_val_1.fq.gz  EPI-184_S18_L003_R1_001_val_1.fq.gz
EPI-111_S29_L005_R2_001_val_2.fq.gz  EPI-184_S18_L003_R2_001_val_2.fq.gz
EPI-113_S30_L005_R1_001_val_1.fq.gz  EPI-185_S19_L003_R1_001_val_1.fq.gz
EPI-113_S30_L005_R2_001_val_2.fq.gz  EPI-185_S19_L003_R2_001_val_2.fq.gz
EPI-119_S31_L005_R1_001_val_1.fq.gz  EPI-187_S20_L003_R1_001_val_1.fq.gz
EPI-119_S31_L005_R2_001_val_2.fq.gz  EPI-187_S20_L003_R2_001_val_2.fq.gz
EPI-120_S32_L005_R1_001_val_1.fq.gz  EPI-188_S21_L003_R1_001_val_1.fq.gz
EPI-120_S32_L005_R2_001_val_2.fq.gz  EPI-188_S21_L003_R2_001_val_2.fq.gz
EPI-127_S33_L005_R1_001_val_1.fq.gz  EPI-193_S22_L003_R1_001_val_1.fq.gz
EPI-127_S33_L005_R2_001_val_2.fq.gz  EPI-193_S22_L003_R2_001_val_2.fq.gz
EPI-128_S34_L005_R1_001_val_1.fq.gz  EPI-194_S23_L003_R1_001_val_1.fq.gz
EPI-128_S34_L005_R2_001_val_2.fq.gz  EPI-194_S23_L003_R2_001_val_2.fq.gz
EPI-135_S35_L005_R1_001_val_1.fq.gz  EPI-199_S24_L003_R1_001_val_1.fq.gz
EPI-135_S35_L005_R2_001_val_2.fq.gz  EPI-199_S24_L003_R2_001_val_2.fq.gz
EPI-136_S36_L005_R1_001_val_1.fq.gz  EPI-200_S25_L003_R1_001_val_1.fq.gz
EPI-136_S36_L005_R2_001_val_2.fq.gz  EPI-200_S25_L003_R2_001_val_2.fq.gz
EPI-143_S37_L005_R1_001_val_1.fq.gz  EPI-205_S26_L004_R1_001_val_1.fq.gz
EPI-143_S37_L005_R2_001_val_2.fq.gz  EPI-205_S26_L004_R2_001_val_2.fq.gz
EPI-145_S38_L005_R1_001_val_1.fq.gz  EPI-206_S27_L004_R1_001_val_1.fq.gz
EPI-145_S38_L005_R2_001_val_2.fq.gz  EPI-206_S27_L004_R2_001_val_2.fq.gz
EPI-151_S2_L002_R1_001_val_1.fq.gz   EPI-208_S28_L004_R1_001_val_1.fq.gz
EPI-151_S2_L002_R2_001_val_2.fq.gz   EPI-208_S28_L004_R2_001_val_2.fq.gz
EPI-152_S3_L002_R1_001_val_1.fq.gz   EPI-209_S29_L004_R1_001_val_1.fq.gz
EPI-152_S3_L002_R2_001_val_2.fq.gz   EPI-209_S29_L004_R2_001_val_2.fq.gz
EPI-153_S4_L002_R1_001_val_1.fq.gz   EPI-214_S30_L004_R1_001_val_1.fq.gz
EPI-153_S4_L002_R2_001_val_2.fq.gz   EPI-214_S30_L004_R2_001_val_2.fq.gz
EPI-154_S5_L002_R1_001_val_1.fq.gz   EPI-215_S31_L004_R1_001_val_1.fq.gz
EPI-154_S5_L002_R2_001_val_2.fq.gz   EPI-215_S31_L004_R2_001_val_2.fq.gz
EPI-159_S6_L002_R1_001_val_1.fq.gz   EPI-220_S32_L004_R1_001_val_1.fq.gz
EPI-159_S6_L002_R2_001_val_2.fq.gz   EPI-220_S32_L004_R2_001_val_2.fq.gz
EPI-160_S7_L002_R1_001_val_1.fq.gz   EPI-221_S33_L004_R1_001_val_1.fq.gz
EPI-160_S7_L002_R2_001_val_2.fq.gz   EPI-221_S33_L004_R2_001_val_2.fq.gz
EPI-161_S8_L002_R1_001_val_1.fq.gz   EPI-226_S34_L004_R1_001_val_1.fq.gz
EPI-161_S8_L002_R2_001_val_2.fq.gz   EPI-226_S34_L004_R2_001_val_2.fq.gz
EPI-162_S9_L002_R1_001_val_1.fq.gz   EPI-227_S35_L004_R1_001_val_1.fq.gz
EPI-162_S9_L002_R2_001_val_2.fq.gz   EPI-227_S35_L004_R2_001_val_2.fq.gz
EPI-167_S10_L002_R1_001_val_1.fq.gz  EPI-229_S36_L004_R1_001_val_1.fq.gz
EPI-167_S10_L002_R2_001_val_2.fq.gz  EPI-229_S36_L004_R2_001_val_2.fq.gz
EPI-168_S11_L002_R1_001_val_1.fq.gz  EPI-230_S37_L004_R1_001_val_1.fq.gz
EPI-168_S11_L002_R2_001_val_2.fq.gz  EPI-230_S37_L004_R2_001_val_2.fq.gz
EPI-169_S12_L002_R1_001_val_1.fq.gz  EPI-41_S38_L005_R1_001_val_1.fq.gz
EPI-169_S12_L002_R2_001_val_2.fq.gz  EPI-41_S38_L005_R2_001_val_2.fq.gz
EPI-170_S13_L002_R1_001_val_1.fq.gz  EPI-42_S39_L005_R1_001_val_1.fq.gz
EPI-170_S13_L002_R2_001_val_2.fq.gz  EPI-42_S39_L005_R2_001_val_2.fq.gz
EPI-175_S14_L003_R1_001_val_1.fq.gz  EPI-43_S40_L005_R1_001_val_1.fq.gz
EPI-175_S14_L003_R2_001_val_2.fq.gz  EPI-43_S40_L005_R2_001_val_2.fq.gz
EPI-176_S15_L003_R1_001_val_1.fq.gz  EPI-44_S41_L005_R1_001_val_1.fq.gz
EPI-176_S15_L003_R2_001_val_2.fq.gz  EPI-44_S41_L005_R2_001_val_2.fq.gz
```

## Each lane was aligned separately...

Here is the script for lane 002

```
[sr320@mox2 2019]$ cat 0806_1200.sh
#!/bin/bash
## Job Name
#SBATCH --job-name=gd-002
## Allocation Definition
#SBATCH --account=coenv
#SBATCH --partition=coenv
## Resources
## Nodes (We only get 1, so this is fixed)
#SBATCH --nodes=1
## Walltime (days-hours:minutes:seconds format)
#SBATCH --time=06-00:00:00
## Memory per node
#SBATCH --mem=100G
#SBATCH --mail-type=ALL
#SBATCH --mail-user=sr320@uw.edu
## Specify the working directory for this job
#SBATCH --workdir=/gscratch/scrubbed/sr320/0807/



# Directories and programs
bismark_dir="/gscratch/srlab/programs/Bismark-0.21.0"
bowtie2_dir="/gscratch/srlab/programs/bowtie2-2.3.4.1-linux-x86_64/"
samtools="/gscratch/srlab/programs/samtools-1.9/samtools"
reads_dir="/gscratch/srlab/strigg/data/Pgenr/FASTQS/"



source /gscratch/srlab/programs/scripts/paths.sh




find ${reads_dir}*_L002_R1_001_val_1.fq.gz \
| xargs basename -s _L002_R1_001_val_1.fq.gz | xargs -I{} ${bismark_dir}/bismark \
--path_to_bowtie ${bowtie2_dir} \
-genome /gscratch/srlab/sr320/data/geoduck/v074 \
-p 4 \
-score_min L,0,-0.6 \
-1 /gscratch/srlab/strigg/data/Pgenr/FASTQS/{}_L002_R1_001_val_1.fq.gz \
-2 /gscratch/srlab/strigg/data/Pgenr/FASTQS/{}_L002_R2_001_val_2.fq.gz \



find *.bam | \
xargs basename -s .bam | \
xargs -I{} ${bismark_dir}/deduplicate_bismark \
--bam \
--paired \
{}.bam



${bismark_dir}/bismark_methylation_extractor \
--bedGraph --counts --scaffolds \
--multicore 14 \
--buffer_size 75% \
*deduplicated.bam



# Bismark processing report

${bismark_dir}/bismark2report

#Bismark summary report

${bismark_dir}/bismark2summary



# Sort files for methylkit and IGV

find *deduplicated.bam | \
xargs basename -s .bam | \
xargs -I{} ${samtools} \
sort --threads 28 {}.bam \
-o {}.sorted.bam

# Index sorted files for IGV
# The "-@ 16" below specifies number of CPU threads to use.

find *.sorted.bam | \
xargs basename -s .sorted.bam | \
xargs -I{} ${samtools} \
index -@ 28 {}.sorted.bam
```
---

With respective scripts for [L003](https://d.pr/n/his3i5), [L004](https://d.pr/n/Mq7lY2), and [L005](https://d.pr/n/f7UXSy) available for review.

Lane | output directory |
-----|------------------|
002 | https://gannet.fish.washington.edu/seashell/bu-mox/scrubbed/0807/ |
003 | https://gannet.fish.washington.edu/seashell/bu-mox/scrubbed/0807-003/ |
004 | https://gannet.fish.washington.edu/seashell/bu-mox/scrubbed/0807-004/ |
005 | https://gannet.fish.washington.edu/seashell/bu-mox/scrubbed/0809-005/

___

### OK! but how do I download only the deduplicated sorted bams?


```
wget -r \
--no-directories --no-parent \
-P path/to/local/directory \
-A deduplicated.sorted.bam https://gannet.fish.washington.edu/seashell/bu-mox/scrubbed/0807/
```
```
wget -r \
--no-directories --no-parent \
-P path/to/local/directory \
-A deduplicated.sorted.bam https://gannet.fish.washington.edu/seashell/bu-mox/scrubbed/0807-003/
```
```
wget -r \
--no-directories --no-parent \
-P path/to/local/directory \
-A deduplicated.sorted.bam https://gannet.fish.washington.edu/seashell/bu-mox/scrubbed/0807-004/
```
```
wget -r \
--no-directories --no-parent \
-P path/to/local/directory \
-A deduplicated.sorted.bam https://gannet.fish.washington.edu/seashell/bu-mox/scrubbed/0809-005/
```

(Yes you need to edit `path/to/local/directory`)
