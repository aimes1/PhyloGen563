# Final Project Reproducible Script

## Create multiple sequence alignment files 

### Prepare sequence files for alignment 
1. Compiled sequence data are from selected *Vibrio fischeri* strains in the [Vfischeri_rscS_DNAfasta.fasta](data/large_files/Vfischeri_rscS_DNAfasta.fasta) file. This file contains the DNA sequence of the annotated *rscS* gene region from the listed *V. fischeri* strain. 

Note that the path commands below are shown as local paths on the device, and do not correlate to where the data is stored in the github. File names, however, are consistent and can be used to determine which file is being used. 

2. Use the above file as the input to align sequences using both the MUSCLE program and the CLUSTALW program as specified below. 

Note: Use strain MJ8.1 as the outgroup strain for *rscS* analysis. This is a *V. fischeri* that has a divergent RscS as it is a fish symbiont rather than squid symbiont like the other strains. MJ8.1 is unable to colonize squid ([Rotman et al. 2019](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6456852/))

Note: Several software elements were run on Jackie Lemaire's MacBook Air as the machine due to incompatibility with the M2 chip on my machine that I was unable to resolve by the end of the project. Commands, choices, and physical input were made by myself. This was done for MUSCLE, CLUSTALW, and IQ-TREE.  

### Alignment method 1: MUSCLE
1. Download [MUSLCE](https://github.com/rcedgar/muscle/releases/tag/5.1.0) as the file [muscle5.1.macos_intel64](https://github.com/rcedgar/muscle/releases/download/5.1.0/muscle5.1.macos_intel64). 

2. Run MUSCLE on data using input: 
```shell
jacquelinelemaire@Jacquelines-Air ~ % muscle -align /Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNAfasta.fasta -output ~/Documents/phylo_class/rscS/Vfischeri_rscS_DNA_muscle-aligned.fasta
```

3. The output reads out: 
```shell
jacquelinelemaire@Jacquelines-Air ~ % muscle -align /Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNAfasta.fasta -output ~/Documents/phylo_class/rscS/Vfischeri_rscS_DNA_muscle-aligned.fasta

muscle 5.1.osx64 []  8.6Gb RAM, 8 cores
Built Feb 10 2022 07:52:24
(C) Copyright 2004-2021 Robert C. Edgar.
https://drive5.com

Input: 12 seqs, avg length 2784, max 2802

00:00 6.0Mb  CPU has 8 cores, running 8 threads
00:13 347Mb   100.0% Calc posteriors
00:14 380Mb   100.0% Consistency (1/2)
00:14 380Mb   100.0% Consistency (2/2)
00:14 380Mb   100.0% UPGMA5
00:17 487Mb   100.0% Refining
jacquelinelemaire@Jacquelines-Air ~ %
```

4. The MUSCLE multiple sequence alignment stored in the file [Vfischeri_rscS_DNA_muscle-aligned.fasta](results/rscS_multiple-seq-alignments/Vfischeri_rscS_DNA_muscle-aligned.fasta)

### Alignment method 2: CLUSTALW
1. Download CLUSTALW file clustalw-2.1-macosx.dmg as modified on 2010-11-17. 
   A. Link to download file: http://www.clustal.org/download/current/clustalw-2.1-macosx.dmg
   B. Running commands for CLUSTAL 2.0.12 are found in the [docs](http://www.clustal.org/download/clustalw_help.txt).
   C. The input file is the 12 nucleotide sequence FASTA file: [Vfischeri_rscS_DNAfasta.fasta](PhyloGen563/data/large_files/Vfischeri_rscS_DNAfasta.fasta)

2. Run the input command to align sequences: 
```shell
jacquelinelemaire@Jacquelines-Air ~ % clustalw2 -ALIGN -INFILE=/Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNAfasta.fasta -OUTFILE=/Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNA-clustal-aligned.fasta -OUTPUT=FASTA
```

1. The output reads as follows: 
```shell
CLUSTAL 2.1 Multiple Sequence Alignments


Sequence format is Pearson
Sequence 1: EM17        2784 bp
Sequence 2: EM18        2784 bp
Sequence 3: EM24        2784 bp
Sequence 4: EM30        2784 bp
Sequence 5: ES114       2784 bp
Sequence 6: ES213       2783 bp
Sequence 7: KB2B1       2783 bp
Sequence 8: MB11B1      2783 bp
Sequence 9: MB13B1      2784 bp
Sequence 10: MB14A1      2772 bp
Sequence 11: MJ102       2784 bp
Sequence 12: MJ8.1       2802 bp
Start of Pairwise alignments
Aligning...

Sequences (1:2) Aligned. Score:  99
Sequences (1:3) Aligned. Score:  98
Sequences (1:4) Aligned. Score:  98
Sequences (1:5) Aligned. Score:  97
Sequences (1:6) Aligned. Score:  99
Sequences (1:7) Aligned. Score:  99
Sequences (1:8) Aligned. Score:  99
Sequences (1:9) Aligned. Score:  99
Sequences (1:10) Aligned. Score:  99
Sequences (1:11) Aligned. Score:  97
Sequences (1:12) Aligned. Score:  89
Sequences (2:3) Aligned. Score:  98
Sequences (2:4) Aligned. Score:  98
Sequences (2:5) Aligned. Score:  97
Sequences (2:6) Aligned. Score:  98
Sequences (2:7) Aligned. Score:  98
Sequences (2:8) Aligned. Score:  98
Sequences (2:9) Aligned. Score:  99
Sequences (2:10) Aligned. Score:  99
Sequences (2:11) Aligned. Score:  97
Sequences (2:12) Aligned. Score:  88
Sequences (3:4) Aligned. Score:  99
Sequences (3:5) Aligned. Score:  97
Sequences (3:6) Aligned. Score:  98
Sequences (3:7) Aligned. Score:  98
Sequences (3:8) Aligned. Score:  98
Sequences (3:9) Aligned. Score:  98
Sequences (3:10) Aligned. Score:  98
Sequences (3:11) Aligned. Score:  97
Sequences (3:12) Aligned. Score:  89
Sequences (4:5) Aligned. Score:  97
Sequences (4:6) Aligned. Score:  98
Sequences (4:7) Aligned. Score:  98
Sequences (4:8) Aligned. Score:  98
Sequences (4:9) Aligned. Score:  98
Sequences (4:10) Aligned. Score:  98
Sequences (4:11) Aligned. Score:  97
Sequences (4:12) Aligned. Score:  89
Sequences (5:6) Aligned. Score:  97
Sequences (5:7) Aligned. Score:  97
Sequences (5:8) Aligned. Score:  97
Sequences (5:9) Aligned. Score:  97
Sequences (5:10) Aligned. Score:  98
Sequences (5:11) Aligned. Score:  99
Sequences (5:12) Aligned. Score:  90
Sequences (6:7) Aligned. Score:  100
Sequences (6:8) Aligned. Score:  100
Sequences (6:9) Aligned. Score:  99
Sequences (6:10) Aligned. Score:  99
Sequences (6:11) Aligned. Score:  97
Sequences (6:12) Aligned. Score:  89
Sequences (7:8) Aligned. Score:  100
Sequences (7:9) Aligned. Score:  99
Sequences (7:10) Aligned. Score:  99
Sequences (7:11) Aligned. Score:  97
Sequences (7:12) Aligned. Score:  89
Sequences (8:9) Aligned. Score:  99
Sequences (8:10) Aligned. Score:  99
Sequences (8:11) Aligned. Score:  97
Sequences (8:12) Aligned. Score:  89
Sequences (9:10) Aligned. Score:  99
Sequences (9:11) Aligned. Score:  98
Sequences (9:12) Aligned. Score:  89
Sequences (10:11) Aligned. Score:  98
Sequences (10:12) Aligned. Score:  89
Sequences (11:12) Aligned. Score:  90
Guide tree file created:   [/Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNAfasta.dnd]

There are 11 groups
Start of Multiple Alignment

Aligning...
Group 1: Sequences:   2      Score:52877
Group 2: Sequences:   2      Score:52877
Group 3: Sequences:   2      Score:52820
Group 4: Sequences:   2      Score:52461
Group 5: Sequences:   4      Score:52549
Group 6: Sequences:   2      Score:52877
Group 7: Sequences:   3      Score:52877
Group 8: Sequences:   7      Score:52424
Group 9: Sequences:   9      Score:52365
Group 10: Sequences:  11      Score:52155
Group 11: Sequences:  12      Score:48862
Alignment Score 1150741
firstres = 1 lastres = 2808
FASTA file created!

Fasta-Alignment file created    [/Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNA-clustal-aligned.fasta]
```
1. Output file stored as [Vfischeri_rscS_DNA-clustal-aligned.fasta](results/rscS_multiple-seq-alignments/Vfischeri_rscS_DNA-clustal-aligned.fasta). 


## Estimating Distance and Parsimony

### Estimate a distance-based tree using software R package _ape_

* _ape_ is one of the most widely used phylogenetic software. It is an R package and it has a huge variety of functions
* In particular, it will be used here for distance-based tree estimation methods
  * [Full documentation](https://cran.r-project.org/web/packages/ape/index.html)
  * Procedure here based on this [tutorial](https://adegenet.r-forge.r-project.org/files/MSc-intro-phylo.1.1.pdf)
* Summary of Software R package _ape_
  * Main distance functions:
    * `nj` (`ape` package): the classical Neighbor-Joining algorithm.
    * [`bionj`](https://www.rdocumentation.org/packages/ape/versions/5.4-1/topics/BIONJ) (`ape`): an improved version of Neighbor-Joining: [Gascuel 1997](https://pubmed.ncbi.nlm.nih.gov/9254330/). It uses information on variances of evolutionary distances
    * [`fastme.bal` and `fastme.ols`](https://www.rdocumentation.org/packages/ape/versions/5.4-1/topics/FastME) (`ape`): minimum evolution algorithms: [Desper and Gascuel, 2002](https://pubmed.ncbi.nlm.nih.gov/12487758/)
    * `hclust` (`stats`): classical hierarchical clustering algorithms including single linkage, complete linkage, UPGMA, and others.


1. Within RStudio, install necessary packages:
   A. The following are the packages: 
```r
install.packages("adegenet", dep=TRUE)
install.packages("phangorn", dep=TRUE)
``` 
   B. The screen output is: 
```r
install.packages("adegenet", dep=TRUE)

trying URL 'https://cran.rstudio.com/bin/macosx/big-sur-arm64/contrib/4.3/adegenet_2.1.10.tgz'
Content type 'application/x-gzip' length 2855081 bytes (2.7 MB)
==================================================
downloaded 2.7 MB

The downloaded binary packages are in
	/var/folders/gk/9plsjd_s07b7jlmhsnjy4yxh0000gn/T//RtmpGhzj78/downloaded_packages

install.packages("phangorn", dep=TRUE)

Warning in install.packages :
  dependencies ‘Biostrings’, ‘seqLogo’ are not available
trying URL 'https://cran.rstudio.com/bin/macosx/big-sur-arm64/contrib/4.3/phangorn_2.11.1.tgz'
Content type 'application/x-gzip' length 3408275 bytes (3.3 MB)
==================================================
downloaded 3.3 MB


The downloaded binary packages are in
	/var/folders/gk/9plsjd_s07b7jlmhsnjy4yxh0000gn/T//RtmpGhzj78/downloaded_packages
```

2. Load the packages
   A. Input the following commands: 
```r
library(ape)
library(adegenet)
library(phangorn)
```
   B. The screen output will be: 
```r
library(ape)
library(adegenet)
Loading required package: ade4

   /// adegenet 2.1.10 is loaded ////////////

   > overview: '?adegenet'
   > tutorials/doc/questions: 'adegenetWeb()' 
   > bug reports/feature requests: adegenetIssues()

library(phangorn)
Attaching package: ‘phangorn’

The following object is masked from ‘package:adegenet’:

    AICc
```

3. Load data from MUSCLE alignment with following command: 
   A. Note: data input must be aligned sequences.
```r
muscledna <- fasta2DNAbin(file="/Users/aimes/Temp/PhyloGen563/data/large_files/rscS_multiple-seq-alignments/Vfischeri_rscS_DNA_muscle-aligned.fasta")
```

Output: 
```r
 Converting FASTA alignment into a DNAbin object... 


 Finding the size of a single genome... 


 genome size is: 2,808 nucleotides 

( 37  lines per genome )

 Importing sequences... 
..............................
 Forming final object... 

...done.
```

1. Compute the genetic distances from the MUSCLE alignment using the Tamura and Nei 1993 model, which allows for different rates of transitions and transversions, heterogeneous base frequencies, and between-site variation of the substitution rate. 
   A. TN93 details: Tamura and Nei (1993) developed a model which assumes distinct rates for both kinds of transition (A <-> G versus C <-> T), and transversions. The base frequencies are not assumed to be equal and are estimated from the data. A gamma correction of the inter-site variation in substitution rates is possible.
   B. Input the following: 
```r
DTN93 <- dist.dna(muscledna, model="TN93")
```
   A. Get the NJ tree with the following input: 
```r
treTN93 <- nj(DTN93)
```

1. Recompute the genetic distances from the MUSCLE alignment using the Gailtier and Gouy 1995 model.
   A. GG95 details: Galtier and Gouy (1995) introduced a model where the G+C content may change through time. Different rates are assumed for transitions and transversions. 
   B. Input the following: 
```r
DGG95 <- dist.dna(muscledna, model="GG95")
```
   A. Get the NJ tree with the following input: 
```r
treGG95 <- nj(DGG95)
```

1. Repeat the above steps using the ClustalW alignment data as detailed below. 

2. Load in ClustalW alignment data: 
```r
clustaldna <- fasta2DNAbin(file="/Users/aimes/Temp/PhyloGen563/data/large_files/rscS_multiple-seq-alignments/Vfischeri_rscS_DNA-clustal-aligned.fasta")
```

Output: 
```r
 Converting FASTA alignment into a DNAbin object... 


 Finding the size of a single genome... 


 genome size is: 2,808 nucleotides 

( 48  lines per genome )

 Importing sequences... 
..............................
 Forming final object... 

...done.
```
8. Compute the genetic distances using the Tamura and Nei 1993 model as detailed above: 
```r
DCTN93 <- dist.dna(clustaldna, model="TN93")
```

   A. Get the NJ tree: 
```r
treCTN93 <- nj(DCTN93)
```

9. Recompute the genetic distances from the ClustalW alignment using the Gailtier and Gouy 1995 model.
```r
DCGG95 <- dist.dna(clustaldna, model="GG95")
```
   A. Get the NJ tree: 
```r
treCGG95 <- nj(DCGG95)
```

10. Before plotting, use the [`ladderize` function](https://rdrr.io/cran/ape/man/ladderize.html) which reorganizes the internal structure of the tree to get the ladderized effect when plotted.
```r
treTN93 <- ladderize(treTN93)
treCTN93 <- ladderize(treCTN93)
treGG95 <- ladderize(treGG95)
treCGG95 <- ladderize(treCGG95)
```
11. Root all the trees to outgroup MJ8.1
```r
M93.rooted <- root(treTN93, outgroup = "MJ8.1", resolve.root = TRUE)
C93.rooted <- root(treCTN93, outgroup = "MJ8.1", resolve.root = TRUE)
M95.rooted <- root(treGG95, outgroup = "MJ8.1", resolve.root = TRUE)
C95.rooted <- root(treCGG95, outgroup = "MJ8.1", resolve.root = TRUE)

```

12. Plot the rooted trees
```r
plot(C95.rooted, cex=.6)
title("Clustal GG95 NJ tree")

plot(M95.rooted, cex=.6)
title("Muscle GG95 NJ tree")

plot(C93.rooted, cex=.6)
title("Clustal TN93 NJ tree")

plot(M93.rooted, cex=.6)
title("Muscle TN93 NJ tree")
```

### Estimate a parsimony-based tree using software: R package _phangorn_

* _phangorn_ is another widely used phylogenetic software. It is an R package and it has a huge variety of functions.
* Used here for parsimony-based tree estimation methods.
  * Full documentation](https://cran.r-project.org/web/packages/phangorn/vignettes/Trees.pdf)
  * Procedure here based on this [tutorial](https://adegenet.r-forge.r-project.org/files/MSc-intro-phylo.1.1.pdf)
  * The commands are listed in the [PDF tutorial]((https://adegenet.r-forge.r-project.org/files/MSc-intro-phylo.1.1.pdf)) that was used as guideline, or as seen in crsl4 class reproducible script [notebook-log.md](https://github.com/crsl4/phylogenetics-class/blob/master/exercises/notebook-log.md). 

1. Install necessary packages (if not installed for the distance section above)
```r
install.packages("adegenet", dep=TRUE)
install.packages("phangorn", dep=TRUE)
```

2. Load the packages
```r
library(ape)
library(adegenet)
library(phangorn)
```

3. Convert uploaded multiple sequence alignment files from above ape steps to a phangorn object:
```r
dnaM <- as.phyDat(muscledna)
dnaC <- as.phyDat(clustaldna)
```

4. Create a starting tree for the search on tree space and compute the parsimony score of this tree. Do this for both the MUSCLE and ClustalW files. 
```r
treM.ini <- nj(dist.dna(muscledna,model="raw"))
parsimony(treM.ini, dnaM)
```
Output parsimony score: 374

```r
treC.ini <- nj(dist.dna(clustaldna,model="raw"))
parsimony(treC.ini, dnaC)
```
Output parsimony score: 372

5. Search for the tree with maximum parsimony:
```r
treM.pars <- optim.parsimony(treM.ini, dnaM)
treC.pars <- optim.parsimony(treC.ini, dnaC)
```
treM: Final p-score 373 after  1 nni operations 
treC: Final p-score 371 after  1 nni operations 

6. Root the trees to outgroup MJ8.1 
```r
Muscle.rooted.parsimony <- root(treM.pars, outgroup = "MJ8.1", resolve.root = TRUE)
Clustal.rooted.parsimony <- root(treC.pars, outgroup = "MJ8.1", resolve.root = TRUE)

```

7. Plot trees:
```r
plot(Muscle.rooted.parsimony, cex=0.6)
title("Muscle pangorn tree")

plot(Clustal.rooted.parsimony, cex=0.6)
title("Clustal pangorn tree")
```


## Maximum Likelihood Tree Esimation Using IQ-TREE

Summary steps: 
1. Download IQ-TREE for Mac [here](http://www.iqtree.org/#download). Downloaded the zipped folder `iqtree-2.2.2.6-MacOSX`.

Note: Use the m MF function to predict the best fit model. The predicted best fit model for this data was HKY+F+G4.  

2. Run a trial with 1000 bootstraps on the MUSCLE aligned file.  
3. Run a trial with 5000 bootstraps on the MUSCLE aligned file. Keep the same model. 
4. Repeat steps 1 and 2 on the CLUSTALW aligned data. 
5. The input and output for each trial are detailed below: 

All output files stored within the [iq-tree-files](results/iq-tree-files) folder in the results directory. 

### MUSCLE trial with 1000 bootstraps 
```shell
(base) jacquelinelemaire@Jacquelines-Air iqtree-2.2.2.6-MacOSX % bin/iqtree2 -s /Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNA_muscle-aligned.fasta -m HKY+F+G4 --prefix T1000 -B 1000
IQ-TREE multicore version 2.2.2.6 COVID-edition for Mac OS X 64-bit built May 27 2023
Developed by Bui Quang Minh, James Barbetti, Nguyen Lam Tung,
Olga Chernomor, Heiko Schmidt, Dominik Schrempf, Michael Woodhams, Ly Trong Nhan.

Host:    Jacquelines-Air.lan (SSE4.2, 8 GB RAM)
Command: bin/iqtree2 -s /Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNA_muscle-aligned.fasta -m HKY+F+G4 --prefix T1000 -B 1000
Seed:    241514 (Using SPRNG - Scalable Parallel Random Number Generator)
Time:    Sun Apr 28 16:39:48 2024
Kernel:  SSE2 - 1 threads (8 CPU cores detected)

HINT: Use -nt option to specify number of threads because your CPU has 8 cores!
HINT: -nt AUTO will automatically determine the best number of threads to use.

Reading alignment file /Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNA_musclealigned.fasta ... Fasta format detected
Reading fasta file: done in 0.000770092 secs using 81.29% CPU
Alignment most likely contains DNA/RNA sequences
Constructing alignment: done in 0.00144696 secs using 68.97% CPU
Alignment has 12 sequences with 2808 columns, 97 distinct patterns
94 parsimony-informative, 254 singleton sites, 2460 constant sites
        Gap/Ambiguity  Composition  p-value
Analyzing sequences: done in 0.00012207 secs using 5.734% CPU
   1  KB2B1     0.89%    passed     99.98%
   2  ES114     0.85%    passed     99.79%
   3  EM30      0.85%    passed     99.95%
   4  EM24      0.85%    passed     99.93%
   5  MB14A1    1.28%    passed     99.97%
   6  MB13B1    0.85%    passed     99.93%
   7  MJ8.1     0.21%    passed     95.97%
   8  EM18      0.85%    passed     99.97%
   9  ES213     0.89%    passed     99.98%
  10  MJ102     0.85%    passed     99.79%
  11  EM17      0.85%    passed     99.88%
  12  MB11B1    0.89%    passed     99.98%
****  TOTAL     0.85%  0 sequences failed composition chi2 test (p-value<5%; df=3)
NOTE: ES213 is identical to KB2B1 but kept for subsequent analysis
Checking for duplicate sequences: done in 0.00014782 secs using 13.53% CPU
Identifying sites to remove: done in 0.000854015 secs using 99.06% CPU
NOTE: 1 identical sequences (see below) will be ignored for subsequent analysis
NOTE: MB11B1 (identical to KB2B1) is ignored but added at the end
Alignment was printed to T1000.uniqueseq.phy

For your convenience alignment with unique sequences printed to T1000.uniqueseq.phy

Create initial parsimony tree by phylogenetic likelihood library (PLL)... 0.002 seconds
Generating 1000 samples for ultrafast bootstrap (seed: 241514)...

NOTE: 0 MB RAM (0 GB) is required!
Estimate model parameters (epsilon = 0.100)
1. Initial log-likelihood: -5673.306
2. Current log-likelihood: -5628.053
3. Current log-likelihood: -5614.883
4. Current log-likelihood: -5607.174
5. Current log-likelihood: -5594.771
6. Current log-likelihood: -5584.116
7. Current log-likelihood: -5556.030
8. Current log-likelihood: -5529.474
9. Current log-likelihood: -5523.764
10. Current log-likelihood: -5522.910
Optimal log-likelihood: -5522.806
Rate parameters:  A-C: 1.00000  A-G: 6.81542  A-T: 1.00000  C-G: 1.00000  C-T: 6.81542  G-T: 1.00000
Base frequencies:  A: 0.388  C: 0.172  G: 0.145  T: 0.295
Gamma shape alpha: 0.556
Parameters optimization took 10 rounds (0.016 sec)
Wrote distance file to...
Computing ML distances based on estimated model parameters...
Calculating distance matrix: done in 0.000668049 secs using 47.6% CPU
Computing ML distances took 0.000832 sec (of wall-clock time) 0.000343 sec (of CPU time)
Setting up auxiliary I and S matrices: done in 1.5974e-05 secs using 175.3% CPU
Constructing RapidNJ tree: done in 2.19345e-05 secs using 164.1% CPU
Computing RapidNJ tree took 0.000066 sec (of wall-clock time) 0.000096 sec (of CPU time)
Log-likelihood of RapidNJ tree: -5526.333
--------------------------------------------------------------------
|             INITIALIZING CANDIDATE TREE SET                      |
--------------------------------------------------------------------
Generating 98 parsimony trees... 0.022 second
Computing log-likelihood of 95 initial trees ... 0.021 seconds
Current best score: -5520.155

Do NNI search on 20 best initial trees
Optimizing NNI: done in 0.00333714 secs using 166.9% CPU
Estimate model parameters (epsilon = 0.100)
BETTER TREE FOUND at iteration 1: -5519.831
Optimizing NNI: done in 0.00460696 secs using 197.2% CPU
Optimizing NNI: done in 0.00341296 secs using 197.9% CPU
Optimizing NNI: done in 0.00238609 secs using 197.8% CPU
Optimizing NNI: done in 0.00344515 secs using 198% CPU
Optimizing NNI: done in 0.00345922 secs using 195.1% CPU
Optimizing NNI: done in 0.00361514 secs using 195.9% CPU
Optimizing NNI: done in 0.00355005 secs using 191.7% CPU
Optimizing NNI: done in 0.00578189 secs using 198.2% CPU
Optimizing NNI: done in 0.00553012 secs using 194.5% CPU
Iteration 10 / LogL: -5519.831 / Time: 0h:0m:0s
Optimizing NNI: done in 0.00458097 secs using 197.4% CPU
Optimizing NNI: done in 0.00468802 secs using 198.8% CPU
UPDATE BEST LOG-LIKELIHOOD: -5519.828
Optimizing NNI: done in 0.00347185 secs using 181.3% CPU
Optimizing NNI: done in 0.00466919 secs using 191.9% CPU
Optimizing NNI: done in 0.00374699 secs using 187.9% CPU
Optimizing NNI: done in 0.00687099 secs using 197.1% CPU
Optimizing NNI: done in 0.00361109 secs using 190.4% CPU
Optimizing NNI: done in 0.00418711 secs using 198.6% CPU
Optimizing NNI: done in 0.005656 secs using 198.5% CPU
Optimizing NNI: done in 0.00559187 secs using 191.2% CPU
UPDATE BEST LOG-LIKELIHOOD: -5519.828
Iteration 20 / LogL: -5519.828 / Time: 0h:0m:0s
Finish initializing candidate tree set (3)
Current best tree score: -5519.828 / CPU time: 0.136
Number of iterations: 20
--------------------------------------------------------------------
|               OPTIMIZING CANDIDATE TREE SET                      |
--------------------------------------------------------------------
Optimizing NNI: done in 0.002877 secs using 194.6% CPU
Optimizing NNI: done in 0.00484896 secs using 198.2% CPU
Optimizing NNI: done in 0.00310683 secs using 191.7% CPU
UPDATE BEST LOG-LIKELIHOOD: -5519.827
Optimizing NNI: done in 0.00440192 secs using 198.5% CPU
Optimizing NNI: done in 0.00192904 secs using 197.6% CPU
Optimizing NNI: done in 0.004076 secs using 196.3% CPU
Optimizing NNI: done in 0.00408196 secs using 199.9% CPU
UPDATE BEST LOG-LIKELIHOOD: -5519.827
Optimizing NNI: done in 0.00274396 secs using 99.93% CPU
UPDATE BEST LOG-LIKELIHOOD: -5519.827
Optimizing NNI: done in 0.00392008 secs using 180.1% CPU
Optimizing NNI: done in 0.00475717 secs using 99.93% CPU
Iteration 30 / LogL: -5519.831 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00280499 secs using 456.4% CPU
Optimizing NNI: done in 0.00438094 secs using 99.64% CPU
Optimizing NNI: done in 0.00523782 secs using 99.49% CPU
Optimizing NNI: done in 0.00379896 secs using 99.47% CPU
Optimizing NNI: done in 0.00487089 secs using 98.63% CPU
Optimizing NNI: done in 0.00379801 secs using 99.95% CPU
Optimizing NNI: done in 0.00355697 secs using 99.47% CPU
Optimizing NNI: done in 0.00269198 secs using 99.44% CPU
Optimizing NNI: done in 0.00353503 secs using 99.94% CPU
Optimizing NNI: done in 0.00310302 secs using 99.93% CPU
Iteration 40 / LogL: -5551.015 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00295591 secs using 97.94% CPU
Optimizing NNI: done in 0.00338197 secs using 99.53% CPU
Optimizing NNI: done in 0.00329208 secs using 99.75% CPU
Optimizing NNI: done in 0.00285387 secs using 98.39% CPU
Optimizing NNI: done in 0.0025332 secs using 99.99% CPU
Optimizing NNI: done in 0.0025301 secs using 99.92% CPU
Optimizing NNI: done in 0.00288105 secs using 99.93% CPU
Optimizing NNI: done in 0.00303316 secs using 98.15% CPU
Optimizing NNI: done in 0.00197387 secs using 99.96% CPU
Optimizing NNI: done in 0.00275993 secs using 98.88% CPU
Iteration 50 / LogL: -5519.827 / Time: 0h:0m:0s (0h:0m:0s left)
Log-likelihood cutoff on original alignment: -5559.698
Optimizing NNI: done in 0.00195599 secs using 99.08% CPU
Optimizing NNI: done in 0.00391698 secs using 99.16% CPU
Optimizing NNI: done in 0.00456309 secs using 98.27% CPU
Optimizing NNI: done in 0.00393605 secs using 98.58% CPU
Optimizing NNI: done in 0.00327086 secs using 99.94% CPU
Optimizing NNI: done in 0.00362086 secs using 99.81% CPU
Optimizing NNI: done in 0.0036521 secs using 99.31% CPU
Optimizing NNI: done in 0.00436306 secs using 99.84% CPU
Optimizing NNI: done in 0.00305915 secs using 99.47% CPU
Optimizing NNI: done in 0.0036552 secs using 99.26% CPU
Iteration 60 / LogL: -5519.940 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00458193 secs using 99.83% CPU
Optimizing NNI: done in 0.000953913 secs using 99.8% CPU
Optimizing NNI: done in 0.00438404 secs using 98.79% CPU
Optimizing NNI: done in 0.0016911 secs using 99.64% CPU
Optimizing NNI: done in 0.00402117 secs using 99.62% CPU
Optimizing NNI: done in 0.00307989 secs using 99.94% CPU
Optimizing NNI: done in 0.00465584 secs using 98.44% CPU
Optimizing NNI: done in 0.002424 secs using 99.83% CPU
Optimizing NNI: done in 0.00253415 secs using 99.76% CPU
Optimizing NNI: done in 0.00250101 secs using 98.52% CPU
Iteration 70 / LogL: -5519.832 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00445104 secs using 99.84% CPU
Optimizing NNI: done in 0.00185919 secs using 98.54% CPU
Optimizing NNI: done in 0.00461698 secs using 99.42% CPU
Optimizing NNI: done in 0.00285387 secs using 99.97% CPU
Optimizing NNI: done in 0.00269914 secs using 99.59% CPU
Optimizing NNI: done in 0.00178599 secs using 99.94% CPU
Optimizing NNI: done in 0.00277781 secs using 99.86% CPU
Optimizing NNI: done in 0.00447011 secs using 99.77% CPU
Optimizing NNI: done in 0.00501394 secs using 99.2% CPU
Optimizing NNI: done in 0.00156593 secs using 98.6% CPU
Iteration 80 / LogL: -5550.936 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00253892 secs using 98.94% CPU
Optimizing NNI: done in 0.0036869 secs using 99.84% CPU
Optimizing NNI: done in 0.00356102 secs using 99.94% CPU
Optimizing NNI: done in 0.0035851 secs using 99.94% CPU
Optimizing NNI: done in 0.0049181 secs using 99.67% CPU
Optimizing NNI: done in 0.00191903 secs using 100% CPU
Optimizing NNI: done in 0.00190401 secs using 96.8% CPU
Optimizing NNI: done in 0.00381708 secs using 99.79% CPU
Optimizing NNI: done in 0.00472093 secs using 99.85% CPU
Optimizing NNI: done in 0.00354409 secs using 99.77% CPU
Iteration 90 / LogL: -5519.827 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00184584 secs using 99.74% CPU
Optimizing NNI: done in 0.00200701 secs using 99.95% CPU
Optimizing NNI: done in 0.00302911 secs using 98.87% CPU
Optimizing NNI: done in 0.00268412 secs using 97.24% CPU
Optimizing NNI: done in 0.00282001 secs using 99.75% CPU
Optimizing NNI: done in 0.00284886 secs using 99.97% CPU
Optimizing NNI: done in 0.00281501 secs using 98.72% CPU
Optimizing NNI: done in 0.00245595 secs using 99.76% CPU
Optimizing NNI: done in 0.00421095 secs using 99% CPU
Optimizing NNI: done in 0.00624895 secs using 98.88% CPU
Iteration 100 / LogL: -5519.833 / Time: 0h:0m:0s (0h:0m:0s left)
Log-likelihood cutoff on original alignment: -5559.699
NOTE: Bootstrap correlation coefficient of split occurrence frequencies: 1.000
Optimizing NNI: done in 0.00554085 secs using 99.39% CPU
Optimizing NNI: done in 0.00432801 secs using 99.79% CPU
TREE SEARCH COMPLETED AFTER 102 ITERATIONS / Time: 0h:0m:0s

--------------------------------------------------------------------
|                    FINALIZING TREE SEARCH                        |
--------------------------------------------------------------------
Performs final model parameters optimization
Estimate model parameters (epsilon = 0.010)
1. Initial log-likelihood: -5519.827
Optimal log-likelihood: -5519.821
Rate parameters:  A-C: 1.00000  A-G: 6.99798  A-T: 1.00000  C-G: 1.00000  C-T: 6.99798  G-T: 1.00000
Base frequencies:  A: 0.388  C: 0.172  G: 0.145  T: 0.295
Gamma shape alpha: 0.493
Parameters optimization took 1 rounds (0.001 sec)
BEST SCORE FOUND : -5519.821
Creating bootstrap support values...
Split supports printed to NEXUS file T1000.splits.nex
Total tree length: 0.160

Total number of iterations: 102
CPU time used for tree search: 0.767 sec (0h:0m:0s)
Wall-clock time used for tree search: 0.593 sec (0h:0m:0s)
Total CPU time used: 0.811 sec (0h:0m:0s)
Total wall-clock time used: 0.649 sec (0h:0m:0s)

Computing bootstrap consensus tree...
Reading input file T1000.splits.nex...
11 taxa and 40 splits.
Consensus tree written to T1000.contree
Reading input trees file T1000.contree
Log-likelihood of consensus tree: -5519.836

Analysis results written to:
  IQ-TREE report:                T1000.iqtree
  Maximum-likelihood tree:       T1000.treefile
  Likelihood distances:          T1000.mldist

Ultrafast bootstrap approximation results written to:
  Split support values:          T1000.splits.nex
  Consensus tree:                T1000.contree
  Screen log file:               T1000.log

Date and Time: Sun Apr 28 16:39:48 2024
(base) jacquelinelemaire@Jacquelines-Air iqtree-2.2.2.6-MacOSX %
```

### MUSCLE trial with 5000 bootstraps 
```shell
(base) jacquelinelemaire@Jacquelines-Air iqtree-2.2.2.6-MacOSX % bin/iqtree2 -s /Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNA_musclealigned.fasta -m HKY+F+G4 --prefix T5000 -B 5000
IQ-TREE multicore version 2.2.2.6 COVID-edition for Mac OS X 64-bit built May 27 2023
Developed by Bui Quang Minh, James Barbetti, Nguyen Lam Tung,
Olga Chernomor, Heiko Schmidt, Dominik Schrempf, Michael Woodhams, Ly Trong Nhan.

Host:    Jacquelines-Air.lan (SSE4.2, 8 GB RAM)
Command: bin/iqtree2 -s /Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNA_musclealigned.fasta -m HKY+F+G4 --prefix T5000 -B 5000
Seed:    902640 (Using SPRNG - Scalable Parallel Random Number Generator)
Time:    Sun Apr 28 16:41:00 2024
Kernel:  SSE2 - 1 threads (8 CPU cores detected)

HINT: Use -nt option to specify number of threads because your CPU has 8 cores!
HINT: -nt AUTO will automatically determine the best number of threads to use.

Reading alignment file /Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNA_musclealigned.fasta ... Fasta format detected
Reading fasta file: done in 0.000818968 secs using 77.17% CPU
Alignment most likely contains DNA/RNA sequences
Constructing alignment: done in 0.00136399 secs using 67.6% CPU
Alignment has 12 sequences with 2808 columns, 97 distinct patterns
94 parsimony-informative, 254 singleton sites, 2460 constant sites
        Gap/Ambiguity  Composition  p-value
Analyzing sequences: done in 0.000118971 secs using 5.043% CPU
   1  KB2B1     0.89%    passed     99.98%
   2  ES114     0.85%    passed     99.79%
   3  EM30      0.85%    passed     99.95%
   4  EM24      0.85%    passed     99.93%
   5  MB14A1    1.28%    passed     99.97%
   6  MB13B1    0.85%    passed     99.93%
   7  MJ8.1     0.21%    passed     95.97%
   8  EM18      0.85%    passed     99.97%
   9  ES213     0.89%    passed     99.98%
  10  MJ102     0.85%    passed     99.79%
  11  EM17      0.85%    passed     99.88%
  12  MB11B1    0.89%    passed     99.98%
****  TOTAL     0.85%  0 sequences failed composition chi2 test (p-value<5%; df=3)
NOTE: ES213 is identical to KB2B1 but kept for subsequent analysis
Checking for duplicate sequences: done in 0.000136852 secs using 13.88% CPU
Identifying sites to remove: done in 0.000825167 secs using 98.89% CPU
NOTE: 1 identical sequences (see below) will be ignored for subsequent analysis
NOTE: MB11B1 (identical to KB2B1) is ignored but added at the end
Alignment was printed to T5000.uniqueseq.phy

For your convenience alignment with unique sequences printed to T5000.uniqueseq.phy

Create initial parsimony tree by phylogenetic likelihood library (PLL)... 0.002 seconds
Generating 5000 samples for ultrafast bootstrap (seed: 902640)...

NOTE: 2 MB RAM (0 GB) is required!
Estimate model parameters (epsilon = 0.100)
1. Initial log-likelihood: -5673.306
2. Current log-likelihood: -5628.053
3. Current log-likelihood: -5614.883
4. Current log-likelihood: -5607.174
5. Current log-likelihood: -5594.771
6. Current log-likelihood: -5584.116
7. Current log-likelihood: -5556.030
8. Current log-likelihood: -5529.474
9. Current log-likelihood: -5523.764
10. Current log-likelihood: -5522.910
Optimal log-likelihood: -5522.806
Rate parameters:  A-C: 1.00000  A-G: 6.81542  A-T: 1.00000  C-G: 1.00000  C-T: 6.81542  G-T: 1.00000
Base frequencies:  A: 0.388  C: 0.172  G: 0.145  T: 0.295
Gamma shape alpha: 0.556
Parameters optimization took 10 rounds (0.015 sec)
Wrote distance file to...
Computing ML distances based on estimated model parameters...
Calculating distance matrix: done in 0.000519037 secs using 60.5% CPU
Computing ML distances took 0.000704 sec (of wall-clock time) 0.000345 sec (of CPU time)
Setting up auxiliary I and S matrices: done in 2.69413e-05 secs using 51.96% CPU
Constructing RapidNJ tree: done in 3.19481e-05 secs using 122.1% CPU
Computing RapidNJ tree took 0.000100 sec (of wall-clock time) 0.000081 sec (of CPU time)
Log-likelihood of RapidNJ tree: -5526.333
--------------------------------------------------------------------
|             INITIALIZING CANDIDATE TREE SET                      |
--------------------------------------------------------------------
Generating 98 parsimony trees... 0.023 second
Computing log-likelihood of 94 initial trees ... 0.021 seconds
Current best score: -5522.806

Do NNI search on 20 best initial trees
Optimizing NNI: done in 0.00974488 secs using 187.8% CPU
Estimate model parameters (epsilon = 0.100)
BETTER TREE FOUND at iteration 1: -5519.830
Optimizing NNI: done in 0.00611901 secs using 197.4% CPU
Optimizing NNI: done in 0.00858903 secs using 195.9% CPU
UPDATE BEST LOG-LIKELIHOOD: -5519.828
Optimizing NNI: done in 0.00754809 secs using 197.2% CPU
Optimizing NNI: done in 0.00801301 secs using 196% CPU
Optimizing NNI: done in 0.0100329 secs using 196.6% CPU
Optimizing NNI: done in 0.0101891 secs using 196.7% CPU
Optimizing NNI: done in 0.00551796 secs using 196.6% CPU
UPDATE BEST LOG-LIKELIHOOD: -5519.827
Optimizing NNI: done in 0.00834894 secs using 193.8% CPU
Optimizing NNI: done in 0.00573707 secs using 198.2% CPU
Iteration 10 / LogL: -5519.968 / Time: 0h:0m:0s
Optimizing NNI: done in 0.00577497 secs using 192.7% CPU
Optimizing NNI: done in 0.00548697 secs using 197.7% CPU
Optimizing NNI: done in 0.00826907 secs using 197.6% CPU
Optimizing NNI: done in 0.00605989 secs using 198.3% CPU
Optimizing NNI: done in 0.00960708 secs using 197.8% CPU
Optimizing NNI: done in 0.00991797 secs using 196.1% CPU
Optimizing NNI: done in 0.010401 secs using 194.6% CPU
Optimizing NNI: done in 0.00787997 secs using 197.3% CPU
Optimizing NNI: done in 0.0101008 secs using 138.8% CPU
Optimizing NNI: done in 0.0073812 secs using 99.92% CPU
Iteration 20 / LogL: -5519.833 / Time: 0h:0m:0s
Finish initializing candidate tree set (3)
Current best tree score: -5519.827 / CPU time: 0.219
Number of iterations: 20
--------------------------------------------------------------------
|               OPTIMIZING CANDIDATE TREE SET                      |
--------------------------------------------------------------------
Optimizing NNI: done in 0.00759482 secs using 99.91% CPU
Optimizing NNI: done in 0.00248694 secs using 99.68% CPU
Optimizing NNI: done in 0.00276303 secs using 99.96% CPU
Optimizing NNI: done in 0.0044961 secs using 99.98% CPU
Optimizing NNI: done in 0.00430012 secs using 99.88% CPU
Optimizing NNI: done in 0.00242996 secs using 100% CPU
UPDATE BEST LOG-LIKELIHOOD: -5519.827
Optimizing NNI: done in 0.00315094 secs using 97.59% CPU
Optimizing NNI: done in 0.0056951 secs using 99.65% CPU
Optimizing NNI: done in 0.00427389 secs using 99.89% CPU
Optimizing NNI: done in 0.00470996 secs using 99.49% CPU
Iteration 30 / LogL: -5519.828 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00385094 secs using 97.72% CPU
Optimizing NNI: done in 0.00364995 secs using 99.21% CPU
Optimizing NNI: done in 0.00470018 secs using 99.06% CPU
Optimizing NNI: done in 0.00466681 secs using 98.95% CPU
Optimizing NNI: done in 0.00544 secs using 99.61% CPU
Optimizing NNI: done in 0.00290608 secs using 98.72% CPU
Optimizing NNI: done in 0.00453615 secs using 99.29% CPU
Optimizing NNI: done in 0.00389194 secs using 99.87% CPU
Optimizing NNI: done in 0.00313902 secs using 99.2% CPU
Optimizing NNI: done in 0.00604987 secs using 99.29% CPU
Iteration 40 / LogL: -5519.827 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00774479 secs using 99.62% CPU
Optimizing NNI: done in 0.00452995 secs using 98.74% CPU
Optimizing NNI: done in 0.00436401 secs using 99.89% CPU
Optimizing NNI: done in 0.00785708 secs using 99.92% CPU
Optimizing NNI: done in 0.00398707 secs using 98.97% CPU
Optimizing NNI: done in 0.00437522 secs using 99.81% CPU
Optimizing NNI: done in 0.00471401 secs using 98.11% CPU
Optimizing NNI: done in 0.00728297 secs using 99.51% CPU
Optimizing NNI: done in 0.00497293 secs using 99.26% CPU
Optimizing NNI: done in 0.00487304 secs using 99.81% CPU
Iteration 50 / LogL: -5522.320 / Time: 0h:0m:0s (0h:0m:0s left)
Log-likelihood cutoff on original alignment: -5568.602
Optimizing NNI: done in 0.00420499 secs using 97.48% CPU
Optimizing NNI: done in 0.00482202 secs using 99.34% CPU
Optimizing NNI: done in 0.0041039 secs using 98.95% CPU
Optimizing NNI: done in 0.00317597 secs using 98.87% CPU
Optimizing NNI: done in 0.00683594 secs using 99.53% CPU
Optimizing NNI: done in 0.00336003 secs using 99.73% CPU
Optimizing NNI: done in 0.00557709 secs using 99.28% CPU
Optimizing NNI: done in 0.00620914 secs using 99.48% CPU
Optimizing NNI: done in 0.00480318 secs using 98.98% CPU
Optimizing NNI: done in 0.00466895 secs using 99.02% CPU
Iteration 60 / LogL: -5519.847 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.0030272 secs using 99.86% CPU
Optimizing NNI: done in 0.0049789 secs using 99.16% CPU
Optimizing NNI: done in 0.00588179 secs using 99.43% CPU
Optimizing NNI: done in 0.00473022 secs using 99.04% CPU
Optimizing NNI: done in 0.00330591 secs using 99.58% CPU
Optimizing NNI: done in 0.0092051 secs using 99.75% CPU
Optimizing NNI: done in 0.00572991 secs using 99.93% CPU
Optimizing NNI: done in 0.00442386 secs using 99.98% CPU
Optimizing NNI: done in 0.003227 secs using 99.81% CPU
Optimizing NNI: done in 0.0039351 secs using 98.6% CPU
Iteration 70 / LogL: -5519.830 / Time: 0h:0m:1s (0h:0m:0s left)
Optimizing NNI: done in 0.00471997 secs using 99.58% CPU
Optimizing NNI: done in 0.00599003 secs using 99.95% CPU
Optimizing NNI: done in 0.00701785 secs using 99.97% CPU
Optimizing NNI: done in 0.00426197 secs using 99.86% CPU
Optimizing NNI: done in 0.00443506 secs using 99.39% CPU
Optimizing NNI: done in 0.00517893 secs using 98.8% CPU
Optimizing NNI: done in 0.00445199 secs using 99.39% CPU
Optimizing NNI: done in 0.00496602 secs using 99.82% CPU
Optimizing NNI: done in 0.00341916 secs using 99.85% CPU
Optimizing NNI: done in 0.00554895 secs using 99.96% CPU
Iteration 80 / LogL: -5519.830 / Time: 0h:0m:1s (0h:0m:0s left)
Optimizing NNI: done in 0.00417209 secs using 99.18% CPU
Optimizing NNI: done in 0.00442004 secs using 99.55% CPU
Optimizing NNI: done in 0.00342202 secs using 99.85% CPU
Optimizing NNI: done in 0.0030241 secs using 99.73% CPU
Optimizing NNI: done in 0.0024929 secs using 98.64% CPU
Optimizing NNI: done in 0.0035212 secs using 99.11% CPU
Optimizing NNI: done in 0.00479603 secs using 99.96% CPU
Optimizing NNI: done in 0.00454307 secs using 99.14% CPU
Optimizing NNI: done in 0.00672102 secs using 98.5% CPU
Optimizing NNI: done in 0.00599813 secs using 98.18% CPU
Iteration 90 / LogL: -5519.841 / Time: 0h:0m:1s (0h:0m:0s left)
Optimizing NNI: done in 0.00465703 secs using 99.7% CPU
Optimizing NNI: done in 0.00247908 secs using 99.84% CPU
Optimizing NNI: done in 0.00525594 secs using 99.3% CPU
Optimizing NNI: done in 0.00427985 secs using 98.48% CPU
Optimizing NNI: done in 0.00621891 secs using 98.8% CPU
Optimizing NNI: done in 0.00266314 secs using 99.84% CPU
Optimizing NNI: done in 0.00308919 secs using 99.86% CPU
Optimizing NNI: done in 0.00342202 secs using 98.51% CPU
Optimizing NNI: done in 0.0034678 secs using 99% CPU
Optimizing NNI: done in 0.00373602 secs using 99.95% CPU
Iteration 100 / LogL: -5519.827 / Time: 0h:0m:1s (0h:0m:0s left)
Log-likelihood cutoff on original alignment: -5561.679
NOTE: Bootstrap correlation coefficient of split occurrence frequencies: 1.000
Optimizing NNI: done in 0.00391102 secs using 99.85% CPU
Optimizing NNI: done in 0.00220108 secs using 99.5% CPU
TREE SEARCH COMPLETED AFTER 102 ITERATIONS / Time: 0h:0m:1s

--------------------------------------------------------------------
|                    FINALIZING TREE SEARCH                        |
--------------------------------------------------------------------
Performs final model parameters optimization
Estimate model parameters (epsilon = 0.010)
1. Initial log-likelihood: -5519.827
Optimal log-likelihood: -5519.821
Rate parameters:  A-C: 1.00000  A-G: 6.99806  A-T: 1.00000  C-G: 1.00000  C-T: 6.99806  G-T: 1.00000
Base frequencies:  A: 0.388  C: 0.172  G: 0.145  T: 0.295
Gamma shape alpha: 0.493
Parameters optimization took 1 rounds (0.001 sec)
BEST SCORE FOUND : -5519.821
Creating bootstrap support values...
Split supports printed to NEXUS file T5000.splits.nex
Total tree length: 0.160

Total number of iterations: 102
CPU time used for tree search: 1.596 sec (0h:0m:1s)
Wall-clock time used for tree search: 1.432 sec (0h:0m:1s)
Total CPU time used: 1.712 sec (0h:0m:1s)
Total wall-clock time used: 1.565 sec (0h:0m:1s)

Computing bootstrap consensus tree...
Reading input file T5000.splits.nex...
11 taxa and 46 splits.
Consensus tree written to T5000.contree
Reading input trees file T5000.contree
Log-likelihood of consensus tree: -5519.836

Analysis results written to:
  IQ-TREE report:                T5000.iqtree
  Maximum-likelihood tree:       T5000.treefile
  Likelihood distances:          T5000.mldist

Ultrafast bootstrap approximation results written to:
  Split support values:          T5000.splits.nex
  Consensus tree:                T5000.contree
  Screen log file:               T5000.log

Date and Time: Sun Apr 28 16:41:02 2024
(base) jacquelinelemaire@Jacquelines-Air iqtree-2.2.2.6-MacOSX %
```

### ClustalW trial with 1000 bootstraps 
```shell
(base) jacquelinelemaire@Jacquelines-Air iqtree-2.2.2.6-MacOSX % bin/iqtree2 -s /Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNA-clustal-aligned.fasta -m HKY+F+G4 --prefix CT1000 -B 1000
IQ-TREE multicore version 2.2.2.6 COVID-edition for Mac OS X 64-bit built May 27 2023
Developed by Bui Quang Minh, James Barbetti, Nguyen Lam Tung,
Olga Chernomor, Heiko Schmidt, Dominik Schrempf, Michael Woodhams, Ly Trong Nhan.

Host:    Jacquelines-Air.lan (SSE4.2, 8 GB RAM)
Command: bin/iqtree2 -s /Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNA-clustal-aligned.fasta -m HKY+F+G4 --prefix CT1000 -B 1000
Seed:    864423 (Using SPRNG - Scalable Parallel Random Number Generator)
Time:    Sun Apr 28 16:43:16 2024
Kernel:  SSE2 - 1 threads (8 CPU cores detected)

HINT: Use -nt option to specify number of threads because your CPU has 8 cores!
HINT: -nt AUTO will automatically determine the best number of threads to use.

Reading alignment file /Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNA-clustal-aligned.fasta ... Fasta format detected
Reading fasta file: done in 0.000845194 secs using 79.39% CPU
Alignment most likely contains DNA/RNA sequences
Constructing alignment: done in 0.00154686 secs using 63.87% CPU
Alignment has 12 sequences with 2808 columns, 95 distinct patterns
94 parsimony-informative, 252 singleton sites, 2462 constant sites
        Gap/Ambiguity  Composition  p-value
Analyzing sequences: done in 1.40667e-05 secs using 56.87% CPU
   1  ES114     0.85%    passed     99.79%
   2  MJ102     0.85%    passed     99.79%
   3  EM24      0.85%    passed     99.93%
   4  EM30      0.85%    passed     99.95%
   5  EM17      0.85%    passed     99.88%
   6  EM18      0.85%    passed     99.97%
   7  MB13B1    0.85%    passed     99.93%
   8  MB14A1    1.28%    passed     99.97%
   9  ES213     0.89%    passed     99.98%
  10  KB2B1     0.89%    passed     99.98%
  11  MB11B1    0.89%    passed     99.98%
  12  MJ8.1     0.21%    passed     95.97%
****  TOTAL     0.85%  0 sequences failed composition chi2 test (p-value<5%; df=3)
NOTE: KB2B1 is identical to ES213 but kept for subsequent analysis
Checking for duplicate sequences: done in 0.000206947 secs using 16.43% CPU
Identifying sites to remove: done in 0.000922203 secs using 98.68% CPU
NOTE: 1 identical sequences (see below) will be ignored for subsequent analysis
NOTE: MB11B1 (identical to ES213) is ignored but added at the end
Alignment was printed to CT1000.uniqueseq.phy

For your convenience alignment with unique sequences printed to CT1000.uniqueseq.phy

Create initial parsimony tree by phylogenetic likelihood library (PLL)... 0.002 seconds
Generating 1000 samples for ultrafast bootstrap (seed: 864423)...

NOTE: 0 MB RAM (0 GB) is required!
Estimate model parameters (epsilon = 0.100)
1. Initial log-likelihood: -5654.374
2. Current log-likelihood: -5605.158
3. Current log-likelihood: -5591.227
4. Current log-likelihood: -5582.494
5. Current log-likelihood: -5555.515
6. Current log-likelihood: -5523.441
7. Current log-likelihood: -5507.293
8. Current log-likelihood: -5504.111
9. Current log-likelihood: -5503.623
Optimal log-likelihood: -5503.561
Rate parameters:  A-C: 1.00000  A-G: 6.97109  A-T: 1.00000  C-G: 1.00000  C-T: 6.97109  G-T: 1.00000
Base frequencies:  A: 0.388  C: 0.172  G: 0.145  T: 0.295
Gamma shape alpha: 0.512
Parameters optimization took 9 rounds (0.015 sec)
Wrote distance file to...
Computing ML distances based on estimated model parameters...
Calculating distance matrix: done in 0.000674963 secs using 46.22% CPU
Computing ML distances took 0.000839 sec (of wall-clock time) 0.000336 sec (of CPU time)
Setting up auxiliary I and S matrices: done in 2.09808e-05 secs using 171.6% CPU
Constructing RapidNJ tree: done in 3.19481e-05 secs using 156.5% CPU
Computing RapidNJ tree took 0.000084 sec (of wall-clock time) 0.000132 sec (of CPU time)
Log-likelihood of RapidNJ tree: -5502.523
--------------------------------------------------------------------
|             INITIALIZING CANDIDATE TREE SET                      |
--------------------------------------------------------------------
Generating 98 parsimony trees... 0.023 second
Computing log-likelihood of 95 initial trees ... 0.021 seconds
Current best score: -5502.523

Do NNI search on 20 best initial trees
Optimizing NNI: done in 0.00504494 secs using 138.2% CPU
Estimate model parameters (epsilon = 0.100)
BETTER TREE FOUND at iteration 1: -5500.470
Optimizing NNI: done in 0.00353384 secs using 195.3% CPU
UPDATE BEST LOG-LIKELIHOOD: -5500.463
Optimizing NNI: done in 0.00461698 secs using 196.4% CPU
UPDATE BEST LOG-LIKELIHOOD: -5500.463
Optimizing NNI: done in 0.00346303 secs using 195.7% CPU
Optimizing NNI: done in 0.00337887 secs using 198.8% CPU
Optimizing NNI: done in 0.00346494 secs using 198.5% CPU
Optimizing NNI: done in 0.00354099 secs using 195.6% CPU
Optimizing NNI: done in 0.00340796 secs using 198.7% CPU
Optimizing NNI: done in 0.00439906 secs using 198.6% CPU
Optimizing NNI: done in 0.00466204 secs using 198.7% CPU
Iteration 10 / LogL: -5500.488 / Time: 0h:0m:0s
Optimizing NNI: done in 0.00339198 secs using 197.6% CPU
Optimizing NNI: done in 0.00462294 secs using 193.1% CPU
Optimizing NNI: done in 0.00450802 secs using 198.8% CPU
Optimizing NNI: done in 0.0056169 secs using 197.8% CPU
Optimizing NNI: done in 0.00339794 secs using 196% CPU
Optimizing NNI: done in 0.00339794 secs using 198.2% CPU
Optimizing NNI: done in 0.00566101 secs using 198.2% CPU
Optimizing NNI: done in 0.00690794 secs using 194.8% CPU
Optimizing NNI: done in 0.00315619 secs using 195.7% CPU
Optimizing NNI: done in 0.00565505 secs using 197.8% CPU
Iteration 20 / LogL: -5500.463 / Time: 0h:0m:0s
Finish initializing candidate tree set (3)
Current best tree score: -5500.463 / CPU time: 0.136
Number of iterations: 20
--------------------------------------------------------------------
|               OPTIMIZING CANDIDATE TREE SET                      |
--------------------------------------------------------------------
Optimizing NNI: done in 0.00211191 secs using 197.3% CPU
Optimizing NNI: done in 0.00329614 secs using 182.8% CPU
Optimizing NNI: done in 0.00258708 secs using 198.7% CPU
Optimizing NNI: done in 0.00291204 secs using 198.2% CPU
Optimizing NNI: done in 0.00382805 secs using 191.8% CPU
Optimizing NNI: done in 0.00321984 secs using 198.4% CPU
Optimizing NNI: done in 0.00195384 secs using 198.1% CPU
Optimizing NNI: done in 0.00243616 secs using 191.8% CPU
Optimizing NNI: done in 0.00355601 secs using 194.2% CPU
Optimizing NNI: done in 0.0020752 secs using 198% CPU
Iteration 30 / LogL: -5500.476 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.0038619 secs using 198.5% CPU
Optimizing NNI: done in 0.00383806 secs using 196.5% CPU
Optimizing NNI: done in 0.00564599 secs using 156.1% CPU
Optimizing NNI: done in 0.00160599 secs using 99.88% CPU
Optimizing NNI: done in 0.00137115 secs using 99.7% CPU
Optimizing NNI: done in 0.00276279 secs using 98.63% CPU
Optimizing NNI: done in 0.00186515 secs using 99.94% CPU
Optimizing NNI: done in 0.00147891 secs using 100% CPU
UPDATE BEST LOG-LIKELIHOOD: -5500.463
Optimizing NNI: done in 0.00282502 secs using 99.15% CPU
Optimizing NNI: done in 0.00251603 secs using 99.96% CPU
Iteration 40 / LogL: -5530.394 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00376701 secs using 99.92% CPU
UPDATE BEST LOG-LIKELIHOOD: -5500.462
Optimizing NNI: done in 0.00284004 secs using 100% CPU
Optimizing NNI: done in 0.00189185 secs using 99.74% CPU
Optimizing NNI: done in 0.00384188 secs using 99.98% CPU
Optimizing NNI: done in 0.00250697 secs using 99.64% CPU
Optimizing NNI: done in 0.00373697 secs using 98.45% CPU
Optimizing NNI: done in 0.00321007 secs using 99.94% CPU
Optimizing NNI: done in 0.00353217 secs using 99.97% CPU
Optimizing NNI: done in 0.00369096 secs using 99.57% CPU
Optimizing NNI: done in 0.00333095 secs using 99.97% CPU
Iteration 50 / LogL: -5530.531 / Time: 0h:0m:0s (0h:0m:0s left)
Log-likelihood cutoff on original alignment: -5535.264
Optimizing NNI: done in 0.00350094 secs using 99.77% CPU
Optimizing NNI: done in 0.00373197 secs using 99.65% CPU
Optimizing NNI: done in 0.0045619 secs using 99.96% CPU
Optimizing NNI: done in 0.00360394 secs using 99.09% CPU
Optimizing NNI: done in 0.00165105 secs using 99.94% CPU
Optimizing NNI: done in 0.00405788 secs using 99.58% CPU
Optimizing NNI: done in 0.00409389 secs using 99.98% CPU
Optimizing NNI: done in 0.00202703 secs using 99.26% CPU
Optimizing NNI: done in 0.00260305 secs using 100% CPU
Optimizing NNI: done in 0.00428605 secs using 99.86% CPU
Iteration 60 / LogL: -5530.471 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00381303 secs using 99.89% CPU
Optimizing NNI: done in 0.00319791 secs using 97.85% CPU
Optimizing NNI: done in 0.00226498 secs using 100% CPU
Optimizing NNI: done in 0.00365901 secs using 99.95% CPU
Optimizing NNI: done in 0.0034368 secs using 99.54% CPU
Optimizing NNI: done in 0.00298595 secs using 99.8% CPU
Optimizing NNI: done in 0.00462699 secs using 99.22% CPU
Optimizing NNI: done in 0.00393915 secs using 97.89% CPU
Optimizing NNI: done in 0.00243282 secs using 99.84% CPU
Optimizing NNI: done in 0.00460315 secs using 99.84% CPU
Iteration 70 / LogL: -5500.464 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00285697 secs using 99.55% CPU
Optimizing NNI: done in 0.00248694 secs using 99.96% CPU
Optimizing NNI: done in 0.00283504 secs using 99.93% CPU
Optimizing NNI: done in 0.00461602 secs using 99.8% CPU
Optimizing NNI: done in 0.00241399 secs using 99.5% CPU
Optimizing NNI: done in 0.00324607 secs using 99.97% CPU
Optimizing NNI: done in 0.00569296 secs using 99.95% CPU
Optimizing NNI: done in 0.00321794 secs using 99.97% CPU
Optimizing NNI: done in 0.00385404 secs using 99.87% CPU
Optimizing NNI: done in 0.00363588 secs using 99.89% CPU
Iteration 80 / LogL: -5500.489 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00330687 secs using 98.43% CPU
Optimizing NNI: done in 0.00310087 secs using 99.97% CPU
Optimizing NNI: done in 0.00266886 secs using 99.63% CPU
Optimizing NNI: done in 0.00321603 secs using 99.97% CPU
Optimizing NNI: done in 0.00362897 secs using 99.53% CPU
Optimizing NNI: done in 0.00269818 secs using 99.96% CPU
Optimizing NNI: done in 0.00327587 secs using 98.84% CPU
Optimizing NNI: done in 0.00264597 secs using 99.96% CPU
Optimizing NNI: done in 0.00342393 secs using 99.83% CPU
Optimizing NNI: done in 0.00444984 secs using 99.58% CPU
Iteration 90 / LogL: -5500.483 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00334716 secs using 99.82% CPU
Optimizing NNI: done in 0.00436211 secs using 99.97% CPU
Optimizing NNI: done in 0.002321 secs using 99.96% CPU
Optimizing NNI: done in 0.00369096 secs using 99.97% CPU
Optimizing NNI: done in 0.00329208 secs using 99.97% CPU
Optimizing NNI: done in 0.00368309 secs using 99.7% CPU
Optimizing NNI: done in 0.00144792 secs using 99.73% CPU
Optimizing NNI: done in 0.00411391 secs using 99.98% CPU
Optimizing NNI: done in 0.00265908 secs using 99.96% CPU
Optimizing NNI: done in 0.00258493 secs using 99.85% CPU
Iteration 100 / LogL: -5530.453 / Time: 0h:0m:0s (0h:0m:0s left)
Log-likelihood cutoff on original alignment: -5535.201
NOTE: Bootstrap correlation coefficient of split occurrence frequencies: 1.000
Optimizing NNI: done in 0.00240088 secs using 99.34% CPU
Optimizing NNI: done in 0.00348186 secs using 99.98% CPU
TREE SEARCH COMPLETED AFTER 102 ITERATIONS / Time: 0h:0m:0s

--------------------------------------------------------------------
|                    FINALIZING TREE SEARCH                        |
--------------------------------------------------------------------
Performs final model parameters optimization
Estimate model parameters (epsilon = 0.010)
1. Initial log-likelihood: -5500.462
Optimal log-likelihood: -5500.454
Rate parameters:  A-C: 1.00000  A-G: 7.20565  A-T: 1.00000  C-G: 1.00000  C-T: 7.20565  G-T: 1.00000
Base frequencies:  A: 0.388  C: 0.172  G: 0.145  T: 0.295
Gamma shape alpha: 0.452
Parameters optimization took 1 rounds (0.001 sec)
BEST SCORE FOUND : -5500.454
Creating bootstrap support values...
Split supports printed to NEXUS file CT1000.splits.nex
Total tree length: 0.161

Total number of iterations: 102
CPU time used for tree search: 0.755 sec (0h:0m:0s)
Wall-clock time used for tree search: 0.577 sec (0h:0m:0s)
Total CPU time used: 0.797 sec (0h:0m:0s)
Total wall-clock time used: 0.631 sec (0h:0m:0s)

Computing bootstrap consensus tree...
Reading input file CT1000.splits.nex...
11 taxa and 41 splits.
Consensus tree written to CT1000.contree
Reading input trees file CT1000.contree
Log-likelihood of consensus tree: -5500.469

Analysis results written to:
  IQ-TREE report:                CT1000.iqtree
  Maximum-likelihood tree:       CT1000.treefile
  Likelihood distances:          CT1000.mldist

Ultrafast bootstrap approximation results written to:
  Split support values:          CT1000.splits.nex
  Consensus tree:                CT1000.contree
  Screen log file:               CT1000.log

Date and Time: Sun Apr 28 16:43:17 2024
(base) jacquelinelemaire@Jacquelines-Air iqtree-2.2.2.6-MacOSX %
```
### ClustalW trial with 5000 bootstraps
```shell
(base) jacquelinelemaire@Jacquelines-Air iqtree-2.2.2.6-MacOSX % bin/iqtree2 -s /Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNA-clustal-aligned.fasta -m HKY+F+G4 --prefix CT5000 -B 5000
IQ-TREE multicore version 2.2.2.6 COVID-edition for Mac OS X 64-bit built May 27 2023
Developed by Bui Quang Minh, James Barbetti, Nguyen Lam Tung,
Olga Chernomor, Heiko Schmidt, Dominik Schrempf, Michael Woodhams, Ly Trong Nhan.

Host:    Jacquelines-Air.lan (SSE4.2, 8 GB RAM)
Command: bin/iqtree2 -s /Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNA-clustal-aligned.fasta -m HKY+F+G4 --prefix CT5000 -B 5000
Seed:    508176 (Using SPRNG - Scalable Parallel Random Number Generator)
Time:    Sun Apr 28 16:44:05 2024
Kernel:  SSE2 - 1 threads (8 CPU cores detected)

HINT: Use -nt option to specify number of threads because your CPU has 8 cores!
HINT: -nt AUTO will automatically determine the best number of threads to use.

Reading alignment file /Users/jacquelinelemaire/Documents/phylo_class/rscS/Vfischeri_rscS_DNA-clustal-aligned.fasta ... Fasta format detected
Reading fasta file: done in 0.000918865 secs using 69.98% CPU
Alignment most likely contains DNA/RNA sequences
Constructing alignment: done in 0.00143003 secs using 68.74% CPU
Alignment has 12 sequences with 2808 columns, 95 distinct patterns
94 parsimony-informative, 252 singleton sites, 2462 constant sites
        Gap/Ambiguity  Composition  p-value
Analyzing sequences: done in 0.000145912 secs using 6.853% CPU
   1  ES114     0.85%    passed     99.79%
   2  MJ102     0.85%    passed     99.79%
   3  EM24      0.85%    passed     99.93%
   4  EM30      0.85%    passed     99.95%
   5  EM17      0.85%    passed     99.88%
   6  EM18      0.85%    passed     99.97%
   7  MB13B1    0.85%    passed     99.93%
   8  MB14A1    1.28%    passed     99.97%
   9  ES213     0.89%    passed     99.98%
  10  KB2B1     0.89%    passed     99.98%
  11  MB11B1    0.89%    passed     99.98%
  12  MJ8.1     0.21%    passed     95.97%
****  TOTAL     0.85%  0 sequences failed composition chi2 test (p-value<5%; df=3)
NOTE: KB2B1 is identical to ES213 but kept for subsequent analysis
Checking for duplicate sequences: done in 0.000155926 secs using 14.75% CPU
Identifying sites to remove: done in 0.000886917 secs using 98.99% CPU
NOTE: 1 identical sequences (see below) will be ignored for subsequent analysis
NOTE: MB11B1 (identical to ES213) is ignored but added at the end
Alignment was printed to CT5000.uniqueseq.phy

For your convenience alignment with unique sequences printed to CT5000.uniqueseq.phy

Create initial parsimony tree by phylogenetic likelihood library (PLL)... 0.002 seconds
Generating 5000 samples for ultrafast bootstrap (seed: 508176)...

NOTE: 2 MB RAM (0 GB) is required!
Estimate model parameters (epsilon = 0.100)
1. Initial log-likelihood: -5654.374
2. Current log-likelihood: -5605.158
3. Current log-likelihood: -5591.227
4. Current log-likelihood: -5582.494
5. Current log-likelihood: -5555.515
6. Current log-likelihood: -5523.441
7. Current log-likelihood: -5507.293
8. Current log-likelihood: -5504.111
9. Current log-likelihood: -5503.623
Optimal log-likelihood: -5503.561
Rate parameters:  A-C: 1.00000  A-G: 6.97109  A-T: 1.00000  C-G: 1.00000  C-T: 6.97109  G-T: 1.00000
Base frequencies:  A: 0.388  C: 0.172  G: 0.145  T: 0.295
Gamma shape alpha: 0.512
Parameters optimization took 9 rounds (0.015 sec)
Wrote distance file to...
Computing ML distances based on estimated model parameters...
Calculating distance matrix: done in 0.000509977 secs using 63.92% CPU
Computing ML distances took 0.002289 sec (of wall-clock time) 0.000359 sec (of CPU time)
Setting up auxiliary I and S matrices: done in 1.40667e-05 secs using 78.2% CPU
Constructing RapidNJ tree: done in 2.19345e-05 secs using 91.18% CPU
Computing RapidNJ tree took 0.000066 sec (of wall-clock time) 0.000046 sec (of CPU time)
Log-likelihood of RapidNJ tree: -5502.523
--------------------------------------------------------------------
|             INITIALIZING CANDIDATE TREE SET                      |
--------------------------------------------------------------------
Generating 98 parsimony trees... 0.022 second
Computing log-likelihood of 95 initial trees ... 0.021 seconds
Current best score: -5502.523

Do NNI search on 20 best initial trees
Optimizing NNI: done in 0.00576019 secs using 180.4% CPU
Estimate model parameters (epsilon = 0.100)
BETTER TREE FOUND at iteration 1: -5500.470
Optimizing NNI: done in 0.00794196 secs using 198.6% CPU
UPDATE BEST LOG-LIKELIHOOD: -5500.463
Optimizing NNI: done in 0.00797415 secs using 195.8% CPU
UPDATE BEST LOG-LIKELIHOOD: -5500.462
Optimizing NNI: done in 0.00604606 secs using 188.2% CPU
Optimizing NNI: done in 0.00587201 secs using 198.6% CPU
Optimizing NNI: done in 0.00791693 secs using 195% CPU
Optimizing NNI: done in 0.00601792 secs using 198.4% CPU
Optimizing NNI: done in 0.00420117 secs using 192.2% CPU
Optimizing NNI: done in 0.00979185 secs using 195.8% CPU
Optimizing NNI: done in 0.00964713 secs using 197.8% CPU
Iteration 10 / LogL: -5500.466 / Time: 0h:0m:0s
Optimizing NNI: done in 0.00571299 secs using 198.5% CPU
UPDATE BEST LOG-LIKELIHOOD: -5500.462
Optimizing NNI: done in 0.00364685 secs using 197.7% CPU
Optimizing NNI: done in 0.00754595 secs using 193.8% CPU
Optimizing NNI: done in 0.00608206 secs using 194% CPU
Optimizing NNI: done in 0.00755 secs using 191.7% CPU
Optimizing NNI: done in 0.00586796 secs using 142.9% CPU
Optimizing NNI: done in 0.00907612 secs using 235.3% CPU
Optimizing NNI: done in 0.00984693 secs using 194.6% CPU
Optimizing NNI: done in 0.00981498 secs using 180.6% CPU
Optimizing NNI: done in 0.00791502 secs using 225.3% CPU
Iteration 20 / LogL: -5500.577 / Time: 0h:0m:0s
Finish initializing candidate tree set (3)
Current best tree score: -5500.462 / CPU time: 0.200
Number of iterations: 20
--------------------------------------------------------------------
|               OPTIMIZING CANDIDATE TREE SET                      |
--------------------------------------------------------------------
Optimizing NNI: done in 0.00448799 secs using 98.82% CPU
Optimizing NNI: done in 0.00282693 secs using 99.3% CPU
Optimizing NNI: done in 0.00408602 secs using 100% CPU
Optimizing NNI: done in 0.00271082 secs using 99.97% CPU
Optimizing NNI: done in 0.00568199 secs using 98.57% CPU
Optimizing NNI: done in 0.00416398 secs using 98.97% CPU
Optimizing NNI: done in 0.00745296 secs using 99.71% CPU
Optimizing NNI: done in 0.005481 secs using 99.01% CPU
Optimizing NNI: done in 0.00394297 secs using 99.95% CPU
Optimizing NNI: done in 0.00504613 secs using 99.18% CPU
Iteration 30 / LogL: -5530.459 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00450301 secs using 98.2% CPU
Optimizing NNI: done in 0.005476 secs using 99.63% CPU
Optimizing NNI: done in 0.00430799 secs using 99.88% CPU
Optimizing NNI: done in 0.00393486 secs using 99.8% CPU
Optimizing NNI: done in 0.00396514 secs using 99.47% CPU
Optimizing NNI: done in 0.00311422 secs using 99.45% CPU
Optimizing NNI: done in 0.00494003 secs using 99.82% CPU
Optimizing NNI: done in 0.00411391 secs using 99.81% CPU
Optimizing NNI: done in 0.00443101 secs using 99.59% CPU
Optimizing NNI: done in 0.00637221 secs using 97.55% CPU
Iteration 40 / LogL: -5530.403 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00394607 secs using 98.93% CPU
Optimizing NNI: done in 0.00527096 secs using 99.62% CPU
Optimizing NNI: done in 0.00479794 secs using 99.21% CPU
Optimizing NNI: done in 0.00309181 secs using 99.84% CPU
Optimizing NNI: done in 0.00731802 secs using 98.28% CPU
Optimizing NNI: done in 0.00575614 secs using 98.82% CPU
Optimizing NNI: done in 0.00704217 secs using 99.05% CPU
Optimizing NNI: done in 0.0042429 secs using 99.41% CPU
Optimizing NNI: done in 0.00680685 secs using 99.88% CPU
Optimizing NNI: done in 0.00346184 secs using 99.89% CPU
Iteration 50 / LogL: -5530.391 / Time: 0h:0m:0s (0h:0m:0s left)
Log-likelihood cutoff on original alignment: -5547.659
Optimizing NNI: done in 0.00683212 secs using 99.95% CPU
Optimizing NNI: done in 0.00768209 secs using 99.91% CPU
Optimizing NNI: done in 0.00349784 secs using 99.89% CPU
Optimizing NNI: done in 0.0042119 secs using 98.67% CPU
Optimizing NNI: done in 0.00362992 secs using 99.95% CPU
Optimizing NNI: done in 0.005162 secs using 99.9% CPU
Optimizing NNI: done in 0.00497198 secs using 99.9% CPU
Optimizing NNI: done in 0.00366282 secs using 99.08% CPU
Optimizing NNI: done in 0.00432301 secs using 97.78% CPU
UPDATE BEST LOG-LIKELIHOOD: -5500.462
Optimizing NNI: done in 0.00420189 secs using 99.46% CPU
Iteration 60 / LogL: -5500.468 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00375414 secs using 99.76% CPU
Optimizing NNI: done in 0.00496197 secs using 99.15% CPU
Optimizing NNI: done in 0.00548005 secs using 98.39% CPU
Optimizing NNI: done in 0.00428295 secs using 98.41% CPU
Optimizing NNI: done in 0.00325918 secs using 99.99% CPU
Optimizing NNI: done in 0.00467396 secs using 99.96% CPU
Optimizing NNI: done in 0.00324202 secs using 98.49% CPU
Optimizing NNI: done in 0.00585198 secs using 98.55% CPU
Optimizing NNI: done in 0.00357914 secs using 99.47% CPU
Optimizing NNI: done in 0.00465512 secs using 99.83% CPU
Iteration 70 / LogL: -5500.462 / Time: 0h:0m:0s (0h:0m:0s left)
Optimizing NNI: done in 0.00331807 secs using 99.97% CPU
Optimizing NNI: done in 0.00446796 secs using 98.3% CPU
Optimizing NNI: done in 0.00617599 secs using 97.57% CPU
Optimizing NNI: done in 0.00667405 secs using 98.46% CPU
Optimizing NNI: done in 0.00298285 secs using 99.97% CPU
Optimizing NNI: done in 0.00616407 secs using 99.84% CPU
Optimizing NNI: done in 0.0035181 secs using 99.83% CPU
Optimizing NNI: done in 0.00220609 secs using 99.95% CPU
Optimizing NNI: done in 0.0043509 secs using 99.98% CPU
Optimizing NNI: done in 0.00408196 secs using 99.83% CPU
Iteration 80 / LogL: -5500.462 / Time: 0h:0m:1s (0h:0m:0s left)
Optimizing NNI: done in 0.00417304 secs using 99.95% CPU
Optimizing NNI: done in 0.00281 secs using 98.97% CPU
Optimizing NNI: done in 0.00380611 secs using 99.94% CPU
Optimizing NNI: done in 0.00343704 secs using 99.71% CPU
Optimizing NNI: done in 0.00363398 secs using 99.86% CPU
Optimizing NNI: done in 0.00501585 secs using 98.71% CPU
Optimizing NNI: done in 0.00307298 secs using 99.38% CPU
Optimizing NNI: done in 0.00369191 secs using 99.84% CPU
Optimizing NNI: done in 0.00310898 secs using 99.84% CPU
Optimizing NNI: done in 0.00441504 secs using 98.14% CPU
Iteration 90 / LogL: -5500.465 / Time: 0h:0m:1s (0h:0m:0s left)
Optimizing NNI: done in 0.00831604 secs using 99.07% CPU
Optimizing NNI: done in 0.00538683 secs using 99.09% CPU
Optimizing NNI: done in 0.00546908 secs using 99.72% CPU
Optimizing NNI: done in 0.00373006 secs using 99.86% CPU
Optimizing NNI: done in 0.00342512 secs using 99.91% CPU
Optimizing NNI: done in 0.00274897 secs using 98.66% CPU
Optimizing NNI: done in 0.00393701 secs using 99.9% CPU
Optimizing NNI: done in 0.00615001 secs using 99.9% CPU
Optimizing NNI: done in 0.00301385 secs using 99.84% CPU
Optimizing NNI: done in 0.00613284 secs using 99.3% CPU
Iteration 100 / LogL: -5500.468 / Time: 0h:0m:1s (0h:0m:0s left)
Log-likelihood cutoff on original alignment: -5547.653
NOTE: Bootstrap correlation coefficient of split occurrence frequencies: 1.000
Optimizing NNI: done in 0.00268006 secs using 99.85% CPU
Optimizing NNI: done in 0.00369287 secs using 98.54% CPU
TREE SEARCH COMPLETED AFTER 102 ITERATIONS / Time: 0h:0m:1s

--------------------------------------------------------------------
|                    FINALIZING TREE SEARCH                        |
--------------------------------------------------------------------
Performs final model parameters optimization
Estimate model parameters (epsilon = 0.010)
1. Initial log-likelihood: -5500.462
Optimal log-likelihood: -5500.454
Rate parameters:  A-C: 1.00000  A-G: 7.20567  A-T: 1.00000  C-G: 1.00000  C-T: 7.20567  G-T: 1.00000
Base frequencies:  A: 0.388  C: 0.172  G: 0.145  T: 0.295
Gamma shape alpha: 0.452
Parameters optimization took 1 rounds (0.001 sec)
BEST SCORE FOUND : -5500.454
Creating bootstrap support values...
Split supports printed to NEXUS file CT5000.splits.nex
Total tree length: 0.161

Total number of iterations: 102
CPU time used for tree search: 1.582 sec (0h:0m:1s)
Wall-clock time used for tree search: 1.413 sec (0h:0m:1s)
Total CPU time used: 1.696 sec (0h:0m:1s)
Total wall-clock time used: 1.545 sec (0h:0m:1s)

Computing bootstrap consensus tree...
Reading input file CT5000.splits.nex...
11 taxa and 51 splits.
Consensus tree written to CT5000.contree
Reading input trees file CT5000.contree
Log-likelihood of consensus tree: -5500.469

Analysis results written to:
  IQ-TREE report:                CT5000.iqtree
  Maximum-likelihood tree:       CT5000.treefile
  Likelihood distances:          CT5000.mldist

Ultrafast bootstrap approximation results written to:
  Split support values:          CT5000.splits.nex
  Consensus tree:                CT5000.contree
  Screen log file:               CT5000.log

Date and Time: Sun Apr 28 16:44:07 2024
(base) jacquelinelemaire@Jacquelines-Air iqtree-2.2.2.6-MacOSX %
```

### Visualizing IQ-Tree Output 

1. Within RStudio, install necessary packages:
```r
install.packages("adegenet", dep=TRUE)
trying URL 'https://cran.rstudio.com/bin/macosx/big-sur-arm64/contrib/4.3/adegenet_2.1.10.tgz'
Content type 'application/x-gzip' length 2855081 bytes (2.7 MB)
==================================================
downloaded 2.7 MB


The downloaded binary packages are in
	/var/folders/gk/9plsjd_s07b7jlmhsnjy4yxh0000gn/T//Rtmpm4u6B0/downloaded_packages

install.packages("phangorn", dep=TRUE)
Warning in install.packages :
  dependencies ‘Biostrings’, ‘seqLogo’ are not available
trying URL 'https://cran.rstudio.com/bin/macosx/big-sur-arm64/contrib/4.3/phangorn_2.11.1.tgz'
Content type 'application/x-gzip' length 3408275 bytes (3.3 MB)
==================================================
downloaded 3.3 MB


The downloaded binary packages are in
	/var/folders/gk/9plsjd_s07b7jlmhsnjy4yxh0000gn/T//Rtmpm4u6B0/downloaded_packages
```

2. Load the packages:
```r
library(ape)
library(adegenet)
Loading required package: ade4

   /// adegenet 2.1.10 is loaded ////////////

   > overview: '?adegenet'
   > tutorials/doc/questions: 'adegenetWeb()' 
   > bug reports/feature requests: adegenetIssues()

library(phangorn)
Attaching package: ‘phangorn’

The following object is masked from ‘package:adegenet’:

    AICc

```

3. Load the best tree from the IQTree output for all trial runs:
```r
iqtree_c1k <- read.tree(file= "iq-tree-files/CT1000.treefile")
iqtree_c5k <- read.tree(file= "iq-tree-files/CT5000.treefile")
iqtree_w1k <- read.tree(file= "iq-tree-files/T1000.treefile")
iqtree_w5k <- read.tree(file= "iq-tree-files/T5000.treefile")
```

4. Root the trees to MJ8.1:
```r
iqtree_c1k.rooted <- root(iqtree_c1k, outgroup = "MJ8.1", resolve.root = TRUE)
iqtree_c5k.rooted <- root(iqtree_c5k, outgroup = "MJ8.1", resolve.root = TRUE)
iqtree_w1k.rooted <- root(iqtree_w1k, outgroup = "MJ8.1", resolve.root = TRUE)
iqtree_w5k.rooted <- root(iqtree_w5k, outgroup = "MJ8.1", resolve.root = TRUE)
```

1. Plot the tree with node labels visible to show bootstrap supports (%). 
```r
plot(iqtree_c1k.rooted, show.node.label=TRUE)
title("IQ-Tree 1k Bootstrap ClustalW Tree")

plot(iqtree_c5k.rooted, show.node.label=TRUE)
title("IQ-Tree 5k Bootstrap ClustalW Tree")

plot(iqtree_w1k.rooted, show.node.label=TRUE)
title("IQ-Tree 1k Bootstrap MUSCLE Tree")

plot(iqtree_w5k.rooted, show.node.label=TRUE)
title("IQ-Tree 5k Bootstrap MUSCLE Tree")
```

## Bayesian Inference of Phylogeny Using MrBayes

1. Install MrBayes as shown [here](http://nbisweden.github.io/MrBayes/) through homebrew. Note that command line tools through xcode must be installed first, otherwise MrBayes will fail to install. 

Input commands are:

```shell
xcode-select --install
arch -arm64 brew install mrbayes
```

2. Convert multiple sequence alignment files of RscS DNA sequence .fasta to .nxs in R Studio using _seqinr_ and _ape_ packages. Note that input for MrBayes must be .nxs files.  
   A. Input file of MUSCLE alignment: [Vfischeri_rscS_DNA_muscle-aligned.fasta](results/rscS_multiple-seq-alignments/Vfischeri_rscS_DNA_muscle-aligned.fasta)
```shell
install.packages("seqinr")
install.packages("ape")
library(seqinr)
library(ape)

msaM = read.FASTA("/Users/aimes/Temp/PhyloGen563/data/large_files/rscS_multiple-seq-alignments/Vfischeri_rscS_DNA_muscle-aligned.fasta")
write.nexus.data(msaM, file="/Users/aimes/Temp/PhyloGen563/data/large_files/rscS_multiple-seq-alignments/Vfischeri_rscS_DNA_muscle-aligned.nex", format="DNA")

```
   B. Input file of ClustalW alignment: [Vfischeri_rscS_DNA-clustal-aligned.fasta](results/rscS_multiple-seq-alignments/Vfischeri_rscS_DNA-clustal-aligned.fasta)

      a. Only install and load packages if not present from previous step.

```shell
install.packages("seqinr")
install.packages("ape")
library(seqinr)
library(ape)

msaC = read.FASTA("/Users/aimes/Temp/PhyloGen563/data/large_files/rscS_multiple-seq-alignments/Vfischeri_rscS_DNA-clustal-aligned.fasta")
write.nexus.data(msaC, file="/Users/aimes/Temp/PhyloGen563/data/large_files/rscS_multiple-seq-alignments/Vfischeri_rscS_DNA-clustal-aligned.nex", format="DNA")
```

3. Create a MrBayes block in a text (.txt) file called `mbblock.txt` with the following text. The file I created can be found [here](scripts/mbblock.txt). 
   
   A. Note that the commands `mcmc;sumt;` must be present at the end so that the mb block is executed.'mcm' runs MCMC and 'sumt' is the command to obtain a summary tree. 
```
begin mrbayes;
 set autoclose=yes;
 prset brlenspr=unconstrained:exp(10.0);
 prset shapepr=exp(1.0);
 prset tratiopr=beta(1.0,1.0);
 prset statefreqpr=dirichlet(1.0,1.0,1.0,1.0);
 lset nst=2 rates=gamma ngammacat=4;
 mcmcp ngen=1000000 samplefreq=100 printfreq=1000 nruns=3 nchains=3 savebrlens=yes;
 outgroup MJ8.1;
 mcmc;
 sumt;
end;
```

   B. Notes on the choices specified: 
* nst=2 to specify HKY, the same model used when running IQ-Tree
* ngen=1000000 tells MrBayes that its robots should each take 1 million steps.
* samplefreq=100 says to only save parameter values and the tree topology every 100 steps.
* printfreq=1000 specifies a progress report every 1000 steps.
* nruns=3 says to just do three independent runs. MrBayes performs two separate analyses by default.
* nchains=3 says that we would like to have 2 heated chains running in addition to the cold chain.
* savebrlens=yes tells MrBayes that we would like it to save branch lengths when it saves the sampled tree topologies.
* outgroup MJ8.1 specifies that as the outgroup to root the tree. 

4. Append the MrBayes block to the end of the nexus files with the data: [`Vfischeri_rscS_DNA_muscle-aligned.nex`](results/rscS_multiple-seq-alignments/Vfischeri_rscS_DNA_muscle-aligned.nex) and [`Vfischeri_rscS_DNA-clustal-aligned.nex`](results/rscS_multiple-seq-alignments/Vfischeri_rscS_DNA-clustal-aligned.nex). My examples are linked. 

Note: the cat command erased the data portion of the file during testing, so the text of the mbblock.txt was manually copy and pasted in the bottom of the relevant .nex file. 

### Run MUSCLE-aligned Nexus File 

Input command: 
```shell
mb Vfischeri_rscS_DNA_muscle-aligned.nex
```

Output: 
```shell
e local chains...] (...0 remote chains...) -- 0:00:25
      730000 -- (-5534.533) [-5533.171] (-5546.231) * (-5534.514) [-5538.093] (-5536.251) * (-5537.274) [-5536.329] [...1 more local chains...] (...0 remote chains...) -- 0:00:25

      Average standard deviation of split frequencies: 0.003978

      731000 -- [-5541.092] (-5542.759) (-5539.736) * (-5539.739) [-5537.530] (-5543.947) * (-5537.174) [-5536.102] [...1 more local chains...] (...0 remote chains...) -- 0:00:25
      732000 -- (-5539.500) (-5535.276) [-5536.043] * [-5537.596] (-5534.080) (-5536.083) * (-5540.519) [-5536.351] [...1 more local chains...] (...0 remote chains...) -- 0:00:25
      733000 -- [-5537.060] (-5543.271) (-5535.536) * (-5535.919) [-5536.822] (-5542.123) * (-5544.848) (-5533.850) [...1 more local chains...] (...0 remote chains...) -- 0:00:25
      734000 -- (-5534.796) [-5537.547] (-5542.361) * [-5545.288] (-5540.505) (-5540.314) * (-5533.685) (-5548.777) [...1 more local chains...] (...0 remote chains...) -- 0:00:25
      735000 -- (-5549.954) [-5532.580] (-5535.597) * [-5547.399] (-5543.720) (-5541.244) * (-5541.047) [-5535.001] [...1 more local chains...] (...0 remote chains...) -- 0:00:24

      Average standard deviation of split frequencies: 0.004231

      736000 -- [-5540.825] (-5546.522) (-5543.456) * (-5544.488) (-5531.750) [-5532.978] * (-5539.215) (-5531.335) [...1 more local chains...] (...0 remote chains...) -- 0:00:25
      737000 -- (-5543.955) (-5545.529) [-5529.503] * (-5540.253) [-5536.605] (-5541.069) * (-5536.662) [-5544.857] [...1 more local chains...] (...0 remote chains...) -- 0:00:24
      738000 -- (-5538.625) (-5539.365) [-5546.018] * (-5539.267) [-5530.383] (-5540.095) * [-5538.792] (-5541.192) [...1 more local chains...] (...0 remote chains...) -- 0:00:24
      739000 -- (-5548.536) [-5540.945] (-5537.813) * (-5536.279) [-5537.254] (-5537.896) * [-5533.229] (-5534.301) [...1 more local chains...] (...0 remote chains...) -- 0:00:24
      740000 -- (-5531.869) [-5531.003] (-5539.252) * (-5536.379) [-5538.571] (-5542.162) * (-5539.033) (-5533.094) [...1 more local chains...] (...0 remote chains...) -- 0:00:24

      Average standard deviation of split frequencies: 0.004258

      741000 -- [-5535.251] (-5534.102) (-5538.416) * (-5543.375) [-5538.798] (-5550.190) * (-5530.705) (-5542.462) [...1 more local chains...] (...0 remote chains...) -- 0:00:24
      742000 -- [-5538.762] (-5541.864) (-5542.205) * [-5529.408] (-5536.319) (-5536.308) * (-5536.091) [-5534.128] [...1 more local chains...] (...0 remote chains...) -- 0:00:24
      743000 -- (-5534.047) [-5537.687] (-5539.133) * [-5534.200] (-5535.259) (-5539.010) * (-5543.456) (-5539.701) [...1 more local chains...] (...0 remote chains...) -- 0:00:24
      744000 -- (-5531.344) (-5533.706) [-5530.911] * (-5538.488) (-5538.936) [-5540.165] * (-5544.843) (-5530.416) [...1 more local chains...] (...0 remote chains...) -- 0:00:24
      745000 -- (-5541.029) (-5537.189) [-5530.831] * (-5533.501) [-5542.969] (-5533.026) * (-5533.731) (-5542.259) [...1 more local chains...] (...0 remote chains...) -- 0:00:23

      Average standard deviation of split frequencies: 0.004363

      746000 -- [-5546.343] (-5537.349) (-5539.458) * (-5546.349) (-5530.100) [-5534.984] * (-5541.981) (-5542.551) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      747000 -- [-5536.457] (-5540.530) (-5541.320) * (-5546.184) [-5541.012] (-5533.460) * (-5534.021) (-5535.685) [...1 more local chains...] (...0 remote chains...) -- 0:00:24
      748000 -- [-5540.362] (-5540.775) (-5536.617) * (-5540.639) (-5541.670) [-5533.543] * (-5539.008) (-5537.870) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      749000 -- (-5543.679) (-5532.040) [-5531.958] * [-5540.953] (-5534.408) (-5533.496) * [-5535.027] (-5541.572) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      750000 -- (-5539.125) [-5535.636] (-5540.684) * [-5533.640] (-5537.624) (-5541.829) * (-5526.980) (-5543.886) [...1 more local chains...] (...0 remote chains...) -- 0:00:23

      Average standard deviation of split frequencies: 0.004283

      751000 -- (-5538.154) [-5541.766] (-5540.955) * (-5543.632) [-5537.691] (-5532.975) * (-5540.699) (-5533.080) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      752000 -- (-5536.830) (-5541.971) [-5538.032] * [-5532.579] (-5542.450) (-5538.833) * (-5537.265) (-5534.689) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      753000 -- (-5534.610) (-5540.511) [-5540.455] * (-5550.998) (-5534.367) [-5534.929] * (-5540.238) (-5534.996) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      754000 -- [-5533.221] (-5533.033) (-5540.370) * [-5542.074] (-5537.581) (-5541.836) * (-5535.286) (-5540.486) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      755000 -- (-5545.385) (-5542.040) [-5537.470] * (-5540.071) (-5539.815) [-5540.468] * (-5538.857) [-5535.851] [...1 more local chains...] (...0 remote chains...) -- 0:00:23

      Average standard deviation of split frequencies: 0.004241

      756000 -- (-5541.685) [-5531.919] (-5529.006) * (-5536.107) [-5536.184] (-5535.154) * (-5537.653) (-5532.878) [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      757000 -- (-5543.202) [-5532.236] (-5540.903) * (-5533.447) [-5537.489] (-5542.794) * (-5538.254) (-5543.202) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      758000 -- (-5539.726) [-5534.207] (-5542.668) * [-5537.513] (-5532.316) (-5539.332) * [-5534.576] (-5534.809) [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      759000 -- (-5535.178) (-5530.450) [-5537.226] * [-5534.210] (-5538.544) (-5533.866) * (-5540.238) [-5541.086] [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      760000 -- (-5543.553) [-5541.698] (-5543.713) * (-5533.177) [-5532.754] (-5529.130) * (-5547.072) [-5541.365] [...1 more local chains...] (...0 remote chains...) -- 0:00:22

      Average standard deviation of split frequencies: 0.004340

      761000 -- (-5538.394) [-5534.934] (-5534.619) * (-5541.368) (-5536.973) [-5536.272] * (-5549.139) [-5537.503] [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      762000 -- (-5536.721) (-5547.345) [-5531.657] * (-5532.822) [-5538.789] (-5542.998) * (-5539.715) [-5539.617] [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      763000 -- [-5532.118] (-5545.361) (-5535.195) * (-5533.727) [-5535.947] (-5544.639) * [-5543.105] (-5545.915) [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      764000 -- (-5537.836) [-5530.250] (-5539.825) * (-5540.609) [-5542.077] (-5541.971) * [-5541.537] (-5541.732) [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      765000 -- (-5543.733) (-5539.706) [-5535.219] * (-5539.273) [-5533.682] (-5535.719) * [-5538.077] (-5535.168) [...1 more local chains...] (...0 remote chains...) -- 0:00:22

      Average standard deviation of split frequencies: 0.004118

      766000 -- (-5537.552) (-5544.760) [-5534.878] * (-5558.100) (-5538.388) [-5528.290] * (-5538.050) (-5540.162) [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      767000 -- (-5544.894) (-5539.331) [-5535.028] * [-5532.099] (-5531.083) (-5536.936) * [-5537.998] (-5539.566) [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      768000 -- [-5541.611] (-5541.109) (-5540.838) * (-5532.229) [-5540.575] (-5556.429) * (-5541.237) (-5533.499) [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      769000 -- (-5539.215) (-5545.012) [-5530.588] * [-5541.715] (-5542.180) (-5533.495) * (-5541.134) [-5534.253] [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      770000 -- (-5545.832) (-5539.220) [-5539.289] * (-5535.285) (-5532.787) [-5534.367] * (-5541.283) (-5538.671) [...1 more local chains...] (...0 remote chains...) -- 0:00:21

      Average standard deviation of split frequencies: 0.004024

      771000 -- [-5536.532] (-5536.387) (-5540.462) * (-5536.923) [-5531.842] (-5529.572) * (-5543.156) (-5545.333) [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      772000 -- [-5534.812] (-5536.570) (-5536.230) * (-5548.461) (-5541.346) [-5540.692] * (-5551.238) (-5531.912) [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      773000 -- (-5547.067) [-5530.948] (-5549.891) * (-5538.120) (-5545.291) [-5536.169] * (-5544.412) [-5538.372] [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      774000 -- (-5554.521) (-5537.774) [-5535.596] * (-5532.570) (-5540.871) [-5531.286] * (-5530.898) [-5546.339] [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      775000 -- [-5541.973] (-5538.292) (-5540.916) * (-5539.032) [-5529.698] (-5540.988) * [-5542.570] (-5544.102) [...1 more local chains...] (...0 remote chains...) -- 0:00:21

      Average standard deviation of split frequencies: 0.004087

      776000 -- (-5544.712) (-5538.741) [-5533.166] * (-5540.133) (-5539.433) [-5532.993] * [-5537.037] (-5548.281) [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      777000 -- (-5536.460) [-5531.701] (-5547.175) * (-5536.326) (-5543.138) [-5535.526] * [-5532.995] (-5550.565) [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      778000 -- [-5533.701] (-5536.502) (-5540.142) * (-5537.606) [-5540.965] (-5536.578) * [-5536.639] (-5544.630) [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      779000 -- (-5542.135) (-5541.622) [-5560.728] * (-5540.104) [-5530.352] (-5541.319) * [-5537.415] (-5536.363) [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      780000 -- (-5539.217) (-5537.199) [-5537.887] * [-5534.224] (-5539.478) (-5537.791) * (-5545.697) [-5532.916] [...1 more local chains...] (...0 remote chains...) -- 0:00:20

      Average standard deviation of split frequencies: 0.004046

      781000 -- (-5538.734) [-5541.170] (-5547.553) * (-5552.164) (-5532.930) [-5537.027] * (-5532.021) (-5554.658) [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      782000 -- [-5537.377] (-5530.208) (-5535.326) * (-5529.543) (-5542.756) [-5533.735] * (-5539.231) (-5540.852) [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      783000 -- [-5542.041] (-5535.893) (-5535.574) * (-5545.050) (-5541.066) [-5532.202] * (-5545.472) [-5541.723] [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      784000 -- [-5536.294] (-5534.129) (-5531.516) * [-5532.812] (-5537.072) (-5534.474) * [-5536.603] (-5540.283) [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      785000 -- (-5536.067) (-5541.195) [-5544.971] * (-5544.338) [-5537.380] (-5534.756) * [-5535.859] (-5533.200) [...1 more local chains...] (...0 remote chains...) -- 0:00:20

      Average standard deviation of split frequencies: 0.003954

      786000 -- [-5532.543] (-5536.834) (-5543.457) * (-5541.286) (-5540.489) [-5533.376] * (-5536.020) [-5538.003] [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      787000 -- [-5530.871] (-5536.472) (-5543.718) * (-5539.451) [-5540.206] (-5541.428) * [-5533.714] (-5534.597) [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      788000 -- (-5538.211) (-5537.985) [-5532.776] * (-5539.594) (-5541.254) [-5530.214] * (-5532.289) (-5544.397) [...1 more local chains...] (...0 remote chains...) -- 0:00:19
      789000 -- (-5536.461) (-5537.080) [-5530.024] * (-5540.367) (-5537.315) [-5538.302] * (-5534.709) [-5537.026] [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      790000 -- (-5537.859) (-5540.017) [-5535.488] * (-5542.432) [-5533.232] (-5538.284) * [-5539.247] (-5545.619) [...1 more local chains...] (...0 remote chains...) -- 0:00:19

      Average standard deviation of split frequencies: 0.003983

      791000 -- [-5534.830] (-5539.846) (-5543.303) * (-5540.436) (-5542.315) [-5530.186] * (-5543.743) [-5530.516] [...1 more local chains...] (...0 remote chains...) -- 0:00:19
      792000 -- [-5537.092] (-5541.675) (-5533.163) * (-5548.059) [-5531.703] (-5543.352) * (-5541.523) (-5540.361) [...1 more local chains...] (...0 remote chains...) -- 0:00:19
      793000 -- [-5538.681] (-5538.822) (-5537.442) * (-5542.014) (-5541.404) [-5531.128] * (-5544.349) [-5537.200] [...1 more local chains...] (...0 remote chains...) -- 0:00:19
      794000 -- [-5533.767] (-5538.294) (-5532.778) * (-5537.584) [-5537.720] (-5539.628) * (-5541.447) [-5542.414] [...1 more local chains...] (...0 remote chains...) -- 0:00:19
      795000 -- (-5535.237) [-5531.249] (-5539.282) * [-5538.910] (-5538.307) (-5546.909) * [-5537.108] (-5535.018) [...1 more local chains...] (...0 remote chains...) -- 0:00:19

      Average standard deviation of split frequencies: 0.003890

      796000 -- [-5542.845] (-5545.553) (-5538.147) * (-5543.496) (-5546.648) [-5533.984] * (-5539.291) (-5538.211) [...1 more local chains...] (...0 remote chains...) -- 0:00:19
      797000 -- [-5530.924] (-5536.457) (-5535.987) * (-5537.512) (-5534.289) [-5538.734] * [-5534.892] (-5530.585) [...1 more local chains...] (...0 remote chains...) -- 0:00:19
      798000 -- (-5541.685) [-5538.047] (-5535.959) * (-5536.272) (-5537.870) [-5539.220] * (-5536.333) (-5531.170) [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      799000 -- (-5548.074) [-5529.630] (-5556.624) * [-5537.275] (-5537.414) (-5549.382) * (-5535.865) (-5540.828) [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      800000 -- [-5545.094] (-5536.848) (-5544.210) * (-5540.183) (-5536.862) [-5537.881] * (-5538.787) [-5532.551] [...1 more local chains...] (...0 remote chains...) -- 0:00:19

      Average standard deviation of split frequencies: 0.003751

      801000 -- [-5538.196] (-5539.314) (-5553.366) * (-5535.782) (-5535.876) [-5540.757] * (-5530.595) (-5535.138) [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      802000 -- (-5545.901) (-5542.065) [-5543.093] * (-5536.522) (-5547.884) [-5540.377] * (-5540.097) (-5535.043) [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      803000 -- [-5538.020] (-5536.319) (-5541.117) * [-5537.979] (-5549.151) (-5535.470) * [-5537.086] (-5531.691) [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      804000 -- (-5537.994) [-5530.339] (-5543.228) * (-5531.226) [-5540.453] (-5542.437) * [-5527.636] (-5542.297) [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      805000 -- (-5546.052) [-5533.453] (-5537.035) * (-5541.534) (-5539.520) [-5544.223] * [-5535.933] (-5542.311) [...1 more local chains...] (...0 remote chains...) -- 0:00:18

      Average standard deviation of split frequencies: 0.003341

      806000 -- (-5540.134) [-5529.935] (-5532.947) * [-5544.430] (-5548.425) (-5536.353) * (-5531.681) [-5544.122] [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      807000 -- [-5531.136] (-5536.575) (-5532.280) * (-5543.959) (-5540.192) [-5531.857] * (-5540.013) [-5533.539] [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      808000 -- (-5536.329) (-5536.591) [-5536.432] * [-5532.194] (-5536.550) (-5533.827) * (-5534.075) [-5533.729] [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      809000 -- (-5543.904) [-5534.220] (-5533.208) * (-5546.853) [-5537.521] (-5534.343) * (-5540.239) [-5542.314] [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      810000 -- (-5535.539) [-5536.675] (-5544.402) * [-5539.597] (-5536.890) (-5541.367) * [-5540.433] (-5541.410) [...1 more local chains...] (...0 remote chains...) -- 0:00:18

      Average standard deviation of split frequencies: 0.003505

      811000 -- [-5534.110] (-5540.056) (-5536.274) * (-5536.929) (-5533.936) [-5532.747] * (-5533.070) [-5533.694] [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      812000 -- [-5533.181] (-5545.491) (-5541.773) * [-5530.949] (-5541.191) (-5537.047) * (-5543.102) [-5538.091] [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      813000 -- (-5540.193) [-5536.522] (-5543.640) * (-5534.296) [-5534.298] (-5537.189) * (-5535.755) (-5535.067) [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      814000 -- [-5533.425] (-5535.000) (-5535.149) * (-5532.954) (-5549.670) [-5536.630] * (-5547.074) [-5539.952] [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      815000 -- [-5535.542] (-5531.094) (-5542.536) * [-5542.962] (-5532.605) (-5536.987) * [-5534.445] (-5531.892) [...1 more local chains...] (...0 remote chains...) -- 0:00:17

      Average standard deviation of split frequencies: 0.003445

      816000 -- [-5531.789] (-5533.495) (-5539.115) * [-5532.859] (-5535.443) (-5545.282) * [-5538.542] (-5534.528) [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      817000 -- (-5537.788) (-5534.495) [-5530.585] * (-5537.113) (-5535.261) [-5534.601] * [-5540.829] (-5541.700) [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      818000 -- (-5535.383) [-5541.157] (-5546.571) * (-5545.289) (-5542.359) [-5531.363] * (-5560.607) [-5532.519] [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      819000 -- [-5534.351] (-5537.889) (-5537.955) * (-5537.542) [-5536.760] (-5548.040) * (-5547.415) (-5538.260) [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      820000 -- (-5541.593) (-5541.690) [-5531.054] * (-5545.510) (-5548.474) [-5534.633] * (-5540.902) [-5538.178] [...1 more local chains...] (...0 remote chains...) -- 0:00:16

      Average standard deviation of split frequencies: 0.003348

      821000 -- (-5536.784) [-5533.243] (-5539.876) * (-5544.528) (-5535.440) [-5529.660] * (-5540.315) (-5540.556) [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      822000 -- (-5540.788) [-5538.554] (-5544.884) * (-5532.503) [-5544.827] (-5546.630) * (-5540.983) (-5545.010) [...1 more local chains...] (...0 remote chains...) -- 0:00:16
      823000 -- [-5535.194] (-5544.358) (-5536.364) * (-5539.071) (-5534.603) [-5529.174] * [-5535.341] (-5535.205) [...1 more local chains...] (...0 remote chains...) -- 0:00:16
      824000 -- (-5535.188) (-5536.419) [-5544.802] * [-5532.327] (-5534.788) (-5538.877) * [-5532.551] (-5542.475) [...1 more local chains...] (...0 remote chains...) -- 0:00:16
      825000 -- (-5530.476) (-5539.905) [-5540.331] * (-5532.571) (-5547.315) [-5540.499] * (-5535.040) [-5539.287] [...1 more local chains...] (...0 remote chains...) -- 0:00:16

      Average standard deviation of split frequencies: 0.003518

      826000 -- [-5537.132] (-5538.452) (-5532.594) * (-5535.077) (-5546.591) [-5546.163] * (-5534.618) [-5528.952] [...1 more local chains...] (...0 remote chains...) -- 0:00:16
      827000 -- (-5542.376) (-5540.627) [-5533.915] * (-5536.143) [-5538.205] (-5547.699) * (-5545.163) (-5540.071) [...1 more local chains...] (...0 remote chains...) -- 0:00:16
      828000 -- (-5536.815) [-5538.635] (-5547.556) * [-5534.565] (-5535.339) (-5541.443) * (-5534.910) [-5538.039] [...1 more local chains...] (...0 remote chains...) -- 0:00:16
      829000 -- (-5538.633) (-5543.169) [-5541.922] * (-5535.781) [-5538.992] (-5533.779) * (-5542.602) (-5537.738) [...1 more local chains...] (...0 remote chains...) -- 0:00:16
      830000 -- (-5544.184) [-5540.817] (-5529.305) * (-5537.611) (-5541.800) [-5537.584] * (-5545.400) (-5543.736) [...1 more local chains...] (...0 remote chains...) -- 0:00:15

      Average standard deviation of split frequencies: 0.003280

      831000 -- (-5541.590) [-5538.829] (-5529.856) * (-5529.488) [-5536.049] (-5542.671) * (-5530.571) [-5540.322] [...1 more local chains...] (...0 remote chains...) -- 0:00:16
      832000 -- (-5539.022) [-5534.967] (-5539.334) * (-5535.590) [-5540.260] (-5539.709) * (-5549.215) (-5535.846) [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      833000 -- [-5540.374] (-5536.470) (-5536.458) * (-5537.754) (-5534.593) [-5535.833] * [-5547.094] (-5534.409) [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      834000 -- [-5533.840] (-5539.375) (-5535.847) * [-5538.831] (-5539.423) (-5529.147) * (-5539.478) [-5528.426] [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      835000 -- (-5536.407) [-5536.395] (-5537.581) * (-5539.361) (-5542.998) [-5537.570] * (-5550.490) [-5540.110] [...1 more local chains...] (...0 remote chains...) -- 0:00:15

      Average standard deviation of split frequencies: 0.003240

      836000 -- (-5537.368) (-5539.896) [-5529.820] * (-5537.997) [-5545.431] (-5540.715) * (-5542.414) [-5531.130] [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      837000 -- (-5532.961) (-5541.718) [-5538.396] * (-5532.346) [-5539.952] (-5542.879) * (-5530.584) (-5533.929) [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      838000 -- (-5537.906) (-5547.486) [-5538.401] * [-5532.629] (-5538.740) (-5545.370) * (-5536.774) (-5532.992) [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      839000 -- [-5526.027] (-5542.546) (-5541.571) * (-5536.949) [-5532.975] (-5537.554) * [-5536.001] (-5538.904) [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      840000 -- [-5533.135] (-5533.251) (-5538.893) * (-5535.745) [-5527.411] (-5534.065) * [-5535.878] (-5536.969) [...1 more local chains...] (...0 remote chains...) -- 0:00:15

      Average standard deviation of split frequencies: 0.003284

      841000 -- [-5532.725] (-5542.530) (-5543.711) * (-5534.042) (-5540.710) [-5531.827] * (-5544.774) (-5540.053) [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      842000 -- (-5533.805) (-5540.784) [-5534.059] * (-5537.764) (-5542.925) [-5532.625] * [-5538.509] (-5541.950) [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      843000 -- (-5542.055) (-5540.605) [-5539.731] * [-5539.267] (-5542.664) (-5545.453) * [-5537.677] (-5539.402) [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      844000 -- (-5533.918) [-5542.011] (-5537.604) * [-5534.033] (-5552.010) (-5544.505) * [-5533.234] (-5533.175) [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      845000 -- (-5532.232) (-5548.085) [-5539.298] * (-5542.236) (-5536.710) [-5530.910] * (-5539.554) (-5530.445) [...1 more local chains...] (...0 remote chains...) -- 0:00:14

      Average standard deviation of split frequencies: 0.003125

      846000 -- (-5541.289) [-5531.188] (-5537.430) * [-5538.496] (-5541.588) (-5543.060) * [-5530.461] (-5541.381) [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      847000 -- [-5539.058] (-5538.379) (-5545.174) * [-5531.481] (-5530.146) (-5544.368) * (-5545.957) (-5545.604) [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      848000 -- [-5538.944] (-5535.887) (-5540.064) * [-5532.342] (-5542.490) (-5542.340) * (-5538.978) (-5539.837) [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      849000 -- (-5538.012) (-5530.685) [-5543.527] * (-5543.438) (-5537.741) [-5535.257] * (-5537.459) (-5531.177) [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      850000 -- [-5536.640] (-5547.845) (-5538.397) * [-5531.727] (-5535.780) (-5541.888) * [-5539.103] (-5544.288) [...1 more local chains...] (...0 remote chains...) -- 0:00:14

      Average standard deviation of split frequencies: 0.002878

      851000 -- (-5542.660) (-5537.541) [-5539.341] * (-5539.757) [-5537.356] (-5538.044) * [-5537.605] (-5532.739) [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      852000 -- (-5545.587) [-5539.967] (-5540.592) * (-5536.528) (-5543.842) [-5534.454] * (-5545.843) (-5543.970) [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      853000 -- [-5536.236] (-5536.371) (-5538.793) * (-5536.208) (-5537.443) [-5533.313] * (-5541.111) [-5535.449] [...1 more local chains...] (...0 remote chains...) -- 0:00:13
      854000 -- (-5542.199) [-5545.839] (-5537.771) * (-5536.904) [-5534.071] (-5543.288) * (-5543.398) (-5536.222) [...1 more local chains...] (...0 remote chains...) -- 0:00:13
      855000 -- (-5541.317) (-5547.576) [-5538.638] * (-5542.517) (-5541.880) [-5537.200] * [-5534.605] (-5542.486) [...1 more local chains...] (...0 remote chains...) -- 0:00:13

      Average standard deviation of split frequencies: 0.002825

      856000 -- (-5534.599) (-5538.006) [-5537.824] * (-5534.239) (-5539.647) [-5530.705] * [-5531.087] (-5536.705) [...1 more local chains...] (...0 remote chains...) -- 0:00:13
      857000 -- [-5534.495] (-5546.168) (-5530.000) * [-5549.722] (-5552.853) (-5531.333) * [-5533.392] (-5544.909) [...1 more local chains...] (...0 remote chains...) -- 0:00:13
      858000 -- [-5535.626] (-5540.618) (-5539.404) * (-5540.841) (-5537.329) [-5531.830] * (-5539.375) (-5529.298) [...1 more local chains...] (...0 remote chains...) -- 0:00:13
      859000 -- [-5535.146] (-5542.690) (-5545.332) * [-5540.030] (-5533.693) (-5531.839) * (-5550.798) (-5534.582) [...1 more local chains...] (...0 remote chains...) -- 0:00:13
      860000 -- (-5537.573) (-5541.230) [-5536.175] * [-5533.048] (-5540.096) (-5536.980) * (-5545.758) [-5538.724] [...1 more local chains...] (...0 remote chains...) -- 0:00:13

      Average standard deviation of split frequencies: 0.002795

      861000 -- [-5531.229] (-5538.181) (-5531.103) * (-5539.947) [-5537.757] (-5554.284) * (-5545.567) (-5541.477) [...1 more local chains...] (...0 remote chains...) -- 0:00:13
      862000 -- [-5532.706] (-5539.206) (-5538.627) * [-5541.503] (-5541.165) (-5536.425) * [-5535.908] (-5545.525) [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      863000 -- (-5538.140) (-5540.737) [-5534.543] * (-5544.239) (-5530.279) [-5532.430] * [-5535.552] (-5553.007) [...1 more local chains...] (...0 remote chains...) -- 0:00:13
      864000 -- (-5544.304) [-5533.974] (-5535.784) * (-5544.440) [-5531.867] (-5539.982) * [-5546.244] (-5536.633) [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      865000 -- (-5541.017) (-5543.298) [-5531.844] * (-5530.553) [-5534.775] (-5536.660) * (-5542.997) (-5547.535) [...1 more local chains...] (...0 remote chains...) -- 0:00:12

      Average standard deviation of split frequencies: 0.002698

      866000 -- [-5536.400] (-5540.205) (-5548.221) * (-5531.016) [-5539.718] (-5538.406) * (-5536.913) (-5540.943) [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      867000 -- [-5532.586] (-5540.454) (-5535.380) * (-5536.041) [-5542.052] (-5541.945) * (-5540.951) (-5542.600) [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      868000 -- [-5535.794] (-5531.278) (-5543.986) * (-5535.620) (-5545.349) [-5534.967] * (-5541.341) (-5536.854) [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      869000 -- (-5547.708) [-5532.281] (-5536.774) * (-5536.677) (-5536.281) [-5529.635] * [-5535.325] (-5539.106) [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      870000 -- [-5530.374] (-5537.466) (-5538.127) * [-5535.104] (-5529.983) (-5533.197) * (-5535.885) (-5542.893) [...1 more local chains...] (...0 remote chains...) -- 0:00:12

      Average standard deviation of split frequencies: 0.002911

      871000 -- [-5531.422] (-5530.608) (-5536.253) * (-5544.298) [-5538.784] (-5535.114) * [-5544.386] (-5545.713) [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      872000 -- [-5531.152] (-5539.120) (-5535.363) * [-5543.138] (-5538.923) (-5539.386) * (-5536.092) (-5536.630) [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      873000 -- (-5545.433) (-5537.053) [-5534.252] * (-5544.607) (-5538.718) [-5535.449] * [-5533.038] (-5545.738) [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      874000 -- [-5531.915] (-5530.209) (-5533.791) * [-5541.272] (-5537.565) (-5539.060) * (-5532.970) [-5530.908] [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      875000 -- (-5534.715) (-5535.313) [-5537.106] * (-5537.707) [-5543.670] (-5546.917) * (-5539.215) [-5535.231] [...1 more local chains...] (...0 remote chains...) -- 0:00:11

      Average standard deviation of split frequencies: 0.002865

      876000 -- (-5540.817) [-5539.424] (-5535.391) * (-5534.952) [-5533.477] (-5550.695) * (-5544.783) (-5542.644) [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      877000 -- (-5551.325) (-5540.915) [-5532.584] * (-5534.952) [-5531.398] (-5531.643) * (-5537.391) [-5534.374] [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      878000 -- [-5545.437] (-5534.424) (-5535.342) * [-5537.875] (-5543.197) (-5541.959) * (-5545.060) (-5537.381) [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      879000 -- [-5537.044] (-5538.631) (-5533.933) * (-5537.455) (-5539.678) [-5534.310] * (-5532.412) (-5533.462) [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      880000 -- (-5536.254) (-5539.299) [-5535.025] * (-5545.794) (-5546.395) [-5533.043] * (-5535.449) [-5534.411] [...1 more local chains...] (...0 remote chains...) -- 0:00:11

      Average standard deviation of split frequencies: 0.002908

      881000 -- (-5535.747) [-5533.606] (-5534.663) * [-5542.939] (-5539.177) (-5537.681) * (-5539.655) [-5535.538] [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      882000 -- [-5542.635] (-5534.495) (-5541.579) * (-5534.515) (-5548.626) [-5532.202] * (-5537.320) (-5537.191) [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      883000 -- [-5536.589] (-5534.370) (-5538.197) * (-5550.901) (-5536.550) [-5536.310] * (-5531.406) [-5538.140] [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      884000 -- [-5535.394] (-5534.333) (-5542.699) * [-5533.930] (-5539.275) (-5539.745) * (-5538.500) [-5545.635] [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      885000 -- (-5540.473) (-5539.959) [-5542.349] * (-5546.671) [-5533.596] (-5533.026) * (-5536.527) [-5528.409] [...1 more local chains...] (...0 remote chains...) -- 0:00:10

      Average standard deviation of split frequencies: 0.002943

      886000 -- [-5535.284] (-5543.420) (-5534.065) * (-5542.955) [-5538.707] (-5534.856) * [-5536.551] (-5544.874) [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      887000 -- (-5533.659) (-5546.571) [-5537.689] * [-5532.811] (-5540.470) (-5533.678) * (-5535.045) (-5542.727) [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      888000 -- (-5537.268) [-5534.192] (-5542.045) * (-5534.287) (-5531.836) [-5529.616] * (-5532.497) [-5543.300] [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      889000 -- (-5530.935) [-5536.093] (-5536.727) * [-5540.424] (-5538.511) (-5544.702) * (-5533.445) [-5539.790] [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      890000 -- (-5532.609) [-5547.517] (-5539.800) * [-5546.027] (-5546.157) (-5537.884) * (-5547.965) [-5536.280] [...1 more local chains...] (...0 remote chains...) -- 0:00:10

      Average standard deviation of split frequencies: 0.002928

      891000 -- (-5536.307) (-5544.123) [-5535.112] * (-5530.617) (-5538.080) [-5537.367] * (-5536.354) [-5535.560] [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      892000 -- [-5534.239] (-5543.383) (-5540.681) * [-5540.258] (-5532.537) (-5542.178) * (-5540.605) [-5537.188] [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      893000 -- [-5535.200] (-5538.336) (-5536.484) * (-5545.917) [-5531.560] (-5539.087) * [-5537.488] (-5530.700) [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      894000 -- (-5532.943) [-5539.840] (-5543.785) * (-5536.943) (-5543.889) [-5539.531] * (-5536.144) [-5537.430] [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      895000 -- (-5535.184) (-5534.788) [-5541.863] * (-5545.038) (-5538.701) [-5535.234] * (-5540.468) (-5531.934) [...1 more local chains...] (...0 remote chains...) -- 0:00:09

      Average standard deviation of split frequencies: 0.002804

      896000 -- [-5533.207] (-5529.839) (-5534.743) * [-5541.472] (-5535.608) (-5538.877) * [-5543.523] (-5536.242) [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      897000 -- (-5538.610) [-5531.340] (-5535.512) * (-5539.490) [-5538.807] (-5535.637) * (-5528.655) [-5537.591] [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      898000 -- (-5538.323) [-5530.413] (-5541.590) * (-5542.477) [-5537.225] (-5542.052) * (-5542.990) [-5538.820] [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      899000 -- (-5534.541) [-5534.139] (-5540.770) * (-5542.405) [-5540.230] (-5534.432) * (-5543.859) [-5533.860] [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      900000 -- [-5536.654] (-5542.834) (-5535.995) * [-5538.412] (-5542.674) (-5547.298) * (-5534.547) (-5537.818) [...1 more local chains...] (...0 remote chains...) -- 0:00:09

      Average standard deviation of split frequencies: 0.002824

      901000 -- (-5551.021) [-5544.078] (-5539.341) * (-5546.942) [-5538.334] (-5536.053) * [-5533.839] (-5540.915) [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      902000 -- (-5552.095) (-5538.591) [-5532.710] * (-5535.040) (-5545.225) [-5536.910] * (-5537.533) [-5539.263] [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      903000 -- (-5544.745) [-5533.335] (-5546.589) * [-5532.135] (-5539.519) (-5541.521) * (-5540.018) [-5532.470] [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      904000 -- (-5533.589) (-5530.559) [-5542.508] * (-5542.668) [-5535.797] (-5539.779) * [-5532.562] (-5533.156) [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      905000 -- (-5531.859) [-5536.501] (-5545.214) * [-5536.330] (-5538.556) (-5544.446) * (-5534.286) (-5530.807) [...1 more local chains...] (...0 remote chains...) -- 0:00:09

      Average standard deviation of split frequencies: 0.002814

      906000 -- (-5546.309) (-5539.489) [-5538.666] * [-5540.038] (-5535.726) (-5539.616) * [-5535.148] (-5534.816) [...1 more local chains...] (...0 remote chains...) -- 0:00:08
      907000 -- [-5534.995] (-5542.668) (-5541.894) * (-5539.227) (-5555.141) [-5534.767] * (-5537.308) (-5538.776) [...1 more local chains...] (...0 remote chains...) -- 0:00:08
      908000 -- (-5543.862) (-5535.053) [-5541.723] * (-5536.849) [-5538.755] (-5533.729) * (-5545.729) (-5539.053) [...1 more local chains...] (...0 remote chains...) -- 0:00:08
      909000 -- [-5534.041] (-5541.631) (-5532.631) * (-5539.895) (-5542.459) [-5535.571] * [-5538.272] (-5538.472) [...1 more local chains...] (...0 remote chains...) -- 0:00:08
      910000 -- (-5545.520) [-5538.447] (-5537.960) * (-5536.553) [-5534.764] (-5541.521) * (-5535.727) (-5538.982) [...1 more local chains...] (...0 remote chains...) -- 0:00:08

      Average standard deviation of split frequencies: 0.002893

      911000 -- (-5536.437) [-5532.868] (-5537.610) * [-5537.803] (-5550.775) (-5545.244) * [-5536.435] (-5541.792) [...1 more local chains...] (...0 remote chains...) -- 0:00:08
      912000 -- (-5538.016) (-5536.076) [-5542.158] * (-5540.400) [-5536.413] (-5540.712) * (-5534.170) [-5533.518] [...1 more local chains...] (...0 remote chains...) -- 0:00:08
      913000 -- (-5539.100) [-5528.602] (-5541.490) * (-5531.215) (-5537.162) [-5532.717] * [-5532.356] (-5542.492) [...1 more local chains...] (...0 remote chains...) -- 0:00:08
      914000 -- (-5536.085) (-5541.107) [-5536.273] * (-5532.777) (-5542.019) [-5533.520] * (-5544.329) [-5537.040] [...1 more local chains...] (...0 remote chains...) -- 0:00:08
      915000 -- (-5537.069) [-5537.994] (-5542.215) * (-5535.097) (-5541.328) [-5533.049] * [-5533.514] (-5550.963) [...1 more local chains...] (...0 remote chains...) -- 0:00:07

      Average standard deviation of split frequencies: 0.002930

      916000 -- (-5543.828) (-5539.058) [-5539.630] * (-5548.417) [-5530.162] (-5541.038) * (-5540.698) [-5530.198] [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      917000 -- (-5532.541) [-5533.862] (-5544.216) * (-5544.584) (-5546.288) [-5539.477] * (-5540.218) (-5532.791) [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      918000 -- (-5539.575) [-5540.325] (-5542.553) * [-5537.570] (-5541.788) (-5539.277) * [-5535.393] (-5536.686) [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      919000 -- [-5540.316] (-5540.910) (-5537.402) * [-5536.381] (-5536.542) (-5542.989) * (-5539.476) (-5533.233) [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      920000 -- (-5544.906) [-5545.352] (-5534.193) * (-5534.230) [-5533.367] (-5539.118) * (-5545.866) [-5539.525] [...1 more local chains...] (...0 remote chains...) -- 0:00:07

      Average standard deviation of split frequencies: 0.002911

      921000 -- (-5537.648) [-5536.363] (-5535.690) * (-5534.911) (-5527.563) [-5535.374] * [-5543.625] (-5537.727) [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      922000 -- (-5541.259) [-5546.595] (-5535.421) * (-5539.379) (-5531.726) [-5530.363] * [-5539.071] (-5535.655) [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      923000 -- (-5543.831) (-5541.217) [-5533.371] * [-5533.109] (-5537.176) (-5545.506) * (-5542.409) [-5543.240] [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      924000 -- (-5541.478) [-5534.950] (-5536.020) * (-5532.800) [-5537.660] (-5546.233) * (-5544.692) [-5540.941] [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      925000 -- (-5536.404) (-5539.314) [-5533.948] * (-5549.020) (-5550.465) [-5535.953] * [-5536.679] (-5530.613) [...1 more local chains...] (...0 remote chains...) -- 0:00:07

      Average standard deviation of split frequencies: 0.002866

      926000 -- (-5537.132) [-5543.827] (-5531.953) * (-5538.369) [-5541.147] (-5533.171) * (-5542.422) (-5546.211) [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      927000 -- (-5541.155) [-5543.518] (-5546.452) * [-5537.219] (-5534.894) (-5551.902) * (-5539.749) [-5545.252] [...1 more local chains...] (...0 remote chains...) -- 0:00:06
      928000 -- (-5531.865) [-5532.334] (-5536.288) * [-5538.104] (-5545.029) (-5539.694) * [-5531.836] (-5533.094) [...1 more local chains...] (...0 remote chains...) -- 0:00:06
      929000 -- [-5540.002] (-5542.388) (-5536.420) * (-5548.571) (-5538.572) [-5536.360] * [-5542.472] (-5531.529) [...1 more local chains...] (...0 remote chains...) -- 0:00:06
      930000 -- (-5538.037) (-5534.598) [-5539.442] * (-5541.893) (-5539.959) [-5539.521] * [-5533.671] (-5538.245) [...1 more local chains...] (...0 remote chains...) -- 0:00:06

      Average standard deviation of split frequencies: 0.002855

      931000 -- (-5531.950) (-5532.949) [-5537.716] * [-5535.264] (-5539.022) (-5538.011) * (-5529.036) [-5534.673] [...1 more local chains...] (...0 remote chains...) -- 0:00:06
      932000 -- (-5546.691) [-5534.733] (-5540.285) * [-5535.566] (-5538.678) (-5532.004) * (-5537.991) [-5530.238] [...1 more local chains...] (...0 remote chains...) -- 0:00:06
      933000 -- [-5537.739] (-5545.515) (-5533.673) * (-5546.154) (-5530.819) [-5539.524] * (-5534.270) [-5536.885] [...1 more local chains...] (...0 remote chains...) -- 0:00:06
      934000 -- [-5536.583] (-5540.796) (-5532.371) * [-5535.013] (-5531.955) (-5542.525) * [-5535.943] (-5539.281) [...1 more local chains...] (...0 remote chains...) -- 0:00:06
      935000 -- (-5543.109) [-5529.405] (-5538.573) * [-5541.995] (-5546.088) (-5536.628) * (-5540.449) [-5536.623] [...1 more local chains...] (...0 remote chains...) -- 0:00:06

      Average standard deviation of split frequencies: 0.002809

      936000 -- (-5540.910) [-5536.621] (-5534.572) * (-5543.297) (-5530.524) [-5537.230] * (-5541.060) (-5531.343) [...1 more local chains...] (...0 remote chains...) -- 0:00:06
      937000 -- (-5535.629) [-5530.894] (-5547.706) * (-5531.935) [-5540.404] (-5530.536) * (-5535.272) [-5534.822] [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      938000 -- [-5540.552] (-5542.725) (-5540.148) * (-5535.779) (-5533.033) [-5538.577] * [-5527.762] (-5543.285) [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      939000 -- (-5549.357) [-5532.176] (-5542.628) * (-5539.764) (-5540.730) [-5537.953] * (-5540.890) [-5535.750] [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      940000 -- (-5540.397) (-5545.763) [-5538.462] * [-5532.202] (-5542.741) (-5542.650) * (-5544.615) [-5534.473] [...1 more local chains...] (...0 remote chains...) -- 0:00:05

      Average standard deviation of split frequencies: 0.002737

      941000 -- [-5538.423] (-5541.891) (-5539.028) * [-5535.522] (-5552.083) (-5535.274) * (-5538.877) (-5549.491) [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      942000 -- [-5535.456] (-5542.555) (-5546.341) * (-5538.015) (-5538.776) [-5546.786] * (-5534.933) (-5538.598) [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      943000 -- (-5540.695) [-5533.974] (-5538.160) * [-5538.257] (-5535.606) (-5543.011) * (-5545.029) [-5539.974] [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      944000 -- [-5532.142] (-5533.017) (-5536.004) * [-5537.872] (-5535.942) (-5537.361) * (-5540.851) (-5530.789) [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      945000 -- (-5529.500) [-5538.028] (-5535.892) * (-5530.143) (-5540.512) [-5539.750] * (-5540.310) (-5541.332) [...1 more local chains...] (...0 remote chains...) -- 0:00:05

      Average standard deviation of split frequencies: 0.002635

      946000 -- (-5543.173) (-5534.617) [-5532.546] * (-5543.362) [-5531.764] (-5538.154) * (-5551.165) (-5536.556) [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      947000 -- (-5536.835) [-5543.074] (-5540.800) * (-5535.488) (-5532.916) [-5536.646] * (-5529.785) (-5533.939) [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      948000 -- (-5542.218) (-5545.434) [-5532.041] * (-5540.099) [-5542.771] (-5533.654) * (-5533.143) (-5533.371) [...1 more local chains...] (...0 remote chains...) -- 0:00:04
      949000 -- (-5543.941) [-5542.538] (-5534.445) * (-5540.489) [-5529.114] (-5550.111) * (-5538.103) [-5544.034] [...1 more local chains...] (...0 remote chains...) -- 0:00:04
      950000 -- [-5533.943] (-5544.589) (-5543.144) * [-5530.537] (-5542.987) (-5535.898) * (-5550.930) (-5540.371) [...1 more local chains...] (...0 remote chains...) -- 0:00:04

      Average standard deviation of split frequencies: 0.002438

      951000 -- (-5539.397) (-5539.531) [-5543.305] * (-5531.168) (-5535.543) [-5540.283] * (-5543.247) (-5538.621) [...1 more local chains...] (...0 remote chains...) -- 0:00:04
      952000 -- (-5536.213) [-5535.886] (-5539.289) * [-5532.123] (-5539.549) (-5541.796) * (-5537.827) [-5533.455] [...1 more local chains...] (...0 remote chains...) -- 0:00:04
      953000 -- [-5538.267] (-5547.475) (-5543.876) * (-5550.447) [-5530.737] (-5540.929) * [-5536.158] (-5540.011) [...1 more local chains...] (...0 remote chains...) -- 0:00:04
      954000 -- (-5544.010) (-5542.388) [-5534.957] * (-5548.081) [-5533.373] (-5531.274) * (-5540.337) [-5534.566] [...1 more local chains...] (...0 remote chains...) -- 0:00:04
      955000 -- (-5538.375) (-5535.525) [-5536.672] * (-5549.107) [-5532.488] (-5543.871) * [-5532.591] (-5534.733) [...1 more local chains...] (...0 remote chains...) -- 0:00:04

      Average standard deviation of split frequencies: 0.002473

      956000 -- (-5541.933) (-5539.413) [-5533.682] * (-5537.778) [-5531.622] (-5545.863) * [-5535.263] (-5532.570) [...1 more local chains...] (...0 remote chains...) -- 0:00:04
      957000 -- [-5539.093] (-5537.287) (-5539.126) * (-5528.742) [-5531.763] (-5540.539) * [-5539.307] (-5538.339) [...1 more local chains...] (...0 remote chains...) -- 0:00:04
      958000 -- (-5531.799) [-5539.505] (-5540.208) * (-5533.878) [-5538.504] (-5541.638) * (-5536.693) [-5532.790] [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      959000 -- (-5538.597) [-5542.165] (-5544.724) * [-5535.978] (-5539.773) (-5551.346) * (-5537.824) [-5532.507] [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      960000 -- (-5541.224) (-5534.139) [-5538.721] * (-5532.763) [-5538.172] (-5534.760) * [-5532.430] (-5533.086) [...1 more local chains...] (...0 remote chains...) -- 0:00:03

      Average standard deviation of split frequencies: 0.002488

      961000 -- (-5541.800) [-5533.693] (-5543.115) * [-5547.612] (-5539.593) (-5534.639) * (-5536.222) [-5535.821] [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      962000 -- [-5537.115] (-5541.277) (-5536.320) * [-5534.615] (-5534.070) (-5535.121) * (-5535.285) [-5535.050] [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      963000 -- (-5538.574) (-5543.213) [-5542.579] * (-5532.500) (-5541.983) [-5534.586] * [-5530.243] (-5537.452) [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      964000 -- (-5543.767) [-5535.081] (-5544.158) * (-5530.017) [-5536.211] (-5549.717) * (-5541.820) [-5539.559] [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      965000 -- (-5547.444) (-5540.670) [-5538.136] * (-5542.874) (-5540.124) [-5546.380] * (-5533.545) (-5537.473) [...1 more local chains...] (...0 remote chains...) -- 0:00:03

      Average standard deviation of split frequencies: 0.002422

      966000 -- (-5540.079) [-5538.822] (-5546.382) * (-5542.218) [-5540.496] (-5541.213) * [-5534.402] (-5532.300) [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      967000 -- [-5535.169] (-5536.123) (-5533.386) * (-5539.906) [-5535.434] (-5544.205) * [-5535.317] (-5538.344) [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      968000 -- [-5529.384] (-5533.934) (-5530.199) * (-5533.544) [-5541.584] (-5538.354) * [-5547.239] (-5537.980) [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      969000 -- (-5538.511) (-5538.536) [-5531.611] * (-5542.868) (-5543.880) [-5534.227] * (-5540.562) [-5528.935] [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      970000 -- (-5537.680) [-5539.131] (-5537.080) * (-5539.503) [-5543.804] (-5534.955) * (-5536.837) [-5538.555] [...1 more local chains...] (...0 remote chains...) -- 0:00:02

      Average standard deviation of split frequencies: 0.002409

      971000 -- (-5539.160) [-5534.572] (-5546.588) * (-5532.616) [-5536.235] (-5536.170) * (-5539.118) [-5531.422] [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      972000 -- (-5531.174) [-5545.141] (-5548.706) * (-5532.149) (-5541.732) [-5538.129] * [-5534.876] (-5531.437) [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      973000 -- [-5539.860] (-5542.155) (-5538.562) * [-5538.949] (-5539.186) (-5541.424) * [-5541.752] (-5537.633) [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      974000 -- (-5541.887) [-5535.346] (-5534.210) * [-5534.826] (-5537.771) (-5537.635) * (-5539.944) [-5530.502] [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      975000 -- [-5538.302] (-5538.498) (-5537.611) * [-5544.558] (-5546.334) (-5538.438) * (-5534.003) (-5540.740) [...1 more local chains...] (...0 remote chains...) -- 0:00:02

      Average standard deviation of split frequencies: 0.002454

      976000 -- (-5537.163) [-5530.670] (-5536.173) * (-5539.710) [-5533.421] (-5534.625) * [-5532.960] (-5542.774) [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      977000 -- (-5540.513) (-5536.918) [-5540.339] * [-5539.914] (-5541.741) (-5531.575) * [-5536.373] (-5540.501) [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      978000 -- [-5530.730] (-5537.527) (-5537.238) * (-5549.561) (-5541.743) [-5537.868] * [-5538.332] (-5534.699) [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      979000 -- [-5539.521] (-5537.586) (-5539.818) * (-5545.239) (-5538.134) [-5538.877] * (-5543.870) [-5529.460] [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      980000 -- [-5535.488] (-5541.618) (-5536.937) * [-5537.619] (-5543.308) (-5538.618) * [-5540.791] (-5537.129) [...1 more local chains...] (...0 remote chains...) -- 0:00:01

      Average standard deviation of split frequencies: 0.002409

      981000 -- (-5531.306) (-5538.817) [-5540.656] * (-5550.465) [-5535.752] (-5538.983) * (-5542.232) (-5533.138) [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      982000 -- [-5537.585] (-5544.208) (-5529.183) * (-5539.491) [-5534.878] (-5534.601) * [-5543.776] (-5535.255) [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      983000 -- (-5534.658) [-5530.691] (-5535.633) * (-5541.252) (-5544.198) [-5533.634] * (-5532.550) [-5532.172] [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      984000 -- [-5536.848] (-5539.020) (-5535.842) * (-5536.900) (-5535.413) [-5535.741] * [-5539.905] (-5537.830) [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      985000 -- (-5540.634) [-5533.207] (-5539.200) * (-5532.022) [-5545.094] (-5533.021) * (-5531.966) [-5534.053] [...1 more local chains...] (...0 remote chains...) -- 0:00:01

      Average standard deviation of split frequencies: 0.002471

      986000 -- (-5534.642) [-5539.386] (-5537.021) * (-5539.555) [-5534.796] (-5542.533) * (-5540.616) (-5541.005) [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      987000 -- [-5530.465] (-5532.491) (-5537.997) * (-5538.964) (-5538.073) [-5537.669] * (-5538.695) [-5534.921] [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      988000 -- (-5544.418) (-5535.511) [-5533.154] * [-5532.232] (-5540.852) (-5532.976) * (-5533.125) (-5545.163) [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      989000 -- (-5530.021) (-5535.131) [-5534.725] * (-5538.649) (-5531.510) [-5538.439] * [-5539.491] (-5537.014) [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      990000 -- (-5546.650) [-5532.703] (-5538.747) * [-5540.801] (-5544.760) (-5541.853) * [-5536.960] (-5536.619) [...1 more local chains...] (...0 remote chains...) -- 0:00:00

      Average standard deviation of split frequencies: 0.002402

      991000 -- (-5536.161) (-5542.530) [-5538.504] * (-5536.963) [-5539.867] (-5541.005) * (-5535.921) [-5528.848] [...1 more local chains...] (...0 remote chains...) -- 0:00:00
      992000 -- [-5543.416] (-5538.572) (-5539.047) * (-5539.498) (-5539.196) [-5530.917] * (-5547.671) (-5534.846) [...1 more local chains...] (...0 remote chains...) -- 0:00:00
      993000 -- (-5534.189) (-5539.252) [-5543.059] * (-5540.480) [-5532.050] (-5534.855) * (-5539.198) [-5537.541] [...1 more local chains...] (...0 remote chains...) -- 0:00:00
      994000 -- [-5540.783] (-5538.056) (-5539.684) * (-5550.278) [-5540.408] (-5536.246) * (-5536.792) [-5536.672] [...1 more local chains...] (...0 remote chains...) -- 0:00:00
      995000 -- (-5533.098) [-5536.345] (-5537.377) * [-5539.606] (-5537.156) (-5542.993) * (-5540.199) [-5529.144] [...1 more local chains...] (...0 remote chains...) -- 0:00:00

      Average standard deviation of split frequencies: 0.002451

      996000 -- (-5541.491) (-5536.706) [-5537.658] * (-5536.431) (-5535.301) [-5540.245] * [-5533.911] (-5548.705) [...1 more local chains...] (...0 remote chains...) -- 0:00:00
      997000 -- [-5536.350] (-5540.009) (-5543.724) * [-5541.233] (-5533.686) (-5541.226) * (-5543.785) [-5534.378] [...1 more local chains...] (...0 remote chains...) -- 0:00:00
      998000 -- (-5541.012) [-5532.612] (-5539.603) * (-5546.504) (-5534.439) [-5535.546] * (-5536.928) [-5528.120] [...1 more local chains...] (...0 remote chains...) -- 0:00:00
      999000 -- (-5537.287) [-5532.191] (-5540.453) * [-5534.843] (-5533.754) (-5541.005) * (-5536.979) [-5531.365] [...1 more local chains...] (...0 remote chains...) -- 0:00:00
      1000000 -- (-5534.880) (-5537.818) [-5535.921] * [-5537.168] (-5530.655) (-5538.968) * [-5538.090] (-5543.858) [...1 more local chains...] (...0 remote chains...) -- 0:00:00

      Average standard deviation of split frequencies: 0.002545

      Analysis completed in 1 mins 35 seconds
      Analysis used 94.39 seconds of CPU time on processor 0
      Likelihood of best state for "cold" chain of run 1 was -5524.81
      Likelihood of best state for "cold" chain of run 2 was -5524.48
      Likelihood of best state for "cold" chain of run 3 was -5524.81

      Acceptance rates for the moves in the "cold" chain of run 1:
         With prob.   (last 100)   chain accepted proposals by move
            27.0 %     ( 29 %)     Dirichlet(Tratio)
            14.2 %     ( 19 %)     Dirichlet(Pi)
            23.7 %     ( 22 %)     Slider(Pi)
            49.9 %     ( 24 %)     Multiplier(Alpha)
            14.0 %     ( 12 %)     ExtSPR(Tau,V)
             6.9 %     (  6 %)     ExtTBR(Tau,V)
            17.0 %     ( 20 %)     NNI(Tau,V)
            19.8 %     ( 20 %)     ParsSPR(Tau,V)
            26.5 %     ( 19 %)     Multiplier(V)
            40.0 %     ( 35 %)     Nodeslider(V)
            24.9 %     ( 33 %)     TLMultiplier(V)

      Acceptance rates for the moves in the "cold" chain of run 2:
         With prob.   (last 100)   chain accepted proposals by move
            27.4 %     ( 23 %)     Dirichlet(Tratio)
            14.6 %     ( 25 %)     Dirichlet(Pi)
            23.5 %     ( 29 %)     Slider(Pi)
            48.7 %     ( 37 %)     Multiplier(Alpha)
            14.1 %     ( 21 %)     ExtSPR(Tau,V)
             7.1 %     ( 11 %)     ExtTBR(Tau,V)
            16.9 %     ( 19 %)     NNI(Tau,V)
            19.9 %     ( 16 %)     ParsSPR(Tau,V)
            26.6 %     ( 21 %)     Multiplier(V)
            40.1 %     ( 40 %)     Nodeslider(V)
            24.8 %     ( 22 %)     TLMultiplier(V)

      Acceptance rates for the moves in the "cold" chain of run 3:
         With prob.   (last 100)   chain accepted proposals by move
            27.5 %     ( 20 %)     Dirichlet(Tratio)
            14.8 %     ( 27 %)     Dirichlet(Pi)
            23.5 %     ( 34 %)     Slider(Pi)
            48.7 %     ( 30 %)     Multiplier(Alpha)
            13.9 %     (  9 %)     ExtSPR(Tau,V)
             7.0 %     (  8 %)     ExtTBR(Tau,V)
            17.1 %     ( 27 %)     NNI(Tau,V)
            20.1 %     ( 19 %)     ParsSPR(Tau,V)
            26.7 %     ( 25 %)     Multiplier(V)
            40.2 %     ( 45 %)     Nodeslider(V)
            24.5 %     ( 21 %)     TLMultiplier(V)

      Chain swap information for run 1:

                   1       2       3
           --------------------------
         1 |            0.78    0.59
         2 |  333941            0.79
         3 |  332801  333258

      Chain swap information for run 2:

                   1       2       3
           --------------------------
         1 |            0.78    0.58
         2 |  334035            0.79
         3 |  333600  332365

      Chain swap information for run 3:

                   1       2       3
           --------------------------
         1 |            0.78    0.59
         2 |  333274            0.79
         3 |  333383  333343

      Upper diagonal: Proportion of successful state exchanges between chains
      Lower diagonal: Number of attempted state exchanges between chains

      Chain information:

        ID -- Heat
       -----------
         1 -- 1.00  (cold chain)
         2 -- 0.91
         3 -- 0.83

      Heat = 1 / (1 + T * (ID - 1))
         (where T = 0.10 is the temperature and ID is the chain number)

      Summarizing trees in files "Vfischeri_rscS_DNA_muscle-aligned.nex.run1.t", "Vfischeri_rscS_DNA_muscle-aligned.nex.run2.t",...,"Vfischeri_rscS_DNA_muscle-aligned.nex.run3.t"
      Using relative burnin ('relburnin=yes'), discarding the first 25 % of sampled trees
      Writing statistics to files Vfischeri_rscS_DNA_muscle-aligned.nex.<parts|tstat|vstat|trprobs|con>
      Examining first file ...
      Found one tree block in file "Vfischeri_rscS_DNA_muscle-aligned.nex.run1.t" with 10001 trees in last block
      Expecting the same number of trees in the last tree block of all files

      Tree reading status:

      0      10      20      30      40      50      60      70      80      90     100
      v-------v-------v-------v-------v-------v-------v-------v-------v-------v-------v
      *********************************************************************************

      Read a total of 30003 trees in 3 files (sampling 22503 of them)
         (Each file contained 10001 trees of which 7501 were sampled)

      General explanation:

      In an unrooted tree, a taxon bipartition (split) is specified by removing a
      branch, thereby dividing the species into those to the left and those to the
      right of the branch. Here, taxa to one side of the removed branch are denoted
      '.' and those to the other side are denoted '*'. Specifically, the '.' symbol
      is used for the taxa on the same side as the outgroup.

      In a rooted or clock tree, the tree is rooted using the model and not by
      reference to an outgroup. Each bipartition therefore corresponds to a clade,
      that is, a group that includes all the descendants of a particular branch in
      the tree.  Taxa that are included in each clade are denoted using '*', and
      taxa that are not included are denoted using the '.' symbol.

      The output first includes a key to all the bipartitions with frequency larger
      or equual to (Minpartfreq) in at least one run. Minpartfreq is a parameter to
      sumt command and currently it is set to 0.10.  This is followed by a table
      with statistics for the informative bipartitions (those including at least
      two taxa), sorted from highest to lowest probability. For each bipartition,
      the table gives the number of times the partition or split was observed in all
      runs (#obs) and the posterior probability of the bipartition (Probab.), which
      is the same as the split frequency. If several runs are summarized, this is
      followed by the minimum split frequency (Min(s)), the maximum frequency
      (Max(s)), and the standard deviation of frequencies (Stddev(s)) across runs.
      The latter value should approach 0 for all bipartitions as MCMC runs converge.

      This is followed by a table summarizing branch lengths, node heights (if a
      clock model was used) and relaxed clock parameters (if a relaxed clock model
      was used). The mean, variance, and 95 % credible interval are given for each
      of these parameters. If several runs are summarized, the potential scale
      reduction factor (PSRF) is also given; it should approach 1 as runs converge.
      Node heights will take calibration points into account, if such points were
      used in the analysis.

      Note that Stddev may be unreliable if the partition is not present in all
      runs (the last column indicates the number of runs that sampled the partition
      if more than one run is summarized). The PSRF is not calculated at all if
      the partition is not present in all runs.The PSRF is also sensitive to small
      sample sizes and it should only be considered a rough guide to convergence
      since some of the assumptions allowing one to interpret it as a true potential
      scale reduction factor are violated in MrBayes.

      List of taxa in bipartitions:

         1 -- KB2B1
         2 -- ES114
         3 -- EM30
         4 -- EM24
         5 -- MB14A1
         6 -- MB13B1
         7 -- MJ8.1
         8 -- EM18
         9 -- ES213
        10 -- MJ102
        11 -- EM17
        12 -- MB11B1

      Key to taxon bipartitions (saved to file "Vfischeri_rscS_DNA_muscle-aligned.nex.parts"):

      ID -- Partition
      ------------------
       1 -- *...........
       2 -- .*..........
       3 -- ..*.........
       4 -- ...*........
       5 -- ....*.......
       6 -- .....*......
       7 -- ******.*****
       8 -- .......*....
       9 -- ........*...
      10 -- .........*..
      11 -- ..........*.
      12 -- ...........*
      13 -- ..**........
      14 -- ....**......
      15 -- .......*..*.
      16 -- *.......*..*
      17 -- *.****.**.**
      18 -- .*.......*..
      19 -- ..****.*..*.
      20 -- ..**...*..*.
      21 -- ....**.*..*.
      22 -- *.......*...
      23 -- ........*..*
      24 -- *..........*
      25 -- *...**.**.**
      ------------------

      Summary statistics for informative taxon bipartitions
         (saved to file "Vfischeri_rscS_DNA_muscle-aligned.nex.tstat"):

      ID   #obs     Probab.     Sd(s)+      Min(s)      Max(s)   Nruns
      -----------------------------------------------------------------
      13  22503    1.000000    0.000000    1.000000    1.000000    3
      14  22503    1.000000    0.000000    1.000000    1.000000    3
      15  22503    1.000000    0.000000    1.000000    1.000000    3
      16  22502    0.999956    0.000077    0.999867    1.000000    3
      17  22502    0.999956    0.000077    0.999867    1.000000    3
      18  21956    0.975692    0.000204    0.975470    0.975870    3
      19  18980    0.843443    0.006219    0.836955    0.849353    3
      20  11432    0.508021    0.003705    0.503799    0.510732    3
      21  10252    0.455584    0.002477    0.453540    0.458339    3
      22   7551    0.335555    0.003381    0.333156    0.339421    3
      23   7514    0.333911    0.008736    0.325023    0.342488    3
      24   7437    0.330489    0.005675    0.324357    0.335555    3
      25   2331    0.103586    0.002676    0.101053    0.106386    3
      -----------------------------------------------------------------
      + Convergence diagnostic (standard deviation of split frequencies)
        should approach 0.0 as runs converge.


      Summary statistics for branch and node parameters
         (saved to file "Vfischeri_rscS_DNA_muscle-aligned.nex.vstat"):

                                              95% HPD Interval
                                            --------------------
      Parameter      Mean       Variance     Lower       Upper       Median     PSRF+  Nruns
      --------------------------------------------------------------------------------------
      length[1]     0.000362    0.000000    0.000000    0.001059    0.000253    1.000    3
      length[2]     0.001065    0.000000    0.000088    0.002311    0.000943    1.000    3
      length[3]     0.000364    0.000000    0.000000    0.001093    0.000250    1.000    3
      length[4]     0.001088    0.000000    0.000123    0.002311    0.000969    1.000    3
      length[5]     0.001818    0.000001    0.000406    0.003394    0.001692    1.000    3
      length[6]     0.001810    0.000001    0.000418    0.003399    0.001687    1.000    3
      length[7]     0.117889    0.000105    0.098953    0.138613    0.117289    1.000    3
      length[8]     0.001825    0.000001    0.000430    0.003437    0.001706    1.000    3
      length[9]     0.000361    0.000000    0.000000    0.001080    0.000251    1.000    3
      length[10]    0.000378    0.000000    0.000000    0.001132    0.000261    1.000    3
      length[11]    0.000708    0.000000    0.000001    0.001700    0.000590    1.000    3
      length[12]    0.000361    0.000000    0.000000    0.001080    0.000252    1.000    3
      length[13]    0.009540    0.000004    0.006009    0.013363    0.009384    1.000    3
      length[14]    0.001629    0.000001    0.000296    0.003206    0.001500    1.000    3
      length[15]    0.003597    0.000001    0.001450    0.006008    0.003468    1.000    3
      length[16]    0.005103    0.000002    0.002380    0.008039    0.004967    1.000    3
      length[17]    0.014522    0.000007    0.009495    0.019745    0.014345    1.000    3
      length[18]    0.003168    0.000002    0.000259    0.006152    0.003012    1.000    3
      length[19]    0.001656    0.000001    0.000050    0.003384    0.001526    1.000    3
      length[20]    0.000973    0.000000    0.000025    0.002203    0.000850    1.000    3
      length[21]    0.000789    0.000000    0.000016    0.001860    0.000665    1.000    3
      length[22]    0.000361    0.000000    0.000000    0.001072    0.000251    1.000    3
      length[23]    0.000363    0.000000    0.000000    0.001120    0.000248    1.000    3
      length[24]    0.000366    0.000000    0.000000    0.001113    0.000246    1.000    3
      length[25]    0.001012    0.000001    0.000008    0.002463    0.000843    0.999    3
      --------------------------------------------------------------------------------------
      + Convergence diagnostic (PSRF = Potential Scale Reduction Factor; Gelman
        and Rubin, 1992) should approach 1.0 as runs converge. NA is reported when
        deviation of parameter values within all runs is 0 or when a parameter
        value (a branch length, for instance) is not sampled in all runs.


      Summary statistics for partitions with frequency >= 0.10 in at least one run:
          Average standard deviation of split frequencies = 0.002556
          Maximum standard deviation of split frequencies = 0.008736
          Average PSRF for parameter values (excluding NA and >10.0) = 1.000
          Maximum PSRF for parameter values = 1.000


      Clade credibility values:

      /------------------------------------------------------------------- MJ8.1 (7)
      |
      |                                                     /------------- KB2B1 (1)
      |                                                     |
      |            /-------------------100------------------+------------- ES213 (9)
      |            |                                        |
      |            |                                        \------------- MB11B1 (12)
      |            |
      |            |                                        /------------- EM30 (3)
      |-----100----+                          /-----100-----+
      |            |                          |             \------------- EM24 (4)
      +            |             /-----51-----+
      |            |             |            |             /------------- EM18 (8)
      |            |             |            \-----100-----+
      |            \------84-----+                          \------------- EM17 (11)
      |                          |
      |                          |                          /------------- MB14A1 (5)
      |                          \------------100-----------+
      |                                                     \------------- MB13B1 (6)
      |
      |                                                     /------------- ES114 (2)
      \--------------------------98-------------------------+
                                                            \------------- MJ102 (10)


      Phylogram (based on average branch lengths):

      /--------------------------------------------------------------------- MJ8.1 (7)
      |
      |          /- KB2B1 (1)
      |          |
      |       /--+- ES213 (9)
      |       |  |
      |       |  \- MB11B1 (12)
      |       |
      |       |      /- EM30 (3)
      |-------+ /----+
      |       | |    \- EM24 (4)
      +       |/+
      |       ||| /- EM18 (8)
      |       ||\-+
      |       \+  \ EM17 (11)
      |        |
      |        |/- MB14A1 (5)
      |        \+
      |         \- MB13B1 (6)
      |
      | / ES114 (2)
      \-+
        \ MJ102 (10)

      |----------| 0.020 expected changes per site

      Calculating tree probabilities...

      Credible sets of trees (59 trees sampled):
         50 % credible set contains 4 trees
         90 % credible set contains 10 trees
         95 % credible set contains 16 trees
         99 % credible set contains 31 trees

   Exiting mrbayes block
   Reached end of file

   Tasks completed, exiting program because mode is noninteractive
   To return control to the command line after completion of file processing,
   set mode to interactive with 'mb -i <filename>' (i is for interactive)
   or use 'set mode=interactive'
```

### Run CLUSTALW-aligned Nexus File 

Input command: 
```shell
mb Vfischeri_rscS_DNA_clustal-aligned.nex
```

Output: 
```shell
e local chains...] (...0 remote chains...) -- 0:00:25
      728000 -- [-5515.534] (-5515.540) (-5513.405) * (-5518.818) (-5518.333) [-5509.794] * (-5511.826) (-5523.017) [...1 more local chains...] (...0 remote chains...) -- 0:00:25
      729000 -- (-5514.806) [-5508.888] (-5516.528) * (-5516.580) [-5515.449] (-5512.503) * [-5514.855] (-5525.425) [...1 more local chains...] (...0 remote chains...) -- 0:00:25
      730000 -- [-5513.409] (-5515.250) (-5523.656) * (-5520.554) (-5514.249) [-5517.241] * [-5513.458] (-5522.427) [...1 more local chains...] (...0 remote chains...) -- 0:00:25

      Average standard deviation of split frequencies: 0.002702

      731000 -- (-5517.681) [-5513.384] (-5517.583) * (-5520.019) [-5519.808] (-5515.622) * (-5528.321) [-5517.569] [...1 more local chains...] (...0 remote chains...) -- 0:00:25
      732000 -- [-5518.519] (-5513.285) (-5522.804) * (-5518.805) [-5512.290] (-5522.060) * (-5517.117) [-5522.766] [...1 more local chains...] (...0 remote chains...) -- 0:00:24
      733000 -- (-5519.487) [-5516.021] (-5514.212) * [-5520.727] (-5515.099) (-5513.392) * [-5522.004] (-5515.440) [...1 more local chains...] (...0 remote chains...) -- 0:00:24
      734000 -- (-5515.209) [-5511.499] (-5516.786) * (-5519.371) (-5514.238) [-5521.124] * (-5516.813) [-5517.267] [...1 more local chains...] (...0 remote chains...) -- 0:00:24
      735000 -- (-5521.896) (-5512.687) [-5509.275] * [-5520.247] (-5521.957) (-5511.056) * [-5515.478] (-5516.970) [...1 more local chains...] (...0 remote chains...) -- 0:00:24

      Average standard deviation of split frequencies: 0.002546

      736000 -- (-5524.500) [-5515.418] (-5520.016) * (-5517.971) (-5515.337) [-5515.593] * (-5523.208) (-5523.904) [...1 more local chains...] (...0 remote chains...) -- 0:00:24
      737000 -- (-5518.755) [-5517.045] (-5519.254) * (-5508.616) [-5523.858] (-5522.883) * (-5525.133) (-5517.816) [...1 more local chains...] (...0 remote chains...) -- 0:00:24
      738000 -- [-5516.855] (-5514.704) (-5521.693) * (-5516.331) [-5522.754] (-5532.426) * [-5516.658] (-5516.252) [...1 more local chains...] (...0 remote chains...) -- 0:00:24
      739000 -- [-5521.807] (-5522.197) (-5512.747) * [-5517.131] (-5513.183) (-5518.904) * [-5515.105] (-5521.413) [...1 more local chains...] (...0 remote chains...) -- 0:00:24
      740000 -- [-5522.695] (-5519.417) (-5518.385) * (-5517.575) [-5522.744] (-5520.953) * [-5511.108] (-5525.835) [...1 more local chains...] (...0 remote chains...) -- 0:00:24

      Average standard deviation of split frequencies: 0.002574

      741000 -- (-5515.139) (-5517.758) [-5513.097] * [-5526.738] (-5526.727) (-5529.906) * (-5517.365) (-5514.315) [...1 more local chains...] (...0 remote chains...) -- 0:00:24
      742000 -- (-5515.387) [-5511.845] (-5520.657) * [-5523.783] (-5521.857) (-5516.035) * (-5513.979) (-5514.989) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      743000 -- [-5519.533] (-5519.921) (-5519.055) * (-5518.700) (-5522.073) [-5525.731] * [-5522.700] (-5509.365) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      744000 -- (-5518.134) (-5524.468) [-5518.069] * (-5521.930) (-5527.259) [-5525.016] * (-5516.723) (-5530.984) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      745000 -- (-5516.701) [-5519.110] (-5524.772) * [-5512.649] (-5516.682) (-5518.798) * (-5526.364) (-5518.033) [...1 more local chains...] (...0 remote chains...) -- 0:00:23

      Average standard deviation of split frequencies: 0.002396

      746000 -- (-5526.774) (-5521.895) [-5510.027] * (-5518.509) [-5519.429] (-5520.973) * (-5519.203) (-5519.438) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      747000 -- (-5525.822) (-5524.543) [-5526.064] * [-5511.906] (-5526.491) (-5517.078) * (-5512.544) (-5517.463) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      748000 -- (-5519.966) [-5514.841] (-5519.585) * [-5525.124] (-5520.371) (-5525.034) * (-5520.586) (-5528.202) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      749000 -- [-5518.859] (-5512.455) (-5524.118) * (-5520.654) (-5515.057) [-5518.250] * [-5514.489] (-5513.500) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      750000 -- [-5516.705] (-5517.805) (-5517.410) * (-5522.783) (-5519.263) [-5512.845] * [-5519.364] (-5519.252) [...1 more local chains...] (...0 remote chains...) -- 0:00:23

      Average standard deviation of split frequencies: 0.002207

      751000 -- (-5520.018) (-5531.599) [-5515.883] * (-5516.330) (-5519.741) [-5516.385] * [-5510.711] (-5514.532) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      752000 -- [-5515.016] (-5521.890) (-5515.048) * (-5517.437) [-5513.489] (-5516.480) * [-5516.058] (-5522.059) [...1 more local chains...] (...0 remote chains...) -- 0:00:23
      753000 -- [-5512.107] (-5511.684) (-5514.575) * (-5520.349) (-5521.024) [-5519.649] * (-5537.151) [-5515.624] [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      754000 -- (-5520.781) [-5513.293] (-5517.557) * [-5512.485] (-5516.782) (-5522.256) * [-5523.167] (-5509.393) [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      755000 -- (-5519.051) [-5515.024] (-5520.568) * (-5519.866) (-5515.555) [-5524.739] * [-5512.042] (-5519.026) [...1 more local chains...] (...0 remote chains...) -- 0:00:22

      Average standard deviation of split frequencies: 0.002270

      756000 -- (-5524.243) [-5519.852] (-5522.424) * [-5513.819] (-5521.085) (-5522.978) * (-5512.569) (-5516.528) [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      757000 -- (-5514.901) [-5521.542] (-5524.235) * (-5516.460) (-5514.001) [-5523.934] * (-5519.007) [-5523.328] [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      758000 -- (-5521.803) (-5513.817) [-5511.258] * (-5522.068) [-5510.289] (-5525.390) * [-5520.854] (-5510.383) [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      759000 -- [-5527.632] (-5522.563) (-5516.050) * [-5514.994] (-5521.515) (-5525.778) * (-5517.213) [-5521.082] [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      760000 -- [-5519.000] (-5513.514) (-5518.991) * (-5519.181) (-5520.171) [-5515.812] * (-5511.707) (-5523.144) [...1 more local chains...] (...0 remote chains...) -- 0:00:22

      Average standard deviation of split frequencies: 0.002278

      761000 -- [-5517.969] (-5518.782) (-5525.343) * [-5517.114] (-5512.610) (-5527.666) * (-5519.770) (-5527.613) [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      762000 -- (-5524.908) [-5510.786] (-5520.921) * (-5519.762) [-5522.461] (-5514.237) * (-5522.941) (-5523.540) [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      763000 -- (-5516.234) (-5524.125) [-5516.494] * (-5519.164) [-5509.478] (-5511.318) * [-5519.791] (-5520.984) [...1 more local chains...] (...0 remote chains...) -- 0:00:22
      764000 -- (-5513.863) (-5516.380) [-5514.266] * (-5527.928) (-5522.067) [-5523.701] * [-5514.410] (-5515.280) [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      765000 -- (-5518.678) [-5516.796] (-5526.561) * (-5514.322) [-5514.976] (-5518.525) * [-5512.516] (-5525.262) [...1 more local chains...] (...0 remote chains...) -- 0:00:21

      Average standard deviation of split frequencies: 0.002197

      766000 -- [-5516.868] (-5513.258) (-5519.063) * (-5514.177) (-5516.140) [-5520.089] * (-5516.606) [-5510.958] [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      767000 -- (-5523.038) (-5528.576) [-5520.017] * (-5514.257) (-5517.758) [-5524.180] * (-5507.873) [-5518.140] [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      768000 -- (-5515.638) [-5521.279] (-5523.521) * (-5524.797) (-5516.221) [-5510.259] * [-5518.062] (-5520.285) [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      769000 -- (-5521.091) (-5521.198) [-5513.317] * (-5522.720) [-5513.568] (-5518.832) * (-5517.325) [-5509.132] [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      770000 -- (-5513.952) [-5525.483] (-5525.356) * [-5518.979] (-5508.393) (-5531.453) * (-5521.701) [-5524.250] [...1 more local chains...] (...0 remote chains...) -- 0:00:21

      Average standard deviation of split frequencies: 0.002019

      771000 -- [-5511.897] (-5517.964) (-5517.453) * (-5536.966) (-5524.951) [-5519.948] * (-5519.697) (-5519.463) [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      772000 -- [-5512.372] (-5520.231) (-5528.229) * [-5511.051] (-5516.661) (-5510.958) * (-5523.112) [-5520.203] [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      773000 -- (-5517.475) (-5518.464) [-5523.490] * (-5524.634) (-5529.557) [-5512.963] * (-5519.376) (-5530.684) [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      774000 -- (-5514.890) (-5522.946) [-5519.594] * (-5515.928) (-5519.125) [-5517.097] * (-5519.404) [-5512.191] [...1 more local chains...] (...0 remote chains...) -- 0:00:21
      775000 -- [-5515.205] (-5516.699) (-5522.695) * [-5517.569] (-5520.587) (-5524.596) * [-5520.684] (-5513.962) [...1 more local chains...] (...0 remote chains...) -- 0:00:20

      Average standard deviation of split frequencies: 0.001992

      776000 -- (-5518.862) [-5523.155] (-5516.694) * (-5520.757) [-5512.845] (-5513.369) * [-5514.275] (-5521.703) [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      777000 -- (-5519.434) [-5514.183] (-5518.372) * (-5511.648) (-5518.810) [-5516.469] * (-5520.281) (-5519.951) [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      778000 -- (-5530.979) [-5514.523] (-5514.604) * (-5517.110) [-5517.199] (-5530.008) * (-5524.538) (-5518.492) [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      779000 -- (-5521.418) (-5526.065) [-5526.096] * [-5515.791] (-5523.434) (-5517.220) * [-5515.102] (-5523.190) [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      780000 -- (-5513.343) [-5514.839] (-5518.485) * (-5525.342) [-5516.697] (-5512.887) * (-5525.854) [-5519.022] [...1 more local chains...] (...0 remote chains...) -- 0:00:20

      Average standard deviation of split frequencies: 0.001830

      781000 -- (-5515.371) (-5517.245) [-5512.933] * (-5521.624) [-5516.256] (-5515.265) * [-5522.360] (-5512.273) [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      782000 -- [-5518.450] (-5512.761) (-5519.347) * (-5519.439) [-5525.780] (-5524.456) * (-5518.880) [-5511.615] [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      783000 -- (-5523.993) [-5518.030] (-5519.838) * [-5514.805] (-5519.559) (-5513.935) * (-5518.586) (-5528.022) [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      784000 -- (-5515.379) [-5513.605] (-5519.145) * (-5517.428) (-5517.182) [-5522.461] * (-5513.291) [-5520.825] [...1 more local chains...] (...0 remote chains...) -- 0:00:20
      785000 -- (-5518.102) (-5523.517) [-5520.703] * (-5514.147) [-5514.847] (-5516.026) * (-5520.344) (-5515.920) [...1 more local chains...] (...0 remote chains...) -- 0:00:19

      Average standard deviation of split frequencies: 0.001781

      786000 -- (-5526.658) (-5519.293) [-5511.486] * (-5515.457) [-5528.160] (-5517.499) * [-5520.294] (-5522.643) [...1 more local chains...] (...0 remote chains...) -- 0:00:19
      787000 -- [-5515.705] (-5527.782) (-5522.384) * (-5511.976) [-5522.046] (-5510.381) * [-5518.629] (-5521.674) [...1 more local chains...] (...0 remote chains...) -- 0:00:19
      788000 -- (-5517.295) [-5515.193] (-5512.972) * [-5519.683] (-5524.223) (-5516.321) * [-5520.365] (-5514.107) [...1 more local chains...] (...0 remote chains...) -- 0:00:19
      789000 -- (-5527.773) [-5509.963] (-5519.126) * (-5524.125) (-5517.979) [-5517.271] * [-5512.298] (-5527.184) [...1 more local chains...] (...0 remote chains...) -- 0:00:19
      790000 -- (-5526.481) [-5515.808] (-5527.070) * [-5516.991] (-5524.138) (-5516.601) * (-5523.376) (-5523.936) [...1 more local chains...] (...0 remote chains...) -- 0:00:19

      Average standard deviation of split frequencies: 0.001987

      791000 -- (-5515.852) [-5512.679] (-5512.355) * (-5522.263) [-5512.581] (-5523.773) * [-5523.213] (-5518.832) [...1 more local chains...] (...0 remote chains...) -- 0:00:19
      792000 -- (-5523.995) [-5511.190] (-5516.832) * (-5516.439) [-5518.637] (-5517.673) * [-5514.577] (-5517.446) [...1 more local chains...] (...0 remote chains...) -- 0:00:19
      793000 -- (-5516.177) [-5519.316] (-5518.635) * [-5515.797] (-5525.801) (-5520.199) * (-5516.842) [-5518.637] [...1 more local chains...] (...0 remote chains...) -- 0:00:19
      794000 -- [-5517.483] (-5517.988) (-5525.450) * (-5512.144) (-5517.507) [-5522.171] * [-5521.377] (-5531.253) [...1 more local chains...] (...0 remote chains...) -- 0:00:19
      795000 -- (-5516.658) (-5526.522) [-5517.647] * [-5512.197] (-5514.083) (-5518.192) * (-5514.684) (-5519.520) [...1 more local chains...] (...0 remote chains...) -- 0:00:19

      Average standard deviation of split frequencies: 0.002017

      796000 -- (-5518.402) [-5516.788] (-5528.581) * (-5522.645) [-5519.983] (-5519.289) * [-5515.520] (-5519.181) [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      797000 -- (-5516.606) (-5524.341) [-5512.218] * [-5526.556] (-5523.727) (-5527.425) * (-5520.236) (-5526.328) [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      798000 -- (-5522.543) (-5523.469) [-5515.031] * (-5513.826) (-5518.509) [-5513.760] * (-5522.793) (-5518.032) [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      799000 -- (-5525.016) (-5514.540) [-5514.352] * [-5519.707] (-5518.058) (-5517.498) * (-5521.851) (-5516.744) [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      800000 -- [-5517.385] (-5522.006) (-5513.824) * [-5518.052] (-5513.688) (-5518.092) * (-5519.272) [-5521.405] [...1 more local chains...] (...0 remote chains...) -- 0:00:18

      Average standard deviation of split frequencies: 0.001932

      801000 -- (-5517.708) [-5525.221] (-5515.314) * (-5517.070) [-5516.831] (-5518.329) * [-5524.226] (-5519.131) [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      802000 -- (-5520.268) (-5522.381) [-5515.861] * [-5520.643] (-5519.718) (-5518.109) * [-5516.673] (-5527.617) [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      803000 -- [-5514.418] (-5521.943) (-5516.907) * [-5515.299] (-5513.672) (-5519.756) * [-5516.962] (-5522.887) [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      804000 -- (-5518.561) (-5530.410) [-5514.080] * (-5518.097) [-5517.087] (-5519.733) * (-5515.749) (-5519.346) [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      805000 -- [-5527.406] (-5521.094) (-5515.529) * [-5512.283] (-5512.945) (-5516.482) * (-5514.826) (-5530.107) [...1 more local chains...] (...0 remote chains...) -- 0:00:18

      Average standard deviation of split frequencies: 0.001931

      806000 -- (-5532.153) [-5514.123] (-5516.466) * [-5512.162] (-5525.132) (-5519.609) * (-5524.307) [-5510.173] [...1 more local chains...] (...0 remote chains...) -- 0:00:18
      807000 -- [-5513.991] (-5518.085) (-5519.232) * (-5511.751) [-5516.907] (-5517.435) * [-5518.277] (-5513.502) [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      808000 -- [-5516.598] (-5531.046) (-5524.479) * (-5519.940) [-5516.305] (-5512.075) * [-5515.281] (-5525.159) [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      809000 -- (-5517.665) (-5512.455) [-5518.041] * (-5524.943) [-5520.011] (-5512.873) * (-5518.200) [-5514.314] [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      810000 -- (-5521.326) [-5518.998] (-5515.196) * [-5520.055] (-5520.328) (-5515.969) * (-5522.115) (-5516.148) [...1 more local chains...] (...0 remote chains...) -- 0:00:17

      Average standard deviation of split frequencies: 0.001868

      811000 -- [-5523.422] (-5521.376) (-5521.945) * (-5526.624) [-5530.201] (-5521.006) * [-5510.007] (-5519.875) [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      812000 -- (-5526.355) (-5520.002) [-5519.769] * (-5519.556) (-5523.421) [-5513.673] * [-5516.119] (-5515.547) [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      813000 -- (-5514.279) (-5518.451) [-5522.979] * [-5515.059] (-5522.984) (-5516.927) * (-5525.320) [-5523.803] [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      814000 -- (-5519.811) [-5516.435] (-5521.524) * (-5529.475) (-5532.761) [-5521.736] * (-5518.569) (-5520.076) [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      815000 -- (-5514.708) (-5521.023) [-5514.992] * [-5515.753] (-5524.960) (-5526.971) * (-5519.432) [-5528.068] [...1 more local chains...] (...0 remote chains...) -- 0:00:17

      Average standard deviation of split frequencies: 0.001931

      816000 -- [-5521.375] (-5521.316) (-5514.668) * (-5530.302) [-5510.672] (-5520.542) * [-5515.208] (-5514.209) [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      817000 -- [-5521.779] (-5516.659) (-5514.252) * (-5519.236) (-5517.265) [-5510.850] * [-5514.846] (-5517.336) [...1 more local chains...] (...0 remote chains...) -- 0:00:17
      818000 -- [-5518.785] (-5520.652) (-5518.239) * (-5515.693) (-5522.076) [-5522.730] * (-5517.916) [-5514.827] [...1 more local chains...] (...0 remote chains...) -- 0:00:16
      819000 -- (-5522.900) [-5517.795] (-5516.543) * (-5511.586) (-5528.683) [-5519.043] * (-5511.334) (-5518.394) [...1 more local chains...] (...0 remote chains...) -- 0:00:16
      820000 -- (-5516.347) (-5519.024) [-5517.308] * [-5515.153] (-5513.832) (-5523.169) * [-5515.217] (-5522.771) [...1 more local chains...] (...0 remote chains...) -- 0:00:16

      Average standard deviation of split frequencies: 0.001912

      821000 -- (-5529.386) [-5515.572] (-5517.946) * [-5516.158] (-5517.293) (-5516.890) * (-5522.366) [-5513.251] [...1 more local chains...] (...0 remote chains...) -- 0:00:16
      822000 -- (-5525.558) [-5527.536] (-5522.622) * (-5523.330) [-5508.501] (-5523.719) * [-5525.622] (-5523.825) [...1 more local chains...] (...0 remote chains...) -- 0:00:16
      823000 -- (-5523.127) (-5525.528) [-5520.838] * [-5522.298] (-5529.765) (-5518.849) * [-5513.389] (-5523.238) [...1 more local chains...] (...0 remote chains...) -- 0:00:16
      824000 -- (-5521.915) (-5515.017) [-5511.498] * [-5514.857] (-5522.306) (-5512.973) * [-5512.066] (-5513.439) [...1 more local chains...] (...0 remote chains...) -- 0:00:16
      825000 -- (-5510.657) (-5520.885) [-5511.497] * [-5518.131] (-5515.891) (-5514.746) * (-5517.769) (-5518.655) [...1 more local chains...] (...0 remote chains...) -- 0:00:16

      Average standard deviation of split frequencies: 0.001815

      826000 -- [-5518.500] (-5523.925) (-5530.952) * [-5514.975] (-5520.341) (-5516.492) * [-5517.855] (-5524.314) [...1 more local chains...] (...0 remote chains...) -- 0:00:16
      827000 -- (-5518.293) [-5518.308] (-5514.100) * (-5527.614) [-5521.333] (-5519.442) * (-5522.220) [-5520.650] [...1 more local chains...] (...0 remote chains...) -- 0:00:16
      828000 -- (-5516.981) (-5515.031) [-5513.561] * (-5518.797) (-5518.656) [-5515.355] * (-5519.366) [-5519.043] [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      829000 -- (-5521.065) (-5519.006) [-5515.921] * (-5512.961) [-5515.527] (-5518.741) * (-5518.351) (-5520.663) [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      830000 -- (-5518.483) [-5518.019] (-5516.816) * [-5514.706] (-5522.454) (-5519.536) * (-5517.805) [-5508.446] [...1 more local chains...] (...0 remote chains...) -- 0:00:15

      Average standard deviation of split frequencies: 0.001839

      831000 -- [-5513.276] (-5516.757) (-5513.852) * (-5518.291) [-5517.068] (-5514.553) * (-5511.190) (-5518.123) [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      832000 -- (-5512.608) [-5515.982] (-5518.481) * (-5514.158) (-5513.474) [-5514.081] * [-5517.777] (-5520.411) [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      833000 -- (-5530.138) [-5516.322] (-5516.265) * (-5519.461) (-5513.789) [-5515.880] * (-5531.307) (-5513.090) [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      834000 -- (-5521.460) [-5517.205] (-5521.254) * (-5516.107) [-5511.335] (-5517.727) * (-5525.469) (-5519.443) [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      835000 -- (-5521.175) (-5515.100) [-5523.275] * (-5515.949) [-5512.673] (-5515.796) * (-5509.538) (-5516.223) [...1 more local chains...] (...0 remote chains...) -- 0:00:15

      Average standard deviation of split frequencies: 0.001780

      836000 -- (-5523.918) (-5519.691) [-5515.635] * (-5513.493) [-5515.204] (-5521.705) * (-5527.960) (-5517.321) [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      837000 -- [-5515.394] (-5517.940) (-5518.495) * (-5523.413) (-5523.373) [-5523.089] * [-5513.917] (-5523.999) [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      838000 -- [-5511.738] (-5517.177) (-5515.817) * (-5532.183) [-5516.402] (-5515.582) * (-5522.479) (-5519.433) [...1 more local chains...] (...0 remote chains...) -- 0:00:15
      839000 -- (-5514.906) [-5519.319] (-5518.798) * [-5516.701] (-5519.117) (-5512.294) * (-5519.170) (-5522.677) [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      840000 -- (-5516.784) (-5527.450) [-5517.125] * [-5520.559] (-5516.652) (-5521.218) * (-5521.122) (-5519.686) [...1 more local chains...] (...0 remote chains...) -- 0:00:14

      Average standard deviation of split frequencies: 0.001678

      841000 -- (-5515.929) (-5520.522) [-5525.001] * (-5518.821) [-5518.209] (-5523.088) * (-5527.213) [-5512.418] [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      842000 -- (-5520.333) [-5510.752] (-5519.008) * (-5515.054) [-5511.866] (-5517.356) * [-5509.955] (-5516.484) [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      843000 -- (-5521.594) [-5526.520] (-5516.016) * (-5523.379) (-5517.193) [-5514.234] * [-5521.203] (-5523.432) [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      844000 -- (-5512.269) [-5522.421] (-5523.680) * (-5521.917) [-5521.099] (-5523.099) * (-5515.964) (-5520.692) [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      845000 -- [-5516.194] (-5532.150) (-5526.329) * (-5525.768) (-5526.337) [-5513.937] * (-5518.147) (-5517.693) [...1 more local chains...] (...0 remote chains...) -- 0:00:14

      Average standard deviation of split frequencies: 0.001613

      846000 -- [-5513.441] (-5523.457) (-5519.139) * (-5519.334) [-5513.782] (-5514.210) * (-5515.423) [-5518.826] [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      847000 -- (-5521.963) (-5521.697) [-5518.298] * [-5516.896] (-5520.910) (-5517.000) * (-5516.022) (-5531.151) [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      848000 -- (-5519.922) (-5515.416) [-5518.976] * (-5525.091) [-5518.243] (-5521.932) * (-5521.129) (-5526.114) [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      849000 -- [-5516.610] (-5518.111) (-5525.509) * (-5526.870) [-5515.592] (-5511.784) * [-5520.570] (-5519.826) [...1 more local chains...] (...0 remote chains...) -- 0:00:14
      850000 -- (-5520.377) (-5532.351) [-5512.492] * [-5525.258] (-5521.973) (-5521.494) * (-5523.846) [-5512.437] [...1 more local chains...] (...0 remote chains...) -- 0:00:13

      Average standard deviation of split frequencies: 0.001518

      851000 -- (-5521.555) [-5515.190] (-5523.021) * [-5514.779] (-5516.021) (-5525.174) * (-5517.476) (-5514.622) [...1 more local chains...] (...0 remote chains...) -- 0:00:13
      852000 -- [-5516.349] (-5526.606) (-5516.578) * (-5510.360) (-5518.008) [-5518.571] * [-5511.129] (-5517.152) [...1 more local chains...] (...0 remote chains...) -- 0:00:13
      853000 -- (-5516.112) [-5518.817] (-5526.495) * (-5515.936) [-5512.341] (-5525.128) * (-5525.483) [-5528.123] [...1 more local chains...] (...0 remote chains...) -- 0:00:13
      854000 -- (-5521.108) [-5517.165] (-5521.594) * [-5514.745] (-5510.990) (-5517.858) * [-5512.899] (-5516.240) [...1 more local chains...] (...0 remote chains...) -- 0:00:13
      855000 -- (-5517.380) (-5519.900) [-5521.193] * (-5522.905) (-5508.958) [-5511.045] * (-5527.760) [-5516.923] [...1 more local chains...] (...0 remote chains...) -- 0:00:13

      Average standard deviation of split frequencies: 0.001705

      856000 -- (-5520.585) (-5531.569) [-5520.395] * (-5524.274) (-5513.870) [-5518.835] * (-5521.223) (-5522.117) [...1 more local chains...] (...0 remote chains...) -- 0:00:13
      857000 -- (-5512.673) (-5533.942) [-5510.040] * [-5514.802] (-5517.438) (-5523.067) * (-5523.703) (-5517.193) [...1 more local chains...] (...0 remote chains...) -- 0:00:13
      858000 -- (-5512.766) [-5515.136] (-5513.525) * [-5515.892] (-5511.313) (-5518.811) * (-5522.718) [-5517.011] [...1 more local chains...] (...0 remote chains...) -- 0:00:13
      859000 -- (-5520.299) (-5520.002) [-5517.771] * [-5511.824] (-5520.061) (-5516.014) * (-5517.153) [-5513.302] [...1 more local chains...] (...0 remote chains...) -- 0:00:13
      860000 -- [-5521.848] (-5521.092) (-5511.091) * (-5520.163) (-5517.037) [-5512.642] * (-5523.335) (-5530.837) [...1 more local chains...] (...0 remote chains...) -- 0:00:13

      Average standard deviation of split frequencies: 0.001901

      861000 -- (-5518.265) (-5520.990) [-5524.242] * (-5522.068) [-5515.472] (-5518.812) * (-5518.079) [-5519.195] [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      862000 -- (-5521.612) (-5517.207) [-5508.454] * (-5513.980) [-5529.063] (-5510.500) * (-5521.551) (-5522.570) [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      863000 -- (-5520.945) [-5512.268] (-5522.315) * [-5517.715] (-5518.977) (-5517.973) * (-5513.044) (-5523.465) [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      864000 -- [-5514.943] (-5520.650) (-5516.351) * (-5515.761) (-5533.282) [-5512.857] * (-5519.070) [-5520.304] [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      865000 -- [-5511.411] (-5517.636) (-5517.655) * (-5522.030) (-5527.337) [-5509.995] * [-5513.618] (-5516.671) [...1 more local chains...] (...0 remote chains...) -- 0:00:12

      Average standard deviation of split frequencies: 0.001946

      866000 -- (-5510.875) (-5514.385) [-5510.620] * [-5515.435] (-5526.978) (-5516.526) * [-5521.672] (-5523.239) [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      867000 -- (-5515.199) (-5516.741) [-5517.728] * (-5514.927) [-5519.764] (-5516.572) * (-5520.585) [-5516.235] [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      868000 -- (-5524.156) (-5519.427) [-5523.010] * (-5516.670) [-5510.480] (-5517.321) * [-5514.742] (-5526.206) [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      869000 -- (-5522.598) (-5520.888) [-5511.486] * (-5526.339) (-5527.099) [-5516.643] * (-5526.853) (-5528.450) [...1 more local chains...] (...0 remote chains...) -- 0:00:12
      870000 -- [-5516.760] (-5522.121) (-5512.066) * (-5520.162) (-5514.484) [-5514.850] * [-5516.670] (-5526.644) [...1 more local chains...] (...0 remote chains...) -- 0:00:12

      Average standard deviation of split frequencies: 0.001876

      871000 -- (-5520.515) [-5519.236] (-5509.942) * (-5519.615) [-5514.311] (-5520.848) * (-5513.890) (-5517.446) [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      872000 -- (-5514.262) [-5511.119] (-5517.532) * [-5510.919] (-5512.772) (-5529.876) * (-5514.089) [-5511.790] [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      873000 -- [-5513.916] (-5513.806) (-5522.729) * (-5517.767) [-5518.778] (-5520.146) * [-5513.122] (-5521.879) [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      874000 -- [-5511.434] (-5521.927) (-5514.407) * (-5518.320) (-5520.637) [-5512.816] * [-5517.798] (-5516.338) [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      875000 -- (-5512.681) (-5518.185) [-5512.227] * (-5517.394) (-5521.205) [-5516.076] * (-5515.246) [-5517.685] [...1 more local chains...] (...0 remote chains...) -- 0:00:11

      Average standard deviation of split frequencies: 0.001875

      876000 -- (-5516.380) (-5524.002) [-5521.444] * [-5517.559] (-5519.907) (-5524.688) * (-5517.543) [-5518.992] [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      877000 -- (-5517.691) [-5516.204] (-5512.165) * (-5520.234) (-5521.790) [-5517.892] * (-5514.987) [-5519.031] [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      878000 -- (-5520.984) (-5524.200) [-5512.074] * (-5520.631) (-5512.779) [-5511.184] * (-5516.888) [-5513.555] [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      879000 -- (-5516.077) (-5523.533) [-5515.210] * (-5511.277) (-5519.439) [-5529.359] * [-5517.937] (-5524.032) [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      880000 -- [-5520.293] (-5520.299) (-5517.227) * [-5516.980] (-5517.292) (-5515.998) * [-5513.107] (-5517.177) [...1 more local chains...] (...0 remote chains...) -- 0:00:11

      Average standard deviation of split frequencies: 0.001812

      881000 -- (-5535.957) [-5529.919] (-5522.805) * (-5512.579) [-5522.966] (-5522.171) * (-5526.842) (-5520.684) [...1 more local chains...] (...0 remote chains...) -- 0:00:11
      882000 -- (-5522.793) (-5519.842) [-5514.501] * [-5513.523] (-5521.089) (-5508.633) * (-5516.153) [-5523.398] [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      883000 -- (-5519.319) [-5513.712] (-5522.424) * (-5523.715) [-5519.190] (-5517.547) * (-5517.434) (-5519.823) [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      884000 -- [-5516.406] (-5525.465) (-5521.069) * [-5516.976] (-5521.545) (-5519.519) * [-5515.721] (-5520.026) [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      885000 -- (-5515.395) [-5515.518] (-5510.870) * [-5525.005] (-5515.869) (-5518.683) * (-5523.314) [-5517.876] [...1 more local chains...] (...0 remote chains...) -- 0:00:10

      Average standard deviation of split frequencies: 0.001692

      886000 -- [-5512.457] (-5514.750) (-5525.278) * [-5513.766] (-5518.972) (-5515.203) * [-5511.590] (-5519.871) [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      887000 -- (-5514.237) [-5514.421] (-5514.407) * (-5518.840) (-5517.025) [-5516.355] * [-5512.553] (-5520.388) [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      888000 -- [-5514.184] (-5520.161) (-5512.220) * [-5512.906] (-5513.503) (-5521.019) * [-5516.084] (-5511.786) [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      889000 -- (-5521.499) (-5517.307) [-5518.308] * (-5518.489) (-5531.720) [-5521.048] * [-5527.420] (-5524.778) [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      890000 -- (-5524.133) (-5514.102) [-5511.474] * (-5521.322) [-5517.600] (-5516.729) * [-5526.570] (-5526.906) [...1 more local chains...] (...0 remote chains...) -- 0:00:10

      Average standard deviation of split frequencies: 0.001701

      891000 -- [-5525.188] (-5523.638) (-5519.581) * [-5521.289] (-5515.214) (-5517.990) * [-5515.172] (-5524.997) [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      892000 -- (-5518.585) [-5516.509] (-5517.910) * [-5520.372] (-5527.111) (-5524.641) * (-5525.450) [-5517.183] [...1 more local chains...] (...0 remote chains...) -- 0:00:10
      893000 -- [-5519.122] (-5522.741) (-5524.522) * (-5518.858) [-5523.867] (-5520.721) * (-5517.682) (-5525.950) [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      894000 -- [-5519.845] (-5517.518) (-5525.900) * (-5523.206) [-5513.760] (-5517.057) * [-5511.808] (-5516.278) [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      895000 -- [-5530.025] (-5516.198) (-5518.133) * (-5511.762) (-5515.961) [-5514.926] * (-5516.192) (-5524.823) [...1 more local chains...] (...0 remote chains...) -- 0:00:09

      Average standard deviation of split frequencies: 0.001827

      896000 -- (-5519.652) (-5514.373) [-5520.225] * [-5514.226] (-5518.906) (-5519.972) * (-5515.870) (-5521.368) [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      897000 -- [-5517.832] (-5522.606) (-5519.766) * (-5512.858) (-5515.122) [-5525.953] * (-5527.585) (-5513.872) [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      898000 -- (-5519.565) (-5527.661) [-5518.524] * (-5514.098) [-5519.101] (-5520.560) * (-5512.835) [-5525.898] [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      899000 -- (-5514.073) [-5510.690] (-5516.873) * (-5513.798) (-5521.888) [-5517.733] * (-5522.209) [-5510.651] [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      900000 -- (-5519.891) (-5517.276) [-5520.655] * [-5514.826] (-5512.048) (-5527.114) * [-5517.493] (-5523.746) [...1 more local chains...] (...0 remote chains...) -- 0:00:09

      Average standard deviation of split frequencies: 0.001781

      901000 -- (-5514.595) (-5515.268) [-5522.471] * (-5526.187) (-5519.311) [-5528.899] * (-5512.288) [-5517.481] [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      902000 -- (-5517.780) [-5511.260] (-5516.374) * (-5518.198) [-5515.773] (-5519.515) * (-5521.945) (-5516.044) [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      903000 -- [-5518.271] (-5521.670) (-5515.675) * (-5521.639) [-5513.859] (-5532.258) * [-5518.697] (-5520.533) [...1 more local chains...] (...0 remote chains...) -- 0:00:09
      904000 -- [-5523.838] (-5515.075) (-5516.767) * (-5519.131) (-5522.151) [-5523.103] * [-5517.832] (-5515.490) [...1 more local chains...] (...0 remote chains...) -- 0:00:08
      905000 -- (-5512.970) (-5517.340) [-5520.292] * (-5514.617) (-5536.516) [-5520.010] * (-5522.571) (-5518.793) [...1 more local chains...] (...0 remote chains...) -- 0:00:08

      Average standard deviation of split frequencies: 0.001928

      906000 -- (-5518.501) [-5516.712] (-5516.821) * (-5514.652) (-5518.161) [-5522.160] * (-5524.884) (-5519.243) [...1 more local chains...] (...0 remote chains...) -- 0:00:08
      907000 -- (-5515.448) (-5522.696) [-5519.640] * [-5520.963] (-5522.890) (-5522.562) * (-5519.501) [-5519.362] [...1 more local chains...] (...0 remote chains...) -- 0:00:08
      908000 -- (-5522.677) (-5516.318) [-5514.058] * (-5518.244) [-5515.740] (-5515.928) * [-5513.598] (-5518.804) [...1 more local chains...] (...0 remote chains...) -- 0:00:08
      909000 -- (-5520.195) (-5529.467) [-5514.719] * (-5509.970) (-5527.513) [-5516.178] * (-5517.485) (-5519.666) [...1 more local chains...] (...0 remote chains...) -- 0:00:08
      910000 -- [-5523.517] (-5519.170) (-5517.013) * (-5513.356) [-5513.785] (-5515.254) * (-5516.930) [-5522.464] [...1 more local chains...] (...0 remote chains...) -- 0:00:08

      Average standard deviation of split frequencies: 0.001881

      911000 -- (-5523.535) [-5512.893] (-5516.992) * (-5515.354) [-5513.024] (-5516.531) * [-5514.087] (-5516.024) [...1 more local chains...] (...0 remote chains...) -- 0:00:08
      912000 -- (-5524.014) (-5513.413) [-5512.788] * [-5517.813] (-5517.680) (-5515.475) * (-5517.035) (-5517.767) [...1 more local chains...] (...0 remote chains...) -- 0:00:08
      913000 -- (-5516.532) (-5517.713) [-5514.652] * (-5520.108) [-5519.993] (-5522.988) * [-5525.433] (-5514.304) [...1 more local chains...] (...0 remote chains...) -- 0:00:08
      914000 -- (-5516.649) [-5511.594] (-5511.760) * (-5521.479) (-5522.716) [-5519.188] * (-5520.232) [-5527.645] [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      915000 -- (-5520.224) (-5524.175) [-5519.862] * (-5511.921) (-5535.071) [-5523.626] * [-5514.865] (-5523.795) [...1 more local chains...] (...0 remote chains...) -- 0:00:07

      Average standard deviation of split frequencies: 0.002069

      916000 -- (-5521.570) [-5513.523] (-5518.740) * (-5524.935) [-5520.467] (-5521.609) * (-5519.646) [-5513.876] [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      917000 -- (-5516.821) (-5519.936) [-5519.544] * (-5522.840) [-5513.981] (-5532.981) * [-5521.327] (-5518.421) [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      918000 -- [-5513.195] (-5526.800) (-5524.956) * [-5513.873] (-5522.663) (-5515.792) * (-5516.283) [-5512.513] [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      919000 -- [-5524.905] (-5520.499) (-5518.939) * (-5517.459) (-5523.778) [-5519.786] * (-5524.955) (-5519.597) [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      920000 -- (-5524.307) [-5517.514] (-5527.843) * (-5521.056) [-5512.297] (-5524.589) * (-5528.968) [-5518.045] [...1 more local chains...] (...0 remote chains...) -- 0:00:07

      Average standard deviation of split frequencies: 0.002060

      921000 -- [-5518.353] (-5515.420) (-5515.383) * (-5531.194) (-5515.681) [-5512.571] * (-5519.309) (-5520.533) [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      922000 -- (-5513.824) (-5514.166) [-5516.561] * (-5522.942) [-5521.011] (-5519.217) * [-5526.214] (-5520.948) [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      923000 -- (-5517.640) (-5519.389) [-5520.877] * (-5524.820) [-5514.311] (-5522.244) * (-5524.886) (-5518.383) [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      924000 -- (-5515.259) [-5513.084] (-5518.984) * [-5526.595] (-5514.923) (-5523.702) * (-5522.278) [-5518.616] [...1 more local chains...] (...0 remote chains...) -- 0:00:07
      925000 -- [-5524.999] (-5524.681) (-5525.015) * (-5527.464) [-5515.988] (-5532.443) * (-5521.529) (-5514.320) [...1 more local chains...] (...0 remote chains...) -- 0:00:06

      Average standard deviation of split frequencies: 0.002031

      926000 -- (-5518.252) [-5514.333] (-5522.079) * (-5520.340) (-5523.797) [-5516.857] * (-5519.111) [-5514.651] [...1 more local chains...] (...0 remote chains...) -- 0:00:06
      927000 -- [-5518.074] (-5515.261) (-5527.454) * (-5522.841) [-5516.470] (-5521.544) * [-5516.581] (-5516.349) [...1 more local chains...] (...0 remote chains...) -- 0:00:06
      928000 -- (-5519.006) (-5516.665) [-5516.794] * [-5520.363] (-5521.333) (-5522.061) * (-5521.976) (-5512.141) [...1 more local chains...] (...0 remote chains...) -- 0:00:06
      929000 -- [-5513.073] (-5512.121) (-5517.814) * (-5518.141) [-5522.503] (-5523.715) * (-5512.303) [-5510.493] [...1 more local chains...] (...0 remote chains...) -- 0:00:06
      930000 -- [-5513.290] (-5516.612) (-5520.665) * [-5515.558] (-5519.033) (-5530.450) * (-5517.496) [-5518.021] [...1 more local chains...] (...0 remote chains...) -- 0:00:06

      Average standard deviation of split frequencies: 0.002051

      931000 -- (-5522.710) [-5519.467] (-5518.931) * (-5522.283) (-5515.742) [-5521.546] * [-5509.819] (-5529.649) [...1 more local chains...] (...0 remote chains...) -- 0:00:06
      932000 -- [-5516.443] (-5513.597) (-5519.053) * [-5517.615] (-5517.718) (-5523.272) * [-5519.175] (-5518.269) [...1 more local chains...] (...0 remote chains...) -- 0:00:06
      933000 -- (-5517.672) [-5523.059] (-5516.313) * [-5517.569] (-5513.148) (-5524.769) * (-5515.723) [-5513.354] [...1 more local chains...] (...0 remote chains...) -- 0:00:06
      934000 -- (-5517.977) (-5519.188) [-5514.754] * (-5524.093) (-5524.469) [-5510.684] * (-5522.150) [-5512.504] [...1 more local chains...] (...0 remote chains...) -- 0:00:06
      935000 -- [-5519.438] (-5517.834) (-5522.479) * [-5519.277] (-5514.319) (-5522.380) * [-5514.999] (-5523.609) [...1 more local chains...] (...0 remote chains...) -- 0:00:06

      Average standard deviation of split frequencies: 0.002104

      936000 -- [-5523.747] (-5519.176) (-5520.442) * (-5523.286) [-5520.780] (-5511.824) * (-5513.888) [-5516.947] [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      937000 -- (-5523.373) [-5519.413] (-5513.291) * (-5520.974) (-5517.767) [-5511.670] * (-5518.332) (-5516.416) [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      938000 -- [-5526.037] (-5516.021) (-5523.206) * (-5518.443) (-5521.358) [-5514.377] * (-5528.667) [-5510.236] [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      939000 -- [-5509.760] (-5510.068) (-5525.020) * (-5525.726) [-5518.647] (-5517.642) * (-5520.990) (-5524.669) [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      940000 -- (-5520.454) [-5524.400] (-5525.299) * (-5514.152) (-5513.967) [-5521.321] * (-5517.002) [-5518.666] [...1 more local chains...] (...0 remote chains...) -- 0:00:05

      Average standard deviation of split frequencies: 0.002191

      941000 -- (-5511.933) (-5518.821) [-5513.496] * (-5531.413) [-5516.560] (-5520.180) * (-5521.521) (-5515.415) [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      942000 -- (-5523.659) (-5520.687) [-5514.120] * (-5524.284) [-5513.601] (-5516.642) * [-5517.747] (-5517.702) [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      943000 -- (-5514.176) [-5509.512] (-5522.909) * (-5520.514) (-5515.281) [-5515.802] * (-5512.993) [-5510.533] [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      944000 -- (-5524.313) (-5518.926) [-5527.691] * (-5515.553) (-5538.352) [-5509.048] * [-5518.043] (-5520.003) [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      945000 -- (-5517.119) (-5525.894) [-5517.045] * (-5515.890) (-5515.574) [-5516.330] * (-5515.143) [-5518.478] [...1 more local chains...] (...0 remote chains...) -- 0:00:05

      Average standard deviation of split frequencies: 0.002122

      946000 -- (-5517.552) (-5520.831) [-5514.758] * (-5522.612) [-5524.166] (-5515.316) * (-5517.894) (-5519.415) [...1 more local chains...] (...0 remote chains...) -- 0:00:05
      947000 -- (-5521.116) [-5515.444] (-5520.248) * (-5510.049) (-5518.930) [-5521.230] * (-5526.364) (-5521.167) [...1 more local chains...] (...0 remote chains...) -- 0:00:04
      948000 -- (-5519.274) [-5518.195] (-5519.045) * [-5530.295] (-5515.583) (-5522.992) * [-5522.669] (-5527.633) [...1 more local chains...] (...0 remote chains...) -- 0:00:04
      949000 -- (-5524.814) [-5520.435] (-5513.805) * (-5522.420) (-5512.855) [-5520.130] * (-5524.406) [-5523.762] [...1 more local chains...] (...0 remote chains...) -- 0:00:04
      950000 -- (-5515.480) [-5515.440] (-5516.922) * (-5518.156) [-5522.476] (-5521.519) * [-5518.987] (-5515.593) [...1 more local chains...] (...0 remote chains...) -- 0:00:04

      Average standard deviation of split frequencies: 0.001982

      951000 -- [-5513.918] (-5523.738) (-5515.031) * [-5517.809] (-5518.104) (-5520.089) * [-5513.690] (-5521.047) [...1 more local chains...] (...0 remote chains...) -- 0:00:04
      952000 -- [-5516.458] (-5522.420) (-5517.662) * [-5528.343] (-5515.030) (-5521.163) * (-5526.108) (-5523.123) [...1 more local chains...] (...0 remote chains...) -- 0:00:04
      953000 -- [-5520.066] (-5526.889) (-5511.835) * (-5527.916) [-5518.384] (-5519.674) * (-5514.944) [-5523.239] [...1 more local chains...] (...0 remote chains...) -- 0:00:04
      954000 -- (-5512.723) (-5517.100) [-5518.248] * (-5518.932) [-5517.581] (-5523.667) * (-5512.239) (-5519.785) [...1 more local chains...] (...0 remote chains...) -- 0:00:04
      955000 -- (-5524.247) (-5531.692) [-5518.287] * (-5519.830) (-5516.836) [-5516.637] * (-5515.660) (-5522.371) [...1 more local chains...] (...0 remote chains...) -- 0:00:04

      Average standard deviation of split frequencies: 0.001968

      956000 -- [-5513.086] (-5522.342) (-5516.233) * (-5515.930) (-5518.715) [-5516.460] * (-5516.985) (-5526.599) [...1 more local chains...] (...0 remote chains...) -- 0:00:04
      957000 -- [-5514.043] (-5521.899) (-5526.916) * [-5513.235] (-5519.356) (-5522.907) * [-5518.528] (-5519.804) [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      958000 -- (-5518.233) (-5518.645) [-5514.437] * (-5514.806) [-5509.667] (-5519.804) * (-5517.141) (-5524.977) [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      959000 -- [-5517.357] (-5520.301) (-5519.731) * (-5525.890) (-5517.123) [-5513.715] * (-5512.661) [-5515.619] [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      960000 -- (-5519.671) (-5521.914) [-5514.132] * (-5519.808) [-5517.273] (-5514.703) * (-5520.207) (-5516.349) [...1 more local chains...] (...0 remote chains...) -- 0:00:03

      Average standard deviation of split frequencies: 0.001986

      961000 -- [-5520.148] (-5512.788) (-5515.538) * [-5517.179] (-5519.035) (-5526.858) * (-5522.787) [-5528.451] [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      962000 -- [-5517.554] (-5516.895) (-5519.097) * [-5513.293] (-5520.669) (-5520.772) * [-5510.255] (-5515.170) [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      963000 -- [-5514.011] (-5519.813) (-5516.079) * [-5510.550] (-5511.620) (-5515.604) * [-5513.796] (-5523.235) [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      964000 -- (-5519.149) (-5517.690) [-5516.077] * (-5516.173) [-5519.198] (-5518.925) * (-5512.982) (-5524.092) [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      965000 -- (-5515.786) (-5528.543) [-5513.598] * (-5515.482) (-5516.022) [-5522.588] * (-5512.774) [-5516.007] [...1 more local chains...] (...0 remote chains...) -- 0:00:03

      Average standard deviation of split frequencies: 0.002215

      966000 -- (-5510.659) (-5516.891) [-5517.205] * (-5520.508) (-5522.393) [-5510.319] * [-5519.986] (-5514.551) [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      967000 -- (-5516.576) [-5514.441] (-5520.943) * [-5516.129] (-5522.537) (-5522.834) * (-5528.613) [-5513.000] [...1 more local chains...] (...0 remote chains...) -- 0:00:03
      968000 -- [-5521.611] (-5517.940) (-5524.960) * (-5519.049) (-5524.313) [-5515.450] * [-5520.018] (-5519.981) [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      969000 -- (-5511.220) (-5527.187) [-5514.257] * (-5530.141) (-5536.289) [-5517.889] * [-5520.181] (-5519.999) [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      970000 -- (-5515.314) (-5519.011) [-5513.657] * [-5514.060] (-5511.436) (-5530.041) * (-5518.177) (-5526.682) [...1 more local chains...] (...0 remote chains...) -- 0:00:02

      Average standard deviation of split frequencies: 0.002180

      971000 -- [-5516.747] (-5521.406) (-5509.840) * (-5514.370) [-5515.448] (-5516.493) * (-5515.469) [-5514.419] [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      972000 -- [-5511.975] (-5526.467) (-5518.594) * (-5520.989) [-5516.678] (-5518.164) * (-5519.684) [-5513.689] [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      973000 -- (-5519.202) (-5517.857) [-5512.233] * (-5522.310) [-5515.060] (-5517.867) * [-5522.882] (-5518.659) [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      974000 -- (-5520.900) [-5524.756] (-5522.397) * [-5520.050] (-5510.269) (-5516.030) * (-5524.873) [-5514.007] [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      975000 -- (-5519.575) (-5514.976) [-5513.493] * (-5522.459) [-5515.391] (-5517.103) * [-5523.332] (-5526.061) [...1 more local chains...] (...0 remote chains...) -- 0:00:02

      Average standard deviation of split frequencies: 0.002208

      976000 -- (-5518.794) [-5516.968] (-5522.075) * (-5518.495) (-5515.311) [-5518.723] * (-5534.929) (-5515.583) [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      977000 -- [-5516.524] (-5528.076) (-5516.629) * (-5522.188) [-5517.044] (-5517.040) * [-5517.627] (-5520.278) [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      978000 -- (-5508.722) [-5511.339] (-5522.271) * (-5519.833) [-5519.072] (-5519.111) * (-5514.584) [-5518.595] [...1 more local chains...] (...0 remote chains...) -- 0:00:02
      979000 -- [-5517.604] (-5523.179) (-5517.828) * (-5520.046) (-5520.516) [-5517.075] * (-5520.416) (-5523.395) [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      980000 -- (-5520.451) (-5525.305) [-5520.993] * [-5521.244] (-5522.504) (-5512.282) * (-5521.625) [-5519.706] [...1 more local chains...] (...0 remote chains...) -- 0:00:01

      Average standard deviation of split frequencies: 0.002094

      981000 -- [-5516.051] (-5517.125) (-5517.508) * [-5515.664] (-5525.321) (-5517.395) * (-5526.408) [-5520.413] [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      982000 -- (-5517.843) (-5524.584) [-5518.773] * [-5529.430] (-5514.088) (-5520.584) * [-5513.840] (-5518.165) [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      983000 -- [-5526.659] (-5513.381) (-5512.536) * [-5511.434] (-5519.245) (-5529.950) * [-5519.703] (-5521.574) [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      984000 -- (-5516.622) (-5512.441) [-5511.960] * [-5514.688] (-5524.029) (-5525.807) * [-5532.993] (-5512.724) [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      985000 -- (-5518.576) [-5515.425] (-5513.842) * [-5517.046] (-5523.353) (-5511.340) * [-5518.984] (-5514.238) [...1 more local chains...] (...0 remote chains...) -- 0:00:01

      Average standard deviation of split frequencies: 0.002026

      986000 -- (-5525.977) (-5520.739) [-5517.905] * (-5529.773) (-5518.289) [-5511.964] * [-5516.091] (-5526.778) [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      987000 -- (-5516.014) (-5530.414) [-5522.553] * (-5522.033) (-5522.171) [-5518.647] * (-5516.279) [-5523.024] [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      988000 -- (-5514.366) (-5515.284) [-5525.654] * (-5517.611) [-5513.977] (-5519.648) * (-5519.698) [-5516.267] [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      989000 -- [-5526.406] (-5508.763) (-5518.972) * (-5518.520) (-5522.517) [-5513.035] * [-5515.003] (-5518.341) [...1 more local chains...] (...0 remote chains...) -- 0:00:01
      990000 -- (-5515.508) [-5514.571] (-5518.915) * [-5522.403] (-5519.282) (-5521.701) * [-5516.820] (-5525.514) [...1 more local chains...] (...0 remote chains...) -- 0:00:00

      Average standard deviation of split frequencies: 0.002039

      991000 -- (-5521.554) [-5510.428] (-5523.955) * (-5517.687) (-5519.405) [-5519.381] * (-5514.939) [-5516.664] [...1 more local chains...] (...0 remote chains...) -- 0:00:00
      992000 -- [-5517.334] (-5513.724) (-5529.337) * (-5529.408) (-5510.650) [-5519.215] * (-5520.398) (-5522.952) [...1 more local chains...] (...0 remote chains...) -- 0:00:00
      993000 -- [-5516.596] (-5519.977) (-5526.675) * (-5513.102) [-5512.180] (-5518.607) * (-5518.844) [-5509.802] [...1 more local chains...] (...0 remote chains...) -- 0:00:00
      994000 -- (-5525.502) (-5518.514) [-5513.205] * [-5514.563] (-5522.196) (-5517.496) * (-5519.806) [-5514.748] [...1 more local chains...] (...0 remote chains...) -- 0:00:00
      995000 -- (-5521.881) [-5520.942] (-5521.874) * (-5520.414) (-5515.711) [-5519.201] * [-5516.363] (-5515.583) [...1 more local chains...] (...0 remote chains...) -- 0:00:00

      Average standard deviation of split frequencies: 0.001973

      996000 -- (-5519.193) (-5523.883) [-5514.312] * (-5517.382) [-5517.692] (-5520.985) * [-5510.531] (-5518.190) [...1 more local chains...] (...0 remote chains...) -- 0:00:00
      997000 -- (-5515.785) (-5517.640) [-5520.042] * (-5519.012) (-5511.706) [-5521.707] * (-5516.286) (-5521.795) [...1 more local chains...] (...0 remote chains...) -- 0:00:00
      998000 -- (-5525.190) [-5515.294] (-5525.656) * (-5523.538) (-5517.630) [-5515.828] * (-5518.352) [-5519.428] [...1 more local chains...] (...0 remote chains...) -- 0:00:00
      999000 -- (-5514.207) (-5517.514) [-5514.139] * [-5510.852] (-5518.132) (-5515.235) * [-5511.452] (-5523.452) [...1 more local chains...] (...0 remote chains...) -- 0:00:00
      1000000 -- [-5513.947] (-5516.964) (-5522.121) * (-5515.861) (-5520.064) [-5512.481] * (-5514.853) [-5513.833] [...1 more local chains...] (...0 remote chains...) -- 0:00:00

      Average standard deviation of split frequencies: 0.001842

      Analysis completed in 1 mins 33 seconds
      Analysis used 92.80 seconds of CPU time on processor 0
      Likelihood of best state for "cold" chain of run 1 was -5505.15
      Likelihood of best state for "cold" chain of run 2 was -5504.78
      Likelihood of best state for "cold" chain of run 3 was -5505.22

      Acceptance rates for the moves in the "cold" chain of run 1:
         With prob.   (last 100)   chain accepted proposals by move
            27.3 %     ( 31 %)     Dirichlet(Tratio)
            15.2 %     ( 20 %)     Dirichlet(Pi)
            23.7 %     ( 21 %)     Slider(Pi)
            48.5 %     ( 34 %)     Multiplier(Alpha)
            14.0 %     ( 14 %)     ExtSPR(Tau,V)
             6.8 %     (  5 %)     ExtTBR(Tau,V)
            17.1 %     ( 16 %)     NNI(Tau,V)
            19.7 %     ( 23 %)     ParsSPR(Tau,V)
            26.7 %     ( 23 %)     Multiplier(V)
            36.5 %     ( 39 %)     Nodeslider(V)
            24.6 %     ( 20 %)     TLMultiplier(V)

      Acceptance rates for the moves in the "cold" chain of run 2:
         With prob.   (last 100)   chain accepted proposals by move
            27.2 %     ( 20 %)     Dirichlet(Tratio)
            14.1 %     ( 19 %)     Dirichlet(Pi)
            23.7 %     ( 21 %)     Slider(Pi)
            48.5 %     ( 22 %)     Multiplier(Alpha)
            14.1 %     ( 19 %)     ExtSPR(Tau,V)
             6.9 %     (  5 %)     ExtTBR(Tau,V)
            16.8 %     ( 21 %)     NNI(Tau,V)
            19.9 %     ( 15 %)     ParsSPR(Tau,V)
            26.7 %     ( 24 %)     Multiplier(V)
            36.8 %     ( 32 %)     Nodeslider(V)
            25.1 %     ( 20 %)     TLMultiplier(V)

      Acceptance rates for the moves in the "cold" chain of run 3:
         With prob.   (last 100)   chain accepted proposals by move
            27.1 %     ( 20 %)     Dirichlet(Tratio)
            15.0 %     ( 23 %)     Dirichlet(Pi)
            23.8 %     ( 25 %)     Slider(Pi)
            48.3 %     ( 26 %)     Multiplier(Alpha)
            14.3 %     ( 11 %)     ExtSPR(Tau,V)
             6.9 %     (  6 %)     ExtTBR(Tau,V)
            16.8 %     ( 19 %)     NNI(Tau,V)
            19.8 %     ( 17 %)     ParsSPR(Tau,V)
            26.7 %     ( 25 %)     Multiplier(V)
            36.8 %     ( 32 %)     Nodeslider(V)
            24.5 %     ( 31 %)     TLMultiplier(V)

      Chain swap information for run 1:

                   1       2       3
           --------------------------
         1 |            0.78    0.58
         2 |  333548            0.79
         3 |  333755  332697

      Chain swap information for run 2:

                   1       2       3
           --------------------------
         1 |            0.78    0.59
         2 |  333517            0.79
         3 |  334549  331934

      Chain swap information for run 3:

                   1       2       3
           --------------------------
         1 |            0.78    0.59
         2 |  333597            0.80
         3 |  333807  332596

      Upper diagonal: Proportion of successful state exchanges between chains
      Lower diagonal: Number of attempted state exchanges between chains

      Chain information:

        ID -- Heat
       -----------
         1 -- 1.00  (cold chain)
         2 -- 0.91
         3 -- 0.83

      Heat = 1 / (1 + T * (ID - 1))
         (where T = 0.10 is the temperature and ID is the chain number)

      Summarizing trees in files "Vfischeri_rscS_DNA-clustal-aligned.nex.run1.t", "Vfischeri_rscS_DNA-clustal-aligned.nex.run2.t",...,"Vfischeri_rscS_DNA-clustal-aligned.nex.run3.t"
      Using relative burnin ('relburnin=yes'), discarding the first 25 % of sampled trees
      Writing statistics to files Vfischeri_rscS_DNA-clustal-aligned.nex.<parts|tstat|vstat|trprobs|con>
      Examining first file ...
      Found one tree block in file "Vfischeri_rscS_DNA-clustal-aligned.nex.run1.t" with 10001 trees in last block
      Expecting the same number of trees in the last tree block of all files

      Tree reading status:

      0      10      20      30      40      50      60      70      80      90     100
      v-------v-------v-------v-------v-------v-------v-------v-------v-------v-------v
      *********************************************************************************

      Read a total of 30003 trees in 3 files (sampling 22503 of them)
         (Each file contained 10001 trees of which 7501 were sampled)

      General explanation:

      In an unrooted tree, a taxon bipartition (split) is specified by removing a
      branch, thereby dividing the species into those to the left and those to the
      right of the branch. Here, taxa to one side of the removed branch are denoted
      '.' and those to the other side are denoted '*'. Specifically, the '.' symbol
      is used for the taxa on the same side as the outgroup.

      In a rooted or clock tree, the tree is rooted using the model and not by
      reference to an outgroup. Each bipartition therefore corresponds to a clade,
      that is, a group that includes all the descendants of a particular branch in
      the tree.  Taxa that are included in each clade are denoted using '*', and
      taxa that are not included are denoted using the '.' symbol.

      The output first includes a key to all the bipartitions with frequency larger
      or equual to (Minpartfreq) in at least one run. Minpartfreq is a parameter to
      sumt command and currently it is set to 0.10.  This is followed by a table
      with statistics for the informative bipartitions (those including at least
      two taxa), sorted from highest to lowest probability. For each bipartition,
      the table gives the number of times the partition or split was observed in all
      runs (#obs) and the posterior probability of the bipartition (Probab.), which
      is the same as the split frequency. If several runs are summarized, this is
      followed by the minimum split frequency (Min(s)), the maximum frequency
      (Max(s)), and the standard deviation of frequencies (Stddev(s)) across runs.
      The latter value should approach 0 for all bipartitions as MCMC runs converge.

      This is followed by a table summarizing branch lengths, node heights (if a
      clock model was used) and relaxed clock parameters (if a relaxed clock model
      was used). The mean, variance, and 95 % credible interval are given for each
      of these parameters. If several runs are summarized, the potential scale
      reduction factor (PSRF) is also given; it should approach 1 as runs converge.
      Node heights will take calibration points into account, if such points were
      used in the analysis.

      Note that Stddev may be unreliable if the partition is not present in all
      runs (the last column indicates the number of runs that sampled the partition
      if more than one run is summarized). The PSRF is not calculated at all if
      the partition is not present in all runs.The PSRF is also sensitive to small
      sample sizes and it should only be considered a rough guide to convergence
      since some of the assumptions allowing one to interpret it as a true potential
      scale reduction factor are violated in MrBayes.

      List of taxa in bipartitions:

         1 -- ES114
         2 -- MJ102
         3 -- EM24
         4 -- EM30
         5 -- EM17
         6 -- EM18
         7 -- MB13B1
         8 -- MB14A1
         9 -- ES213
        10 -- KB2B1
        11 -- MB11B1
        12 -- MJ8.1

      Key to taxon bipartitions (saved to file "Vfischeri_rscS_DNA-clustal-aligned.nex.parts"):

      ID -- Partition
      ------------------
       1 -- *...........
       2 -- .*..........
       3 -- ..*.........
       4 -- ...*........
       5 -- ....*.......
       6 -- .....*......
       7 -- ......*.....
       8 -- .......*....
       9 -- ........*...
      10 -- .........*..
      11 -- ..........*.
      12 -- ***********.
      13 -- ....**......
      14 -- ..**........
      15 -- ........***.
      16 -- ......**....
      17 -- ..*********.
      18 -- **..........
      19 -- ..******....
      20 -- ..****......
      21 -- ....****....
      22 -- ........**..
      23 -- .........**.
      24 -- ........*.*.
      ------------------

      Summary statistics for informative taxon bipartitions
         (saved to file "Vfischeri_rscS_DNA-clustal-aligned.nex.tstat"):

      ID   #obs     Probab.     Sd(s)+      Min(s)      Max(s)   Nruns
      -----------------------------------------------------------------
      13  22503    1.000000    0.000000    1.000000    1.000000    3
      14  22503    1.000000    0.000000    1.000000    1.000000    3
      15  22503    1.000000    0.000000    1.000000    1.000000    3
      16  22503    1.000000    0.000000    1.000000    1.000000    3
      17  22503    1.000000    0.000000    1.000000    1.000000    3
      18  21864    0.971604    0.001743    0.970404    0.973604    3
      19  19213    0.853797    0.004888    0.850153    0.859352    3
      20  11612    0.516020    0.000407    0.515665    0.516464    3
      21  10153    0.451184    0.001873    0.449407    0.453140    3
      22   7564    0.336133    0.003956    0.333156    0.340621    3
      23   7553    0.335644    0.004426    0.333022    0.340755    3
      24   7386    0.328223    0.004812    0.324623    0.333689    3
      -----------------------------------------------------------------
      + Convergence diagnostic (standard deviation of split frequencies)
        should approach 0.0 as runs converge.


      Summary statistics for branch and node parameters
         (saved to file "Vfischeri_rscS_DNA-clustal-aligned.nex.vstat"):

                                              95% HPD Interval
                                            --------------------
      Parameter      Mean       Variance     Lower       Upper       Median     PSRF+  Nruns
      --------------------------------------------------------------------------------------
      length[1]     0.001062    0.000000    0.000093    0.002282    0.000945    1.000    3
      length[2]     0.000379    0.000000    0.000000    0.001128    0.000264    1.000    3
      length[3]     0.001081    0.000000    0.000106    0.002305    0.000968    1.000    3
      length[4]     0.000369    0.000000    0.000000    0.001103    0.000253    1.000    3
      length[5]     0.000713    0.000000    0.000002    0.001714    0.000598    1.000    3
      length[6]     0.001824    0.000001    0.000469    0.003481    0.001701    1.000    3
      length[7]     0.001803    0.000001    0.000407    0.003399    0.001693    1.000    3
      length[8]     0.001095    0.000000    0.000089    0.002324    0.000975    1.000    3
      length[9]     0.000358    0.000000    0.000000    0.001090    0.000247    1.000    3
      length[10]    0.000363    0.000000    0.000000    0.001084    0.000255    1.000    3
      length[11]    0.000361    0.000000    0.000000    0.001079    0.000249    1.000    3
      length[12]    0.119359    0.000113    0.099134    0.140622    0.118613    1.000    3
      length[13]    0.003603    0.000001    0.001492    0.006008    0.003469    1.000    3
      length[14]    0.009553    0.000004    0.006001    0.013461    0.009431    1.000    3
      length[15]    0.005083    0.000002    0.002359    0.008004    0.004940    1.000    3
      length[16]    0.001627    0.000001    0.000306    0.003241    0.001500    1.000    3
      length[17]    0.014694    0.000007    0.009632    0.019957    0.014553    1.000    3
      length[18]    0.003119    0.000003    0.000282    0.006165    0.002913    1.000    3
      length[19]    0.001645    0.000001    0.000056    0.003389    0.001505    1.000    3
      length[20]    0.000959    0.000000    0.000001    0.002129    0.000836    1.000    3
      length[21]    0.000786    0.000000    0.000015    0.001864    0.000663    1.000    3
      length[22]    0.000355    0.000000    0.000000    0.001081    0.000246    1.000    3
      length[23]    0.000360    0.000000    0.000000    0.001076    0.000252    1.000    3
      length[24]    0.000352    0.000000    0.000000    0.001050    0.000244    1.000    3
      --------------------------------------------------------------------------------------
      + Convergence diagnostic (PSRF = Potential Scale Reduction Factor; Gelman
        and Rubin, 1992) should approach 1.0 as runs converge. NA is reported when
        deviation of parameter values within all runs is 0 or when a parameter
        value (a branch length, for instance) is not sampled in all runs.


      Summary statistics for partitions with frequency >= 0.10 in at least one run:
          Average standard deviation of split frequencies = 0.001842
          Maximum standard deviation of split frequencies = 0.004888
          Average PSRF for parameter values (excluding NA and >10.0) = 1.000
          Maximum PSRF for parameter values = 1.000


      Clade credibility values:

      /------------------------------------------------------------------- MJ8.1 (12)
      |
      |                                                     /------------- EM24 (3)
      |                                       /-----100-----+
      |                                       |             \------------- EM30 (4)
      |                          /-----52-----+
      |                          |            |             /------------- EM17 (5)
      |                          |            \-----100-----+
      |            /------85-----+                          \------------- EM18 (6)
      |            |             |
      |            |             |                          /------------- MB13B1 (7)
      +            |             \------------100-----------+
      |-----100----+                                        \------------- MB14A1 (8)
      |            |
      |            |                                        /------------- ES213 (9)
      |            |                                        |
      |            \-------------------100------------------+------------- KB2B1 (10)
      |                                                     |
      |                                                     \------------- MB11B1 (11)
      |
      |                                                     /------------- ES114 (1)
      \--------------------------97-------------------------+
                                                            \------------- MJ102 (2)


      Phylogram (based on average branch lengths):

      /-------------------------------------------------------------------- MJ8.1 (12)
      |
      |              /- EM24 (3)
      |         /----+
      |         |    \ EM30 (4)
      |        /+
      |        || / EM17 (5)
      |        |\-+
      |       /+  \- EM18 (6)
      |       ||
      |       ||/- MB13B1 (7)
      +       |\+
      |-------+ \- MB14A1 (8)
      |       |
      |       |  / ES213 (9)
      |       |  |
      |       \--+ KB2B1 (10)
      |          |
      |          \ MB11B1 (11)
      |
      | / ES114 (1)
      \-+
        \ MJ102 (2)

      |----------| 0.020 expected changes per site

      Calculating tree probabilities...

      Credible sets of trees (61 trees sampled):
         50 % credible set contains 4 trees
         90 % credible set contains 10 trees
         95 % credible set contains 17 trees
         99 % credible set contains 31 trees

   Exiting mrbayes block
   Reached end of file

   Tasks completed, exiting program because mode is noninteractive
   To return control to the command line after completion of file processing,
   set mode to interactive with 'mb -i <filename>' (i is for interactive)
   or use 'set mode=interactive'
```
### Visualize MrBayes Consensus Trees
1. Open the consensus tree files (nex.con.tree) in [FigTree](http://tree.bio.ed.ac.uk/software/figtree/). Note that FigTree requires Java to operate. 
2. Within FigTree, reroot the trees to the outgroup MJ8.1. Turn on the node label function to display posterior probabilities (display node label as post) on the tree. 



