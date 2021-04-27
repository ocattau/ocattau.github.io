---
layout: post
title: Geoduck-EPI on Hi-C Draft
date: '2018-05-10'
category: Geoduck
tags: bismark
---

As a better assembly is coming online for the Geoduck, we have started to look at Bismark mapping of prior samples.

For a refresh there are 50 samples (or 53)

I did a run on mox

```
#SBATCH --workdir=/gscratch/srlab/sr320/analyses/0505

source /gscratch/srlab/programs/scripts/paths.sh

find /gscratch/srlab/sr320/data/0504/EPI-*R1* \
| xargs basename -s _L005_R1_001.fastq.gz | xargs -I{} /gscratch/srlab/programs/Bismark-0.19.0/bismark \
--path_to_bowtie /gscratch/srlab/programs/bowtie2-2.1.0 \
-p 28 \
-multicore 4 \
/gscratch/srlab/sr320/data/hi-c \
-1 /gscratch/srlab/sr320/data/0504/{}_L005_R1_001.fastq.gz \
-2 /gscratch/srlab/sr320/data/0504/{}_L005_R2_001.fastq.gz
```

About 17 completed

```
0505/EPI-103_S27_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	28.6%
0505/EPI-104_S28_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	27.8%
0505/EPI-111_S29_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	27.6%
0505/EPI-113_S30_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	27.8%
0505/EPI-119_S31_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	27.9%
0505/EPI-120_S32_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	29.2%
0505/EPI-127_S33_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	29.3%
0505/EPI-128_S34_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	28.9%
0505/EPI-135_S35_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	25.4%
0505/EPI-135WG_S42_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	26.8%
0505/EPI-136_S36_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	25.1%
0505/EPI-143_S37_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	27.4%
0505/EPI-145_S38_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	28.3%
0505/EPI-41_S38_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	19.5%
0505/EPI-42_S39_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	22.2%
0505/EPI-43_S40_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	17.5%
0505/EPI-44_S41_L005_R1_001_bismark_bt2_PE_report.txt:Mapping efficiency:	7.9%
```

Not clear if this was a system error or not, thus running a `-u 10000` to see if I can get all samples processed.


---
In fact it appears there is an error. Again it stops at 44.

