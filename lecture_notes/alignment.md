---
layout: default
title: Alignment I
nav_order: 3
mathjax: true
---

# Alignment methods (Part 1)


### Learn@Home: Sequencing check-up
- We understand sequencing technologies
- We learned a bit about `phyluce` as a pipeline for phylogenomics on UCEs and about `FastQC` for QC of raw reads
- We start thinking about data for the class project and start working on QC if needed -> beginning of work from home in your data!


### Learning objectives

At the end of today's session, you
- will be able to explain the most widely used algorithms for pairwise sequence alignment (Needleman-Wunsch algorithm)

# What is multiple sequence alignment (MSA)?

- Homology is inferred from an input of sequences that are assumed to have an evolutionary relationship: descended from a common ancestor
- Intuitively, an MSA method inserts gap characters (`-`) inside input sequences to produce a set of longer sequences that are all of the same length, such that residues at the same position in different sequences (aligned residues) share some common properties (homology)
- MSA is a crucial step since phylogenetic inference methods assume that residue homology relationships are correctly reflected by the input sequences


<div style="text-align:center"><img src="../assets/pics/fig9.1.png" width="750"/></div>

_Figure 9.1 in Warnow (2018) Computational phylogenetics_


The true MSA reflects the historical substitution, insertion and deletion evolutionary events:

<div style="text-align:center"><img src="../assets/pics/fig9.2.png" width="750"/></div>

_Figure 9.2 in Warnow (2018) Computational phylogenetics_

{: .highlight }
**Why is it one of the most computationally intensive tasks?**
Alignment can be not identifiable or unique.
Multiple solutions are possible, which is what makes alignment one of the most intensive steps with a lot of human validation. 

## Example 9.1
Suppose that we knew the _true_ evolutionary events from sequence `ACAT` to `AGAT`. Suppose that we knew that it was not a substitution, but a deletion of `C` (thus creating `AAT`) followed by an insertion of `G`. Even in this scenario (when we know the truth), there are two ways to represent the alignment:

With no knowledge, we may align as:
ACAT
AGAT
This reflects a substitution of C to G. 
```
With our knowledge: 
AC-AT
A-GAT
```
and
```
A-CAT
AG-AT
```

## In-class activities

**Table 9.1** (Warnow). What would be the alignment of the sequence `S=ACATTA` which evolves into `S'=TACA` if we knew the _true_ evolutionary events?
- deletion of the first two nucleotides `AC`
- deletion of the second `T`
- substitution of `T` into `C`
- insertion of `T` at the front

**Solution:** 
AC-ATTA
--TAC-A

**Table 9.2** (Warnow). Without knowing the _true_ evolutionary events from `S=ACATTA` to `S'=TACA`, what would you think is a good alignment?

Solutions: 
ACATTA
T-AC-A

-ACATTA
TACA---

ACATTA--
----TACA

**Solution:** You probably choose an alignment where none (or few) of the _true_ homology relationships are correct.
- The true alignment has 4 events: 2 deletions, 1 insersion, 1 substitution
- The algorithm will ultimately choose an alignment based on how we penalize each of the events


{: .important }
**First key insight for MSA:**
We are guiding the algorithms by selecting the penalties for evolutionary events: substitutions, deletions, insersions. It has nothing to do with _true_ evolutionary events or _true_ homology.


# MSA algorithm

**Input:** unaligned sequences (different lengths)

**Output:** aligned sequences (same length) where each site is an assertion of homology


**Steps in MSA:**
1. Define cost of each event: deletion, insertion, substitution
2. Learn to obtain the optimal pairwise alignment with the minimum cost ("edit distance")
3. Learn to obtain the optimal multiple sequence alignment: we need to be able to align alignments

## 1. Cost of evolutionary events

- cost of deletion/insersion (cost of gap): 1
- cost of substitution: 1


{: .note }
Some software/books will use "weights" instead of costs: weight for match: 5; weight for gap: -1; weight for mismatch (substitution): -1.
I prefer to use costs because the idea of negative weights is not intuitive.

### In-class activities

**Table 9.3** (Warnow). How would you align the sequences `S=AACT` and `S'=CTGG` when:
- cost of gap: 1
- cost of substitution: 3

Alignment: cost 4 (4 gaps)
AACT--
--CTGG

**Table 9.3** (Warnow). How would you change the alignment between sequences `S=AACT` and `S'=CTGG` if the costs were: 
- cost of gap: 4
- cost of substitution: 1

