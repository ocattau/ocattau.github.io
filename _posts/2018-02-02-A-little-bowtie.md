
Running some alignments for Charlie.

He provided a lot of files (1228 individual PEs) and wanted them aligned to the Chinook genome.

Here is the code - file: 0202_1300.sh 

```
#!/bin/bash
## Job Name
#SBATCH --job-name=supernova
## Allocation Definition
#SBATCH --account=srlab
#SBATCH --partition=srlab
## Resources
## Nodes (We only get 1, so this is fixed)
#SBATCH --nodes=1
## Walltime (days-hours:minutes:seconds format)
#SBATCH --time=5-100:00:00
## Memory per node
#SBATCH --mem=500G
#SBATCH --mail-type=ALL
#SBATCH --mail-user=sr320@uw.edu
## Specify the working directory for this job
## Specify the working directory for this job
#SBATCH --workdir=/gscratch/scrubbed/sr320/cw/out/analyses

source /gscratch/srlab/programs/scripts/paths.sh


for fastq in /gscratch/scrubbed/sr320/cw/*1.fq.gz; do
  read1=$(echo "$fastq")
  read1_array+=("$read1")
done

for fastq in /gscratch/scrubbed/sr320/cw/*2.fq.gz; do
  read2=$(echo "$fastq")
  read2_array+=("$read2")
done

for pair in "${!read1_array[@]}"; do
  i=${read1_array[$pair]}
  j=${read2_array[$pair]}
  filename="${i##*/}"
  no_ext="${filename%%.*}"
  bowtie2 -x \
  /gscratch/scrubbed/sr320/cw/chinook_genome \
  -1 "$i" \
  -2 "$j" \
  -X 2000 --sensitive  --no-mixed --phred33 --no-discordant --no-unal \
  -S /gscratch/scrubbed/sr320/cw/out/"$no_ext"_bowtie2.sam \
  -q \
  -p 28
done
```

Getting about 80% alignment...   - 
slurmout = 

ie 
```
1544741 reads; of these:
  1544741 (100.00%) were paired; of these:
    292538 (18.94%) aligned concordantly 0 times
    886846 (57.41%) aligned concordantly exactly 1 time
    365357 (23.65%) aligned concordantly >1 times
81.06% overall alignment rate
5852048 reads; of these:
  5852048 (100.00%) were paired; of these:
    1126206 (19.24%) aligned concordantly 0 times
    2875283 (49.13%) aligned concordantly exactly 1 time
    1850559 (31.62%) aligned concordantly >1 times
80.76% overall alignment rate
2886233 reads; of these:
  2886233 (100.00%) were paired; of these:
    504916 (17.49%) aligned concordantly 0 times
    1711280 (59.29%) aligned concordantly exactly 1 time
    670037 (23.21%) aligned concordantly >1 times
82.51% overall alignment rate
1803868 reads; of these:
  1803868 (100.00%) were paired; of these:
    327550 (18.16%) aligned concordantly 0 times
    1054310 (58.45%) aligned concordantly exactly 1 time
    422008 (23.39%) aligned concordantly >1 times
81.84% overall alignment rate
6894097 reads; of these:
  6894097 (100.00%) were paired; of these:
    1296960 (18.81%) aligned concordantly 0 times
    3420356 (49.61%) aligned concordantly exactly 1 time
    2176781 (31.57%) aligned concordantly >1 times
81.19% overall alignment rate
824935 reads; of these:
  824935 (100.00%) were paired; of these:
    161138 (19.53%) aligned concordantly 0 times
    467760 (56.70%) aligned concordantly exactly 1 time
    196037 (23.76%) aligned concordantly >1 times
80.47% overall alignment rate
2599640 reads; of these:
  2599640 (100.00%) were paired; of these:
    495137 (19.05%) aligned concordantly 0 times
    1490671 (57.34%) aligned concordantly exactly 1 time
    613832 (23.61%) aligned concordantly >1 times
80.95% overall alignment rate
6435979 reads; of these:
  6435979 (100.00%) were paired; of these:
    1216238 (18.90%) aligned concordantly 0 times
    3185887 (49.50%) aligned concordantly exactly 1 time
    2033854 (31.60%) aligned concordantly >1 times
81.10% overall alignment rate
```

SAM outputs are available in almost real-time @        
http://owl.fish.washington.edu/halfshell/bu-mox/scrubbed/


---
In terms of speed -        
31 alignments have been completed in 2 hours.       
Thus it should take about 40 hours....          

