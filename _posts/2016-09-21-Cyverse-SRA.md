---
layout: post
title: SRA and Cyverse
date: '2016-09-21'
categories: 
tags: cyverse, ncbi, sra, coral, wgs
---



Curious to see how Jay might tackle genome assembly (and looking ahead to FISH546) I wanted to see what could be done. I was able to bring an SRA file directly into Cyverse

```
The status of NCBI_SRA_Import_1.2_analysis1 has changed to Completed.

Description:

Start Date: 2016-09-21T18:58:54.133Z
Results Folder: /iplant/home/sr320/analyses/NCBI_SRA_Import_1.2_analysis1-2016-09-21-18-58-54.2
```
This brought in the SRA file.. then I ran fastq-dump.

```
The status of NCBI_SRA_Toolkit_fastq-dump_2.3.4_analysis1 has changed to Completed.

Description:

Start Date: 2016-09-21T19:53:42.313Z
Results Folder: /iplant/home/sr320/Coral/NCBI_SRA_Toolkit_fastq-dump_2.3.4_analysis1-2016-09-21-19-53-45.1
```

Now I have the Paired-End Reads.

Reached out to Giles an direction on professional approach

>>AllPaths-LG and MaSuRCA.  Both require you to have a small insert library and a 'jump' library, although AllPaths wants a library that has overlapping reads.  Looking at the links you have both, in this case you have the overlapping library, then 2 small jump libraries then three longer jump libraries.

Cyverse does have AllPaths on HPC.

Note all of this was done on a Chromebox!

[edit](https://github.com/sr320/sr320.github.io/edit/master/_posts/2016-09-21-Cyverse-SRA.md)

