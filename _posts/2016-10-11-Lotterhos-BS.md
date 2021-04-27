---
layout: post
title: Analysis of two oyster samples
date: '2016-10-11'
categories: Methylation
tags: gigas, bsmap, oyster
---

I started analysis of two gigas samples to eventually be compared with methylRAD. Below is a snapshot of the Jupyter notebook.
      
Updating @
<https://github.com/sr320/sr320.github.io/blob/master/jupyter/Cgigas/Lotterhos%20BS%20samples.ipynb>

    
The M2 and M3 samples are here:

http://owl.fish.washington.edu/nightingales/C_gigas/9_GATCAG_L001_R1_001.fastq.gz
http://owl.fish.washington.edu/nightingales/C_gigas/10_TAGCTT_L001_R1_001.fastq.gz

```python
bsmaploc="/Applications/bioinfo/BSMAP/bsmap-2.74/"

```

## Genome version


```python
!curl \
ftp://ftp.ensemblgenomes.org/pub/release-32/metazoa/fasta/crassostrea_gigas/dna/Crassostrea_gigas.GCA_000297895.1.dna_sm.toplevel.fa.gz \
> /Volumes/caviar/wd/data/Crassostrea_gigas.GCAz_000297895.1.dna_sm.toplevel.fa.gz    
```

      % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                     Dload  Upload   Total   Spent    Left  Speed
    100  148M  100  148M    0     0  5192k      0  0:00:29  0:00:29 --:--:-- 5790k



```python
!curl ftp://ftp.ensemblgenomes.org/pub/release-32/metazoa/fasta/crassostrea_gigas/dna/CHECKSUMS 
```

    08778 148199 Crassostrea_gigas.GCA_000297895.1.dna.nonchromosomal.fa.gz
    08778 148199 Crassostrea_gigas.GCA_000297895.1.dna.toplevel.fa.gz
    57175 143732 Crassostrea_gigas.GCA_000297895.1.dna_rm.nonchromosomal.fa.gz
    57175 143732 Crassostrea_gigas.GCA_000297895.1.dna_rm.toplevel.fa.gz
    45604 151782 Crassostrea_gigas.GCA_000297895.1.dna_sm.nonchromosomal.fa.gz
    45604 151782 Crassostrea_gigas.GCA_000297895.1.dna_sm.toplevel.fa.gz
    62118     5 README



```python
!ls /Volumes/caviar/wd/data/
```

    Crassostrea_gigas.GCAz_000297895.1.dna_sm.toplevel.fa.gz



```python
!md5 /Volumes/caviar/wd/data/Crassostrea_gigas.GCAz_000297895.1.dna_sm.toplevel.fa.gz
```

    MD5 (/Volumes/caviar/wd/data/Crassostrea_gigas.GCAz_000297895.1.dna_sm.toplevel.fa.gz) = c70084d76bd6d7a1ba52c13843e69ccc



```python
cd /Volumes/caviar/wd/
```

    /Volumes/caviar/wd



```python
mkdir $(date +%F)
```


