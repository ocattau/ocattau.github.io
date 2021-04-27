I have been working through Bismark with a few _Crassosstrea virginica_ datasets. This includes the BS data from the 2015 Oil exposure experiment, OA exposure -  gonad tissue (OAKL), and a full suite of library preps via Qiagen.

A few take aways is are 1) use the `-u` feature to work out analysis on subset, 2) the `--score_min` variable is important for allowing for mismatches, 3) the working directory approach seems to work good given the number of files. 

I have created a few notebooks for running most of the Bismark pipeline. 

- [SE, one file](https://github.com/sr320/nb-2018/blob/master/C_virginica/33-Bismark-pipeline-test.ipynb)
- [PE, fileset](https://github.com/sr320/nb-2018/blob/master/C_virginica/13-OAKL-fullpipe.ipynb)

Most cells do not need much attention besides this one..

```
%%bash
find /Users/sr320/Desktop/trim14/zr2096_*R1* \
| xargs basename -s _s1_R1_val_1.fq.gz | xargs -I{} /Applications/bioinfo/Bismark_v0.19.0/bismark \
--path_to_bowtie /Applications/bioinfo/bowtie2-2.3.4.1-macos-x86_64 \
--genome /Users/sr320/Dropbox/wd/18-03-15/genome \
--score_min L,0,-1.2 \
-u 10000 \
-p 2 \
--non_directional \
-1 /Users/sr320/Desktop/trim14/{}_s1_R1_val_1.fq.gz \
-2 /Users/sr320/Desktop/trim14/{}_s1_R2_val_2.fq.gz \
2> bismark.err
```

Here you need to be aware of file naming structure for `basename` and of course where the files are.

As far as some _results_.
For the **OAKL samples** sample 2 seems a bit off.

![summary](https://d.pr/i/Unsf2D+)

Alignments seem good. Here is one of the files.

![align](https://d.pr/i/QNJp7M+)

The M-bias plots bother me a bit.

![mbias](https://d.pr/i/xUfRxE+)

Plotting bedgraphs does not immediatly show OA impacts

![OA](https://d.pr/i/vk7dsA+)

But this is just mapping 10k reads, going up to 100k is evidient. 

![oamore](https://d.pr/i/juzeMP+)

---
The Qiagen library analysis is indicative of the different prep methods

![sum](https://d.pr/i/KhqDfe+)

![table](https://d.pr/i/apudUH+)

This might be more telling..

![summ](https://d.pr/i/Dc0fjO+)

another way of looking at it.

![sum2](https://d.pr/i/O2aOYf+)

though is worth pointing out these library have not been trimmed and likely need to be done in specific ways.