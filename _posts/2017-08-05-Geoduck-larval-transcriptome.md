In preparation for new proteomic analysis here is a transcriptome from the _NovaSeq_.

What I ran on Hyak.

```
#!/bin/bash
## Job Name
#SBATCH --job-name=Geoduck-trinity-01
## Allocation Definition 
#SBATCH --account=srlab
#SBATCH --partition=srlab
## Resources
## Nodes (We only get 1, so this is fixed)
#SBATCH --nodes=1   
## Walltime (days-hours:minutes:seconds format)
#SBATCH --time=90:30:00
## Memory per node
#SBATCH --mem=500G
## Specify the working directory for this job
#SBATCH --workdir=/gscratch/srlab/sr320/analyses/0804_1818

 
source /gscratch/srlab/programs/scripts/paths.sh

Trinity \
--seqType fq \
--SS_lib_type RF \
--left /gscratch/srlab/sr320/data/NR021_S8_L001_R1_001.fastq,/gscratch/srlab/sr320/data/NR021_S8_L002_R1_001.fastq \
--right /gscratch/srlab/sr320/data/NR021_S8_L001_R2_001.fastq,/gscratch/srlab/sr320/data/NR021_S8_L002_R2_001.fastq \
--CPU 50 --trimmomatic --max_memory 500G
```

The [slurm](http://owl.fish.washington.edu/halfshell/bu-mox/analyses/0804_1818/slurm-54893.out). This is what would be spit out in terminal while running. With Trinity, there is a lot. 


The fasta file (179M).

`http://owl.fish.washington.edu/halfshell/bu-mox/analyses/0804_1818/trinity_out_dir/0804_Pgen_larvae.fasta`

If you want to see the rest of the output [look here](http://owl.fish.washington.edu/halfshell/bu-mox/analyses/0804_1818/trinity_out_dir/).


```
[sr320@mox2 util]$ perl TrinityStats.pl /gscratch/srlab/sr320/analyses/0804_1818/trinity_out_dir/0804_Pgen_larvae.fasta 


################################
## Counts of transcripts, etc.
################################
Total trinity 'genes':	145131
Total trinity transcripts:	219698
Percent GC: 36.30

########################################
Stats based on ALL transcript contigs:
########################################

	Contig N10: 2651
	Contig N20: 1765
	Contig N30: 1263
	Contig N40: 921
	Contig N50: 676

	Median contig length: 331
	Average contig: 533.78
	Total assembled bases: 117271312


#####################################################
## Stats based on ONLY LONGEST ISOFORM per 'GENE':
#####################################################

	Contig N10: 2384
	Contig N20: 1541
	Contig N30: 1090
	Contig N40: 791
	Contig N50: 592

	Median contig length: 324
	Average contig: 500.45
	Total assembled bases: 72630419


```