```python
ls
```

    [34m2016-10-11[m[m/ [34mdata[m[m/



```python
ls /Volumes/web/nightingales/C
```


```python
!curl \
http://owl.fish.washington.edu/nightingales/C_gigas/9_GATCAG_L001_R1_001.fastq.gz \
> /Volumes/caviar/wd/2016-10-11/9_GATCAG_L001_R1_001.fastq.gz
```

      % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                     Dload  Upload   Total   Spent    Left  Speed
    100  560M  100  560M    0     0  55.6M      0  0:00:10  0:00:10 --:--:-- 77.8M



```python
!curl \
http://owl.fish.washington.edu/nightingales/C_gigas/10_TAGCTT_L001_R1_001.fastq.gz \
> /Volumes/caviar/wd/2016-10-11/10_TAGCTT_L001_R1_001.fastq.gz
```

      % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                     Dload  Upload   Total   Spent    Left  Speed
    100  619M  100  619M    0     0  46.1M      0  0:00:13  0:00:13 --:--:-- 44.0M



```python
cd 2016-10-11/
```

    /Volumes/caviar/wd/2016-10-11



```python
!cp 9_GATCAG_L001_R1_001.fastq.gz M2.fastq.gz
```


```python
!cp 10_TAGCTT_L001_R1_001.fastq.gz M3.fastq.gz
```


```python
for i in ("M2","M3"):
    !{bsmaploc}bsmap \
-a {i}.fastq.gz \
-d ../data/Crassostrea_gigas.GCAz_000297895.1.dna_sm.toplevel.fa \
-o bsmap_out_{i}.sam \
-p 6
```

    
    BSMAP v2.74
    Start at:  Tue Oct 11 08:02:27 2016
    
    Input reference file: ../data/Crassostrea_gigas.GCAz_000297895.1.dna_sm.toplevel.fa 	(format: FASTA)
    Load in 7658 db seqs, total size 557717710 bp. 8 secs passed
    total_kmers: 43046721
    Create seed table. 24 secs passed
    max number of mismatches: read_length * 8% 	max gap size: 0
    kmer cut-off ratio: 5e-07
    max multi-hits: 100	max Ns: 5	seed size: 16	index interval: 4
    quality cutoff: 0	base quality char: '!'
    min fragment size:28	max fragemt size:500
    start from read #1	end at read #4294967295
    additional alignment: T in reads => C in reference
    mapping strand: ++,-+
    Single-end alignment(6 threads)
    Input read file: M2.fastq.gz 	(format: gzipped FASTQ)
    Output file: bsmap_out_M2.sam	 (format: SAM)
    Thread #1: 	100000 reads finished. 30 secs passed
    Thread #0: 	50000 reads finished. 30 secs passed
    Thread #2: 	150000 reads finished. 31 secs passed
    Thread #3: 	200000 reads finished. 31 secs passed
    Thread #5: 	250000 reads finished. 31 secs passed
    Thread #4: 	300000 reads finished. 31 secs passed
    Thread #1: 	350000 reads finished. 36 secs passed
    Thread #0: 	400000 reads finished. 36 secs passed
    Thread #2: 	450000 reads finished. 36 secs passed
    Thread #3: 	500000 reads finished. 36 secs passed
    Thread #5: 	550000 reads finished. 37 secs passed
    Thread #4: 	600000 reads finished. 37 secs passed
    Thread #1: 	650000 reads finished. 42 secs passed
    Thread #2: 	750000 reads finished. 42 secs passed
    Thread #0: 	700000 reads finished. 42 secs passed
    Thread #3: 	800000 reads finished. 42 secs passed
    Thread #5: 	850000 reads finished. 42 secs passed
    Thread #4: 	900000 reads finished. 43 secs passed
    Thread #1: 	950000 reads finished. 48 secs passed
    Thread #2: 	1000000 reads finished. 48 secs passed
    Thread #3: 	1100000 reads finished. 48 secs passed
    Thread #0: 	1050000 reads finished. 49 secs passed
    Thread #5: 	1150000 reads finished. 49 secs passed
    Thread #4: 	1200000 reads finished. 49 secs passed
    Thread #1: 	1250000 reads finished. 54 secs passed
    Thread #2: 	1300000 reads finished. 54 secs passed
    Thread #3: 	1350000 reads finished. 55 secs passed
    Thread #5: 	1450000 reads finished. 55 secs passed
    Thread #4: 	1500000 reads finished. 55 secs passed
    Thread #0: 	1400000 reads finished. 55 secs passed
    Thread #1: 	1550000 reads finished. 60 secs passed
    Thread #2: 	1600000 reads finished. 60 secs passed
    Thread #3: 	1650000 reads finished. 61 secs passed
    Thread #4: 	1750000 reads finished. 61 secs passed
    Thread #5: 	1700000 reads finished. 61 secs passed
    Thread #0: 	1800000 reads finished. 61 secs passed
    Thread #1: 	1850000 reads finished. 67 secs passed
    Thread #2: 	1900000 reads finished. 67 secs passed
    Thread #3: 	1950000 reads finished. 68 secs passed
    Thread #4: 	2000000 reads finished. 68 secs passed
    Thread #5: 	2050000 reads finished. 68 secs passed
    Thread #0: 	2100000 reads finished. 68 secs passed
    Thread #1: 	2150000 reads finished. 73 secs passed
    Thread #2: 	2200000 reads finished. 74 secs passed
    Thread #3: 	2250000 reads finished. 74 secs passed
    Thread #4: 	2300000 reads finished. 74 secs passed
    Thread #5: 	2350000 reads finished. 74 secs passed
    Thread #0: 	2400000 reads finished. 75 secs passed
    Thread #1: 	2450000 reads finished. 80 secs passed
    Thread #2: 	2500000 reads finished. 80 secs passed
    Thread #3: 	2550000 reads finished. 80 secs passed
    Thread #4: 	2600000 reads finished. 81 secs passed
    Thread #5: 	2650000 reads finished. 81 secs passed
    Thread #0: 	2700000 reads finished. 81 secs passed
    Thread #2: 	2800000 reads finished. 86 secs passed
    Thread #1: 	2750000 reads finished. 86 secs passed
    Thread #3: 	2850000 reads finished. 86 secs passed
    Thread #4: 	2900000 reads finished. 87 secs passed
    Thread #5: 	2950000 reads finished. 87 secs passed
    Thread #0: 	3000000 reads finished. 88 secs passed
    Thread #2: 	3050000 reads finished. 92 secs passed
    Thread #1: 	3100000 reads finished. 92 secs passed
    Thread #3: 	3150000 reads finished. 92 secs passed
    Thread #4: 	3200000 reads finished. 92 secs passed
    Thread #5: 	3250000 reads finished. 93 secs passed
    Thread #0: 	3300000 reads finished. 94 secs passed
    Thread #2: 	3350000 reads finished. 98 secs passed
    Thread #1: 	3400000 reads finished. 98 secs passed
    Thread #3: 	3450000 reads finished. 98 secs passed
    Thread #4: 	3500000 reads finished. 98 secs passed
    Thread #5: 	3550000 reads finished. 99 secs passed
    Thread #0: 	3600000 reads finished. 100 secs passed
    Thread #2: 	3650000 reads finished. 104 secs passed
    Thread #1: 	3700000 reads finished. 104 secs passed
    Thread #3: 	3750000 reads finished. 104 secs passed
    Thread #4: 	3800000 reads finished. 104 secs passed
    Thread #5: 	3850000 reads finished. 105 secs passed
    Thread #0: 	3900000 reads finished. 106 secs passed
    Thread #2: 	3950000 reads finished. 110 secs passed
    Thread #1: 	4000000 reads finished. 110 secs passed
    Thread #3: 	4050000 reads finished. 110 secs passed
    Thread #4: 	4100000 reads finished. 110 secs passed
    Thread #5: 	4150000 reads finished. 111 secs passed
    Thread #0: 	4200000 reads finished. 112 secs passed
    Thread #2: 	4250000 reads finished. 116 secs passed
    Thread #1: 	4300000 reads finished. 116 secs passed
    Thread #3: 	4350000 reads finished. 116 secs passed
    Thread #4: 	4400000 reads finished. 117 secs passed
    Thread #5: 	4450000 reads finished. 117 secs passed
    Thread #0: 	4500000 reads finished. 119 secs passed
    Thread #2: 	4550000 reads finished. 122 secs passed
    Thread #1: 	4600000 reads finished. 122 secs passed
    Thread #3: 	4650000 reads finished. 122 secs passed
    Thread #4: 	4700000 reads finished. 123 secs passed
    Thread #5: 	4750000 reads finished. 123 secs passed
    Thread #0: 	4800000 reads finished. 125 secs passed
    Thread #2: 	4850000 reads finished. 128 secs passed
    Thread #1: 	4900000 reads finished. 128 secs passed
    Thread #3: 	4950000 reads finished. 129 secs passed
    Thread #4: 	5000000 reads finished. 129 secs passed
    Thread #5: 	5050000 reads finished. 129 secs passed
    Thread #0: 	5100000 reads finished. 131 secs passed
    Thread #2: 	5150000 reads finished. 134 secs passed
    Thread #1: 	5200000 reads finished. 134 secs passed
    Thread #3: 	5250000 reads finished. 134 secs passed
    Thread #4: 	5300000 reads finished. 135 secs passed
    Thread #5: 	5350000 reads finished. 135 secs passed
    Thread #0: 	5400000 reads finished. 137 secs passed
    Thread #2: 	5450000 reads finished. 140 secs passed
    Thread #1: 	5500000 reads finished. 140 secs passed
    Thread #3: 	5550000 reads finished. 141 secs passed
    Thread #4: 	5600000 reads finished. 141 secs passed
    Thread #5: 	5650000 reads finished. 141 secs passed
    Thread #0: 	5700000 reads finished. 143 secs passed
    Thread #2: 	5750000 reads finished. 147 secs passed
    Thread #1: 	5800000 reads finished. 147 secs passed
    Thread #3: 	5850000 reads finished. 147 secs passed
    Thread #4: 	5900000 reads finished. 147 secs passed
    Thread #5: 	5950000 reads finished. 148 secs passed
    Thread #0: 	6000000 reads finished. 150 secs passed
    Thread #2: 	6050000 reads finished. 153 secs passed
    Thread #1: 	6100000 reads finished. 153 secs passed
    Thread #3: 	6150000 reads finished. 153 secs passed
    Thread #4: 	6200000 reads finished. 153 secs passed
    Thread #5: 	6250000 reads finished. 154 secs passed
    Thread #0: 	6300000 reads finished. 156 secs passed
    Thread #1: 	6400000 reads finished. 160 secs passed
    Thread #2: 	6350000 reads finished. 160 secs passed
    Thread #4: 	6500000 reads finished. 160 secs passed
    Thread #3: 	6450000 reads finished. 160 secs passed
    Thread #5: 	6550000 reads finished. 161 secs passed
    Thread #0: 	6600000 reads finished. 164 secs passed
    Thread #1: 	6650000 reads finished. 166 secs passed
    Thread #4: 	6750000 reads finished. 167 secs passed
    Thread #2: 	6700000 reads finished. 167 secs passed
    Thread #3: 	6800000 reads finished. 167 secs passed
    Thread #5: 	6850000 reads finished. 168 secs passed
    Thread #0: 	6900000 reads finished. 171 secs passed
    Thread #1: 	6950000 reads finished. 173 secs passed
    Thread #2: 	7050000 reads finished. 174 secs passed
    Thread #4: 	7000000 reads finished. 174 secs passed
    Thread #3: 	7100000 reads finished. 174 secs passed
    Thread #5: 	7150000 reads finished. 174 secs passed
    Thread #0: 	7200000 reads finished. 177 secs passed
    Thread #1: 	7250000 reads finished. 179 secs passed
    Thread #2: 	7300000 reads finished. 180 secs passed
    Thread #4: 	7350000 reads finished. 180 secs passed
    Thread #3: 	7400000 reads finished. 180 secs passed
    Thread #5: 	7450000 reads finished. 180 secs passed
    Thread #0: 	7500000 reads finished. 184 secs passed
    Thread #1: 	7550000 reads finished. 186 secs passed
    Thread #2: 	7600000 reads finished. 186 secs passed
    Thread #4: 	7650000 reads finished. 187 secs passed
    Thread #3: 	7700000 reads finished. 187 secs passed
    Thread #5: 	7750000 reads finished. 187 secs passed
    Thread #0: 	7800000 reads finished. 191 secs passed
    Thread #1: 	7850000 reads finished. 193 secs passed
    Thread #2: 	7900000 reads finished. 193 secs passed
    Thread #4: 	7950000 reads finished. 193 secs passed
    Thread #3: 	8000000 reads finished. 193 secs passed
    Thread #5: 	8050000 reads finished. 193 secs passed
    Thread #0: 	8100000 reads finished. 196 secs passed
    Thread #1: 	8150000 reads finished. 198 secs passed
    Thread #2: 	8200000 reads finished. 199 secs passed
    Thread #4: 	8250000 reads finished. 199 secs passed
    Thread #3: 	8300000 reads finished. 199 secs passed
    Thread #5: 	8350000 reads finished. 199 secs passed
    Thread #0: 	8400000 reads finished. 203 secs passed
    Thread #1: 	8450000 reads finished. 205 secs passed
    Thread #2: 	8500000 reads finished. 205 secs passed
    Thread #4: 	8550000 reads finished. 205 secs passed
    Thread #5: 	8650000 reads finished. 205 secs passed
    Thread #3: 	8600000 reads finished. 205 secs passed
    Thread #0: 	8700000 reads finished. 209 secs passed
    Thread #1: 	8750000 reads finished. 210 secs passed
    Thread #2: 	8800000 reads finished. 211 secs passed
    Thread #4: 	8850000 reads finished. 211 secs passed
    Thread #5: 	8900000 reads finished. 211 secs passed
    Thread #3: 	8950000 reads finished. 211 secs passed
    Thread #0: 	9000000 reads finished. 215 secs passed
    Thread #1: 	9050000 reads finished. 216 secs passed
    Thread #2: 	9100000 reads finished. 217 secs passed
    Thread #4: 	9150000 reads finished. 217 secs passed
    Thread #5: 	9200000 reads finished. 217 secs passed
    Thread #3: 	9250000 reads finished. 217 secs passed
    Thread #0: 	9300000 reads finished. 221 secs passed
    Thread #1: 	9350000 reads finished. 222 secs passed
    Thread #2: 	9400000 reads finished. 223 secs passed
    Thread #4: 	9450000 reads finished. 223 secs passed
    Thread #5: 	9500000 reads finished. 223 secs passed
    Thread #3: 	9550000 reads finished. 223 secs passed
    Thread #0: 	9600000 reads finished. 227 secs passed
    Thread #1: 	9650000 reads finished. 228 secs passed
    Thread #2: 	9700000 reads finished. 228 secs passed
    Thread #4: 	9750000 reads finished. 229 secs passed
    Thread #5: 	9800000 reads finished. 229 secs passed
    Thread #3: 	9850000 reads finished. 229 secs passed
    Thread #0: 	9900000 reads finished. 233 secs passed
    Thread #1: 	9950000 reads finished. 234 secs passed
    Thread #2: 	10000000 reads finished. 235 secs passed
    Thread #4: 	10050000 reads finished. 235 secs passed
    Thread #5: 	10100000 reads finished. 235 secs passed
    Thread #3: 	10150000 reads finished. 235 secs passed
    Thread #0: 	10200000 reads finished. 239 secs passed
    Thread #1: 	10250000 reads finished. 240 secs passed
    Thread #2: 	10300000 reads finished. 241 secs passed
    Thread #4: 	10350000 reads finished. 241 secs passed
    Thread #5: 	10400000 reads finished. 241 secs passed
    Thread #3: 	10450000 reads finished. 241 secs passed
    Thread #2: 	10564512 reads finished. 242 secs passed



```python
for i in ("M2","M3"):
    !python {bsmaploc}methratio.py \
-d ../data/Crassostrea_gigas.GCAz_000297895.1.dna_sm.toplevel.fa \
-u -z -g \
-o methratio_out_{i}.txt \
-s {bsmaploc}samtools \
bsmap_out_{i}.sam \
```


```python

```
