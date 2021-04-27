Here is a summary of the new data dump. 

>HiSeq folders for RNASeq and Mate Pair libraries;
NovaSeq run for all combined.  The MP libraries have a 800 bp insert and the RNA Seq libraries have a 300bp insert so they were loaded in a 10:1 MP:RNA into the NovaSeq.
There is a sample sheet loaded on the hard drive that should indicate sample identifiers.  Those identifiers are in the sequence files.

>For the HiSeq MP run we had 4 MP libraries, for the HiSeq and MiSeq RNA-seq runs we had 8 RNA-seq libraries. For the NovaSeq we had 5 RNA-seq and 4 MP due to the index collision.

<img src="http://eagle.fish.washington.edu/cnidarian/skitch/nightingales_1F59B97A.png" alt="nightingales_1F59B97A.png"/>

In the original data delivery (Hard Drive).
Only NovaSeq had fastq files....

<img src="http://eagle.fish.washington.edu/cnidarian/skitch/SampleSheet_csv_and_2017-09-01-Geoduck-NS-run_md_1F59BCB3.png" alt="SampleSheet_csv_and_2017-09-01-Geoduck-NS-run_md_1F59BCB3.png"/>

<img src="http://eagle.fish.washington.edu/cnidarian/skitch/nightingales_1F59BD26.png" alt="nightingales_1F59BD26.png"/>


<img src="http://eagle.fish.washington.edu/cnidarian/skitch/Inbox_–_roberts_sbr_gmail_com_1F59B9B9.png" alt="Inbox_–_roberts_sbr_gmail_com_1F59B9B9.png"/>


Looking at 4 `AD0002` files    

```
!/Applications/bioinfo/FastQC/fastqc -t 6 \
AD002_S9_L001_R1_001.fastq.gz \
AD002_S9_L001_R2_001.fastq.gz \
AD002_S9_L002_R1_001.fastq.gz \
AD002_S9_L002_R2_001.fastq.gz
```

Looks good except Nextera transposase

<img src="http://eagle.fish.washington.edu/cnidarian/skitch/MultiQC_Report_1F59CF5B.png" alt="MultiQC_Report_1F59CF5B.png"/>


---

As seen above there are some directories that have indices for RNA and MP libraries.


>It’s actually the other way around, the RNA-seq libraries were pulled out of this run so you should have fewer RNA-seq libraries, but all of the MP libraries. So the NR013_AD013 should just read as AD013. The sample sheet should have been updated to reflect that, but it looks like it was left in.

An effort that is not trivial is getting these files into a single directory.

The DNA MP NovaSeq libraries are found together on owl [here](http://owl.fish.washington.edu/halfshell/working-directory/17-09-01/).

--- 

# RNA files

are found [here](http://owl.fish.washington.edu/halfshell/working-directory/17-09-07/)

```
-rwxrwxrwx  1 sr320  staff   3.4M Sep  7 10:47 NR005_S4_L001_R1_001.fastq.gz
-rwxrwxrwx  1 sr320  staff   3.5M Sep  7 10:47 NR005_S4_L001_R2_001.fastq.gz
-rwxrwxrwx  1 sr320  staff   2.8M Sep  7 11:48 NR005_S4_L002_R1_001.fastq.gz
-rwxrwxrwx  1 sr320  staff   2.9M Sep  7 11:48 NR005_S4_L002_R2_001.fastq.gz
-rwxrwxrwx  1 sr320  staff   262M Sep  7 10:49 NR006_S3_L001_R1_001.fastq.gz
-rwxrwxrwx  1 sr320  staff   270M Sep  7 10:50 NR006_S3_L001_R2_001.fastq.gz
-rwxrwxrwx  1 sr320  staff   217M Sep  7 11:48 NR006_S3_L002_R1_001.fastq.gz
-rwxrwxrwx  1 sr320  staff   225M Sep  7 11:49 NR006_S3_L002_R2_001.fastq.gz
-rwxrwxrwx  1 sr320  staff    25M Sep  7 10:51 NR012_S1_L001_R1_001.fastq.gz
-rwxrwxrwx  1 sr320  staff    26M Sep  7 10:51 NR012_S1_L001_R2_001.fastq.gz
-rwxrwxrwx  1 sr320  staff    27M Sep  7 11:49 NR012_S1_L002_R1_001.fastq.gz
-rwxrwxrwx  1 sr320  staff    29M Sep  7 11:49 NR012_S1_L002_R2_001.fastq.gz
-rwxrwxrwx  1 sr320  staff   4.4M Sep  7 10:51 NR019_S7_L001_R1_001.fastq.gz
-rwxrwxrwx  1 sr320  staff   4.5M Sep  7 10:51 NR019_S7_L001_R2_001.fastq.gz
-rwxrwxrwx  1 sr320  staff   2.4M Sep  7 11:49 NR019_S7_L002_R1_001.fastq.gz
-rwxrwxrwx  1 sr320  staff   2.4M Sep  7 11:49 NR019_S7_L002_R2_001.fastq.gz
-rwxrwxrwx  1 sr320  staff   318M Sep  7 10:51 NR021_S8_L001_R1_001.fastq.gz
-rwxrwxrwx  1 sr320  staff   333M Sep  7 10:51 NR021_S8_L001_R2_001.fastq.gz
-rwxrwxrwx  1 sr320  staff   264M Sep  7 11:51 NR021_S8_L002_R1_001.fastq.gz
-rwxrwxrwx  1 sr320  staff   275M Sep  7 11:52 NR021_S8_L002_R2_001.fastq.gz
```

<img src="http://eagle.fish.washington.edu/cnidarian/skitch/Editing_sr320_github_io_2017-09-01-Geoduck-NovaSeq-files_md_at_master_·_sr320_sr320_github_io_1F6C3716.png" alt="Editing_sr320_github_io_2017-09-01-Geoduck-NovaSeq-files_md_at_master_·_sr320_sr320_github_io_1F6C3716.png"/>
