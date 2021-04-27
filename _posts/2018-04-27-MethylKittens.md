In an attempt to start to visualize differences while waiting on hardware I brought some Bismark alignments into methyKit. 

Note this was done on subsetof data.

```
%%bash
find zr2096_*R1* \
| xargs basename -s _s1_R1_val_1.fq.gz | xargs -I{} /Applications/bioinfo/Bismark_v0.19.0/bismark \
--path_to_bowtie /Applications/bioinfo/bowtie2-2.3.4.1-macos-x86_64 \
--genome /Volumes/Serine/wd/18-03-15/genome \
--score_min L,0,-1.2 \
-u 1000000 \
-p 4 \
--non_directional \
-1 {}_s1_R1_val_1.fq.gz \
-2 {}_s1_R2_val_2.fq.gz \
2> bismark.err
```

```
%%bash
/Applications/bioinfo/Bismark_v0.19.0/deduplicate_bismark \
--bam -p \
*.bam \
2> dedup.err
```

then 
```
%%bash
find *deduplicated.bam \
| xargs basename -s _s1_R1_val_1_bismark_bt2_pe.deduplicated.bam | xargs -I{} /Applications/bioinfo/samtools-1.3.1/samtools \
sort {}_s1_R1_val_1_bismark_bt2_pe.deduplicated.bam -o {}_dedup.sorted.bam
```

These files then go to R.

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

getCorrelation(meth,plot=TRUE)


clusterSamples(meth, dist="correlation", method="ward", plot=TRUE)



hc = clusterSamples(meth, dist="correlation", method="ward", plot=FALSE)

PCASamples(meth, screeplot=TRUE)

PCASamples(meth)

myDiff=calculateDiffMeth(meth)

myDiff25p=getMethylDiff(myDiff,difference=25,qvalue=0.01)

myDiff50p <- getMethylDiff(myDiff,difference=50,qvalue=0.01)

write.table(myDiff50p, file = "analyses/myDiff50p.tab")

View(myDiff50p)
```

Note that install methyKit appears to be unreasonably challenging.
I think something like this might work.

```
install.packages("devtools")

library(devtools)

source("https://bioconductor.org/biocLite.R")
biocLite("methylKit")

install_github("al2na/methylKit", build_vignettes=FALSE, 
               repos=BiocInstaller::biocinstallRepos(),
               dependencies=TRUE)


library(methylKit)
```
Though some of that might be uneccessary.

Here is the spread
![pca](https://d.pr/i/qeJIV6+)

and loci that are >25% different

|     | chr         | start    | end      | strand | pvalue               | qvalue               | meth.diff         |
|-----|-------------|----------|----------|--------|----------------------|----------------------|-------------------|
| 20  | NC_035780.1 | 15379443 | 15379443 | +      | 2.47617043639947e-05 | 0.00212043085682093  | 38.0201765447667  |
| 71  | NC_035780.1 | 32656234 | 32656234 | -      | 0.000145109826063808 | 0.00669106256249466  | 38.8528138528139  |
| 109 | NC_035781.1 | 10426303 | 10426303 | +      | 1.6932361846814e-08  | 1.01498392064377e-05 | 57.843137254902   |
| 120 | NC_035781.1 | 19969110 | 19969110 | -      | 7.46299338989176e-06 | 0.00149119151424154  | -50.2380952380952 |
| 128 | NC_035781.1 | 24140050 | 24140050 | -      | 3.66748482653925e-05 | 0.00274802044881496  | -45.4887218045113 |
| 155 | NC_035781.1 | 52592719 | 52592719 | -      | 5.85906488648296e-06 | 0.00149119151424154  | 31.25             |
| 261 | NC_035783.1 | 25304577 | 25304577 | -      | 7.73779316320534e-05 | 0.00463829896441674  | -36               |
| 262 | NC_035783.1 | 25311877 | 25311877 | -      | 2.0828080039561e-05  | 0.0020808444139187   | -52.6181353767561 |
| 279 | NC_035783.1 | 37123157 | 37123157 | +      | 5.86830327998138e-05 | 0.00390851391523249  | 28.5714285714286  |
| 320 | NC_035784.1 | 32708904 | 32708904 | +      | 0.000258620596152993 | 0.00911918042668046  | 25.8064516129032  |
| 394 | NC_035784.1 | 59988672 | 59988672 | -      | 0.0001931217295665   | 0.00826884265468568  | 26.9230769230769  |
| 427 | NC_035784.1 | 79831996 | 79831996 | -      | 1.54243737109642e-05 | 0.00189025962164751  | 33.3333333333333  |
| 446 | NC_035784.1 | 96979210 | 96979210 | +      | 0.000227468123818534 | 0.00857623927586201  | -29.4117647058823 |
| 478 | NC_035785.1 | 37316796 | 37316796 | -      | 0.000102045172537635 | 0.00556085281824922  | -27.5862068965517 |
| 554 | NC_035787.1 | 47493411 | 47493411 | +      | 1.57670280519601e-05 | 0.00189025962164751  | -46.6525722339676 |
| 714 | NC_035789.1 | 10655735 | 10655735 | -      | 0.000133818035647935 | 0.00668459386152443  | 37.7104377104377  |


Next up is align the complete dataset and not just 1M reads / library.

