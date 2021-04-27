Sam has compiled the current status of Olympia oyster genome assemblies [here](http://faculty.washington.edu/sr320/?p=13567). I am going to try to assess differences. 

Metassembler approach seemed not to produce anything.

Canu which is PacBio only, created a fasta post Pilon polishing.
Renaming `oly_polished_.fasta` to `ol-canu-170623.fa` 

Redundans was used on Illumina and PacBio. 2 runs. Try 2 seemed better. 
will take

```
D-173-250-161-130:NewOlyAssembly Sean$ assembly-stats scaffolds.reduced.fa
stats for scaffolds.reduced.fa
sum = 546928670, n = 300593, ave = 1819.50, largest = 78788
N50 = 3852, n = 36149
N60 = 2917, n = 52500
N70 = 2137, n = 74420
N80 = 1455, n = 105359
N90 = 810, n = 155023
N100 = 200, n = 300593
N_count = 5238187
Gaps = 209203
```

renaming `scaffolds.reduced.fa` to `ol-redundans-170608.fa`

---
Taking "BGI" scaffolds and renaming `ol-bgisoap-161129.fa`.

---

Here is what we have

```
791MB Sep  8 08:10 ol-bgisoap-161129.fa
48MB Sep  8 07:49 ol-canu-170623.fa
558MB Sep  8 07:52 ol-redundans-170608.fa
```
to that lets add what we have been using      
`Ostrea_lurida-Scaff-10k.fa` (131.4 MB)


--- 

Running some bsmap
ie 

```
!/Applications/bsmap-2.74/bsmap \
-a zr_1-sub001.fastq \
-d ol-bgisoap-161129.fa \
-o /Volumes/Monarch/wd/17-09-08/bsmap_out_soap-2.sam \
-p 4 \
2> /Volumes/Monarch/wd/17-09-08/stderr_bsmap_soap-2.txt
```

results are as follows

```
ol-bgisoap-161129.fa - 3.1% aligned reads     
ol-canu-170623.fa - 12% aligned reads     
ol-redundans-170608.fa - 2.3% aligned reads    
Ostrea_lurida-Scaff-10k.fa - 6% aligned reads     
```
---
Canu looks good. Would like to know exactly how that was derived. 
Will go ahead and crunch data with Canu- but will examine metaassemblers to see if we can get Canu (PacBio) and Illumina assembly combined.

