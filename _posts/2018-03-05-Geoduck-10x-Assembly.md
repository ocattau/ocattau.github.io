Supernova completed the 10x Chromium data assembly.

via

```
#!/bin/bash
## Job Name
#SBATCH --job-name=sn-all
## Allocation Definition
#SBATCH --account=srlab
#SBATCH --partition=srlab
## Resources
## Nodes (We only get 1, so this is fixed)
#SBATCH --nodes=1
## Walltime (days-hours:minutes:seconds format)
#SBATCH --time=30-100:00:00
## Memory per node
#SBATCH --mem=500G
#SBATCH --mail-type=ALL
#SBATCH --mail-user=sr320@uw.edu
## Specify the working directory for this job
#SBATCH --workdir=/gscratch/scrubbed/sr320/0220

source /gscratch/srlab/programs/scripts/paths.sh



/gscratch/srlab/programs/supernova-2.0.0/supernova run --id=Geoduck \
--fastqs=/gscratch/scrubbed/sr320/Chrom \
--sample=Geoduck-1,Geoduck-2,Geoduck-5,Geoduck-6
```

Oddly here is what is in `Chrom`

```
[sr320@mox1 jobs]$ ls /gscratch/scrubbed/sr320/Chrom
geoduck_10x_genomics_20171220	   Geoduck-2_S2_L005_I1_001.fastq.gz
Geoduck-1_S1_L001_I1_001.fastq.gz  Geoduck-2_S2_L005_R1_001.fastq.gz
Geoduck-1_S1_L001_R1_001.fastq.gz  Geoduck-2_S2_L005_R2_001.fastq.gz
Geoduck-1_S1_L001_R2_001.fastq.gz  Geoduck-2_S2_L006_I1_001.fastq.gz
Geoduck-1_S1_L002_I1_001.fastq.gz  Geoduck-2_S2_L006_R1_001.fastq.gz
Geoduck-1_S1_L002_R1_001.fastq.gz  Geoduck-2_S2_L006_R2_001.fastq.gz
Geoduck-1_S1_L002_R2_001.fastq.gz  Geoduck-2_S2_L007_I1_001.fastq.gz
Geoduck-1_S1_L003_I1_001.fastq.gz  Geoduck-2_S2_L007_R1_001.fastq.gz
Geoduck-1_S1_L003_R1_001.fastq.gz  Geoduck-2_S2_L007_R2_001.fastq.gz
Geoduck-1_S1_L003_R2_001.fastq.gz  Geoduck-2_S2_L008_I1_001.fastq.gz
Geoduck-1_S1_L004_I1_001.fastq.gz  Geoduck-2_S2_L008_R1_001.fastq.gz
Geoduck-1_S1_L004_R1_001.fastq.gz  Geoduck-2_S2_L008_R2_001.fastq.gz
Geoduck-1_S1_L004_R2_001.fastq.gz
``` 

assuming the other files were automatically deleted on 30 day run. (side note: does mv reset 30 days?)

---

`tail` of the slurm

```
Alerts for ID.Geoduck.ASSEMBLER_CS._ASSEMBLER.ASSEMBLER_PR:
The length-weighted mean molecule length is -1.00 bases. If this value is < 0, it means that the molecule length estimation failed. This could be because your input DNA was very short, or because coverage was too low, or some other reason. Check for other alerts, which may be diagnostic. If the predicted value is > 0, the molecule length estimation was successful. However, ideally, we would expect a larger value. Standard methods starting from blood can yield 100 kb or larger DNA, but it can be difficult to obtain long DNA from other sample types. Short molecules may reduce the scaffold and phase block N50 length, and could result in misassemblies. We have observed assembly quality to improve with longer DNA.
We observe that the raw coverage calculated as total bases in untrimmed reads divided by the estimated genome size is 88.16, which is high.  We recommend 56x coverage, and although greater coverage sometimes improves assembly quality, it can also have a deleterious effect, depending on the dataset.


Outputs:
- Run summary:        /gscratch/scrubbed/sr320/0220/Geoduck/outs/summary.csv
- Run report:         /gscratch/scrubbed/sr320/0220/Geoduck/outs/report.txt
- Raw assembly files: /gscratch/scrubbed/sr320/0220/Geoduck/outs/assembly

Alerts:
The length-weighted mean molecule length is -1.00 bases. If this value is < 0, it means that the molecule length estimation failed. This could be because your input DNA was very short, or because coverage was too low, or some other reason. Check for other alerts, which may be diagnostic. If the predicted value is > 0, the molecule length estimation was successful. However, ideally, we would expect a larger value. Standard methods starting from blood can yield 100 kb or larger DNA, but it can be difficult to obtain long DNA from other sample types. Short molecules may reduce the scaffold and phase block N50 length, and could result in misassemblies. We have observed assembly quality to improve with longer DNA.
We observe that the raw coverage calculated as total bases in untrimmed reads divided by the estimated genome size is 88.16, which is high.  We recommend 56x coverage, and although greater coverage sometimes improves assembly quality, it can also have a deleterious effect, depending on the dataset.
We observe only 63.75 pct of bases on read two with quality scores at least 30. Ideally, we expect at least 75 pct. Data quality issues of this type are difficult to diagnose, but might be caused by defects in sequencing reagents or sequencing instrument condition. Use of low quality reads usually reduces assembly quality.


Running onfinish handler...
Waiting 6 seconds for UI to do final refresh.
Pipestance completed successfully!

Saving pipestance info to Geoduck/Geoduck.mri.tgz
```

