
Running Trinity on EMU

Probably should have Tmuxed..

```
 Trinity \
--seqType fq \
--left data/NR021_S8_L001_R1_001.fastq,data/NR021_S8_L002_R1_001.fastq \
--right data/NR021_S8_L001_R2_001.fastq,data/NR021_S8_L002_R2_001.fastq \
--CPU 24 --trimmomatic --max_memory 48G
```


---

```
  1  [||||||||||||||||||||||||||||||||||||91.1%]   5  [|||||||||||||||||||||||||||||||||||100.0%]   9  [||||||||||||||||||||||||||          61.0%]   13 [|||||||||||||||||||||||||||||||     71.4%]
  2  [||||||||||||||||||||||||||||||||||||95.4%]   6  [||||||||||||||||||||||||||||||||||||97.4%]   10 [||||||||||||||||||||||||||||||||||||95.5%]   14 [||||||||||||||||||||||||||||||||||||96.1%]
  3  [||||||||||||||||||||||||||||||||||||88.9%]   7  [||||||||||||||||||||||||||||||||||||86.4%]   11 [||||||||||||||||||||||||||||||||||||84.4%]   15 [||||||||||||||||||||||||||||||||||| 83.7%]
  4  [||||||||||||||||||||||||||||||||||||94.8%]   8  [||||||||||||||||||||||||||||||||||||86.9%]   12 [|||||||||||||||||||||||||||||||||||100.0%]   16 [||||||||||||||||||||||||||||||||||||92.7%]
  Mem[|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||3.93G/47.2G]   Tasks: 227, 554 thr; 15 running
  Swp[||                                                                              231M/12.0G]   Load average: 9.32 5.50 2.35 
                                                                                                    Uptime: 45 days, 01:19:56

  PID USER      PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
22908 srlab      20   0  947M  650M  3176 R 596.  1.3  1:53.44 /home/shared/trinityrnaseq-Trinity-v2.4.0/util/..//Inchworm/bin/fastaToKmerCoverageStats --reads right.fa --kmers jellyfish.K25.min2.kmer
22905 srlab      20   0  954M  712M  3296 R 594.  1.5  1:53.13 /home/shared/trinityrnaseq-Trinity-v2.4.0/util/..//Inchworm/bin/fastaToKmerCoverageStats --reads left.fa --kmers jellyfish.K25.min2.kmers
22919 srlab      20   0  947M  650M  3176 R 100.  1.3  0:18.20 /home/shared/trinityrnaseq-Trinity-v2.4.0/util/..//Inchworm/bin/fastaToKmerCoverageStats --reads right.fa --kmers jellyfish.K25.min2.kmer
22920 srlab      20   0  947M  650M  3176 R 100.  1.3  0:19.33 /home/shared/trinityrnaseq-Trinity-v2.4.0/util/..//Inchworm/bin/fastaToKmerCoverageStats --reads right.fa --kmers jellyfish.K25.min2.kmer
22913 srlab      20   0  954M  712M  3296 R 99.6  1.5  0:18.64 /home/shared/trinityrnaseq-Trinity-v2.4.0/util/..//Inchworm/bin/fastaToKmerCoverageStats --reads left.fa --kmers jellyfish.K25.min2.kmers
22916 srlab      20   0  954M  712M  3296 R 99.6  1.5  0:18.13 /home/shared/trinityrnaseq-Trinity-v2.4.0/util/..//Inchworm/bin/fastaToKmerCoverageStats --reads left.fa --kmers jellyfish.K25.min2.kmers
22795 srlab      20   0  4640  1580  1296 R 99.6  0.0  1:43.95 gzip NR021_S8_L002_R1_001.fastq.P.qtrim NR021_S8_L002_R1_001.fastq.U.qtrim NR021_S8_L002_R2_001.fastq.P.qtrim NR021_S8_L002_R2_001.fastq.
22918 srlab      20   0  947M  650M  3176 R 98.9  1.3  0:20.44 /home/shared/trinityrnaseq-Trinity-v2.4.0/util/..//Inchworm/bin/fastaToKmerCoverageStats --reads right.fa --kmers jellyfish.K25.min2.kmer
22917 srlab      20   0  954M  712M  3296 R 98.9  1.5  0:18.17 /home/shared/trinityrnaseq-Trinity-v2.4.0/util/..//Inchworm/bin/fastaToKmerCoverageStats --reads left.fa --kmers jellyfish.K25.min2.kmers
22915 srlab      20   0  947M  650M  3176 R 98.9  1.3  0:18.59 /home/shared/trinityrnaseq-Trinity-v2.4.0/util/..//Inchworm/bin/fastaToKmerCoverageStats --reads right.fa --kmers jellyfish.K25.min2.kmer
22921 srlab      20   0  947M  650M  3176 R 98.9  1.3  0:18.13 /home/shared/trinityrnaseq-Trinity-v2.4.0/util/..//Inchworm/bin/fastaToKmerCoverageStats --reads right.fa --kmers jellyfish.K25.min2.kmer
22527 srlab      20   0  4640  1664  1380 R 98.3  0.0  2:59.30 gzip NR021_S8_L001_R1_001.fastq.P.qtrim NR021_S8_L001_R1_001.fastq.U.qtrim NR021_S8_L001_R2_001.fastq.P.qtrim NR021_S8_L001_R2_001.fastq.
22912 srlab      20   0  954M  712M  3296 R 97.6  1.5  0:20.77 /home/shared/trinityrnaseq-Trinity-v2.4.0/util/..//Inchworm/bin/fastaToKmerCoverageStats --reads left.fa --kmers jellyfish.K25.min2.kmers
22914 srlab      20   0  954M  712M  3296 R 97.6  1.5  0:19.24 /home/shared/trinityrnaseq-Trinity-v2.4.0/util/..//Inchworm/bin/fastaToKmerCoverageStats --reads left.fa --kmers jellyfish.K25.min2.kmers
25974 srlab      20   0  577M 58148 23992 S  9.8  0.1 16:05.77 /usr/lib/vino/vino-server --sm-disable
31649 root       20   0  953M  169M 32580 S  9.8  0.4 13h31:23 nautilus
25380 root       20   0  298M 70292 33708 S  3.3  0.1 18:49.81 /usr/lib/xorg/Xorg -core :1 -seat seat0 -auth /var/run/lightdm/root/:1 -nolisten tcp vt8 -novtswitch
22963 srlab      20   0 27344  5188  3264 R  2.0  0.0  0:00.41 htop
22968 root       20   0 96128  6436  5524 S  1.3  0.0  0:00.02 sshd: [accepted]
26033 srlab      20   0 1460M  115M 65152 S  0.7  0.2 12:48.00 compiz
 1223 root       20   0 1193M 31328 13092 S  0.0  0.1  2h09:40 /usr/bin/dockerd -H fd://
 1197 sgeadmin   20   0  136M  8520  7048 S  0.0  0.0 24:31.27 /usr/lib/gridengine/sge_qmaster
 1450 root       20   0  847M 16112  7392 S  0.0  0.0  1h05:45 docker-containerd -l unix:///var/run/docker/libcontainer
 ```
