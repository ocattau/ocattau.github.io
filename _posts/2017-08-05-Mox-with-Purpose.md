Having spent a day in Hyak, I think I know have a workflow that makes sense. 

In short, use a `date` variable to name working directory and sbatch scripts, using `rsync` from owl to sync mox directory to accessible urls. 

1) log into mox. 

2) Navigate to user directory
```
[sr320@mox2 ~]$ cd /gscratch/srlab/sr320/
[sr320@mox2 sr320]$ ls
analyses  blastdb  data  jobs
[sr320@mox2 sr320]$
```
3) set today variable
```
today=`date +%m%d_%H%M`
```

4) Basing sbatch script on prior one. 
```
cp jobs/0804_1818.sh jobs/$today.sh
```

5) nano to edit 

6 set working directory
```
mkdir analyses/$today
```

7 ) `sbatch -p srlab -A srlab 0804_1818.sh`

8) wait, cross fingers, repeat.
 
9) log into Owl via ssh.

10 sync my mox directory to owl
```
rsync -avz sr320@mox.hyak.uw.edu:/gscratch/srlab/sr320/ /var/services/web/halfshell/bu-mox/
```

