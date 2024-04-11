# Maximum Likelihood

Hypothetical run of commands detailed below.

## RAxML Information

| Software | Description | Strengths | Weaknesses | Assumptions | User choices | 
| :---:   | :---: | :---:       | :---:                     | :---: | :---: | 
|RAxML-NG| Maximum likelihood tree inference tool last updated in Nov 2019|Fast, good scalability, scores higher when alignments are taxon-rich, good for large datasets due to it reduces memory space and run time |Not as efficient or high likelihoods as IQ-Tree,  |Iteratively searches by series of Subtree Pruning and Regrafting (SPR) moves| User must provide outgroup to root data, can select from 3 starting tree options (random topology, tree generated by parsimony-based randomized stepwise addition algorithm, or user-defined provided tree), set the model to run, and can set the seed to create reproducible analysis | 


## RAxML-NG Script 

1. Download `raxml-ng` from [here](https://github.com/amkozlov/raxml-ng) as Apple M1 binary download. You get a folder: `raxml-ng_v1` 
   1. Put folder in my `software` folder

2. Checking the version
   1. Note: must manually open the executable file to overcome Mac inability to check for malware. 
```shell
cd Users/aimes/Temp/Software/raxml-ng_v1

./raxml-ng -v

RAxML-NG v. 1.2.1 released on 22.12.2023 by The Exelixis Lab.
Developed by: Alexey M. Kozlov and Alexandros Stamatakis.
Contributors: Diego Darriba, Tomas Flouri, Benoit Morel, Sarah Lutteropp, Ben Bettisworth, Julia Haag, Anastasis Togkousidis.
Latest version: https://github.com/amkozlov/raxml-ng
Questions/problems/suggestions? Please visit: https://groups.google.com/forum/#!forum/raxml

System: Apple M2 Max, 12 cores, 32 GB RAM
```

3. Check for the MSA (hypothetical):
```shell
./raxml-ng --check --msa berryi3isolatesDNA-aligned-muscle.fasta --model GTR+G

RAxML-NG v. 1.2.1 released on 22.12.2023 by The Exelixis Lab.
Developed by: Alexey M. Kozlov and Alexandros Stamatakis.
Contributors: Diego Darriba, Tomas Flouri, Benoit Morel, Sarah Lutteropp, Ben Bettisworth, Julia Haag, Anastasis Togkousidis.
Latest version: https://github.com/amkozlov/raxml-ng
Questions/problems/suggestions? Please visit: https://groups.google.com/forum/#!forum/raxml

System: Apple M2 Max, 12 cores, 32 GB RAM

RAxML-NG was called at 21-Mar-2024 10:00:00 as follows:

./raxml-ng --check --msa berryi3isolatesDNA-aligned-muscle.fasta --model GTR+G
```

RAxML will provide longer output if the alignment can be successfully read by RAxML-NG. 

4. Infer the ML tree using the following command, which will perform 20 tree searches using 10 random and 10 parsimony-based starting trees. 
   1. Very important: set the `--seed` to be able to replicate the analyses exactly.

```shell
aimes@Averys-MacBook-Pro raxml-ng_v1 % ./raxml-ng --msa berryi3isolatesDNA-aligned-muscle.fasta --model GTR+G --prefix T3 --threads 2 --seed 2

RAxML-NG v. 1.2.1 released on 22.12.2023 by The Exelixis Lab.
Developed by: Alexey M. Kozlov and Alexandros Stamatakis.
Contributors: Diego Darriba, Tomas Flouri, Benoit Morel, Sarah Lutteropp, Ben Bettisworth, Julia Haag, Anastasis Togkousidis.
Latest version: https://github.com/amkozlov/raxml-ng
Questions/problems/suggestions? Please visit: https://groups.google.com/forum/#!forum/raxml

System: Apple M2 Max, 12 cores, 32 GB RAM

RAxML-NG was called at 21-Mar-2024 10:00:00 as follows:

./raxml-ng --msa berryi3isolatesDNA-aligned-muscle.fasta --model GTR+G --prefix T3 --threads 2 --seed 2

Analysis options:
  run mode: ML tree search
  start tree(s): random (10) + parsimony (10)
  random seed: 2
  tip-inner: OFF
  pattern compression: ON
  per-rate scalers: OFF
  site repeats: ON
  logLH epsilon: general: 10.000000, brlen-triplet: 1000.000000
  fast spr radius: AUTO
  spr subtree cutoff: 1.000000
  fast CLV updates: ON
  branch lengths: proportional (ML estimate, algorithm: NR-FAST)
  SIMD kernels: SSE3
  parallelization: coarse-grained (auto), PTHREADS (2 threads), thread pinning: OFF

```

Theoretical output: 

```shell
Best ML tree saved to: /Users/aimes/Temp/Software/raxml-ng_v1/T3.raxml.bestTree
All ML trees saved to: /Users/aimes/Temp/Software/raxml-ng_v1/T3.raxml.mlTrees
Optimized model saved to: /Users/aimes/Temp/Software/raxml-ng_v1/T3.raxml.bestModel

Execution log saved to: /Users/aimes/Temp/Software/raxml-ng_v1/T3.raxml.log
```

### Visualizing the Tree Output 

In Rstudio: 

1. Within RStudio, install necessary packages:
```r
install.packages("adegenet", dep=TRUE)
install.packages("phangorn", dep=TRUE)
```

2. Load the packages:
```r
library(ape)
library(adegenet)
library(phangorn)
```

3. Load the best tree from the RAxML output:
```r
phy <- ape::read.tree(file = '/Users/aimes/Temp/Software/raxml-ng_v1/T3.raxml.bestTree')
```

4. Plot the tree:
```r
plot(phy)
```