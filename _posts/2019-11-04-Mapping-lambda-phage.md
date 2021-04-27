---
layout: post
title: Mapping the spiked lambda phage DNA
date: '2019-11-04'
---

First prepared the genome

```
#!/bin/bash
## Job Name
#SBATCH --job-name=bs-prep
## Allocation Definition
#SBATCH --account=srlab
#SBATCH --partition=srlab
## Resources
## Nodes (We only get 1, so this is fixed)
#SBATCH --nodes=1
## Walltime (days-hours:minutes:seconds format)
#SBATCH --time=0-012:00:00
## Memory per node
#SBATCH --mem=100G
#SBATCH --mail-type=ALL
#SBATCH --mail-user=sr320@uw.edu
## Specify the working directory for this job
#SBATCH --chdir=/gscratch/srlab/sr320/analyses/1104



/gscratch/srlab/programs/Bismark-0.21.0/bismark_genome_preparation \
--verbose \
--parallel 28 \
--path_to_aligner /gscratch/srlab/programs/bowtie2-2.3.4.1-linux-x86_64/ \
/gscratch/srlab/sr320/data/lambda/
```

in genome folder is Genbank Accession number J02459

`ce801fabe7edf85b53dfbe969d36538d  lambda-phage.fasta`

---

```
#!/bin/bash
## Job Name
#SBATCH --job-name=lamb-bs
## Allocation Definition
#SBATCH --account=srlab
#SBATCH --partition=srlab
## Resources
## Nodes (We only get 1, so this is fixed)
#SBATCH --nodes=1
## Walltime (days-hours:minutes:seconds format)
#SBATCH --time=00-18:00:00
## Memory per node
#SBATCH --mem=100G
#SBATCH --mail-type=ALL
#SBATCH --mail-user=sr320@uw.edu
## Specify the working directory for this job
#SBATCH --chdir=/gscratch/scrubbed/sr320/1104/



# Directories and programs
bismark_dir="/gscratch/srlab/programs/Bismark-0.21.0"
bowtie2_dir="/gscratch/srlab/programs/bowtie2-2.3.4.1-linux-x86_64/"
samtools="/gscratch/srlab/programs/samtools-1.9/samtools"
reads_dir="/gscratch/srlab/strigg/data/Pgenr/FASTQS/"



source /gscratch/srlab/programs/scripts/paths.sh




find ${reads_dir}*_L002_R1_001_val_1.fq.gz \
| xargs basename -s _L002_R1_001_val_1.fq.gz | xargs -I{} ${bismark_dir}/bismark \
--path_to_bowtie ${bowtie2_dir} \
-genome /gscratch/srlab/sr320/data/lambda \
-p 4 \
-u 100000 \
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

and ran

`[sr320@mox1 1104]$ cat *txt | grep "C methylated in CpG context:"`

```
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.0%
C methylated in CpG context:	0.9%
C methylated in CpG context:	1.3%
C methylated in CpG context:	1.3%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.3%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.4%
C methylated in CpG context:	1.5%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.3%
C methylated in CpG context:	1.8%
C methylated in CpG context:	1.8%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.0%
C methylated in CpG context:	1.6%
C methylated in CpG context:	1.5%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.0%
```


---

Realizing this was only lane 02 went ahead and redid with all data:

script https://d.pr/n/UHEhvQ

and got an average of `1.174038462` when looking at

```
[sr320@mox1 1104b]$ cat *txt | grep "C methylated in CpG context:"
C methylated in CpG context:	0.9%
C methylated in CpG context:	0.9%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.0%
C methylated in CpG context:	0.9%
C methylated in CpG context:	0.9%
C methylated in CpG context:	0.9%
C methylated in CpG context:	0.9%
C methylated in CpG context:	0.9%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.1%
C methylated in CpG context:	0.9%
C methylated in CpG context:	0.7%
C methylated in CpG context:	1.4%
C methylated in CpG context:	1.4%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.1%
C methylated in CpG context:	0.9%
C methylated in CpG context:	0.9%
C methylated in CpG context:	1.0%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.0%
C methylated in CpG context:	0.9%
C methylated in CpG context:	1.3%
C methylated in CpG context:	1.3%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.3%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.4%
C methylated in CpG context:	1.5%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.3%
C methylated in CpG context:	1.8%
C methylated in CpG context:	1.8%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.0%
C methylated in CpG context:	1.6%
C methylated in CpG context:	1.5%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.0%
C methylated in CpG context:	1.0%
C methylated in CpG context:	0.9%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.0%
C methylated in CpG context:	1.0%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.6%
C methylated in CpG context:	1.6%
C methylated in CpG context:	1.5%
C methylated in CpG context:	1.5%
C methylated in CpG context:	1.4%
C methylated in CpG context:	1.5%
C methylated in CpG context:	1.5%
C methylated in CpG context:	1.4%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.3%
C methylated in CpG context:	1.3%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.5%
C methylated in CpG context:	1.5%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.3%
C methylated in CpG context:	1.6%
C methylated in CpG context:	1.6%
C methylated in CpG context:	1.3%
C methylated in CpG context:	1.3%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.4%
C methylated in CpG context:	1.3%
C methylated in CpG context:	1.2%
C methylated in CpG context:	0.7%
C methylated in CpG context:	0.7%
C methylated in CpG context:	1.3%
C methylated in CpG context:	1.4%
C methylated in CpG context:	0.9%
C methylated in CpG context:	0.9%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.2%
C methylated in CpG context:	1.0%
C methylated in CpG context:	1.0%
C methylated in CpG context:	0.9%
C methylated in CpG context:	1.0%
C methylated in CpG context:	1.1%
C methylated in CpG context:	1.2%
C methylated in CpG context:	0.9%
C methylated in CpG context:	0.9%
```