Alignment: cost 4 (4 substitutions)
AACT
CTGG

## Other types of costs

There are other ways to measure cost/penalty:
- sequence identity: number of identical sites in an alignment divided by the total number of aligned positions
- biochemical similarity when assigning costs of substitutions (Figure 3.4 HB 3): PAM weight matrices and BLOSUM62 weight matrices

<div style="text-align:center"><img src="../assets/pics/blosum62.png" width="350"/></div>


We will continue to use cost for simplicity.


## 2. Pairwise sequence alignment

- Pairwise alignment of short toy sequences (like in the examples) can be done by hand
- Pairwise alignment of real sequences would be too difficult to do by hand, so we need smart algorithms: **Needleman-Wunsch algorithm**
- Needleman-Wunsch is a dynamic programming algorithm
- Dynamic programming: optimization algorithm that simplifies a complicated problem by breaking it down into simpler sub-problems in a recursive manner


## Needleman-Wunsch algorithm

- **Ingredients:** 
  - Two sequences: $$A=a_1 a_2 ...a_m$$ and $$B=b_1 b_2 ...b_n$$
  - 1) cost of gap and 2) cost of substitution
- Denote $F(i,j)$ the minimum cost to align sub-sequences $A_i$ and $B_j$ based on the costs

{: .note }
**Main principle:** When we want to compute $F(i,j)$, we assume that we have already computed all smaller sequences (sub-problems): $F(i-1,j-1), F(i,j-1), F(i-1,j)$.

The final site of the alignment must take one of the following forms:

1. $a_i$ and $b_j$ are aligned together in the final site. Then the other sites define a pairwise alignment of $A_{i-1}$ and $B_{j-1}$
2. $a_i$ is aligned with a gap in the final site. Then $A_{i-1}$ and $B_{j}$ defined a pairwise alignment
3. $b_j$ is aligned with a gap in the final site. Then $A_{i}$ and $B_{j-1}$ defined a pairwise alignment


### Example of notation

Let $A=a_1 a_2 a_3 a_4 a_5 a_6$ and $B=b_1 b_2 b_3 b_4 b_5$, and suppose you want to align sites $a_5$ ( $i=5$ ) and $b_3$ ( $j=3$ ). We have three options:

1. $a_5$ and $b_3$ are aligned together in the final site. Then the other sites define a pairwise alignment of $A_4=a_1 a_2 a_3 a_4$ and $B_2=b_1 b_2$ (we do not know how at this point)
2. $a_5$ is aligned with a gap in the final site. Then $A_4=a_1 a_2 a_3 a_4$ and $B_3=b_1 b_2 b_3$ define a pairwise alignment
3. $b_3$ is aligned with a gap in the final site. Then $A_5=a_1 a_2 a_3 a_4 a_5$ and $B_2=b_1 b_2$ define a pairwise alignment


### Needleman-Wunsch algorithm: Costs

1. If $a_i$ and $b_j$ are aligned together in the final site, then the cost is 0 if $a_i=b_j$ and 1 (or whatever cost of substitution defined) if they are different. Hence, the total cost is $F(i,j) = F(i-1,j-1)+cost(a_i,b_j)$
2. If $a_i$ is aligned with a gap in the final site, then the cost is 1 (or whatever the cost of gap is). Hence, the the total cost is $F(i,j) = F(i-1,j)+1$
3. If $b_j$ is aligned with a gap in the final site, then the cost is 1 (or whatever the cost of gap is). Hence, the the total cost is $F(i,j) = F(i,j-1)+1$

How to know which of the three options to do? We choose the one with minimum cost!

$F(i,j)=min \\{F(i-1,j-1)+cost(a_i,b_j), F(i-1,j)+1, F(i,j-1)+1 \\}$.


### Needleman-Wunsch algorithm

1. Compute $F(i,j)$ for every $i,j$ and put in a matrix (sometimes denoted dynamic programming (DP) matrix). First column/row correspond to gap and F(0,0)=0
2. As you fill the matrix, keep track of which of the three entries gave you the minimum with an arrow
3. Trace back the arrows to construct the alignment (diagonal arrow=nucleotide, vertical/horizontal arrow=gap replacing the nucleotide the arrow is pointing)

<div style="text-align:center"><img src="../assets/pics/fig9.3.png" width="450"/></div>

_Figure 9.3 from Warnow (2018) Computational phylogenetics_

