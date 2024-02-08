Literature discussion notes

# T-coffee: a novel method for fast and accurate multiple sequence alignment 

Link: https://www.sciencedirect.com/science/article/pii/S0022283600940427

Summary: describe new method (T-Coffee) for multiple sequence alignment to improve accuracy by sacrificing speed. Based on popular progressive approach to multiple alignment, but better handles difficult test cases and combinations of local and global pair-wise alignments. 
* Pre-processes data set of pair-wise alignments between sequences to provide library of alignment information to guide progressive alignment. 

Introduction 
* Progressive-alignment strategies are the most widely used (take initial phylogenetic tree between sequences and gradually build up alignment following order in the tree) but suffers from greediness (errors made in first alignments can't be changed later)
  * T-coffee is an attempt to minimize this effect while retaining progressive method. 

T-Coffee algorithm
* Two main features
  * Provides simple and flexible means of generating multiple alignments using heterogeneous data sources provided to T-Coffee via a library of pair-wise alignments 
  * Optimization method finds the multiple alignment that best fits the pair-wise alignments in the input library 
    * Progressive strategy used is similar to that of ClustalW but T-Coffee is a progressive alignment that considers information from all sequences during each alignment step not just what is being aligned at that stage. 

Discussion
* combines signals from heterogeneous sources into a unique consensus multiple sequence alignment 
  * combination of local and global alignments leads to significant increase in alignment accuracy 
* Uses position-specific scoring scheme instead of substitution matrix for aligning sequences 
* Primary weighting scheme better tolerates noise from small similar segments arising by chance because these short high-score segments aren't consistent enough to have strong effect on position-specific scoring scheme 
* Final alignments are processed using dynamic programming (progressive alignment). 