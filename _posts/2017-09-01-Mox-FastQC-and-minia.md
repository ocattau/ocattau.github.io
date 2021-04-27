Playing around a bit with Mox (crippled by lack of disk space).
Ran FastQC

```
#!/bin/bash
## Job Name
#SBATCH --job-name=fastqc-NS
## Allocation Definition 
#SBATCH --account=srlab
#SBATCH --partition=srlab
## Resources
## Nodes (We only get 1, so this is fixed)
#SBATCH --nodes=1   
## Walltime (days-hours:minutes:seconds format)
#SBATCH --time=24:00:00
## Memory per node
#SBATCH --mem=500G
## Specify the working directory for this job
#SBATCH --workdir=/gscratch/srlab/sr320/analyses/0901

 
source /gscratch/srlab/programs/scripts/paths.sh

/gscratch/srlab/programs/FastQC/fastqc \
-t 28 \
/gscratch/scrubbed/sr320/AD002_S9_L001_R1_001.fastq.gz 

```

and minia (note location)

```
#!/bin/bash
## Job Name
#SBATCH --job-name=minia
## Allocation Definition 
#SBATCH --account=srlab
#SBATCH --partition=srlab
## Resources
## Nodes (We only get 1, so this is fixed)
#SBATCH --nodes=1   
## Walltime (days-hours:minutes:seconds format)
#SBATCH --time=100:00:00
## Memory per node
#SBATCH --mem=500G
## Specify the working directory for this job
#SBATCH --workdir=/gscratch/srlab/sr320/analyses/0901b

 
source /gscratch/srlab/programs/scripts/paths.sh

/gscratch/srlab/sr320/programs/minia-v2.0.7-bin-Linux/bin/minia \
-nb-cores 28 \
-max-memory 500000 \
-in /gscratch/scrubbed/sr320/AD002_S9_L001_R2_001.fastq.gz \
-out-dir /gscratch/scrubbed/sr320/
```

minia seems to create a lot of temporary files (probably could have wrote to `scrubbed`) 

```
[sr320@mox1 0901b]$ ls
slurm-71843.out			       trashme_32333_dsk_partitions.parts.20  trashme_32333_dsk_partitions.parts.34  trashme_32333_dsk_partitions.parts.48
slurm-71844.out			       trashme_32333_dsk_partitions.parts.21  trashme_32333_dsk_partitions.parts.35  trashme_32333_dsk_partitions.parts.49
trashme_32333_dsk_partitions.parts.0   trashme_32333_dsk_partitions.parts.22  trashme_32333_dsk_partitions.parts.36  trashme_32333_dsk_partitions.parts.5
trashme_32333_dsk_partitions.parts.1   trashme_32333_dsk_partitions.parts.23  trashme_32333_dsk_partitions.parts.37  trashme_32333_dsk_partitions.parts.50
trashme_32333_dsk_partitions.parts.10  trashme_32333_dsk_partitions.parts.24  trashme_32333_dsk_partitions.parts.38  trashme_32333_dsk_partitions.parts.51
trashme_32333_dsk_partitions.parts.11  trashme_32333_dsk_partitions.parts.25  trashme_32333_dsk_partitions.parts.39  trashme_32333_dsk_partitions.parts.52
trashme_32333_dsk_partitions.parts.12  trashme_32333_dsk_partitions.parts.26  trashme_32333_dsk_partitions.parts.4   trashme_32333_dsk_partitions.parts.53
trashme_32333_dsk_partitions.parts.13  trashme_32333_dsk_partitions.parts.27  trashme_32333_dsk_partitions.parts.40  trashme_32333_dsk_partitions.parts.54
trashme_32333_dsk_partitions.parts.14  trashme_32333_dsk_partitions.parts.28  trashme_32333_dsk_partitions.parts.41  trashme_32333_dsk_partitions.parts.55
trashme_32333_dsk_partitions.parts.15  trashme_32333_dsk_partitions.parts.29  trashme_32333_dsk_partitions.parts.42  trashme_32333_dsk_partitions.parts.6
trashme_32333_dsk_partitions.parts.16  trashme_32333_dsk_partitions.parts.3   trashme_32333_dsk_partitions.parts.43  trashme_32333_dsk_partitions.parts.7
trashme_32333_dsk_partitions.parts.17  trashme_32333_dsk_partitions.parts.30  trashme_32333_dsk_partitions.parts.44  trashme_32333_dsk_partitions.parts.8
trashme_32333_dsk_partitions.parts.18  trashme_32333_dsk_partitions.parts.31  trashme_32333_dsk_partitions.parts.45  trashme_32333_dsk_partitions.parts.9
trashme_32333_dsk_partitions.parts.19  trashme_32333_dsk_partitions.parts.32  trashme_32333_dsk_partitions.parts.46
trashme_32333_dsk_partitions.parts.2   trashme_32333_dsk_partitions.parts.33  trashme_32333_dsk_partitions.parts.47
[sr320@mox1 0901b]$ tail slurm-71844.out 
[DSK: Collecting stats on AD002_S9_L... ]  100  %   elapsed:   0 min 47 sec    estimated remaining:   0 min 0  sec   cpu:  243.5 %   mem: [  73,   73,   73] MB 
[DSK: Pass 1/1, Step 2: counting kmers  ]  82.8 %   elapsed:  17 min 8  sec    estimated remaining:   3 min 34 sec   cpu:  368.9 %   mem: [43863, 43863, 43865] MB
```


