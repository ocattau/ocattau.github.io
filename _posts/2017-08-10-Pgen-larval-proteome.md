
Using the [Trandsdecoder](https://github.com/TransDecoder/TransDecoder/wiki) and the [Trinity assembly](https://sr320.github.io/Geoduck-larval-transcriptome/), a deduced proteome was generated.


In Jupyter...

1. extract the long open reading frames
```
!/Applications/bioinfo/TransDecoder-4.0.0/TransDecoder.LongOrfs \
-t $fa \
-S 
```

2. Optionally, identify ORFs with homology to known proteins via blast (Mox)

```
#!/bin/bash
## Job Name
#SBATCH --job-name=blastx
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
#SBATCH --workdir=/gscratch/srlab/sr320/analyses/0810_1100

 
source /gscratch/srlab/programs/scripts/paths.sh

/gscratch/srlab/programs/ncbi-blast-2.6.0+/bin/blastp \
-query \
/gscratch/srlab/sr320/data/PgenlarS-longest_orfs.pep \
-db \
/gscratch/srlab/sr320/blastdb/uniprot_sprot_080917 \
-out \
/gscratch/srlab/sr320/analyses/0810_1100/blastout \
-num_threads 28 \
-evalue 1E-05 \
-max_target_seqs 1 \
-outfmt 6 
```

Blastout: `http://owl.fish.washington.edu/halfshell/bu-mox/analyses/0810_1100/blastout`

3. predict the likely coding regions
```
!/Applications/bioinfo/TransDecoder-4.0.0/TransDecoder.Predict \
-t $fa \
--retain_blastp_hits blastout
```

_[output files explained](https://github.com/TransDecoder/TransDecoder/wiki#output-files-explained)_

**peptide sequences for the final candidate ORFs; all shorter candidates within longer ORFs were removed:**
`http://owl.fish.washington.edu/halfshell/bu-alanine-wd/17-08-10/0804_Pgen_larvae.fasta.transdecoder.pep`

Linkouts:      
Jupyter nb w/o stranded or blast integration - [here](https://github.com/sr320/nb-2017/blob/master/P_generosa/25-Larval-transcriptome.ipynb)              
    - corresponding Alanine wd [17-08-09](http://owl.fish.washington.edu/halfshell/bu-alanine-wd/17-08-09/)     
Jupyter nb w Stranded and blast integration - [here](https://github.com/sr320/nb-2017/blob/master/P_generosa/26-Larval-ded-Proteome.ipynb)    
    - corresponding Alanine wd [17-08-10](http://owl.fish.washington.edu/halfshell/bu-alanine-wd/17-08-10/)    

