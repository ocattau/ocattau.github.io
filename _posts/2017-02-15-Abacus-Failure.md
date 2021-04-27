---
layout: post
title: Abacus fail
date: '2017-02-15'
categories: Proteomics
tag: [gigas, oyster, proteomics]
---


Yesterday [Emma was concerned about Rhonda's Abacus file](https://github.com/sr320/LabDocs/issues/471#issuecomment-279855252). If fact there were [differences](https://github.com/sr320/LabDocs/issues/471#issuecomment-279858333). I created a [new Abacus parameter file](http://owl.fish.washington.edu/halfshell/working-directory/17-02-14b/Abacus-01.param)

```
#
# ABACUS parameter file
# Generated on: 2017Feb14_1919
#

# Name to give the database
dbName=Cg_Giga_cont_AA.fa

# Name of protXML file corresponding to merged/combined results
combinedFile=/home/steven/bioinfo/021417/interact-COMBINED.prot.xml

# The directory that contains the pepXML and protXML files
srcDir=/home/steven/bioinfo/021417

# The name of the file where results will be saved to
outputFile=/home/steven/bioinfo/021417/ABACUS_output.tsv

# The minimum PeptideProphet score the best peptide match of a protein must have
maxIniProbTH=0.99

# The minimum PeptideProphet score a peptide must have in order to be even considered by Abacus
iniProbTH=0.50

# E.P.I: Experimental Peptide-probability Inclusion threshold
# If a protein does not contain at least one peptide exceeding this PeptideProphet score, none of the
# peptide evidence for this protein will be considered. This is applied on an experiment by experiment case.
epiTH=0

# The minimum ProteinProphet score a protein group must have in the COMBINED file
minCombinedFilePw=0.90

# The path the the FASTA formatted file used for the original protein search
# Relative paths are allowed
fasta=Cg_Giga_cont_AA.fa

# If true, Abacus will write ALL protein IDs belonging to a group in the COMBINED file
# Protein IDs starting with ':::' are additional identifiers from the same protein group in
# the COMBINED file. The representative protein for the group does not start with ':::'
verboseResults=false

# The keep the HyperSQL database files that are created after the program is done
keepDB=false

# Should the peptide weights be recalculated in the individual experiment XML files.
# Useful for peptides that are highly degenerate within a single protein groups
recalcPepWts=false

# Spectral count data will be reported in NSAF format.
# NSAF = _N_ormalized _S_pectral _A_bundance _F_actor
# For a detailed explanation of this method refer to this pubmed link:
# http://www.ncbi.nlm.nih.gov/pubmed/20166708
# Abacus reports NSAF values multiplied by a scaling factor. This is done to
# control for numeric underflow (ie: really small numbers). The scaling factor
# that is used is called the NSAF_FACTOR and is reported during runtime in
# case you would like to rescale your data.
asNSAF=true

# If you are using decoy proteins in your searches, specify the first few
# characters of the label indicating decoy proteins here
decoyTag=DECOY_

# Output format that will be produced by this parameter file
output=Default

```

In then proceed to create a new working directory and move all the files created as [doing this](https://sr320.github.io/Going-through-DDA/)

I proceed to add the new Abacus file (and remove the old one) and ran 

```
java -Xmx16g -jar /home/shared/abacus/abacus.jar -p \
Abacus-01.param
```

Here is [stdout](https://gist.github.com/sr320/f11553a40bcb1fb6f38ae100f8b3b379)

of concern:

```
 Adding data from X20161205_SAMPLE_8A

Creating NSAF values table (protein-centric)
  NSAF_FACTOR = 10^5 = 100000.0
java.sql.SQLSyntaxErrorException: user lacks privilege or object not found: NAN
	at org.hsqldb.jdbc.JDBCUtil.sqlException(Unknown Source)
	at org.hsqldb.jdbc.JDBCUtil.sqlException(Unknown Source)
	at org.hsqldb.jdbc.JDBCStatement.fetchResult(Unknown Source)
	at org.hsqldb.jdbc.JDBCStatement.executeUpdate(Unknown Source)
	at abacus.hyperSQLObject.getNSAF_values_prot(hyperSQLObject.java:2961)
	at abacus.abacus.main(abacus.java:221)
	at mainFunction.mainFunction.main(mainFunction.java:49)
Caused by: org.hsqldb.HsqlException: user lacks privilege or object not found: NAN
	at org.hsqldb.error.Error.error(Unknown Source)
	at org.hsqldb.error.Error.error(Unknown Source)
	at org.hsqldb.ExpressionColumn.checkColumnsResolved(Unknown Source)
	at org.hsqldb.ParserDML.resolveUpdateExpressions(Unknown Source)
	at org.hsqldb.ParserDML.compileUpdateStatement(Unknown Source)
	at org.hsqldb.ParserCommand.compilePart(Unknown Source)
	at org.hsqldb.ParserCommand.compileStatements(Unknown Source)
	at org.hsqldb.Session.executeDirectStatement(Unknown Source)
	at org.hsqldb.Session.execute(Unknown Source)
	... 5 more
```
	

And no output from Abacus. 