Geoduck/Geoduck.mri.tgz available       
at      
http://owl.fish.washington.edu/halfshell/bu-mox/analyses/0305/0220_Geoduck.mri.tgz


Report

```
[sr320@mox1 outs]$ cat report.txt 

--------------------------------------------------------------------------------
SUMMARY
--------------------------------------------------------------------------------
- Mon Mar 05 04:11:59 2018
- [Geoduck]  
- software release = 2.0.0(7fba7b4)
- likely sequencers = HiSeq3000/4000
- assembly checksum = -2,318,235,203,015,705,709
--------------------------------------------------------------------------------
INPUT
- 1200.03 M  = READS            = number of reads; ideal 800M-1200M for human
-  139.50  b = MEAN READ LEN    = mean read length after trimming; ideal 140
-   88.16  x = RAW COV          = raw coverage; ideal ~56
-   65.09  x = EFFECTIVE COV    = effective read coverage; ideal ~42 for nominal 56x
-   63.75  % = READ TWO Q30     = fraction of Q30 bases in read 2; ideal 75-85
-  374.00  b = MEDIAN INSERT    = median insert size; ideal 0.35-0.40
-   80.56  % = PROPER PAIRS     = fraction of proper read pairs; ideal >= 75
-    1.00    = BARCODE FRACTION = fraction of barcodes used; between 0 and 1
-    2.06 Gb = EST GENOME SIZE  = estimated genome size
-   16.05  % = REPETITIVE FRAC  = estimated repetitive fraction
-    0.10  % = HIGH AT FRACTION = high AT index
-  219.32    = P10              = molecule count extending 10 kb on both sides
-  150.00  b = HETDIST          = mean distance between heterozygous SNPs
-    6.08  % = UNBAR            = fraction of reads that are not barcoded
-  444.00    = BARCODE N50      = N50 reads per barcode
-   11.58  % = DUPS             = fraction of reads that are duplicates
-   37.42  % = PHASED           = nonduplicate and phased reads; ideal 45-50
--------------------------------------------------------------------------------
OUTPUT
-    9.30 K  = LONG SCAFFOLDS   = number of scaffolds >= 10 kb
-    5.28 Kb = EDGE N50         = N50 edge size
-   14.25 Kb = CONTIG N50       = N50 contig size
-    1.34 Mb = PHASEBLOCK N50   = N50 phase block size
-    1.40 Mb = SCAFFOLD N50     = N50 scaffold size
-   26.47  % = MISSING 10KB     = % of base assembly missing from scaffolds >= 10 kb
-    1.10 Gb = ASSEMBLY SIZE    = assembly size (only scaffolds >= 10 kb)
--------------------------------------------------------------------------------
ALARMS
- We observe only 63.75 pct of bases on read two with quality scores at least
30. Ideally, we expect at least 75 pct. Data quality issues of this type are
difficult to diagnose, but might be caused by defects in sequencing reagents or
sequencing instrument condition. Use of low quality reads usually reduces
assembly quality.
- The length-weighted mean molecule length is -1.00 bases. If this value is < 0,
it means that the molecule length estimation failed. This could be because your
input DNA was very short, or because coverage was too low, or some other reason.
Check for other alerts, which may be diagnostic. If the predicted value is > 0,
the molecule length estimation was successful. However, ideally, we would expect
a larger value. Standard methods starting from blood can yield 100 kb or larger
DNA, but it can be difficult to obtain long DNA from other sample types. Short
molecules may reduce the scaffold and phase block N50 length, and could result
in misassemblies. We have observed assembly quality to improve with longer DNA.
- We observe that the raw coverage calculated as total bases in untrimmed reads
divided by the estimated genome size is 88.16, which is high.  We recommend 56x
coverage, and although greater coverage sometimes improves assembly quality, it
can also have a deleterious effect, depending on the dataset.
--------------------------------------------------------------------------------
```