Now realizing issue in basename (hint):
```
-rw-rw-rw- 1 sr320 hyak-coenv  1.2G Dec 28  2016 EPI-103_S27_L005_R1_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.2G Dec 28  2016 EPI-103_S27_L005_R2_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.7G Dec 28  2016 EPI-104_S28_L005_R1_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.7G Dec 28  2016 EPI-104_S28_L005_R2_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.6G Dec 28  2016 EPI-111_S29_L005_R1_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.5G Dec 28  2016 EPI-111_S29_L005_R2_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.5G Dec 28  2016 EPI-113_S30_L005_R1_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.5G Dec 28  2016 EPI-113_S30_L005_R2_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.7G Dec 28  2016 EPI-119_S31_L005_R1_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.7G Dec 28  2016 EPI-119_S31_L005_R2_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.4G Dec 28  2016 EPI-120_S32_L005_R1_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.4G Dec 28  2016 EPI-120_S32_L005_R2_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.3G Dec 28  2016 EPI-127_S33_L005_R1_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.3G Dec 28  2016 EPI-127_S33_L005_R2_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.4G Dec 28  2016 EPI-128_S34_L005_R1_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.4G Dec 28  2016 EPI-128_S34_L005_R2_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.6G Dec 28  2016 EPI-135_S35_L005_R1_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.7G Dec 28  2016 EPI-135_S35_L005_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv   10G Jan 11  2017 EPI-135WG_S42_L005_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv   10G Jan 12  2017 EPI-135WG_S42_L005_R2_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.6G Dec 28  2016 EPI-136_S36_L005_R1_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.6G Dec 28  2016 EPI-136_S36_L005_R2_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.3G Dec 28  2016 EPI-143_S37_L005_R1_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.3G Dec 28  2016 EPI-143_S37_L005_R2_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.5G Dec 28  2016 EPI-145_S38_L005_R1_001.fastq.gz
-rw-rw-rw- 1 sr320 hyak-coenv  1.5G Dec 28  2016 EPI-145_S38_L005_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.6G Jan 11  2017 EPI-151_S2_L002_R1_001.fastq.gz
-rwxrwxr-x 1 sr320 hyak-coenv  1.7G Feb  1  2017 EPI-151_S2_L002_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.7G Jan 11  2017 EPI-152_S3_L002_R1_001.fastq.gz
-rwxrwxr-x 1 sr320 hyak-coenv  1.7G Feb  1  2017 EPI-152_S3_L002_R2_001.fastq.gz
-rwxrwxr-x 1 sr320 hyak-coenv  1.7G Feb  1  2017 EPI-153_S4_L002_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.8G Jan 11  2017 EPI-153_S4_L002_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.5G Jan 11  2017 EPI-154_S5_L002_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.5G Jan 11  2017 EPI-154_S5_L002_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  889M Jan 11  2017 EPI-159_S6_L002_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  920M Jan 11  2017 EPI-159_S6_L002_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.9G Jan 11  2017 EPI-160_S7_L002_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.9G Jan 11  2017 EPI-160_S7_L002_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.4G Jan 11  2017 EPI-161_S8_L002_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.4G Jan 11  2017 EPI-161_S8_L002_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.3G Jan 11  2017 EPI-162_S9_L002_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.3G Jan 11  2017 EPI-162_S9_L002_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.4G Jan 11  2017 EPI-167_S10_L002_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.4G Jan 11  2017 EPI-167_S10_L002_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.3G Jan 11  2017 EPI-168_S11_L002_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.3G Jan 11  2017 EPI-168_S11_L002_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.2G Jan 11  2017 EPI-169_S12_L002_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.3G Jan 11  2017 EPI-169_S12_L002_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.5G Jan 11  2017 EPI-170_S13_L002_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.6G Jan 11  2017 EPI-170_S13_L002_R2_001.fastq.gz
-rwxrwxr-x 1 sr320 hyak-coenv  1.4G Feb  1  2017 EPI-175_S14_L003_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.4G Jan 11  2017 EPI-175_S14_L003_R2_001.fastq.gz
-rwxrwxr-x 1 sr320 hyak-coenv  2.0G Feb  1  2017 EPI-176_S15_L003_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  2.1G Jan 11  2017 EPI-176_S15_L003_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.6G Jan 11  2017 EPI-181_S16_L003_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.6G Jan 11  2017 EPI-181_S16_L003_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.8G Jan 11  2017 EPI-182_S17_L003_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.8G Jan 11  2017 EPI-182_S17_L003_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.2G Jan 11  2017 EPI-184_S18_L003_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.2G Jan 11  2017 EPI-184_S18_L003_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  643M Jan 11  2017 EPI-185_S19_L003_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  648M Jan 11  2017 EPI-185_S19_L003_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.5G Jan 11  2017 EPI-187_S20_L003_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.5G Jan 11  2017 EPI-187_S20_L003_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.3G Jan 11  2017 EPI-188_S21_L003_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.4G Jan 11  2017 EPI-188_S21_L003_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.8G Jan 11  2017 EPI-193_S22_L003_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.9G Jan 11  2017 EPI-193_S22_L003_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.6G Jan 11  2017 EPI-194_S23_L003_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.6G Jan 11  2017 EPI-194_S23_L003_R2_001.fastq.gz
-rwxrwxr-x 1 sr320 hyak-coenv 1002M Feb  1  2017 EPI-199_S24_L003_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.1G Jan 11  2017 EPI-199_S24_L003_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.5G Jan 11  2017 EPI-200_S25_L003_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.6G Jan 11  2017 EPI-200_S25_L003_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.4G Jan 11  2017 EPI-205_S26_L004_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.4G Jan 11  2017 EPI-205_S26_L004_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.8G Jan 11  2017 EPI-206_S27_L004_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.9G Jan 11  2017 EPI-206_S27_L004_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  2.0G Jan 11  2017 EPI-208_S28_L004_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  2.1G Jan 11  2017 EPI-208_S28_L004_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.7G Jan 11  2017 EPI-209_S29_L004_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.7G Jan 11  2017 EPI-209_S29_L004_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.6G Jan 11  2017 EPI-214_S30_L004_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.6G Jan 11  2017 EPI-214_S30_L004_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.3G Jan 11  2017 EPI-215_S31_L004_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.3G Jan 11  2017 EPI-215_S31_L004_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  941M Jan 11  2017 EPI-220_S32_L004_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  960M Jan 11  2017 EPI-220_S32_L004_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.2G Jan 11  2017 EPI-221_S33_L004_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.3G Jan 11  2017 EPI-221_S33_L004_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  624M Jan 11  2017 EPI-226_S34_L004_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  631M Jan 11  2017 EPI-226_S34_L004_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  836M Jan 11  2017 EPI-227_S35_L004_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  852M Jan 11  2017 EPI-227_S35_L004_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.1G Jan 11  2017 EPI-229_S36_L004_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.1G Jan 11  2017 EPI-229_S36_L004_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.7G Jan 11  2017 EPI-230_S37_L004_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.7G Jan 11  2017 EPI-230_S37_L004_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.5G Jan 11  2017 EPI-41_S38_L005_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.5G Jan 11  2017 EPI-41_S38_L005_R2_001.fastq.gz
-rwxrwxr-x 1 sr320 hyak-coenv  1.7G Feb  1  2017 EPI-42_S39_L005_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.8G Jan 11  2017 EPI-42_S39_L005_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.7G Jan 11  2017 EPI-43_S40_L005_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  1.7G Jan 11  2017 EPI-43_S40_L005_R2_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  2.0G Jan 11  2017 EPI-44_S41_L005_R1_001.fastq.gz
-rwxr-xr-x 1 sr320 hyak-coenv  2.3G Jan 11  2017 EPI-44_S41_L005_R2_001.fastq.gz
```

