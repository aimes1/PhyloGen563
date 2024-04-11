# Bayesian Inference

2024-04-11: hypothetical run of commands for the homework submission, as I want to refine the data I am processing to use a few housekeeping gene proteins. 

Note: want ngen to be at least 1 million when running on real data. 

## Software cheatsheet

| Software | Description | Strengths | Weaknesses | Assumptions | User choices | 
| :---:   | :---: | :---:       | :---:                     | :---: | :---: |
| MrBayes | Performs Bayesian inference of phylogeny using a variant MCMC to approximate posterior probability of trees | Capable of analyzing heterogenous data sets, has mixed models support, and model flexibility.  | No correct way to choose a prior, posterior distributions heavily influenced by priors, high computational cost in models with large number of parameters, needs many posterior samples to accurately infer phylogenetic history. |Assumes provided priors are informative |User specifies model and sets a prior. | 

Protocol below based on following [this tutorial](http://hydrodictyon.eeb.uconn.edu/eebedia/index.php/Phylogenetics:_MrBayes_Lab).

### MrBayes
Note: hypothetical run of commands for homework submission, real data not provided. 

1. Download MrBayes from [here](http://nbisweden.github.io/MrBayes/ and install through homebrew. In Mac, commands are:
```shell
brew tap brewsci/bio
brew install mrbayes --with-open-mpi
```

2. Convert multiple sequence alignment files of RscS and sypF proteins from .fasta to .nxs in R Studio. 
   A. Input file: berryi3isolatesDNA-aligned-muscle.fasta
```shell
install.packages("seqinr")
install.packages("ape")
library(seqinr)
library(ape)

data = read.FASTA("/Users/aimes/Temp/data/processed/berryi3isolatesAA-alignedRscS-muscle.fasta", seqtype = "AA")
write.nexus.data(data, file="/Users/aimes/Temp/data/processed/berryi3isolatesAA-alignedRscS-muscle.nex", format="protein")

data = read.FASTA("/Users/aimes/Temp/data/processed/berryi3isolatesAA-alignedSypF-muscle.fasta", seqtype = "AA")
write.nexus.data(data, file="/Users/aimes/Temp/data/processed/berryi3isolatesAA-alignedSypF-muscle.nex", format="protein")

```

3. Create a MrBayes block in a text file called `mbblock.txt`. Note that we need to add `mcmc;sumt;` at the end so that the mb block is executed.
Note: `mcmc` is the command to run MCMC and `sumt` is the command to obtain a summary tree.

```
begin mrbayes;
 set autoclose=yes;
 prset brlenspr=unconstrained:exp(10.0);
 prset shapepr=exp(1.0);
 prset tratiopr=beta(1.0,1.0);
 prset statefreqpr=dirichlet(1.0,1.0,1.0,1.0);
 lset nst=2 rates=gamma ngammacat=4;
 mcmcp ngen=10000000 samplefreq=10 printfreq=1000 nruns=3 nchains=3 savebrlens=yes;
 outgroup Vfischeri_SR5;
 mcmc;
 sumt;
end;
```

4. Add the MrBayes block to the end of the nexus files:

```shell
cat berryi3isolatesAA-alignedRscS-muscle.nex mbblock.txt > berryi3isolatesAA-alignedRscS-muscle-mb.nex
cat berryi3isolatesAA-alignedSypF-muscle.nex mbblock.txt > berryi3isolatesAA-alignedSypF-muscle-mb.nex
```

5. Run MrBayes on both the RscS and SypF files. Shown below is the command for SypF (repeat with initial command with RscS file): 

```shell
mb berryi3isolatesAA-alignedSypF-muscle-mb.nex
```

The command produces multiple output files:

```shell
(master) $ ls berryi3isolatesAA-alignedSypF-muscle-mb.nex*
berryi3isolatesAA-alignedSypF-muscle-mb.nex         berryi3isolatesAA-alignedSypF-muscle-mb.nex.con.tre berryi3isolatesAA-alignedSypF-muscle-mb.nex.parts   berryi3isolatesAA-alignedSypF-muscle-mb.nex.tstat
berryi3isolatesAA-alignedSypF-muscle-mb.nex.ckp     berryi3isolatesAA-alignedSypF-muscle-mb.nex.mcmc    berryi3isolatesAA-alignedSypF-muscle-mb.nex.t       berryi3isolatesAA-alignedSypF-muscle-mb.nex.vstat
berryi3isolatesAA-alignedSypF-muscle-mb.nex.ckp~    berryi3isolatesAA-alignedSypF-muscle-mb.nex.p       berryi3isolatesAA-alignedSypF-muscle-mb.nex.trprobs
```