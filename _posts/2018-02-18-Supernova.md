About a week ago I started a Supernova 2.0 run to get some of this Chromium 10x data assembled.

Today I got the following exit error.

```
2018-02-17 23:54:55 [runtime] (update)          ID.Geoduck.ASSEMBLER_CS._ASSEMBLER.ASSEMBLER_PR.fork0 chunks_running
2018-02-18 00:00:53 [runtime] (update)          ID.Geoduck.ASSEMBLER_CS._ASSEMBLER.ASSEMBLER_PR.fork0 chunks_running
2018-02-18 00:04:08 [runtime] (failed)          ID.Geoduck.ASSEMBLER_CS._ASSEMBLER.ASSEMBLER_PR

Running onfinish handler...

[error] An unexpected error has occurred.

The following warning(s) were issued prior to encountering an error:


The length-weighted mean molecule length is 16652.62 bases. If this value is < 0, it means that the molecule length estimation failed. This could be because your input DNA was very short, or because coverage was too low, or some other reason. Check for other alerts, which may be diagnostic. If the predicted value is > 0, the molecule length estimation was successful. However, ideally, we would expect a larger value. Standard methods starting from blood can yield 100 kb or larger DNA, but it can be difficult to obtain long DNA from other sample types. Short molecules may reduce the scaffold and phase block N50 length, and could result in misassemblies. We have observed assembly quality to improve with longer DNA.


Saving pipestance info to Geoduck/Geoduck.mri.tgz
For assistance, upload this file to 10x Genomics by running:

supernova upload <your_email> Geoduck/Geoduck.mri.tgz
```
tldr:    
The length-weighted mean molecule length is 16652.62 bases   ...   
If the predicted value is > 0, the molecule length estimation was successful.     
However, ideally, we would expect a larger value.     
Standard methods starting from blood can yield 100 kb or larger DNA


The job script ...

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
#SBATCH --time=30-100:00:00
## Memory per node
#SBATCH --mem=500G
#SBATCH --mail-type=ALL
#SBATCH --mail-user=sr320@uw.edu
## Specify the working directory for this job
#SBATCH --workdir=/gscratch/scrubbed/sr320/0206

source /gscratch/srlab/programs/scripts/paths.sh



/gscratch/srlab/programs/supernova-2.0.0/supernova run --id=Geoduck \
--fastqs=/gscratch/scrubbed/sr320/Chrom/geoduck_10x_genomics_20171220/HM2JYBBXX/outs/fastq_path \
--sample=Geoduck-1,Geoduck-2
```

I will send the mri file to support but also try to restart assembly with all data.
Will also follow up exploring the assemblies we have and how to make fasta...
