While we received a lot of files in HiSeq folder, none were fastq, thus Sam downloaded from BaseSpace. And it is ugly.

see also [this jupyter nb](https://github.com/sr320/nb-2017/blob/master/P_generosa/28-HiSeq-files.ipynb)

<img src="http://eagle.fish.washington.edu/cnidarian/skitch/Geoduck_HiSeq_1F5A1426.png" alt="Geoduck_HiSeq_1F5A1426.png"/>

```
D-172-25-149-231:Ironman-35682656 sr320$ ls
Geoduck1_1-43499537	Geoduck3_1-43493557	Geoduck5_1-43498555	Geoduck7_1-43493558
Geoduck1_2-43501508	Geoduck3_2-43497583	Geoduck5_2-43486134	Geoduck7_2-43498556
Geoduck1_3-43495567	Geoduck3_3-43489715	Geoduck5_3-43497581	Geoduck7_3-43499536
Geoduck1_4-43483166	Geoduck3_4-43499538	Geoduck5_4-43498557	Geoduck7_4-43494561
Geoduck1_5-43489716	Geoduck3_5-43500515	Geoduck5_5-43501509	Geoduck7_5-43498560
Geoduck1_6-43484188	Geoduck3_6-43492568	Geoduck5_6-43495570	Geoduck7_6-43484189
Geoduck1_7-43492569	Geoduck3_7-43496563	Geoduck5_7-43484190	Geoduck7_7-43496564
Geoduck1_8-43490641	Geoduck3_8-43484191	Geoduck5_8-43484192	Geoduck7_8-43484193
Geoduck2_1-43497582	Geoduck4_1-43495568	Geoduck6_1-43494560	Geoduck8_1-43492567
Geoduck2_2-43491623	Geoduck4_2-43484187	Geoduck6_2-43491624	Geoduck8_2-43496562
Geoduck2_3-43492566	Geoduck4_3-43498554	Geoduck6_3-43496561	Geoduck8_3-43502518
Geoduck2_4-43486135	Geoduck4_4-43485200	Geoduck6_4-43498558	Geoduck8_4-43490640
Geoduck2_5-43486136	Geoduck4_5-43498559	Geoduck6_5-43495569	Geoduck8_5-43497584
Geoduck2_6-43494562	Geoduck4_6-43500516	Geoduck6_6-43502519	Geoduck8_6-43491625
Geoduck2_7-43500517	Geoduck4_7-43485201	Geoduck6_7-43489717	Geoduck8_7-43500518
Geoduck2_8-43485202	Geoduck4_8-43497585	Geoduck6_8-43500519	Geoduck8_8-43483167
D-172-25-149-231:Ironman-35682656 sr320$ pwd
/Volumes/web-1/nightingales/Geoduck_HiSeq/170228_ST-K00104_0381_AHHHWNBBXX/Data/Ironman-35682656
```
Here are half of the HiSeq Files, the RNA ones.


```
Geoduck-ctenidia-RNA-1_S3_L001_R1_001.fastq.gz
Geoduck-ctenidia-RNA-1_S3_L001_R2_001.fastq.gz
Geoduck-ctenidia-RNA-2_S11_L002_R1_001.fastq.gz
Geoduck-ctenidia-RNA-2_S11_L002_R2_001.fastq.gz
Geoduck-ctenidia-RNA-3_S19_L003_R1_001.fastq.gz
Geoduck-ctenidia-RNA-3_S19_L003_R2_001.fastq.gz
Geoduck-ctenidia-RNA-4_S27_L004_R1_001.fastq.gz
Geoduck-ctenidia-RNA-4_S27_L004_R2_001.fastq.gz
Geoduck-ctenidia-RNA-5_S35_L005_R1_001.fastq.gz
Geoduck-ctenidia-RNA-5_S35_L005_R2_001.fastq.gz
Geoduck-ctenidia-RNA-6_S43_L006_R1_001.fastq.gz
Geoduck-ctenidia-RNA-6_S43_L006_R2_001.fastq.gz
Geoduck-ctenidia-RNA-7_S51_L007_R1_001.fastq.gz
Geoduck-ctenidia-RNA-7_S51_L007_R2_001.fastq.gz
Geoduck-ctenidia-RNA-8_S59_L008_R1_001.fastq.gz
Geoduck-ctenidia-RNA-8_S59_L008_R2_001.fastq.gz
Geoduck-gonad-RNA-1_S1_L001_R1_001.fastq.gz
Geoduck-gonad-RNA-1_S1_L001_R2_001.fastq.gz
Geoduck-gonad-RNA-2_S9_L002_R1_001.fastq.gz
Geoduck-gonad-RNA-2_S9_L002_R2_001.fastq.gz
Geoduck-gonad-RNA-3_S17_L003_R1_001.fastq.gz
Geoduck-gonad-RNA-3_S17_L003_R2_001.fastq.gz
Geoduck-gonad-RNA-4_S25_L004_R1_001.fastq.gz
Geoduck-gonad-RNA-4_S25_L004_R2_001.fastq.gz
Geoduck-gonad-RNA-5_S33_L005_R1_001.fastq.gz
Geoduck-gonad-RNA-5_S33_L005_R2_001.fastq.gz
Geoduck-gonad-RNA-6_S41_L006_R1_001.fastq.gz
Geoduck-gonad-RNA-6_S41_L006_R2_001.fastq.gz
Geoduck-gonad-RNA-7_S49_L007_R1_001.fastq.gz
Geoduck-gonad-RNA-7_S49_L007_R2_001.fastq.gz
Geoduck-gonad-RNA-8_S57_L008_R1_001.fastq.gz
Geoduck-gonad-RNA-8_S57_L008_R2_001.fastq.gz
Geoduck-heart-RNA-1_S2_L001_R1_001.fastq.gz
Geoduck-heart-RNA-1_S2_L001_R2_001.fastq.gz
Geoduck-heart-RNA-2_S10_L002_R1_001.fastq.gz
Geoduck-heart-RNA-2_S10_L002_R2_001.fastq.gz
Geoduck-heart-RNA-3_S18_L003_R1_001.fastq.gz
Geoduck-heart-RNA-3_S18_L003_R2_001.fastq.gz
Geoduck-heart-RNA-4_S26_L004_R1_001.fastq.gz
Geoduck-heart-RNA-4_S26_L004_R2_001.fastq.gz
Geoduck-heart-RNA-5_S34_L005_R1_001.fastq.gz
Geoduck-heart-RNA-5_S34_L005_R2_001.fastq.gz
Geoduck-heart-RNA-6_S42_L006_R1_001.fastq.gz
Geoduck-heart-RNA-6_S42_L006_R2_001.fastq.gz
Geoduck-heart-RNA-7_S50_L007_R1_001.fastq.gz
Geoduck-heart-RNA-7_S50_L007_R2_001.fastq.gz
Geoduck-heart-RNA-8_S58_L008_R1_001.fastq.gz
Geoduck-heart-RNA-8_S58_L008_R2_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-123-1_S6_L001_R1_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-123-1_S6_L001_R2_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-123-2_S14_L002_R1_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-123-2_S14_L002_R2_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-123-3_S22_L003_R1_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-123-3_S22_L003_R2_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-123-4_S30_L004_R1_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-123-4_S30_L004_R2_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-123-5_S38_L005_R1_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-123-5_S38_L005_R2_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-123-6_S46_L006_R1_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-123-6_S46_L006_R2_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-123-7_S54_L007_R1_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-123-7_S54_L007_R2_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-123-8_S62_L008_R1_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-123-8_S62_L008_R2_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-124-1_S7_L001_R1_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-124-1_S7_L001_R2_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-124-2_S15_L002_R1_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-124-2_S15_L002_R2_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-124-3_S23_L003_R1_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-124-3_S23_L003_R2_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-124-4_S31_L004_R1_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-124-4_S31_L004_R2_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-124-5_S39_L005_R1_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-124-5_S39_L005_R2_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-124-6_S47_L006_R1_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-124-6_S47_L006_R2_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-124-7_S55_L007_R1_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-124-7_S55_L007_R2_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-124-8_S63_L008_R1_001.fastq.gz
Geoduck-juvenile-ambient-exposure-RNA-EPI-124-8_S63_L008_R2_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-115-1_S4_L001_R1_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-115-1_S4_L001_R2_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-115-2_S12_L002_R1_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-115-2_S12_L002_R2_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-115-3_S20_L003_R1_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-115-3_S20_L003_R2_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-115-4_S28_L004_R1_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-115-4_S28_L004_R2_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-115-5_S36_L005_R1_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-115-5_S36_L005_R2_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-115-6_S44_L006_R1_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-115-6_S44_L006_R2_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-115-7_S52_L007_R1_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-115-7_S52_L007_R2_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-115-8_S60_L008_R1_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-115-8_S60_L008_R2_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-116-1_S5_L001_R1_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-116-1_S5_L001_R2_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-116-2_S13_L002_R1_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-116-2_S13_L002_R2_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-116-3_S21_L003_R1_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-116-3_S21_L003_R2_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-116-4_S29_L004_R1_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-116-4_S29_L004_R2_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-116-5_S37_L005_R1_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-116-5_S37_L005_R2_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-116-6_S45_L006_R1_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-116-6_S45_L006_R2_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-116-7_S53_L007_R1_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-116-7_S53_L007_R2_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-116-8_S61_L008_R1_001.fastq.gz
Geoduck-juvenile-OA-exposure-RNA-EPI-116-8_S61_L008_R2_001.fastq.gz
Geoduck-larvae-day5-RNA-EPI-99-1_S8_L001_R1_001.fastq.gz
Geoduck-larvae-day5-RNA-EPI-99-1_S8_L001_R2_001.fastq.gz
Geoduck-larvae-day5-RNA-EPI-99-2_S16_L002_R1_001.fastq.gz
Geoduck-larvae-day5-RNA-EPI-99-2_S16_L002_R2_001.fastq.gz
Geoduck-larvae-day5-RNA-EPI-99-3_S24_L003_R1_001.fastq.gz
Geoduck-larvae-day5-RNA-EPI-99-3_S24_L003_R2_001.fastq.gz
Geoduck-larvae-day5-RNA-EPI-99-4_S32_L004_R1_001.fastq.gz
Geoduck-larvae-day5-RNA-EPI-99-4_S32_L004_R2_001.fastq.gz
Geoduck-larvae-day5-RNA-EPI-99-5_S40_L005_R1_001.fastq.gz
Geoduck-larvae-day5-RNA-EPI-99-5_S40_L005_R2_001.fastq.gz
Geoduck-larvae-day5-RNA-EPI-99-6_S48_L006_R1_001.fastq.gz
Geoduck-larvae-day5-RNA-EPI-99-6_S48_L006_R2_001.fastq.gz
Geoduck-larvae-day5-RNA-EPI-99-7_S56_L007_R1_001.fastq.gz
Geoduck-larvae-day5-RNA-EPI-99-7_S56_L007_R2_001.fastq.gz
Geoduck-larvae-day5-RNA-EPI-99-8_S64_L008_R1_001.fastq.gz
Geoduck-larvae-day5-RNA-EPI-99-8_S64_L008_R2_001.fastq.gz
```


This files via web facing owl [here](http://owl.fish.washington.edu/halfshell/working-directory/17-09-01b/).



### The other half are MP DNA libraries

```
./Geoduck1_9-43483188/Geoduck-NMP-gDNA-1_S1_L001_R2_001.fastq.gz
./Geoduck1_9-43483188/Geoduck-NMP-gDNA-1_S1_L001_R1_001.fastq.gz
./Geoduck2_10-43489748/Geoduck-NMP-gDNA-2to4kb-2_S6_L002_R1_001.fastq.gz
./Geoduck2_10-43489748/Geoduck-NMP-gDNA-2to4kb-2_S6_L002_R2_001.fastq.gz
./Geoduck1_10-43500557/Geoduck-NMP-gDNA-2to4kb-1_S2_L001_R2_001.fastq.gz
./Geoduck1_10-43500557/Geoduck-NMP-gDNA-2to4kb-1_S2_L001_R1_001.fastq.gz
./Geoduck2_9-43495606/Geoduck-NMP-gDNA-2_S5_L002_R2_001.fastq.gz
./Geoduck2_9-43495606/Geoduck-NMP-gDNA-2_S5_L002_R1_001.fastq.gz
./Geoduck3_10-43491664/Geoduck-NMP-gDNA-2to4kb-3_S10_L003_R2_001.fastq.gz
./Geoduck3_10-43491664/Geoduck-NMP-gDNA-2to4kb-3_S10_L003_R1_001.fastq.gz
./Geoduck7_10-43484224/Geoduck-NMP-gDNA-2to4kb-7_S26_L007_R1_001.fastq.gz
./Geoduck7_10-43484224/Geoduck-NMP-gDNA-2to4kb-7_S26_L007_R2_001.fastq.gz
./Geoduck5_10-43485247/Geoduck-NMP-gDNA-2to4kb-5_S18_L005_R1_001.fastq.gz
./Geoduck5_10-43485247/Geoduck-NMP-gDNA-2to4kb-5_S18_L005_R2_001.fastq.gz
./Geoduck6_10-43493587/Geoduck-NMP-gDNA-2to4kb-6_S22_L006_R1_001.fastq.gz
./Geoduck6_10-43493587/Geoduck-NMP-gDNA-2to4kb-6_S22_L006_R2_001.fastq.gz
./Geoduck4_11-43483194/Geoduck-NMP-gDNA-5to7kb-4_S15_L004_R1_001.fastq.gz
./Geoduck4_11-43483194/Geoduck-NMP-gDNA-5to7kb-4_S15_L004_R2_001.fastq.gz
./Geoduck1_11-43485248/Geoduck-NMP-gDNA-5to7kb-1_S3_L001_R1_001.fastq.gz
./Geoduck1_11-43485248/Geoduck-NMP-gDNA-5to7kb-1_S3_L001_R2_001.fastq.gz
./Geoduck2_11-43498595/Geoduck-NMP-gDNA-5to7kb-2_S7_L002_R1_001.fastq.gz
./Geoduck2_11-43498595/Geoduck-NMP-gDNA-5to7kb-2_S7_L002_R2_001.fastq.gz
./Geoduck3_11-43498596/Geoduck-NMP-gDNA-5to7kb-3_S11_L003_R1_001.fastq.gz
./Geoduck3_11-43498596/Geoduck-NMP-gDNA-5to7kb-3_S11_L003_R2_001.fastq.gz
./Geoduck4_10-43494609/Geoduck-NMP-gDNA-2to4kb-4_S14_L004_R2_001.fastq.gz
./Geoduck4_10-43494609/Geoduck-NMP-gDNA-2to4kb-4_S14_L004_R1_001.fastq.gz
./Geoduck3_9-43486166/Geoduck-NMP-gDNA-3_S9_L003_R1_001.fastq.gz
./Geoduck3_9-43486166/Geoduck-NMP-gDNA-3_S9_L003_R2_001.fastq.gz
./Geoduck8_10-43484225/Geoduck-NMP-gDNA-2to4kb-8_S30_L008_R1_001.fastq.gz
./Geoduck8_10-43484225/Geoduck-NMP-gDNA-2to4kb-8_S30_L008_R2_001.fastq.gz
./Geoduck4_9-43498594/Geoduck-NMP-gDNA-4_S13_L004_R1_001.fastq.gz
./Geoduck4_9-43498594/Geoduck-NMP-gDNA-4_S13_L004_R2_001.fastq.gz
./Geoduck5_9-43495612/Geoduck-NMP-gDNA-5_S17_L005_R1_001.fastq.gz
./Geoduck5_9-43495612/Geoduck-NMP-gDNA-5_S17_L005_R2_001.fastq.gz
./Geoduck5_11-43498597/Geoduck-NMP-gDNA-5to7kb-5_S19_L005_R2_001.fastq.gz
./Geoduck5_11-43498597/Geoduck-NMP-gDNA-5to7kb-5_S19_L005_R1_001.fastq.gz
./Geoduck7_11-43493588/Geoduck-NMP-gDNA-5to7kb-7_S27_L007_R1_001.fastq.gz
./Geoduck7_11-43493588/Geoduck-NMP-gDNA-5to7kb-7_S27_L007_R2_001.fastq.gz
./Geoduck8_11-43497614/Geoduck-NMP-gDNA-5to7kb-8_S31_L008_R1_001.fastq.gz
./Geoduck8_11-43497614/Geoduck-NMP-gDNA-5to7kb-8_S31_L008_R2_001.fastq.gz
./Geoduck3_12-43493589/Geoduck-NMP-gDNA-8to10kb-3_S12_L003_R1_001.fastq.gz
./Geoduck3_12-43493589/Geoduck-NMP-gDNA-8to10kb-3_S12_L003_R2_001.fastq.gz
./Geoduck5_12-43484226/Geoduck-NMP-gDNA-8to10kb-5_S20_L005_R1_001.fastq.gz
./Geoduck5_12-43484226/Geoduck-NMP-gDNA-8to10kb-5_S20_L005_R2_001.fastq.gz
./Geoduck1_12-43494613/Geoduck-NMP-gDNA-8to10kb-1_S4_L001_R1_001.fastq.gz
./Geoduck1_12-43494613/Geoduck-NMP-gDNA-8to10kb-1_S4_L001_R2_001.fastq.gz
./Geoduck2_12-43489752/Geoduck-NMP-gDNA-8to10kb-2_S8_L002_R1_001.fastq.gz
./Geoduck2_12-43489752/Geoduck-NMP-gDNA-8to10kb-2_S8_L002_R2_001.fastq.gz
./Geoduck6_11-43496601/Geoduck-NMP-gDNA-5to7kb-6_S23_L006_R2_001.fastq.gz
./Geoduck6_11-43496601/Geoduck-NMP-gDNA-5to7kb-6_S23_L006_R1_001.fastq.gz
./Geoduck6_9-43498598/Geoduck-NMP-gDNA-6_S21_L006_R1_001.fastq.gz
./Geoduck6_9-43498598/Geoduck-NMP-gDNA-6_S21_L006_R2_001.fastq.gz
./Geoduck7_9-43501547/Geoduck-NMP-gDNA-7_S25_L007_R1_001.fastq.gz
./Geoduck7_9-43501547/Geoduck-NMP-gDNA-7_S25_L007_R2_001.fastq.gz
./Geoduck6_12-43494614/Geoduck-NMP-gDNA-8to10kb-6_S24_L006_R1_001.fastq.gz
./Geoduck6_12-43494614/Geoduck-NMP-gDNA-8to10kb-6_S24_L006_R2_001.fastq.gz
./Geoduck4_12-43497615/Geoduck-NMP-gDNA-8to10kb-4_S16_L004_R1_001.fastq.gz
./Geoduck4_12-43497615/Geoduck-NMP-gDNA-8to10kb-4_S16_L004_R2_001.fastq.gz
./Geoduck8_9-43483196/Geoduck-NMP-gDNA-8_S29_L008_R1_001.fastq.gz
./Geoduck8_9-43483196/Geoduck-NMP-gDNA-8_S29_L008_R2_001.fastq.gz
./Geoduck7_12-43495615/Geoduck-NMP-gDNA-8to10kb-7_S28_L007_R2_001.fastq.gz
./Geoduck7_12-43495615/Geoduck-NMP-gDNA-8to10kb-7_S28_L007_R1_001.fastq.gz
./Geoduck8_12-43486170/Geoduck-NMP-gDNA-8to10kb-8_S32_L008_R2_001.fastq.gz
./Geoduck8_12-43486170/Geoduck-NMP-gDNA-8to10kb-8_S32_L008_R1_001.fastq.gz
```


and available online [here](http://owl.fish.washington.edu/halfshell/working-directory/17-09-06/)