---

Rewrite

```
find /gscratch/srlab/sr320/data/0504/EPI-*R1* \
| xargs basename -s _R1_001.fastq.gz | xargs -I{} /gscratch/srlab/programs/Bismark-0.19.0/bismark \
--path_to_bowtie /gscratch/srlab/programs/bowtie2-2.1.0 \
-p 28 \
-multicore 4 \
-u 10000 \
/gscratch/srlab/sr320/data/hi-c \
-1 /gscratch/srlab/sr320/data/0504/{}_R1_001.fastq.gz \
-2 /gscratch/srlab/sr320/data/0504/{}_R2_001.fastq.gz
```

This took 7 hours on Mox. Mapping efficiency a little less that 20%.
Will modify min score. `--score_min L,0,-0.9`

```
#SBATCH --workdir=/gscratch/srlab/sr320/analyses/0512

source /gscratch/srlab/programs/scripts/paths.sh

find /gscratch/srlab/sr320/data/0504/EPI-*R1* \
| xargs basename -s _R1_001.fastq.gz | xargs -I{} /gscratch/srlab/programs/Bismark-0.19.0/bismark \
--path_to_bowtie /gscratch/srlab/programs/bowtie2-2.1.0 \
--score_min L,0,-0.9 \
-p 28 \
-u 10000 \
-multicore 4 \
/gscratch/srlab/sr320/data/hi-c \
-1 /gscratch/srlab/sr320/data/0504/{}_R1_001.fastq.gz \
-2 /gscratch/srlab/sr320/data/0504/{}_R2_001.fastq.gz
```

Mapping efficiency increased

