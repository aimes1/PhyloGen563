---
layout: default
nav_exclude: true
---

# Distance and Parsimony HW

Note: I tried to provide the programs the berryiisolatesall.xmfa from the Mauve alignment, but this generated an error. I'm still troubleshooting the use of MUSCLE and ClustalW to generate an alignment, but the hypothetical entry of my own data is detailed below: 

1. Estimate a distance-based tree and a parsimony-based tree for bacterial isolate data using the `ape` and `phangorn` R packages.
  - Don't forget to include in your reproducible script a short description of the chosen algorithm, its assumptions and limitations (see the [software cheatsheet](https://github.com/crsl4/phylogenetics-class/blob/master/exercises/software-cheatsheet.md))
2. Make sure to keep notes in your reproducible script and keep the most updated version on github (it is important to push your work to github since this allows me to check what you are doing and offer suggestions)
3. Submit the link to the github commit in canvas

## Software R package _ape_: Distance-based methods

- _ape_ is one of the most widely used phylogenetic software
- It is an R package and it has a huge variety of functions
- In particular, today we will use it for distance-based tree estimation methods
- [Full documentation](https://cran.r-project.org/web/packages/ape/index.html)
- Follow this [great tutorial](https://adegenet.r-forge.r-project.org/files/MSc-intro-phylo.1.1.pdf)

### Estimate a distance-based tree and a parsimony-based tree for your data using the `ape` and `phangorn` R packages.

1) Within RStudio, install necessary packages:
```r
install.packages("adegenet", dep=TRUE)
install.packages("phangorn", dep=TRUE)
```

2) Load the packages
```r
library(ape)
library(adegenet)
library(phangorn)
```

3) Load data
   1) Note: data must be aligned sequences.
   2) Note: the selected file contains is the Mauve alignment produced from all E. berryi bacterial isolates. 
```r
dna <- fasta2DNAbin(file="/Users/aimes/Temp/PhyloGen563/data/large_files/genome_processing/berryi3isolatesDNA-aligned-muscle.fasta")
```

1) Computing the genetic distances. They choose a Tamura and Nei 1993 model which allows for different rates of transitions and transversions, heterogeneous base frequencies, and between-site variation of the substitution rate (more on Models of Evolution).
```r
D <- dist.dna(dna, model="TN93")
```

1) Get the NJ tree
```r
tre <- nj(D)
```

1) Before plotting, we can use the [`ladderize` function](https://rdrr.io/cran/ape/man/ladderize.html) which reorganizes the internal structure of the tree to get the ladderized effect when plotted
```r
tre <- ladderize(tre)
```


7) Plot the tree
```r
plot(tre, cex=.6)
title("Berryi 3 isolates NJ tree")
```

## Summary of Software R package _ape_

Main distance functions:
- `nj` (`ape` package): the classical Neighbor-Joining algorithm.
- [`bionj`](https://www.rdocumentation.org/packages/ape/versions/5.4-1/topics/BIONJ) (`ape`): an improved version of Neighbor-Joining: [Gascuel 1997](https://pubmed.ncbi.nlm.nih.gov/9254330/). It uses information on variances of evolutionary distances
- [`fastme.bal` and `fastme.ols`](https://www.rdocumentation.org/packages/ape/versions/5.4-1/topics/FastME) (`ape`): minimum evolution algorithms: [Desper and Gascuel, 2002](https://pubmed.ncbi.nlm.nih.gov/12487758/)
- `hclust` (`stats`): classical hierarchical clustering algorithms including single
linkage, complete linkage, UPGMA, and others.


# Software: R package _phangorn_: Parsimony-based methods

- _phangorn_ is another widely used phylogenetic software
- It is an R package and it has a huge variety of functions
- In particular, today we will use it for parsimony-based tree estimation methods
- [Full documentation](https://cran.r-project.org/web/packages/phangorn/vignettes/Trees.pdf)
- Can follow this [great tutorial](https://adegenet.r-forge.r-project.org/files/MSc-intro-phylo.1.1.pdf)
- Aim: Follow the R commands to obtain a MP tree from my own data. The commands are listed in the [PDF tutorial]((https://adegenet.r-forge.r-project.org/files/MSc-intro-phylo.1.1.pdf)) that we are using as guideline or in our reproducible script [notebook-log.md](https://github.com/crsl4/phylogenetics-class/blob/master/exercises/notebook-log.md) or on the following slides.

1) Installing necessary packages (if not installed for the distance section above)
```r
install.packages("adegenet", dep=TRUE)
install.packages("phangorn", dep=TRUE)
```

1) Loading packages (if not done from section above)
```r
library(ape)
library(adegenet)
library(phangorn)
```

1) Loading data and convert to phangorn object:
```r
dna <- fasta2DNAbin(file="/Users/aimes/Temp/PhyloGen563/data/large_files/genome_processing/berryi3isolatesDNA-aligned-muscle.fasta")
dna2 <- as.phyDat(dna)
```

1) We need a starting tree for the search on tree space and compute the parsimony score of this tree (422)
```r
tre.ini <- nj(dist.dna(dna,model="raw"))
parsimony(tre.ini, dna2)
```

1) Search for the tree with maximum parsimony:
```r
tre.pars <- optim.parsimony(tre.ini, dna2)
```

1) Plot tree:
```r
plot(tre.pars, cex=0.6)
```