{: .highlight }
**In-class example:**
We want to align $S_1=ATCG$ and $S_2=TCA$ for a cost of substitution of 1 and cost of gap of 2. We will work through the steps of creating the F matrix in class, and then, as homework, you can complete the whole matrix.

cost of gap = 2
cost of substitution = 1

  - A T C G
- 0 2 4 6 8
T 2 1 
C 4 
A 6

From diagonal: aligning A with T is a cost of 1 (substitution) plus the cost of the diagonal -,- alignment (0) for a total cost of 1. So we commit to the diagonal (we follow the area back through the matrix to create the aligment)

From the top: the cost (A/-) is 4: 2 + F(0,1) = 4
From the side: the cost (-/T) is 4: 2 + F(1,0) = 4

## How do we get the alignment after building the F matrix?

We trace back the arrows from the bottom right corner:

<div style="text-align:center"><img src="../assets/pics/nw-ex.png" width="300"/></div>

```
ATCG
-TCA
```

{: .important }
**Take-home message:** The final alignment depends on the costs of gaps and substitutions.



---
layout: default
title: Alignment IV
nav_order: 6
---



# Alignment methods (Part 4: computer lab: 2024-02-13)

### Learning objectives

At the end of today's session, you
- will learn to use different software options: ClustalW, T-Coffee and MUSCLE


