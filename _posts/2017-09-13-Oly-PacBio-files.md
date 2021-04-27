Exploring the different aspects of data generated for the Oly genome.

Most recently did some PacBio that resulted in about 14x coverage assuming 500Mb genome size. We have decent assembly of these data with Canu. 

The raw file 
```
m170211_224036_42134_c101073082550000001823236402101737_s1_X0_filtered_subreads.fastq*
m170301_100013_42134_c101174162550000001823269408211761_s1_p0_filtered_subreads.fastq*
m170301_162825_42134_c101174162550000001823269408211762_s1_p0_filtered_subreads.fastq*
m170301_225711_42134_c101174162550000001823269408211763_s1_p0_filtered_subreads.fastq*
m170308_163922_42134_c101174252550000001823269408211742_s1_p0_filtered_subreads.fastq*
m170308_230815_42134_c101174252550000001823269408211743_s1_p0_filtered_subreads.fastq*
m170315_001112_42134_c101169372550000001823273008151717_s1_p0_filtered_subreads.fastq*
m170315_063041_42134_c101169382550000001823273008151700_s1_p0_filtered_subreads.fastq*
m170315_124938_42134_c101169382550000001823273008151701_s1_p0_filtered_subreads.fastq*
m170315_190851_42134_c101169382550000001823273008151702_s1_p0_filtered_subreads.fastq* 
```

I cat 'd them up to a plain fasta 
```
!cat *.fastq > m170-all.fastq
!cat m170-all.fastq | awk 'NR%4==1{printf ">%s\n", substr($0,2)}NR%4==2{print}' > m170-all.fa
!perl /Users/sr320/git-repos/nb-2017/scripts/count_fasta.pl -i 10000 \
m170-all.fa
```
---

```
0:9999 	1432866
10000:19999 	310387
20000:29999 	32184
30000:39999 	3849
40000:49999 	563
50000:59999 	60
60000:69999 	8

Total length of sequence:	12591188319 bp
Total number of sequences:	1779917
N25 stats:			25% of total sequence length is contained in the 181750 sequences >= 12785 bp
N50 stats:			50% of total sequence length is contained in the 486270 sequences >= 8657 bp
N75 stats:			75% of total sequence length is contained in the 912149 sequences >= 6401 bp
Total GC count:			4720472838 bp
GC %:				37.49 %
```


