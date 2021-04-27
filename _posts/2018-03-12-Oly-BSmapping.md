I am exploring a few versions of the [PBjelly Olympia oyster genome assembly](http://onsnetwork.org/kubu4/2017/11/30/genome-assembly-olympia-oyster-illumina-pacbio-using-pb-jelly-wbgi-scaffold-assembly-2/) and bisulfite read mapping.


tldr:

Libraries 	|	Genome	| aligned reads	|  unique reads 	| non-unique reads
----------|---------|-----------------|----------------|-------------------
WGBS(#)	|	PBjelly10k	|	60%	|	35%	|   25% 
MBDBS(zr)	| PBjelly10k  |  21%  |  12%   |  9%  
WGBS(#)	|	PBjelly1k	|	73%	|	46%	|   27% 
MBDBS(zr)	| PBjelly1k  |  26%  |  16%   |  10%  
WGBS(#)	|	PBjelly	|	76%	|	48%	|   28% 
MBDBS(zr)	| PBjelly  |  nn%  |  nn%   |  nn%  


The samples being run...

![t](https://d.pr/i/cetxkK+)

[Details on MBDBS](https://github.com/RobertsLab/project-olympia.oyster-genomic/wiki/MBD-BSseq-December-2015)

```
1_ATCACG_L001_R1_001.fastq.gz
2_CGATGT_L001_R1_001.fastq.gz
...
8_ACTTGA_L001_R1_001.fastq.gz
zr1394_10_s456.fastq.gz
zr1394_11_s456.fastq.gz
zr1394_12_s456.fastq.gz
...
zr1394_8_s456.fastq.gz
zr1394_9_s456.fastq.gz
```

First I ran the samples against the 1k minimum contig version. 

```
find /gscratch/srlab/sr320/data/olurida-bs/*gz \
| xargs basename -s .fastq.gz | xargs -I{} /gscratch/srlab/programs/bsmap-2.89/bsmap \
-a /gscratch/srlab/sr320/data/olurida-bs/{}.fastq.gz \
-d /gscratch/srlab/sr320/data/olurida-bs/Ol-pbjelly1k.fa \
-o /gscratch/srlab/sr320/analyses/0308/{}-bsmap_out_jelly1k.sam \
-p 28
```

Align rates are around

## Ol-pbjelly1k.fa

```
aligned reads: 9182783 (72.9%), unique reads: 5809087 (46.1%), non-unique reads: 3373696 (26.8%)
	aligned reads: 9062496 (72.6%), unique reads: 5713274 (45.7%), non-unique reads: 3349222 (26.8%)
	aligned reads: 7705853 (74.8%), unique reads: 4848598 (47.1%), non-unique reads: 2857255 (27.8%)
	aligned reads: 10413946 (72.4%), unique reads: 6563073 (45.7%), non-unique reads: 3850873 (26.8%)
	aligned reads: 23824115 (30.1%), unique reads: 14883271 (18.8%), non-unique reads: 8940844 (11.3%)
	aligned reads: 13906105 (25.2%), unique reads: 8148998 (14.8%), non-unique reads: 5757107 (10.4%)
	aligned reads: 14755154 (24.5%), unique reads: 9580125 (15.9%), non-unique reads: 5175029 (8.6%)
```

In short the number prefix are mapping back at a higher rate compared to `zr`.  



---

Next up was 

```
find /gscratch/srlab/sr320/data/olurida-bs/*gz \
| xargs basename -s .fastq.gz | xargs -I{} /gscratch/srlab/programs/bsmap-2.89/bsmap \
-a /gscratch/srlab/sr320/data/olurida-bs/{}.fastq.gz \
-d /gscratch/srlab/sr320/data/olurida-bs/Ol-pbjelly10k.fa \
-o /gscratch/srlab/sr320/analyses/0308/{}-bsmap_out_jelly10k.sam \
-p 28



find /gscratch/srlab/sr320/data/olurida-bs/*gz \
| xargs basename -s .fastq.gz | xargs -I{} /gscratch/srlab/programs/bsmap-2.89/bsmap \
-a /gscratch/srlab/sr320/data/olurida-bs/{}.fastq.gz \
-d /gscratch/srlab/sr320/data/olurida-bs/Ol-pbjelly.fa \
-o /gscratch/srlab/sr320/analyses/0308/{}-bsmap_out_jelly.sam \
-p 28
```

## Ol-pbjelly10k.fa	

```
	aligned reads: 7376298 (59.1%), unique reads: 4372377 (35.0%), non-unique reads: 3003921 (24.1%)
	aligned reads: 6279322 (61.0%), unique reads: 3716523 (36.1%), non-unique reads: 2562799 (24.9%)
	aligned reads: 8473650 (58.9%), unique reads: 5016823 (34.9%), non-unique reads: 3456827 (24.0%)
	aligned reads: 18848015 (23.8%), unique reads: 11097392 (14.0%), non-unique reads: 7750623 (9.8%)
	aligned reads: 11264261 (20.4%), unique reads: 6207698 (11.3%), non-unique reads: 5056563 (9.2%)
	aligned reads: 11743992 (19.5%), unique reads: 7167324 (11.9%), non-unique reads: 4576668 (7.6%)
```	
		
		
## Ol-pbjelly.fa

The WGBS samples ran, taking about 4 hours per sample with averages in the table above. There was a slight increase in mapped reads (~2%) but I do not see it worth it for the data end point and time. The MBDBS samples take over 12 hours per sample. I killed the job before 1 completed.
	