{: .highlight }
Let's take a look at data from last year's projects [here](https://github.com/crsl4/phylogenetics-class/blob/master/exercises/data-examples.md).


# MSA software key insights

- No perfect method
- No automatic method
  - All methods require manual work of comparing results from different alignment parameters and from different sofware
- Take notes of the choices you made and keep track of all comparisons to justify final choice
- We probably don't spend as much time as we should on the alignment step of the phylogenomic pipeline
  - We want a blackbox that does not exist yet!

## Other algorithms

### Genetic algorithm
- SAGA uses the WSP objective function but uses genetic algorithms instead of dynamic programming (individual=alignment)
- very accurate
- more scalable than T-coffee, but still not super scalable

### Hidden markov model
- [UPP](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-015-0688-z)
- [pasta](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4424971/)

### Simultaneous estimation tree/alignment
- [sate](https://phylo.bio.ku.edu/software/sate/sate.html)


### Other considerations

- Nucleotide vs amino acid sequence
  - when there is choice (protein-coding genes), amino acid alignments are easier to carry out and less ambiguous; also nucleotide alignments do not recognize codon as a unit and can break up the reading frame; typically, you align the amino acids and then generate the corresponding nucleotide sequence alignment
  - when sequences are not protein coding, only choice is to align nucleotides
- Manual editing and visualizing alignments
  - manual editing is scary because it is not reproducible
  - but many times it is necessary because automatic alignment methods are not as accurate as they should be


### Which program to choose?
- Not a clear answer
- Scalability vs accuracy
- HW reading: [Alignathon](https://genome.cshlp.org/content/24/12/2077)
- **Strategy:**
  - Run multiple programs and parameter choices
  - Filtering is more important than the specific program used (more on filtering later)
  - Read program papers and documentation carefully
  - Take good note of choices and keep track of all comparisons to justify final choice


# Software tools for alignment

## ClustalW

- [ClustalW](http://www.clustal.org/clustal2/)
- From the [docs](http://www.clustal.org/download/clustalw_help.txt):

```
DATA (sequences)

-INFILE=file.ext                             :input sequences.
-PROFILE1=file.ext  and  -PROFILE2=file.ext  :profiles (old alignment).


                VERBS (do things)

-OPTIONS            :list the command line parameters
-HELP  or -CHECK    :outline the command line params.
-FULLHELP           :output full help content.
-ALIGN              :do full multiple alignment.
-TREE               :calculate NJ tree.
-PIM                :output percent identity matrix (while calculating the tree)
-BOOTSTRAP(=n)      :bootstrap a NJ tree (n= number of bootstraps; def. = 1000).
-CONVERT            :output the input sequences in a different file format.

                PARAMETERS (set things)

***General settings:****
-INTERACTIVE :read command line, then enter normal interactive menus
-QUICKTREE   :use FAST algorithm for the alignment guide tree
-TYPE=       :PROTEIN or DNA sequences
-NEGATIVE    :protein alignment with negative values in matrix
-OUTFILE=    :sequence alignment file name
-OUTPUT=     :GCG, GDE, PHYLIP, PIR or NEXUS
-OUTORDER=   :INPUT or ALIGNED
-CASE        :LOWER or UPPER (for GDE output only)
-SEQNOS=     :OFF or ON (for Clustal output only)
-SEQNO_RANGE=:OFF or ON (NEW: for all output formats)
-RANGE=m,n   :sequence range to write starting m to m+n
-MAXSEQLEN=n :maximum allowed input sequence length
-QUIET       :Reduce console output to minimum
-STATS=      :Log some alignents statistics to file

***Multiple Alignments:***
-NEWTREE=      :file for new guide tree
-USETREE=      :file for old guide tree
-MATRIX=       :Protein weight matrix=BLOSUM, PAM, GONNET, ID or filename
-DNAMATRIX=    :DNA weight matrix=IUB, CLUSTALW or filename
-GAPOPEN=f     :gap opening penalty        
-GAPEXT=f      :gap extension penalty
-ENDGAPS       :no end gap separation pen. 
-GAPDIST=n     :gap separation pen. range
-NOPGAP        :residue-specific gaps off  
-NOHGAP        :hydrophilic gaps off
-HGAPRESIDUES= :list hydrophilic res.    
-MAXDIV=n      :% ident. for delay
-TYPE=         :PROTEIN or DNA
-TRANSWEIGHT=f :transitions weighting
-ITERATION=    :NONE or TREE or ALIGNMENT
-NUMITER=n     :maximum number of iterations to perform
-NOWEIGHTS     :disable sequence weighting
```


What are the default values of these options?

Another thing to notice:

```
==ITERATION==

 A remove first iteration scheme has been added. This can be used to improve the final
 alignment or improve the alignment at each stage of the progressive alignment. During the 
 iteration step each sequence is removed in turn and realigned. If the resulting alignment 
 is better than the  previous alignment it is kept. This process is repeated until the score
 converges (the  score is not improved) or until the maximum number of iterations is 
 reached. The user can  iterate at each step of the progressive alignment by setting the 
 iteration parameter to  TREE or just on the final alignment by seting the iteration 
 parameter to ALIGNMENT. The default is no iteration. The maximum number of  iterations can 
 be set using the numiter parameter. The default number of iterations is 3.
  
 -ITERATION=    :NONE or TREE or ALIGNMENT
 
 -NUMITER=n     :Maximum number of iterations to perform
```


**Further reading:** Read the ClustalW [documentation](http://www.clustal.org/download/clustalw_help.txt). Is it clear what the algorithm is doing and how to best select the parameters involved? What is missing (if any) from this documentation?


## T-Coffee

[T-Coffee documentation](http://www.tcoffee.org/Projects/tcoffee/documentation/index.html#quick-start-t-coffee)

```shell
$ t_coffee sample_seq1.fasta
```

- When aligning, T-Coffee will always at least generate three files:
  - `sample_seq1.aln` : Multiple Sequence Alignment (ClustalW format by default)
  - `sample_seq1.dnd` : guide tree (Newick format)
  - `sample_seq1.html` : colored MSA according to consistency (html format)
- `T-Coffee` also has a great [documentation](http://www.tcoffee.org/Projects/tcoffee/documentation/index.html#document-tcoffee_main_documentation)
- Specifically, it has a good description of the parameters, see [here](http://www.tcoffee.org/Projects/tcoffee/documentation/index.html#t-coffee-parameters-flags)
- Don't forget to check out [M-Coffee](http://www.tcoffee.org/Projects/tcoffee/documentation/index.html#m-coffee) that combines the output of eight aligners (MUSCLE, ProbCons, POA, DIALIGN-T, MAFFT, ClustalW, PCMA and T-Coffee)


## MUSCLE

- [MUSCLE documentation](https://www.drive5.com/muscle/)
- The different parameter options are explained [here](https://www.drive5.com/muscle/manual/options.html)
- The default settings are chosen for maximum accuracy (how?), but you can change the settings for more speed (see [here](https://www.drive5.com/muscle/manual/index.html))





## **Homework:** Check out the alignment HW [here](https://github.com/crsl4/phylogenetics-class/blob/master/exercises/hw-alignment.md).


# Learn more!

- Read Chapter 3 of the Phylogenetic Handbook (HB)
- Read Sections 9.1-9.5, 9.11, 9.12, 9.13 of [Computational phylogenetics](https://www.amazon.com/Computational-Phylogenetics-Introduction-Designing-Estimation/dp/1107184711) (Warnow) 
- Read HAL 2.3 on a new alignment method `MACSE`