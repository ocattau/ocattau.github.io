---
layout: post
title: find-xargs-basename
date: '2016-12-01'
categories: snippet
---


```
!find /Volumes/web/nightingales/O_lurida/20160223_gbs/1NF*1.fq.gz | xargs basename -s _1.fq.gz \
| xargs -I{} /Applications/bioinfo/bowtie2-2.2.4/bowtie2 \
-x /Users/sr320/git-repos/student-fish546-2016/data/Ostrea_lurida-Scaff-10k-bowtie-index \
-1 /Volumes/web/nightingales/O_lurida/20160223_gbs/{}_1.fq.gz \
-2 /Volumes/web/nightingales/O_lurida/20160223_gbs/{}_2.fq.gz \
-p 8 \
--very-sensitive-local  \
-S /Volumes/caviar/wd/2016-12-01/{}.sam
```

