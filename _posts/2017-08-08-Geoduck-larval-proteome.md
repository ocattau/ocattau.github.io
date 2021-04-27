Deduced protein sequences for `0804_Pgen_larvae.fasta`


Ran Transdecoder

```
#!/bin/bash
## Job Name
#SBATCH --job-name=Transdecoder
## Allocation Definition 
#SBATCH --account=srlab
#SBATCH --partition=srlab
## Resources
## Nodes (We only get 1, so this is fixed)
#SBATCH --nodes=1   
## Walltime (days-hours:minutes:seconds format)
#SBATCH --time=01:00:00
## Memory per node
#SBATCH --mem=50G
## Specify the working directory for this job
#SBATCH --workdir=/gscratch/srlab/sr320/analyses/0808_1550

 
source /gscratch/srlab/programs/scripts/paths.sh

TransDecoder.LongOrfs \
-t /gscratch/srlab/sr320/analyses/0804_1818/trinity_out_dir/0804_Pgen_larvae.fasta
```

slurm

```
-first extracting base frequencies, we'll need them later.
CMD: /gscratch/srlab/programs/transdecoder/util/compute_base_probs.pl /gscratch/srlab/sr320/analyses/0804_1818/trinity_out_dir/0804_Pgen_larvae.fasta 0 > 0804_Pgen_larvae.fasta.transdecoder_dir/base_freqs.dat
CMD: touch 0804_Pgen_larvae.fasta.transdecoder_dir/base_freqs.dat.ok


- extracting ORFs from transcripts.
-total transcripts to examine: 219698
[219600/219698] = 99.96% done    

#################################
### Done preparing long ORFs.  ###
##################################

	Use file: 0804_Pgen_larvae.fasta.transdecoder_dir/longest_orfs.pep  for Pfam and/or BlastP searches to enable homology-based coding region identification.

	Then, run TransDecoder.Predict for your final coding region predictions.
  ```
  
  
  
  ---
  
  ```
  
  NAME
    Transdecoder <http://transdecoder.sourceforge.net> - Transcriptome
    Protein Prediction

USAGE
    Required:

     -t <string>                            transcripts.fasta

    Common options:

     --retain_long_orfs <int>               retain all ORFs found that are equal or longer than these many nucleotides even if no other evidence 
                                             marks it as coding (default: 900 bp => 300aa)

     --retain_pfam_hits <string>            domain table output file from running hmmscan to search Pfam (see transdecoder.github.io for info)     
                                            Any ORF with a pfam domain hit will be retained in the final output.
 
     --retain_blastp_hits <string>          blastp output in '-outfmt 6' format.
                                            Any ORF with a blast match will be retained in the final output.

     --single_best_orf                      Retain only the single best ORF per transcript.
                                            (Best is defined as having (optionally pfam and/or blast support) and longest orf)

     --cpu <int>                            Use multiple cores for cd-hit-est. (default=1)

     -G <string>                            genetic code (default: universal; see PerlDoc; options: Euplotes, Tetrahymena, Candida, Acetabularia, ...)

    Advanced options

     --train <string>                       FASTA file with ORFs to train Markov Mod for protein identification; otherwise 
                                            longest non-redundant ORFs used

     -T <int>                               If no --train, top longest ORFs to train Markov Model (hexamer stats) (default: 500)
                                            Note, 10x this value are first selected for use with cd-hit to remove redundancies,
                                            and then this -T value of longest ORFs are selected from the non-redundant set.

Genetic Codes
    See <http://golgi.harvard.edu/biolinks/gencode.html>. These are
    currently supported:

     universal (default)
     Euplotes
     Tetrahymena
     Candida
     Acetabularia
     Mitochondrial-Canonical
     Mitochondrial-Vertebrates
     Mitochondrial-Arthropods
     Mitochondrial-Echinoderms
     Mitochondrial-Molluscs
     Mitochondrial-Ascidians
     Mitochondrial-Nematodes
     Mitochondrial-Platyhelminths
     Mitochondrial-Yeasts
     Mitochondrial-Euascomycetes
     Mitochondrial-Protozoans
     
```     
     