```
Mapping efficiency:	59.6%
Mapping efficiency:	58.5%
Mapping efficiency:	57.9%
Mapping efficiency:	58.2%
Mapping efficiency:	57.6%
Mapping efficiency:	59.2%
Mapping efficiency:	59.3%
Mapping efficiency:	58.7%
Mapping efficiency:	54.2%
Mapping efficiency:	56.8%
Mapping efficiency:	54.6%
Mapping efficiency:	56.0%
Mapping efficiency:	57.5%
Mapping efficiency:	43.4%
Mapping efficiency:	50.4%
Mapping efficiency:	42.0%
Mapping efficiency:	48.4%
Mapping efficiency:	51.4%
Mapping efficiency:	42.3%
Mapping efficiency:	41.7%
Mapping efficiency:	41.4%
Mapping efficiency:	55.6%
Mapping efficiency:	51.9%
Mapping efficiency:	46.1%
Mapping efficiency:	42.5%
Mapping efficiency:	52.9%
Mapping efficiency:	49.2%
Mapping efficiency:	53.2%
Mapping efficiency:	53.8%
Mapping efficiency:	49.8%
Mapping efficiency:	48.3%
Mapping efficiency:	47.3%
Mapping efficiency:	39.0%
Mapping efficiency:	37.8%
Mapping efficiency:	55.0%
Mapping efficiency:	41.7%
Mapping efficiency:	42.4%
Mapping efficiency:	26.1%
Mapping efficiency:	27.4%
Mapping efficiency:	31.5%
Mapping efficiency:	49.3%
Mapping efficiency:	46.8%
Mapping efficiency:	42.6%
Mapping efficiency:	45.0%
Mapping efficiency:	32.5%
Mapping efficiency:	52.8%
Mapping efficiency:	43.6%
Mapping efficiency:	47.3%
Mapping efficiency:	40.4%
Mapping efficiency:	45.9%
Mapping efficiency:	50.1%
Mapping efficiency:	39.4%
Mapping efficiency:	17.3%
```

---

Then went full fun

```
#SBATCH --workdir=/gscratch/srlab/sr320/analyses/0513

source /gscratch/srlab/programs/scripts/paths.sh

find /gscratch/srlab/sr320/data/0504/EPI-*R1* \
| xargs basename -s _R1_001.fastq.gz | xargs -I{} /gscratch/srlab/programs/Bismark-0.19.0/bismark \
--path_to_bowtie /gscratch/srlab/programs/bowtie2-2.1.0 \
--score_min L,0,-0.9 \
-p 28 \
-multicore 4 \
/gscratch/srlab/sr320/data/hi-c \
-1 /gscratch/srlab/sr320/data/0504/{}_R1_001.fastq.gz \
-2 /gscratch/srlab/sr320/data/0504/{}_R2_001.fastq.gz
````

It seemed to end

```
[sr320@mox1 0513]$ cat *.txt | grep "Mapping"
Mapping efficiency:	60.1%
Mapping efficiency:	58.5%
Mapping efficiency:	57.9%
Mapping efficiency:	58.4%
Mapping efficiency:	57.5%
Mapping efficiency:	59.8%
Mapping efficiency:	59.7%
Mapping efficiency:	58.9%
```

Now running with 30k version of genome

```
#SBATCH --workdir=/gscratch/srlab/sr320/analyses/0515

source /gscratch/srlab/programs/scripts/paths.sh

find /gscratch/srlab/sr320/data/0504/EPI-*R1* \
| xargs basename -s _R1_001.fastq.gz | xargs -I{} /gscratch/srlab/programs/Bismark-0.19.0/bismark \
--path_to_bowtie /gscratch/srlab/programs/bowtie2-2.1.0 \
--score_min L,0,-0.9 \
-p 28 \
-multicore 4 \
/gscratch/srlab/sr320/data/hi-c_30k \
-1 /gscratch/srlab/sr320/data/0504/{}_R1_001.fastq.gz \
-2 /gscratch/srlab/sr320/data/0504/{}_R2_001.fastq.gz
```

at 05-22-18 it had run `6-21:11:47` with about 33 complete.

---
UPDATE: 05-25-18- completed. So about 10 days.

output:       
 http://gannet.fish.washington.edu/seashell/bu-mox/analyses/0515/

---
Next step

```
#SBATCH --workdir=/gscratch/srlab/sr320/analyses/0525

source /gscratch/srlab/programs/scripts/paths.sh


/gscratch/srlab/programs/Bismark-0.19.0/deduplicate_bismark \
--bam -p \
/gscratch/srlab/sr320/analyses/0515/*.bam



find /gscratch/srlab/sr320/analyses/0525/*deduplicated.bam \
| xargs basename -s _R1_001_bismark_bt2_pe.deduplicated.bam | xargs -I{} /gscratch/srlab/programs/samtools-1.4/samtools \
sort -@ 28 {}_R1_001_bismark_bt2_pe.deduplicated.bam \
-o /gscratch/srlab/sr320/analyses/0525/{}_dedup.sorted.bam
```
