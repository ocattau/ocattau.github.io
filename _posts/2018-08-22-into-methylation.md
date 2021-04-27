---
layout: post
title: Getting into DNA Methylation
date: '2018-08-23'
---


I have to share some information with several new folks, and there are likely old folks that should give this a refresh… thus I am posting it here. 

## What to read
A good place to start in term of biology are a few reviews including

- Gavery, M., & Roberts, S. (2018). Genetics & Epigenetics in Life History and Reproduction: Oysters. In M. K. Skinner (Ed.), Encyclopedia of Reproduction. vol. 6, pp. 736–742. Academic Press: Elsevier. http://dx.doi.org/10.1016/B978-0-12-809633-8.20621-3 : [pdf](http://eagle.fish.washington.edu/whale/pub/C20621.pdf)
- Gavery MR, Roberts SB. (2017) Epigenetic considerations in aquaculture. PeerJ 5:e4147 https://doi.org/10.7717/peerj.4147
- Mackenzie R. Gavery, Steven B. Roberts; A context dependent role for DNA methylation in bivalves, Briefings in Functional Genomics, Volume 13, Issue 3, 1 May 2014, Pages 217–222, https://doi.org/10.1093/bfgp/elt054

Some good primary papers include

- Dimond JL, Gamblewood SK, Roberts SB. (2017) Genetic and epigenetic insight into morphospecies in a reef coral Molecular Ecology. 00:1–12. doi: [10.1111/mec.14252](http://dx.doi.org/10.1111/mec.14252)
- Olson CE and Roberts SB. (2014). Genome-wide profiling of DNA methylation and gene expression in Crassostrea gigas male gametes Frontiers in Physiology. 5:224. doi: [10.3389/fphys.2014.0022](http://journal.frontiersin.org/Journal/10.3389/fphys.2014.00224/abstract)
- Gavery MR and Roberts SB. (2013) Predominant intragenic methylation is associated with gene expression characteristics in a bivalve mollusc PeerJ 1:e215. doi:[10.7717/peerj.215](https://peerj.com/articles/215/)


There are a few other relevant products

- Gavery M, Delrow J, Basom R, Roberts S (2015) Influence of 17α-ethinylestradiol on DNA methylation in oysters. [GitHub](https://github.com/sr320/paper-Oyster-EE2/blob/master/README.md)
- Olson CE, Roberts SB (2015) Indication of family-specific DNA methylation patterns in developing oysters. *bioRxiv (preprint)*.  doi: https://doi.org/10.1101/012831


If you are looking for an older deep dive.

- NSF Award: [DNA methylation as a mechanism to increase adaptive potential in invertebrates](https://figshare.com/articles/DNA_methylation_as_a_mechanism_to_increase_adaptive_potential_in_invertebrates/97107/1)

## Computational Approaches
Jumping into our Onboarding repo: [Computing · RobertsLab/onboarding Wiki · GitHub](https://github.com/RobertsLab/onboarding/wiki/Computing) is a good place to start.

Some examples of how we work can be seen here [9 Ways to Make Papers a Little More Open and Reproducible – Roberts Lab](https://faculty.washington.edu/sr320/?p=11381)

And a recent review
Roberts and Gavery (2018) [OPPORTUNITIES IN FUNCTIONAL GENOMICS: A PRIMER ON LAB AND COMPUTATIONAL ASPECTS](http://eagle.fish.washington.edu/whale/pub/jsr37309_1r8rd0.pdf) . Journal of Shellfish Research, Vol. 37, No. 3, 1–8, 2018. DOI: 10.2983/035.037.0300

## Good books
- [Bioinformatics Data Skills: Reproducible and Robust Research with Open Source Tools: Vince Buffalo: 9781449367374: Amazon.com: Books](https://www.amazon.com/Bioinformatics-Data-Skills-Reproducible-Research/dp/1449367372/ref=mt_paperback?_encoding=UTF8&me=&qid=)
- [R for Data Science](http://r4ds.had.co.nz/)

## Gitting to Work
So now you have mastered Git, fluent in Bash, and are launching Jupyter notebooks on a regular basis. Here are some resources to get you going on analysis.

- From when Jupyter was still IPython [GitHub - che625/olson-ms-nb](https://github.com/che625/olson-ms-nb)
- A set of notebooks from on coral epigenetics. [GitHub - jldimond/Coral-CpG: Repository associated with article “Germline DNA methylation in reef corals: patterns and potential roles in response to environmental change”](https://github.com/jldimond/Coral-CpG/)
- Some recent work in R : [gavery-testdrive-Rproject/DMR-2-GeneIDs.Rmd at master · sr320/gavery-testdrive-Rproject · GitHub](https://github.com/sr320/gavery-testdrive-Rproject/blob/master/scripts/DMR-2-GeneIDs.Rmd)
- and my notebooks [GitHub - sr320/nb-2018](https://github.com/sr320/nb-2018)


## Just data
If you want to play around with some data…

- Geoduck Genome : [Genomic Resources · RobertsLab/resources Wiki · GitHub](https://github.com/RobertsLab/resources/wiki/Genomic-Resources#panopea-generosa)
- Lots of RRBS data (prefix `EPI` : [Index of /nightingales/P_generosa](http://owl.fish.washington.edu/nightingales/P_generosa/) ;[sample description · hputnam/project_juvenile_geoduck_OA · GitHub](https://github.com/hputnam/project_juvenile_geoduck_OA/blob/master/Setup_Notes/Sample_List.csv)
- [manuscript draft](https://www.authorea.com/users/73479/articles/117835-environmental-memory-through-dynamic-dna-methylation-provides-acclimatization-of-geoduck-clams-to-ocean-acidification/_show_article) .   
- Eastern Oyster Genome: [Genomic Resources · RobertsLab/resources Wiki · GitHub](https://github.com/RobertsLab/resources/wiki/Genomic-Resources#crassostrea-virginica)
- Simple Oyster BS Comparison Data
	- `http://owl.fish.washington.edu/halfshell/bu-serine-wd/18-04-10/oil/20150414_trimmed_2112_lane1_HB2_Oil_25000ppm_ATCACG.fastq.gz`
	- `http://owl.fish.washington.edu/halfshell/bu-serine-wd/18-04-10/oil/20150414_trimmed_2112_lane1_HB16_Oil_25000ppm_TTAGGC.fastq.gz`
	- `http://owl.fish.washington.edu/halfshell/bu-serine-wd/18-04-10/oil/20150414_trimmed_2112_lane1_HB30_Oil_25000ppm_TGACCA.fastq.gz`
	- `http://owl.fish.washington.edu/halfshell/bu-serine-wd/18-04-10/oil/20150414_trimmed_2112_lane1_NB3_NoOil_ACAGTG.fastq.gz`
	- `http://owl.fish.washington.edu/halfshell/bu-serine-wd/18-04-10/oil/20150414_trimmed_2112_lane1_NB6_NoOil_GCCAAT.fastq.gz`
	- `http://owl.fish.washington.edu/halfshell/bu-serine-wd/18-04-10/oil/20150414_trimmed_2112_lane1_NB11_NoOil_CAGATC.fastq.gz`


## Questions
Post any practical how-to questions [here](https://github.com/RobertsLab/resources/issues/new).