in `_finalstate` file we do see all 4 files represented

```
     "barcode": null,
                                    "barcode_reverse_complement": false,
                                    "bc_in_read": 1,
                                    "bc_length": 16,
                                    "gem_group": 1,
                                    "read1": "/gscratch/scrubbed/sr320/Chrom/Geoduck-2_S2_L008_R1_001.fastq.gz",
                                    "read2": "/gscratch/scrubbed/sr320/Chrom/Geoduck-2_S2_L008_R2_001.fastq.gz",
                                    "read_group": "Geoduck:None:1:HM2JYBBXX:8",
                                    "reads_interleaved": false,
                                    "sample_index": "/gscratch/scrubbed/sr320/Chrom/Geoduck-2_S2_L008_I1_001.fastq.gz",
                                    "subsample_rate": 0.15334852921202502
                                },
                                {
                                    "barcode": null,
                                    "barcode_reverse_complement": false,
                                    "bc_in_read": 1,
                                    "bc_length": 16,
                                    "gem_group": 1,
                                    "read1": "/gscratch/scrubbed/sr320/Chrom/Geoduck-5_S1_L001_R1_001.fastq.gz",
                                    "read2": "/gscratch/scrubbed/sr320/Chrom/Geoduck-5_S1_L001_R2_001.fastq.gz",
                                    "read_group": "Geoduck:None:1:HN3JCBBXX:1",
                                    "reads_interleaved": false,
                                    "sample_index": "/gscratch/scrubbed/sr320/Chrom/Geoduck-5_S1_L001_I1_001.fastq.gz",
                                    "subsample_rate": 0.15334852921202502
                                },
                                {
                                    "barcode": null,
                                    "barcode_reverse_complement": false,
                                    "bc_in_read": 1,
                                    "bc_length": 16,
                                    "gem_group": 1,
                                    "read1": "/gscratch/scrubbed/sr320/Chrom/Geoduck-5_S1_L002_R1_001.fastq.gz",
                                    "read2": "/gscratch/scrubbed/sr320/Chrom/Geoduck-5_S1_L002_R2_001.fastq.gz",
                                    "read_group": "Geoduck:None:1:HN3JCBBXX:2",
                                    "reads_interleaved": false,
                                    "sample_index": "/gscratch/scrubbed/sr320/Chrom/Geoduck-5_S1_L002_I1_001.fastq.gz",
                                    "subsample_rate": 0.15334852921202502
                                },
                                {
```


I am going to assume all four groups of data were assembled

---

Ran `mkoutput`
```
#!/bin/bash
## Job Name
#SBATCH --job-name=super-duck1
## Allocation Definition
#SBATCH --account=srlab
#SBATCH --partition=srlab
## Resources
## Nodes (We only get 1, so this is fixed)
#SBATCH --nodes=1
## Walltime (days-hours:minutes:seconds format)
#SBATCH --time=10-100:00:00
## Memory per node
#SBATCH --mem=500G
#SBATCH --mail-type=ALL
#SBATCH --mail-user=sr320@uw.edu
## Specify the working directory for this job
#SBATCH --workdir=/gscratch/srlab/sr320/analyses/0305





source /gscratch/srlab/programs/scripts/paths.sh


/gscratch/srlab/programs/supernova-2.0.0/supernova mkoutput \
        --asmdir=/gscratch/scrubbed/sr320/0220/Geoduck/outs/assembly \
        --outprefix=/gscratch/srlab/sr320/analyses/0305/duck4 \
        --style=pseudohap2
```


Then reran with `--minsize=10000`

```
 /gscratch/srlab/programs/supernova-2.0.0/supernova mkoutput \
        --asmdir=/gscratch/scrubbed/sr320/0220/Geoduck/outs/assembly \
        --outprefix=/gscratch/srlab/sr320/analyses/0305/duck4-10k \
        --style=pseudohap2 \
        --minsize=10000  
```    

All fasta outputs can be accessed
at
http://owl.fish.washington.edu/halfshell/bu-mox/analyses/0305/    

---

fu: Assembly out available:http://owl.fish.washington.edu/halfshell/working-directory/18-03-05/
