# Maximum Likelihood

Note: RAxML and IQ-Tree provide unrooted trees, and so must be provided an outgroup to root the data. 

## RAxML-NG

### RAxML-NG Tutorial
We are following HAL 1.3.

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

3. Clone the [ng-tutorial](https://github.com/amkozlov/ng-tutorial) to have the datasets and scripts. Do this inside the same folder above.
```shell
git clone https://github.com/amkozlov/ng-tutorial.git

Cloning into 'ng-tutorial'...
remote: Enumerating objects: 60, done.
remote: Counting objects: 100% (32/32), done.
remote: Compressing objects: 100% (28/28), done.
remote: Total 60 (delta 16), reused 9 (delta 3), pack-reused 28
Receiving objects: 100% (60/60), 130.15 KiB | 2.21 MiB/s, done.
Resolving deltas: 100% (18/18), done.
```

4. Check for the MSA:
```shell
./raxml-ng --check --msa ng-tutorial/bad.fa --model GTR+G

RAxML-NG v. 1.2.1 released on 22.12.2023 by The Exelixis Lab.
Developed by: Alexey M. Kozlov and Alexandros Stamatakis.
Contributors: Diego Darriba, Tomas Flouri, Benoit Morel, Sarah Lutteropp, Ben Bettisworth, Julia Haag, Anastasis Togkousidis.
Latest version: https://github.com/amkozlov/raxml-ng
Questions/problems/suggestions? Please visit: https://groups.google.com/forum/#!forum/raxml

System: Apple M2 Max, 12 cores, 32 GB RAM

RAxML-NG was called at 14-Mar-2024 13:26:21 as follows:

./raxml-ng --check --msa ng-tutorial/bad.fa --model GTR+G

Analysis options:
  run mode: Alignment validation
  start tree(s): 
  random seed: 1710440781
  SIMD kernels: SSE3
  parallelization: coarse-grained (auto), PTHREADS (auto)

[00:00:00] Reading alignment from file: ng-tutorial/bad.fa
[00:00:00] Loaded alignment with 9 taxa and 8 sites

WARNING: Fully undetermined columns found: 2

WARNING: Fully undetermined sequences found: 2

WARNING: Sequences t3 and t8 are exactly identical!
WARNING: Duplicate sequences found: 1

NOTE: Reduced alignment (with duplicates and gap-only sites/taxa removed) 
NOTE: was saved to: /Users/aimes/Temp/Software/raxml-ng_v1/ng-tutorial/bad.fa.raxml.reduced.phy

ERROR: Following taxon name contains invalid characters: t9'
ERROR: Following taxon name contains invalid characters: t6)

NOTE: Following symbols are not allowed in taxa names to ensure Newick compatibility:
NOTE: " " (space), ";" (semicolon), ":" (colon), "," (comma), "()" (parentheses), "'" (quote). 
NOTE: Please either correct the names manually, or use the reduced alignment file
NOTE: generated by RAxML-NG (see above).

ERROR: Alignment check failed (see details above)!

```

Note: RAXML tried to solve most of the issue and created the following files:
```
bad.fa.raxml.log
bad.fa.raxml.reduced.phy
```

5. Rerun the MSA check for the corrected file:
```shell
./raxml-ng --check --msa ng-tutorial/bad.fa.raxml.reduced.phy --model GTR+G

RAxML-NG v. 1.2.1 released on 22.12.2023 by The Exelixis Lab.
Developed by: Alexey M. Kozlov and Alexandros Stamatakis.
Contributors: Diego Darriba, Tomas Flouri, Benoit Morel, Sarah Lutteropp, Ben Bettisworth, Julia Haag, Anastasis Togkousidis.
Latest version: https://github.com/amkozlov/raxml-ng
Questions/problems/suggestions? Please visit: https://groups.google.com/forum/#!forum/raxml

System: Apple M2 Max, 12 cores, 32 GB RAM

RAxML-NG was called at 14-Mar-2024 13:29:12 as follows:

./raxml-ng --check --msa ng-tutorial/bad.fa.raxml.reduced.phy --model GTR+G

Analysis options:
  run mode: Alignment validation
  start tree(s): 
  random seed: 1710440952
  SIMD kernels: SSE3
  parallelization: coarse-grained (auto), PTHREADS (auto)

[00:00:00] Reading alignment from file: ng-tutorial/bad.fa.raxml.reduced.phy
[00:00:00] Loaded alignment with 6 taxa and 6 sites

Alignment comprises 1 partitions and 6 sites

Partition 0: noname
Model: GTR+FO+G4m
Alignment sites: 6
Gaps: 13.89 %
Invariant sites: 16.67 %



Alignment can be successfully read by RAxML-NG.


Execution log saved to: /Users/aimes/Temp/Software/raxml-ng_v1/ng-tutorial/bad.fa.raxml.reduced.phy.raxml.log

Analysis started: 14-Mar-2024 13:29:12 / finished: 14-Mar-2024 13:29:12

Elapsed time: 0.002 seconds
```
Note this file has 6 sites!

1. Check on a larger file with 12 taxa and 898 sites. For this case, raxml recommends using the `--parse` option to compress the sequences for efficient use in raxml:
```shell
./raxml-ng --parse --msa ng-tutorial/prim.phy --model GTR+G

RAxML-NG v. 1.2.1 released on 22.12.2023 by The Exelixis Lab.
Developed by: Alexey M. Kozlov and Alexandros Stamatakis.
Contributors: Diego Darriba, Tomas Flouri, Benoit Morel, Sarah Lutteropp, Ben Bettisworth, Julia Haag, Anastasis Togkousidis.
Latest version: https://github.com/amkozlov/raxml-ng
Questions/problems/suggestions? Please visit: https://groups.google.com/forum/#!forum/raxml

System: Apple M2 Max, 12 cores, 32 GB RAM

RAxML-NG was called at 14-Mar-2024 13:31:27 as follows:

./raxml-ng --parse --msa ng-tutorial/prim.phy --model GTR+G

Analysis options:
  run mode: Alignment parsing and compression
  start tree(s): 
  random seed: 1710441087
  tip-inner: OFF
  pattern compression: ON
  per-rate scalers: OFF
  site repeats: ON
  logLH epsilon: general: 10.000000, brlen-triplet: 1000.000000
  branch lengths: proportional (ML estimate, algorithm: NR-FAST)
  SIMD kernels: SSE3
  parallelization: coarse-grained (auto), PTHREADS (auto)

[00:00:00] Reading alignment from file: ng-tutorial/prim.phy
[00:00:00] Loaded alignment with 12 taxa and 898 sites

Alignment comprises 1 partitions and 413 patterns

Partition 0: noname
Model: GTR+FO+G4m
Alignment sites / patterns: 898 / 413
Gaps: 0.28 %
Invariant sites: 41.98 %


NOTE: Binary MSA file created: ng-tutorial/prim.phy.raxml.rba


* Estimated memory requirements                : 2 MB

* Recommended number of threads / MPI processes: 2

Please note that numbers given above are rough estimates only. 
Actual memory consumption and parallel performance on your system may differ!

Alignment can be successfully read by RAxML-NG.


Execution log saved to: /Users/aimes/Temp/Software/raxml-ng_v1/ng-tutorial/prim.phy.raxml.log

Analysis started: 14-Mar-2024 13:31:27 / finished: 14-Mar-2024 13:31:27

Elapsed time: 0.004 seconds
```

1. Infer the ML tree using the following command, which will perform 20 tree searches using 10 random and 10 parsimony-based starting trees. 
   1. Very important: set the `--seed` to be able to replicate the analyses exactly.

```shell
aimes@Averys-MacBook-Pro raxml-ng_v1 % ./raxml-ng --msa ng-tutorial/prim.phy --model GTR+G --prefix T3 --threads 2 --seed 2

RAxML-NG v. 1.2.1 released on 22.12.2023 by The Exelixis Lab.
Developed by: Alexey M. Kozlov and Alexandros Stamatakis.
Contributors: Diego Darriba, Tomas Flouri, Benoit Morel, Sarah Lutteropp, Ben Bettisworth, Julia Haag, Anastasis Togkousidis.
Latest version: https://github.com/amkozlov/raxml-ng
Questions/problems/suggestions? Please visit: https://groups.google.com/forum/#!forum/raxml

System: Apple M2 Max, 12 cores, 32 GB RAM

RAxML-NG was called at 14-Mar-2024 13:32:52 as follows:

./raxml-ng --msa ng-tutorial/prim.phy --model GTR+G --prefix T3 --threads 2 --seed 2

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

[00:00:00] Reading alignment from file: ng-tutorial/prim.phy
[00:00:00] Loaded alignment with 12 taxa and 898 sites

Alignment comprises 1 partitions and 413 patterns

Partition 0: noname
Model: GTR+FO+G4m
Alignment sites / patterns: 898 / 413
Gaps: 0.28 %
Invariant sites: 41.98 %


NOTE: Binary MSA file created: T3.raxml.rba

Parallelization scheme autoconfig: 2 worker(s) x 1 thread(s)

[00:00:00] Generating 10 random starting tree(s) with 12 taxa
[00:00:00] Generating 10 parsimony starting tree(s) with 12 taxa
Parallel parsimony with 2 threads
Parallel reduction/worker buffer size: 1 KB  / 0 KB

[00:00:00] Data distribution: max. partitions/sites/weight per thread: 1 / 413 / 6608
[00:00:00] Data distribution: max. searches per worker: 10

Starting ML tree search with 20 distinct starting trees

[00:00:00 -7100.975772] Initial branch length optimization
[00:00:00 -6718.627048] Model parameter optimization (eps = 10.000000)
[00:00:00 -6060.511107] AUTODETECT spr round 1 (radius: 5)
[00:00:00 -5734.635421] AUTODETECT spr round 2 (radius: 10)
[00:00:00 -5733.660149] SPR radius for FAST iterations: 10 (autodetect)
[00:00:00 -5733.660149] Model parameter optimization (eps = 3.000000)
[00:00:00 -5728.547247] FAST spr round 1 (radius: 10)
[00:00:00 -5709.432123] FAST spr round 2 (radius: 10)
[00:00:00 -5709.065994] Model parameter optimization (eps = 1.000000)
[00:00:00 -5708.953348] SLOW spr round 1 (radius: 5)
[00:00:00] [worker #1] ML tree search #2, logLikelihood: -5708.968625
[00:00:00 -5708.952941] SLOW spr round 2 (radius: 10)
[00:00:00 -5708.952934] Model parameter optimization (eps = 0.100000)

[00:00:00] [worker #0] ML tree search #1, logLikelihood: -5708.939541

[00:00:00 -7700.174878] Initial branch length optimization
[00:00:00 -7138.141093] Model parameter optimization (eps = 10.000000)
[00:00:00 -6364.898197] AUTODETECT spr round 1 (radius: 5)
[00:00:00 -5721.973718] AUTODETECT spr round 2 (radius: 10)
[00:00:00 -5720.822534] SPR radius for FAST iterations: 10 (autodetect)
[00:00:00 -5720.822534] Model parameter optimization (eps = 3.000000)
[00:00:00 -5708.961321] FAST spr round 1 (radius: 10)
[00:00:00 -5708.959520] Model parameter optimization (eps = 1.000000)
[00:00:00 -5708.935106] SLOW spr round 1 (radius: 5)
[00:00:00 -5708.935052] SLOW spr round 2 (radius: 10)
[00:00:00 -5708.935052] Model parameter optimization (eps = 0.100000)

[00:00:00] [worker #0] ML tree search #3, logLikelihood: -5708.930374

[00:00:00 -7778.801668] Initial branch length optimization
[00:00:00 -7235.863172] Model parameter optimization (eps = 10.000000)
[00:00:00] [worker #1] ML tree search #4, logLikelihood: -5708.925218
[00:00:00 -6367.362968] AUTODETECT spr round 1 (radius: 5)
[00:00:00 -5729.954682] AUTODETECT spr round 2 (radius: 10)
[00:00:00 -5729.113364] SPR radius for FAST iterations: 10 (autodetect)
[00:00:00 -5729.113364] Model parameter optimization (eps = 3.000000)
[00:00:00 -5716.362386] FAST spr round 1 (radius: 10)
[00:00:00 -5709.268253] Model parameter optimization (eps = 1.000000)
[00:00:00 -5709.058118] SLOW spr round 1 (radius: 5)
[00:00:00 -5709.052707] SLOW spr round 2 (radius: 10)
[00:00:00 -5709.052627] Model parameter optimization (eps = 0.100000)

[00:00:00] [worker #0] ML tree search #5, logLikelihood: -5708.984034

[00:00:00 -7811.514281] Initial branch length optimization
[00:00:00 -7237.827569] Model parameter optimization (eps = 10.000000)
[00:00:00 -6437.017329] AUTODETECT spr round 1 (radius: 5)
[00:00:00] [worker #1] ML tree search #6, logLikelihood: -5708.932311
[00:00:00 -5727.068038] AUTODETECT spr round 2 (radius: 10)
[00:00:00 -5726.369015] SPR radius for FAST iterations: 10 (autodetect)
[00:00:00 -5726.369015] Model parameter optimization (eps = 3.000000)
[00:00:00 -5714.451902] FAST spr round 1 (radius: 10)
[00:00:00 -5709.104408] Model parameter optimization (eps = 1.000000)
[00:00:00 -5708.953808] SLOW spr round 1 (radius: 5)
[00:00:01 -5708.932687] SLOW spr round 2 (radius: 10)
[00:00:01 -5708.932169] Model parameter optimization (eps = 0.100000)

[00:00:01] [worker #0] ML tree search #7, logLikelihood: -5708.923669

[00:00:01 -7919.170192] Initial branch length optimization
[00:00:01 -7338.014745] Model parameter optimization (eps = 10.000000)
[00:00:01] [worker #1] ML tree search #8, logLikelihood: -5708.955806
[00:00:01 -6390.067896] AUTODETECT spr round 1 (radius: 5)
[00:00:01 -5745.836878] AUTODETECT spr round 2 (radius: 10)
[00:00:01 -5745.043049] SPR radius for FAST iterations: 10 (autodetect)
[00:00:01 -5745.043049] Model parameter optimization (eps = 3.000000)
[00:00:01 -5728.961638] FAST spr round 1 (radius: 10)
[00:00:01 -5712.939281] FAST spr round 2 (radius: 10)
[00:00:01 -5712.915434] Model parameter optimization (eps = 1.000000)
[00:00:01 -5709.376360] SLOW spr round 1 (radius: 5)
[00:00:01 -5709.341431] SLOW spr round 2 (radius: 10)
[00:00:01 -5709.340959] Model parameter optimization (eps = 0.100000)

[00:00:01] [worker #0] ML tree search #9, logLikelihood: -5709.026250

[00:00:01 -6553.430050] Initial branch length optimization
[00:00:01 -6281.948016] Model parameter optimization (eps = 10.000000)
[00:00:01 -5722.896251] AUTODETECT spr round 1 (radius: 5)
[00:00:01 -5716.523362] AUTODETECT spr round 2 (radius: 10)
[00:00:01 -5715.876482] SPR radius for FAST iterations: 10 (autodetect)
[00:00:01 -5715.876482] Model parameter optimization (eps = 3.000000)
[00:00:01] [worker #1] ML tree search #10, logLikelihood: -5708.982248
[00:00:01 -5710.597305] FAST spr round 1 (radius: 10)
[00:00:01 -5710.560861] Model parameter optimization (eps = 1.000000)
[00:00:01 -5709.692786] SLOW spr round 1 (radius: 5)
[00:00:01 -5709.677670] SLOW spr round 2 (radius: 10)
[00:00:01 -5709.677571] Model parameter optimization (eps = 0.100000)

[00:00:01] [worker #0] ML tree search #11, logLikelihood: -5709.017405

[00:00:01 -6553.430050] Initial branch length optimization
[00:00:01 -6281.720014] Model parameter optimization (eps = 10.000000)
[00:00:01 -5722.956569] AUTODETECT spr round 1 (radius: 5)
[00:00:01] [worker #1] ML tree search #12, logLikelihood: -5709.015538
[00:00:01 -5716.079949] AUTODETECT spr round 2 (radius: 10)
[00:00:01 -5715.917663] SPR radius for FAST iterations: 10 (autodetect)
[00:00:01 -5715.917663] Model parameter optimization (eps = 3.000000)
[00:00:01 -5710.629342] FAST spr round 1 (radius: 10)
[00:00:01 -5710.588328] Model parameter optimization (eps = 1.000000)
[00:00:01 -5709.707667] SLOW spr round 1 (radius: 5)
[00:00:01 -5709.690920] SLOW spr round 2 (radius: 10)
[00:00:01 -5709.690824] Model parameter optimization (eps = 0.100000)

[00:00:01] [worker #0] ML tree search #13, logLikelihood: -5709.019098

[00:00:01 -6543.163074] Initial branch length optimization
[00:00:01 -6277.041098] Model parameter optimization (eps = 10.000000)
[00:00:02 -5715.997980] AUTODETECT spr round 1 (radius: 5)
[00:00:02 -5715.829621] AUTODETECT spr round 2 (radius: 10)
[00:00:02 -5715.817929] SPR radius for FAST iterations: 5 (autodetect)
[00:00:02 -5715.817929] Model parameter optimization (eps = 3.000000)
[00:00:02] [worker #1] ML tree search #14, logLikelihood: -5709.013044
[00:00:02 -5710.637975] FAST spr round 1 (radius: 5)
[00:00:02 -5710.579269] Model parameter optimization (eps = 1.000000)
[00:00:02 -5709.686182] SLOW spr round 1 (radius: 5)
[00:00:02 -5709.663938] SLOW spr round 2 (radius: 10)
[00:00:02 -5709.663803] Model parameter optimization (eps = 0.100000)

[00:00:02] [worker #0] ML tree search #15, logLikelihood: -5709.011551

[00:00:02 -6543.163074] Initial branch length optimization
[00:00:02 -6277.026357] Model parameter optimization (eps = 10.000000)
[00:00:02 -5716.073867] AUTODETECT spr round 1 (radius: 5)
[00:00:02] [worker #1] ML tree search #16, logLikelihood: -5709.011256
[00:00:02 -5715.918665] AUTODETECT spr round 2 (radius: 10)
[00:00:02 -5715.909029] SPR radius for FAST iterations: 5 (autodetect)
[00:00:02 -5715.909029] Model parameter optimization (eps = 3.000000)
[00:00:02 -5710.668237] FAST spr round 1 (radius: 5)
[00:00:02 -5710.612965] Model parameter optimization (eps = 1.000000)
[00:00:02 -5709.697518] SLOW spr round 1 (radius: 5)
[00:00:02 -5709.675302] SLOW spr round 2 (radius: 10)
[00:00:02 -5709.675179] Model parameter optimization (eps = 0.100000)

[00:00:02] [worker #0] ML tree search #17, logLikelihood: -5709.012850

[00:00:02 -6553.430050] Initial branch length optimization
[00:00:02 -6281.719836] Model parameter optimization (eps = 10.000000)
[00:00:02 -5722.968512] AUTODETECT spr round 1 (radius: 5)
[00:00:02] [worker #1] ML tree search #18, logLikelihood: -5709.014263
[00:00:02 -5716.079033] AUTODETECT spr round 2 (radius: 10)
[00:00:02 -5715.916245] SPR radius for FAST iterations: 10 (autodetect)
[00:00:02 -5715.916245] Model parameter optimization (eps = 3.000000)
[00:00:02 -5710.631272] FAST spr round 1 (radius: 10)
[00:00:02 -5710.588608] Model parameter optimization (eps = 1.000000)
[00:00:02 -5709.705947] SLOW spr round 1 (radius: 5)
[00:00:02 -5709.687903] SLOW spr round 2 (radius: 10)
[00:00:02 -5709.687799] Model parameter optimization (eps = 0.100000)

[00:00:02] [worker #0] ML tree search #19, logLikelihood: -5709.014344

[00:00:02] [worker #1] ML tree search #20, logLikelihood: -5709.013760

Optimized model parameters:

   Partition 0: noname
   Rate heterogeneity: GAMMA (4 cats, mean),  alpha: 0.368201 (ML),  weights&rates: (0.250000,0.012407) (0.250000,0.157634) (0.250000,0.694443) (0.250000,3.135516) 
   Base frequencies (ML): 0.355143 0.322256 0.080175 0.242425 
   Substitution rates (ML): 3.628312 44.212102 3.092487 2.376704 35.366753 1.000000 


Final LogLikelihood: -5708.923669

AIC score: 11477.847338 / AICc score: 11479.992666 / BIC score: 11621.852440
Free parameters (model + branch lengths): 30

Best ML tree saved to: /Users/aimes/Temp/Software/raxml-ng_v1/T3.raxml.bestTree
All ML trees saved to: /Users/aimes/Temp/Software/raxml-ng_v1/T3.raxml.mlTrees
Optimized model saved to: /Users/aimes/Temp/Software/raxml-ng_v1/T3.raxml.bestModel

Execution log saved to: /Users/aimes/Temp/Software/raxml-ng_v1/T3.raxml.log

Analysis started: 14-Mar-2024 13:32:52 / finished: 14-Mar-2024 13:32:54

Elapsed time: 2.810 seconds
```

**Note:** We did not find any information on convergence of the algorithm.

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

## IQ-Tree

We are following the tutorial in [here](http://www.iqtree.org/workshop/molevol2019).

1. Download for mac [here](http://www.iqtree.org/#download). Downloaded a zipped folder `iqtree-2.2.2.6-MacOSX` and placed in `Software` folder.

2. Check the installation worked, following steps [here](http://www.iqtree.org/doc/Quickstart).

Read carefully the output file as it provides information on starting tree and parameters used. No information found on convergence criteria, but they do provide information on how long it took to converge.

/Users/aimes/Temp/Software/iqtree-2.2.2.6-MacOSX/bin/iqtree2

```shell
cd /Users/aimes/Temp/Software/iqtree-2.2.2.6-MacOSX

aimes@Averys-MacBook-Pro iqtree-2.2.2.6-MacOSX % bin/iqtree2 -s example.phy

IQ-TREE multicore version 2.2.2.6 COVID-edition for Mac OS X 64-bit built May 27 2023
Developed by Bui Quang Minh, James Barbetti, Nguyen Lam Tung,
Olga Chernomor, Heiko Schmidt, Dominik Schrempf, Michael Woodhams, Ly Trong Nhan.

Host:    Averys-MacBook-Pro.local (SSE4.2, 32 GB RAM)
Command: bin/iqtree2 -s example.phy
Seed:    280844 (Using SPRNG - Scalable Parallel Random Number Generator)
Time:    Thu Mar 14 13:46:20 2024
Kernel:  SSE2 - 1 threads (12 CPU cores detected)

HINT: Use -nt option to specify number of threads because your CPU has 12 cores!
HINT: -nt AUTO will automatically determine the best number of threads to use.

Reading alignment file example.phy ... Phylip format detected
Alignment most likely contains DNA/RNA sequences
Constructing alignment: done in 0.00222707 secs using 66.72% CPU
Alignment has 17 sequences with 1998 columns, 1152 distinct patterns
1009 parsimony-informative, 303 singleton sites, 686 constant sites
           Gap/Ambiguity  Composition  p-value
Analyzing sequences: done in 6.50883e-05 secs using 79.89% CPU
   1  LngfishAu    0.15%    passed      6.20%
   2  LngfishSA    0.00%    failed      0.62%
   3  LngfishAf    0.05%    failed      1.60%
   4  Frog         0.05%    passed     58.01%
   5  Turtle       0.15%    passed     44.25%
   6  Sphenodon    0.10%    passed     59.78%
   7  Lizard       0.90%    passed     38.67%
   8  Crocodile    0.35%    failed      2.51%
   9  Bird         0.00%    failed      0.00%
  10  Human        0.00%    failed      0.85%
  11  Seal         0.00%    passed     68.93%
  12  Cow          0.00%    passed     59.11%
  13  Whale        0.00%    passed     97.83%
  14  Mouse        0.05%    failed      1.43%
  15  Rat          0.00%    passed     39.69%
  16  Platypus     0.00%    failed      3.46%
  17  Opossum      0.00%    failed      0.01%
****  TOTAL        0.11%  8 sequences failed composition chi2 test (p-value<5%; df=3)
Checking for duplicate sequences: done in 8.41618e-05 secs using 80.8% CPU


Create initial parsimony tree by phylogenetic likelihood library (PLL)... 0.001 seconds
Perform fast likelihood tree search using GTR+I+G model...
Estimate model parameters (epsilon = 5.000)
Perform nearest neighbor interchange...
Optimizing NNI: done in 0.0288138 secs using 98.24% CPU
Estimate model parameters (epsilon = 1.000)
1. Initial log-likelihood: -21149.206
Optimal log-likelihood: -21149.084
Rate parameters:  A-C: 3.74122  A-G: 5.20675  A-T: 3.87495  C-G: 0.42428  C-T: 15.34724  G-T: 1.00000
Base frequencies:  A: 0.355  C: 0.228  G: 0.192  T: 0.225
Proportion of invariable sites: 0.157
Gamma shape alpha: 0.740
Parameters optimization took 1 rounds (0.021 sec)
Time for fast ML tree search: 0.256 seconds

NOTE: ModelFinder requires 6 MB RAM!
ModelFinder will test up to 484 DNA models (sample size: 1998) ...
 No. Model         -LnL         df  AIC          AICc         BIC
  1  GTR+F         22701.459    39  45480.919    45482.512    45699.315
  2  GTR+F+I       21615.547    40  43311.095    43312.771    43535.091
  3  GTR+F+G4      21155.969    40  42391.937    42393.613    42615.933
  4  GTR+F+I+G4    21148.848    41  42379.696    42381.456    42609.292
  5  GTR+F+R2      21235.664    41  42553.328    42555.088    42782.924
  6  GTR+F+R3      21147.208    43  42380.415    42382.352    42621.211
  7  GTR+F+R4      21145.839    45  42381.677    42383.798    42633.673
 14  GTR+F+I+R2    21174.481    42  42432.962    42434.809    42668.158
 15  GTR+F+I+R3    21146.623    44  42381.246    42383.273    42627.641
 16  GTR+F+I+R4    21146.279    46  42384.558    42386.774    42642.153
 25  SYM+G4        21317.780    37  42709.561    42710.995    42916.757
 26  SYM+I+G4      21306.170    38  42688.340    42689.854    42901.137
 47  TVM+F+G4      21300.237    39  42678.474    42680.067    42896.870
 48  TVM+F+I+G4    21288.271    40  42656.541    42658.217    42880.537
 69  TVMe+G4       21422.187    36  42916.374    42917.732    43117.970
 70  TVMe+I+G4     21407.601    37  42889.202    42890.637    43096.398
 91  TIM3+F+G4     21367.926    38  42811.853    42813.366    43024.649
 92  TIM3+F+I+G4   21359.480    39  42796.960    42798.553    43015.356
113  TIM3e+G4      21717.461    35  43504.923    43506.207    43700.919
114  TIM3e+I+G4    21708.566    36  43489.131    43490.490    43690.728
135  TIM2+F+G4     21159.705    38  42395.410    42396.923    42608.206
136  TIM2+F+I+G4   21152.488    39  42382.976    42384.570    42601.372
157  TIM2e+G4      21320.880    35  42711.760    42713.045    42907.757
158  TIM2e+I+G4    21309.127    36  42690.254    42691.613    42891.851
179  TIM+F+G4      21368.783    38  42813.565    42815.078    43026.361
180  TIM+F+I+G4    21360.243    39  42798.486    42800.080    43016.882
201  TIMe+G4       21718.131    35  43506.263    43507.547    43702.259
202  TIMe+I+G4     21709.220    36  43490.440    43491.798    43692.036
223  TPM3u+F+G4    21488.893    37  43051.785    43053.220    43258.982
224  TPM3u+F+I+G4  21474.934    38  43025.868    43027.381    43238.664
245  TPM3+G4       21847.239    34  43762.478    43763.690    43952.875
246  TPM3+I+G4     21833.460    35  43736.920    43738.204    43932.916
267  TPM2u+F+G4    21303.797    37  42681.595    42683.029    42888.791
268  TPM2u+F+I+G4  21291.866    38  42659.733    42661.246    42872.529
289  TPM2+G4       21424.733    34  42917.467    42918.679    43107.863
290  TPM2+I+G4     21410.280    35  42890.560    42891.844    43086.556
311  K3Pu+F+G4     21489.348    37  43052.696    43054.130    43259.892
312  K3Pu+F+I+G4   21475.430    38  43026.859    43028.372    43239.656
333  K3P+G4        21847.491    34  43762.981    43764.193    43953.378
334  K3P+I+G4      21833.794    35  43737.588    43738.873    43933.585
355  TN+F+G4       21369.048    37  42812.096    42813.531    43019.292
356  TN+F+I+G4     21360.518    38  42797.036    42798.549    43009.832
377  TNe+G4        21718.202    34  43504.403    43505.616    43694.800
378  TNe+I+G4      21709.280    35  43488.560    43489.844    43684.556
399  HKY+F+G4      21489.737    36  43051.474    43052.833    43253.071
400  HKY+F+I+G4    21475.767    37  43025.534    43026.968    43232.730
421  K2P+G4        21847.675    33  43761.349    43762.492    43946.146
422  K2P+I+G4      21833.948    34  43735.895    43737.108    43926.292
443  F81+F+G4      22031.578    35  44133.155    44134.440    44329.152
444  F81+F+I+G4    22019.574    36  44111.149    44112.507    44312.745
465  JC+G4         22258.086    32  44580.172    44581.246    44759.368
466  JC+I+G4       22245.552    33  44557.104    44558.246    44741.900
Akaike Information Criterion:           GTR+F+I+G4
Corrected Akaike Information Criterion: GTR+F+I+G4
Bayesian Information Criterion:         TIM2+F+I+G4
Best-fit model: TIM2+F+I+G4 chosen according to BIC

All model information printed to example.phy.model.gz
CPU time for ModelFinder: 4.881 seconds (0h:0m:4s)
Wall-clock time for ModelFinder: 4.958 seconds (0h:0m:4s)

NOTE: 2 MB RAM (0 GB) is required!
Estimate model parameters (epsilon = 0.100)
Thoroughly optimizing +I+G parameters from 10 start values...
Init pinv, alpha: 0.000, 0.738 / Estimate: 0.000, 0.482 / LogL: -21159.748
Init pinv, alpha: 0.038, 0.738 / Estimate: 0.043, 0.532 / LogL: -21156.977
Init pinv, alpha: 0.076, 0.738 / Estimate: 0.085, 0.592 / LogL: -21154.641
Init pinv, alpha: 0.114, 0.738 / Estimate: 0.120, 0.654 / LogL: -21153.215
Init pinv, alpha: 0.153, 0.738 / Estimate: 0.153, 0.726 / LogL: -21152.514
Init pinv, alpha: 0.191, 0.738 / Estimate: 0.183, 0.803 / LogL: -21152.778
Init pinv, alpha: 0.229, 0.738 / Estimate: 0.185, 0.810 / LogL: -21152.836
Init pinv, alpha: 0.267, 0.738 / Estimate: 0.186, 0.813 / LogL: -21152.863
Init pinv, alpha: 0.305, 0.738 / Estimate: 0.186, 0.813 / LogL: -21152.876
Init pinv, alpha: 0.343, 0.738 / Estimate: 0.187, 0.816 / LogL: -21152.903
Optimal pinv,alpha: 0.153, 0.726 / LogL: -21152.514

Parameters optimization took 0.989 sec
Wrote distance file to... 
Computing ML distances based on estimated model parameters...
Calculating distance matrix: done in 0.000727892 secs using 96.58% CPU
Computing ML distances took 0.000837 sec (of wall-clock time) 0.000791 sec (of CPU time)
Setting up auxiliary I and S matrices: done in 2.28882e-05 secs using 109.2% CPU
Constructing RapidNJ tree: done in 3.79086e-05 secs using 163.6% CPU
Computing RapidNJ tree took 0.000096 sec (of wall-clock time) 0.000128 sec (of CPU time)
Log-likelihood of RapidNJ tree: -21161.696
--------------------------------------------------------------------
|             INITIALIZING CANDIDATE TREE SET                      |
--------------------------------------------------------------------
Generating 98 parsimony trees... 0.127 second
Computing log-likelihood of 98 initial trees ... 0.302 seconds
Current best score: -21152.514

Do NNI search on 20 best initial trees
Optimizing NNI: done in 0.0113189 secs using 97.05% CPU
Estimate model parameters (epsilon = 0.100)
BETTER TREE FOUND at iteration 1: -21152.510
Optimizing NNI: done in 0.017468 secs using 97.93% CPU
Optimizing NNI: done in 0.029588 secs using 97.26% CPU
Optimizing NNI: done in 0.0311589 secs using 97.47% CPU
Optimizing NNI: done in 0.030371 secs using 98.38% CPU
Optimizing NNI: done in 0.0374069 secs using 98.47% CPU
Optimizing NNI: done in 0.030812 secs using 97.94% CPU
Optimizing NNI: done in 0.0409119 secs using 97.89% CPU
Optimizing NNI: done in 0.0312121 secs using 97.7% CPU
Optimizing NNI: done in 0.0305409 secs using 97.86% CPU
Iteration 10 / LogL: -21158.319 / Time: 0h:0m:1s
Optimizing NNI: done in 0.0575271 secs using 97.61% CPU
Optimizing NNI: done in 0.025079 secs using 97.97% CPU
Optimizing NNI: done in 0.0500231 secs using 97.73% CPU
Optimizing NNI: done in 0.0428419 secs using 98.07% CPU
Optimizing NNI: done in 0.044075 secs using 97.53% CPU
Optimizing NNI: done in 0.0348651 secs using 97.76% CPU
Optimizing NNI: done in 0.0369608 secs using 97.7% CPU
Optimizing NNI: done in 0.0335839 secs using 98.05% CPU
Optimizing NNI: done in 0.0448811 secs using 98.31% CPU
Optimizing NNI: done in 0.0393069 secs using 98.4% CPU
Iteration 20 / LogL: -21157.831 / Time: 0h:0m:2s
Finish initializing candidate tree set (2)
Current best tree score: -21152.510 / CPU time: 1.155
Number of iterations: 20
--------------------------------------------------------------------
|               OPTIMIZING CANDIDATE TREE SET                      |
--------------------------------------------------------------------
Optimizing NNI: done in 0.0325279 secs using 98.41% CPU
Optimizing NNI: done in 0.039938 secs using 97.62% CPU
Optimizing NNI: done in 0.0437181 secs using 97.94% CPU
Optimizing NNI: done in 0.044981 secs using 98.02% CPU
Optimizing NNI: done in 0.0440478 secs using 97.93% CPU
Optimizing NNI: done in 0.041682 secs using 98.1% CPU
Optimizing NNI: done in 0.0633509 secs using 98.06% CPU
Optimizing NNI: done in 0.0401359 secs using 97.72% CPU
Optimizing NNI: done in 0.0427251 secs using 97.77% CPU
Optimizing NNI: done in 0.0346761 secs using 97.93% CPU
Iteration 30 / LogL: -21152.810 / Time: 0h:0m:2s (0h:0m:6s left)
Optimizing NNI: done in 0.0373049 secs using 98.56% CPU
Optimizing NNI: done in 0.032711 secs using 98.01% CPU
Optimizing NNI: done in 0.0440218 secs using 97.81% CPU
Optimizing NNI: done in 0.041002 secs using 97.46% CPU
Optimizing NNI: done in 0.0347941 secs using 97.8% CPU
Optimizing NNI: done in 0.0383849 secs using 97.32% CPU
Optimizing NNI: done in 0.0413959 secs using 97.61% CPU
Optimizing NNI: done in 0.0564661 secs using 97.53% CPU
Optimizing NNI: done in 0.037878 secs using 97.39% CPU
Optimizing NNI: done in 0.0530961 secs using 97.57% CPU
Iteration 40 / LogL: -21152.527 / Time: 0h:0m:3s (0h:0m:4s left)
Optimizing NNI: done in 0.0359809 secs using 97.47% CPU
Optimizing NNI: done in 0.0364931 secs using 97.62% CPU
Optimizing NNI: done in 0.038471 secs using 97.8% CPU
Optimizing NNI: done in 0.0381041 secs using 97.87% CPU
Optimizing NNI: done in 0.030838 secs using 99.14% CPU
Optimizing NNI: done in 0.0352988 secs using 98.33% CPU
Optimizing NNI: done in 0.0329142 secs using 97.96% CPU
Optimizing NNI: done in 0.0440369 secs using 97.57% CPU
Optimizing NNI: done in 0.0455999 secs using 97.59% CPU
Optimizing NNI: done in 0.054302 secs using 99.75% CPU
Iteration 50 / LogL: -21152.561 / Time: 0h:0m:3s (0h:0m:3s left)
Optimizing NNI: done in 0.0359819 secs using 99.91% CPU
Optimizing NNI: done in 0.0402451 secs using 99.71% CPU
Optimizing NNI: done in 0.0432479 secs using 97.39% CPU
Optimizing NNI: done in 0.0454121 secs using 97.57% CPU
Optimizing NNI: done in 0.0469451 secs using 97.77% CPU
Optimizing NNI: done in 0.033488 secs using 98.01% CPU
Optimizing NNI: done in 0.036474 secs using 97.88% CPU
Optimizing NNI: done in 0.0481319 secs using 97.89% CPU
Optimizing NNI: done in 0.0421438 secs using 97.52% CPU
Optimizing NNI: done in 0.02842 secs using 98.31% CPU
Iteration 60 / LogL: -21152.704 / Time: 0h:0m:3s (0h:0m:2s left)
Optimizing NNI: done in 0.0427251 secs using 97.71% CPU
Optimizing NNI: done in 0.038887 secs using 97.94% CPU
Optimizing NNI: done in 0.028614 secs using 97.9% CPU
Optimizing NNI: done in 0.0336249 secs using 97.83% CPU
Optimizing NNI: done in 0.0597372 secs using 97.97% CPU
Optimizing NNI: done in 0.0297079 secs using 97.76% CPU
Optimizing NNI: done in 0.040714 secs using 97.75% CPU
Optimizing NNI: done in 0.0441821 secs using 97.68% CPU
Optimizing NNI: done in 0.0396829 secs using 97.78% CPU
Optimizing NNI: done in 0.0421879 secs using 99.05% CPU
Iteration 70 / LogL: -21157.807 / Time: 0h:0m:4s (0h:0m:1s left)
Optimizing NNI: done in 0.0335898 secs using 97.41% CPU
Optimizing NNI: done in 0.0197279 secs using 97.59% CPU
Optimizing NNI: done in 0.032922 secs using 97.67% CPU
Optimizing NNI: done in 0.0459611 secs using 97.89% CPU
Optimizing NNI: done in 0.0590391 secs using 98.06% CPU
Optimizing NNI: done in 0.0445211 secs using 97.62% CPU
Optimizing NNI: done in 0.034096 secs using 97.99% CPU
Optimizing NNI: done in 0.039376 secs using 97.58% CPU
Optimizing NNI: done in 0.0516131 secs using 97.98% CPU
Optimizing NNI: done in 0.0360548 secs using 97.65% CPU
Iteration 80 / LogL: -21158.085 / Time: 0h:0m:4s (0h:0m:1s left)
Optimizing NNI: done in 0.031949 secs using 97.76% CPU
Optimizing NNI: done in 0.0411479 secs using 98.17% CPU
Optimizing NNI: done in 0.0496941 secs using 97.75% CPU
Optimizing NNI: done in 0.0322771 secs using 98.09% CPU
Optimizing NNI: done in 0.047349 secs using 98.41% CPU
Optimizing NNI: done in 0.0408101 secs using 97.81% CPU
Optimizing NNI: done in 0.0375972 secs using 98.08% CPU
Optimizing NNI: done in 0.0343449 secs using 98.2% CPU
Optimizing NNI: done in 0.0382192 secs using 97.9% CPU
Optimizing NNI: done in 0.0372319 secs using 97.52% CPU
Iteration 90 / LogL: -21152.772 / Time: 0h:0m:5s (0h:0m:0s left)
Optimizing NNI: done in 0.04719 secs using 97.58% CPU
Optimizing NNI: done in 0.034471 secs using 97.66% CPU
Optimizing NNI: done in 0.031249 secs using 97.83% CPU
Optimizing NNI: done in 0.0561588 secs using 97.91% CPU
Optimizing NNI: done in 0.0371861 secs using 98.57% CPU
Optimizing NNI: done in 0.034302 secs using 97.91% CPU
Optimizing NNI: done in 0.0313349 secs using 97.7% CPU
Optimizing NNI: done in 0.024997 secs using 97.69% CPU
Optimizing NNI: done in 0.04141 secs using 97.86% CPU
Optimizing NNI: done in 0.0410771 secs using 98.18% CPU
Iteration 100 / LogL: -21152.518 / Time: 0h:0m:5s (0h:0m:0s left)
Optimizing NNI: done in 0.0408421 secs using 97.62% CPU
Optimizing NNI: done in 0.0568919 secs using 97.97% CPU
TREE SEARCH COMPLETED AFTER 102 ITERATIONS / Time: 0h:0m:5s

--------------------------------------------------------------------
|                    FINALIZING TREE SEARCH                        |
--------------------------------------------------------------------
Performs final model parameters optimization
Estimate model parameters (epsilon = 0.010)
1. Initial log-likelihood: -21152.510
Optimal log-likelihood: -21152.506
Rate parameters:  A-C: 5.71262  A-G: 7.80712  A-T: 5.71262  C-G: 1.00000  C-T: 23.18142  G-T: 1.00000
Base frequencies:  A: 0.355  C: 0.228  G: 0.192  T: 0.225
Proportion of invariable sites: 0.154
Gamma shape alpha: 0.728
Parameters optimization took 1 rounds (0.012 sec)
BEST SCORE FOUND : -21152.506
Total tree length: 4.226

Total number of iterations: 102
CPU time used for tree search: 4.607 sec (0h:0m:4s)
Wall-clock time used for tree search: 4.524 sec (0h:0m:4s)
Total CPU time used: 5.625 sec (0h:0m:5s)
Total wall-clock time used: 5.545 sec (0h:0m:5s)

Analysis results written to: 
  IQ-TREE report:                example.phy.iqtree
  Maximum-likelihood tree:       example.phy.treefile
  Likelihood distances:          example.phy.mldist
  Screen log file:               example.phy.log

Date and Time: Thu Mar 14 13:46:30 2024

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

3. Load the best tree from the IQTree output:
```r
iqtree <- ape::read.tree(file = '/Users/aimes/Temp/Software/iqtree-2.2.2.6-MacOSX/example.phy.treefile')
```

4. Plot the tree:
```r
plot(iqtree)
```