---
slurm tail 

```
minia                                   
    -nb-cores                                : 28
    -max-memory                              : 500000
    -in                                      : /gscratch/scrubbed/sr320/AD002_S9_L001_R2_001.fastq.gz
    -out-dir                                 : /gscratch/scrubbed/sr320/
    -traversal                               : contig
    -starter                                 : best
    -contig-max-len                          : 10000000
    -bfs-max-depth                           : 500
    -bfs-max-breadth                         : 20
    -fasta-line                              : 0
    -kmer-size                               : 31
    -abundance-min                           : 3
    -abundance-max                           : 4294967295
    -histo-max                               : 10000
    -solidity-kind                           : sum
    -max-disk                                : 0
    -minimizer-type                          : 0
    -minimizer-size                          : 8
    -repartition-type                        : 0
    -bloom                                   : neighbor
    -debloom                                 : cascading
    -debloom-impl                            : minimizer
    -branching-nodes                         : stored
    -topology-stats                          : 0
    -mphf                                    : emphf
    -verbose                                 : 1
    -integer-precision                       : 0
    -verbose                                 : 1
    stats                                   
        traversal                                : contig
        start_selector                           : best
        nb_contigs                               : 8044789
        nb_small_contigs_discarded               : 9241683
        nt_assembled                             : 1160242262
        max_length                               : 5239
        max_length_left                          : 4197
        max_length_right                         : 4855
        debugging traversal stats               
        large breadth                            : 1344
        large depth                              : 135
        marked kmer inside traversal             : 5595051
        traversal ends with dead-ends            : 2587076
        in-branching large depth                 : 2178233
        in-branching large breadth               : 2196283
        in-branching other                       : 3276932
        couldn't validate consensuses            : 154210
    time                                     : 36742.777
        assembly                                 : 36742.777
 ```


and

```
[sr320@mox1 0901b]$ ls
AD002_S9_L001_R2_001.contigs.fa  slurm-71843.out  slurm-71844.out
[sr320@mox1 0901b]$ head AD002_S9_L001_R2_001.contigs.fa 
>0__len__91
AAAAAAAAAAAAAAAAAAAAAAAAAACCTCACAAGCTTTGACATATTAATGTTACACTTATTGGTGTACTTAAAAGAAATTACTAGTATAC
>1__len__126
AAAAAAAAAAAAAAAAAAAAAAAAAAACTGCCAGCCAATTAACACAAATTTATAAAATATAATCAGTGACTTAATACATGGGATAGATACGGTGACATTAAGGGATGTGTATTCAGAGCTGTCAAT
>2__len__461
AAAAAAAAAAAAAAAAAAAAAAAAAACGATTTCAGATTGAAATGTAAATATGTTAAGATGCAGCATATTATTTCACATCAACATAAGGTCAAACCTTTGGCAGGTTCGACATGATGATTAATCAAAATATGTTTTGAAATGTATATATACAGGTAACATTGGGTTTATATATATAAACATAATTAAACCCAATGTTGTTGTCTGAAATTCCGGGACTTAGATAAAACAAAAGTTGTATATTTTCCACAGTGAACTATGGTAAAATGGTAAAAACATACATCTTTCTTATTCTTACAGTCCATGGTTGGATTTCTCCATCTTCTTCAAATGGAAATAGAATATATCGTCCTTTTAAAAGTATTATCCTGTACTTTTACAAATCAGACACAATTCATACTTCCGCTCGTCCTCGGTAACAGTTCTTTGTAATAGTGTTACTACTGTCCTTCCTAAAAAAGAAA
>3__len__84
AAAAAAAAAAAAAAAAAAAAAAAAAACGTTGACAAATATGAAAGCAGCATTTTTTCAAATAAAAGCACTGTTTGTCTAGTTAAA
>4__len__101
AAAAAAAAAAAAAAAAAAAAAAAAAATCGGAAAAATACTAATTTCGAAAATTAAAAGGAATGTTAAGGGGCGTGTTAGTTATAACAGCGGAAAAGGTTTCT
```
