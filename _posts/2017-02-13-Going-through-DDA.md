---
layout: post
title: Going through DDA
date: '2017-02-13'
categories: Proteomics
tag: [gigas, oyster, proteomics, dda, linux, windows]
---

In an attempt to go from mzXML to Abacus, I took Rhonda's mzXML files on Emu, copied them to my directory and rand the following

```

/home/shared/comet/comet.2016012.linux.exe \
-Pcomet.params.high-low_de \
-DCg-Giga_cont_AA.fa \
*.mzXML \
&>> output.error.comet.log

find *xml | \
xargs basename -s .pep.xml | \
xargs -I {} /usr/tpp_install/tpp/bin/xinteract \
-dDECOY_ \
-N{} \
{}.pep.xml \
-p0.9 \
-OAp \
&>> output.error.xin.log

/usr/tpp_install/tpp/bin/ProteinProphet \
interact*.pep.xml \
interact-COMBINED.prot.xml \
&>> output.error.PP.log

java -Xmx16g -jar /home/shared/abacus/abacus.jar -p \
Abacus.params
```

The intact directory is available on owl here:    
<http://owl.fish.washington.edu/halfshell/index.php?dir=working-directory%2F17-02-13%2F>

Download the ABACUS output [here](http://owl.fish.washington.edu/halfshell/working-directory/17-02-13/ABACUS_output.tsv)

---

At the end of the day these are all the files.
```
steven@emu:~/bioinfo/021217$ ls
20161205_Sample_11A.mzXML
20161205_Sample_11A.pep.xml
20161205_Sample_11.mzXML
20161205_Sample_11.pep.xml
20161205_Sample_12A.mzXML
20161205_Sample_12A.pep.xml
20161205_Sample_12.mzXML
20161205_Sample_12.pep.xml
20161205_Sample_16A.mzXML
20161205_Sample_16A.pep.xml
20161205_Sample_16.mzXML
20161205_Sample_16.pep.xml
20161205_Sample_19A.mzXML
20161205_Sample_19A.pep.xml
20161205_Sample_19.mzXML
20161205_Sample_19.pep.xml
20161205_Sample_1A.mzXML
20161205_Sample_1A.pep.xml
20161205_sample_1.mzXML
20161205_sample_1.pep.xml
20161205_Sample_20A.mzXML
20161205_Sample_20A.pep.xml
20161205_Sample_20.mzXML
20161205_Sample_20.pep.xml
20161205_Sample_24A.mzXML
20161205_Sample_24A.pep.xml
20161205_Sample_24.mzXML
20161205_Sample_24.pep.xml
20161205_Sample_27A.mzXML
20161205_Sample_27A.pep.xml
20161205_Sample_27.mzXML
20161205_Sample_27.pep.xml
20161205_Sample_28A.mzXML
20161205_Sample_28A.pep.xml
20161205_Sample_28.mzXML
20161205_Sample_28.pep.xml
20161205_Sample_32A.mzXML
20161205_Sample_32A.pep.xml
20161205_Sample_32.mzXML
20161205_Sample_32.pep.xml
20161205_Sample_35A.mzXML
20161205_Sample_35A.pep.xml
20161205_Sample_35.mzXML
20161205_Sample_35.pep.xml
20161205_Sample_36A.mzXML
20161205_Sample_36A.pep.xml
20161205_Sample_36.mzXML
20161205_Sample_36.pep.xml
20161205_Sample_3A.mzXML
20161205_Sample_3A.pep.xml
20161205_Sample_3.mzXML
20161205_Sample_3.pep.xml
20161205_Sample_40A.mzXML
20161205_Sample_40A.pep.xml
20161205_Sample_40.mzXML
20161205_Sample_40.pep.xml
20161205_Sample_43A.mzXML
20161205_Sample_43A.pep.xml
20161205_Sample_43.mzXML
20161205_Sample_43.pep.xml
20161205_Sample_44A.mzXML
20161205_Sample_44A.pep.xml
20161205_Sample_44.mzXML
20161205_Sample_44.pep.xml
20161205_Sample_48A.mzXML
20161205_Sample_48A.pep.xml
20161205_Sample_48.mzXML
20161205_Sample_48.pep.xml
20161205_Sample_4A.mzXML
20161205_Sample_4A.pep.xml
20161205_Sample_4.mzXML
20161205_Sample_4.pep.xml
20161205_Sample_51A.mzXML
20161205_Sample_51A.pep.xml
20161205_Sample_51.mzXML
20161205_Sample_51.pep.xml
20161205_Sample_52A.mzXML
20161205_Sample_52A.pep.xml
20161205_Sample_52.mzXML
20161205_Sample_52.pep.xml
20161205_Sample_56A.mzXML
20161205_Sample_56A.pep.xml
20161205_Sample_56.mzXML
20161205_Sample_56.pep.xml
20161205_Sample_8A.mzXML
20161205_Sample_8A.pep.xml
20161205_Sample_8.mzXML
20161205_Sample_8.pep.xml
ABACUS_output.tsv
Abacus.param
Cg-Giga_cont_AA.fa
```
