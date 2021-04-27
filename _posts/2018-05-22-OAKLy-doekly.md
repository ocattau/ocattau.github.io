---
layout: post
title: OAKLy Doekly
date: '2018-05-22'
category: OAKL
tags: bismark, R, DML
---

Full running of the OAKL samples.




First there was [this](https://github.com/sr320/nb-2018/blob/master/C_virginica/17-OAKL-fullpipe-mk.ipynb) where the alignment code was:

```
%%bash
find /Volumes/Serine/wd/18-04-27/zr2096_*R1* %%bash f \
| xargs basename -s _s1_R1_val_1.fq.gz | xargs -I{} /Applications/bioinfo/Bismark_v0.19.0/bismark \
--path_to_bowtie /Applications/bioinfo/bowtie2-2.3.4.1-macos-x86_64 \
--genome /Volumes/Serine/wd/18-03-15/genome \
--score_min L,0,-1.2 \
-p 4 \
--non_directional \
-1 /Volumes/Serine/wd/18-04-27/{}_s1_R1_val_1.fq.gz \
-2 /Volumes/Serine/wd/18-04-27/{}_s1_R2_val_2.fq.gz \
2> bismark.err
```

With output files @      
http://owl.fish.washington.edu/halfshell/bu-serine-wd/18-04-29/

This included the R code

```
library(methylKit)

file.list_a=list('zr2096_1_dedup.sorted.bam',
 'zr2096_2_dedup.sorted.bam',
  'zr2096_3_dedup.sorted.bam',
  'zr2096_4_dedup.sorted.bam',
  'zr2096_5_dedup.sorted.bam',
  'zr2096_6_dedup.sorted.bam',
  'zr2096_6_dedup.sorted.bam',
  'zr2096_8_dedup.sorted.bam',
  'zr2096_9_dedup.sorted.bam',
  'zr2096_10_dedup.sorted.bam'
  )



myobj2 = processBismarkAln(location = file.list_a, sample.id = list("1","2","3","4","5","6","7","8","9","10"), assembly = "v3", read.context="CpG", mincov=1, treatment = c(0,0,0,0,0,1,1,1,1,1))



getMethylationStats(myobj2[[1]],plot=FALSE,both.strands=FALSE)

getMethylationStats(myobj2[[1]],plot=TRUE,both.strands=FALSE)

getCoverageStats(myobj2[[4]],plot=TRUE,both.strands=FALSE)




meth=unite(myobj2)



getCorrelation(meth,plot=TRUE)


clusterSamples(meth, dist="correlation", method="ward", plot=TRUE)
```

[R code](http://htmlpreview.github.io/?https://github.com/sr320/nb-2018/blob/master/C_virginica/R/0510/md/mk-02.html)

[myDiff50p.csv](https://github.com/sr320/nb-2018/blob/master/C_virginica/R/0510/analyses/myDiff50p.csv)




---

Then it was done again [here](https://github.com/sr320/nb-2018/blob/master/C_virginica/19-OAKL-fullpipe-mk.ipynb).

just changing score min.

```
%%bash
find /Volumes/Serine/wd/18-04-27/zr2096_*R1* \
| xargs basename -s _s1_R1_val_1.fq.gz | xargs -I{} /Applications/bioinfo/Bismark_v0.19.0/bismark \
--path_to_bowtie /Applications/bioinfo/bowtie2-2.3.4.1-macos-x86_64 \
--genome /Volumes/Serine/wd/18-03-15/genome \
--score_min L,0,-0.9 \
-p 4 \
--non_directional \
-1 /Volumes/Serine/wd/18-04-27/{}_s1_R1_val_1.fq.gz \
-2 /Volumes/Serine/wd/18-04-27/{}_s1_R2_val_2.fq.gz \
2> bismark.err
```  

Here is the output
http://owl.fish.washington.edu/halfshell/bu-serine-wd/18-05-10/



---
[quick-edit](https://github.com/sr320/sr320.github.io/edit/master/_posts/2018-05-22-OAKLy-doekly.md)       
[raw](https://raw.githubusercontent.com/sr320/sr320.github.io/master/_posts/2018-05-22-OAKLy-doekly.md)


---

