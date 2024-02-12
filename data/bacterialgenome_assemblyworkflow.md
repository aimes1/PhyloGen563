### Bacterial Genome Assembly Workflow

Note: all information below was written and performed by Delaney Miller in reference to the 2024_Vfischeri_MillerAseemblies data and its state as of 2024-02-12. 

##### De-compress raw reads
Untar and unzip
```
tar -zxvf directory.tar.gz
tar -xvf directory.tar
gzip -d filename.fastq.gz
```
##### A Note on Software Installation
All bioinformatics software used in this pipeline is maintained on the open source Biocontainers repository. https://biocontainers.pro/registry
Assuming Miniconda3 and Bioconda are installed (see below), you can create a conda environment and install the software from the maintained biocontainer. 

Install MiniConda: https://chtc.cs.wisc.edu/uw-research-computing/conda-installation

Install BioConda:
https://bioconda.github.io/#install-conda

For example, to set up a conda environment for the software "filtlong" and install the software and all its dependencies in that environment:

```
(root)$conda create -n env-filtlong
(root)$conda activate env-filtlong
(env-filtlong)$ conda install filtlong
```
Now as long as you are within the environment (env-filtlong) you can run any filtlong commands. Importantly this does not change your working directory. Any output files you generate will populate within your current working directory. 

##### QC and filtering
For Nanopore reads, the most user-friendly QC software is Nanoplot. Instead of filtering before QC (with filtlong) you can set filter short reads out of the Nanoplot QC with the flag --minlength N to compare your reads before and after filtering. Similarly you can do this with quality score --minqual N. There are also lots of options to customize visualized output which is just nice. It outputs Q values and N50s but not L50s unfortunately. Currently it doesn't seem like there are optiosn for providing a reference. 

Filtlong can be used to filter out short or low-quality reads prior to assembly. For one isolate, MJM1059, I went ahead and filtered out anything below 10,000 bp and a minimum quality window of 60% or greater matching to see how that would affect our QC ouput from Nanoplot. Can be viewed here: 

file://research.drive.wisc.edu/mmandel/Lab-Members/dlmiller22/nanoplot_out/nanoplot_results_1059/NanoPlot-report.html
file://research.drive.wisc.edu/mmandel/Lab-Members/dlmiller22/nanoplot_out/nanoplot_results1059_filtlong/NanoPlot-report.html

For this example, filtering out short reads is actually taking away our highest quality reads. If the other isolates show the same trend I won't filter any of them. 

Update 12/15/23: Ok so across these samples, the mean read N50 is around 10,000 so filtering out anything below that is trashing half the data. After running the below command for Nanoplot QC, we have decent N50s across the board, great coverage (around 200 to 350xs), but kinda short reads (would like to have an average of 15-20,000bp). Overall our quality scores are decent, but since we have great coverage, it would be best to throw out anything below a Quality score of 10 (https://www.zymoresearch.com/blogs/blog/what-are-phred-scores) using the flag --keep_percent 90. 

```
filtlong data.fastq  – min_length 10000 –min_window_q 60 > output.fastq
filtlong --keep_percent 90 data.fastq > output.fastq
nanoplot --fastq 1059_nanopore.fastq --loglength -t 8 -o nanoplot_output/
```

##### De novo assembly
Ideally I would like to assemble with both canu and flye. Looking at the comparisons from this pub: chrome-extension://bomfdkbfpdhijjbeoicnfhjbdhncfhig/view.html?mp=hOFA3jKy
Canu is better at recovering contiguous plasmids (and chromosomes), although this is bimodal, due to the nondeterinistic subsampling of reads at the get-go. If we run canu we should do it in triplicate. For some reason canu crashes whenever I run it on my personal desktop. Not sure if its just hitting a wall with processing power, or if there is some incompatibility. Will try on the new Mac when it comes. 
Flye, however, which has the next best results (high contiguity, low indel size) ran successfully. This is also what Plasmidsaurus uses so might cut down on time if this looks as good as canu results. 

```
canu -d 1059_canu -p 1059 genome_size=4M -nanopore 1059_nanopore.fastq
flye –nano-hq raw_reads_nano/1059_nanopore.fastq -o flye_assemblies
flye --nano-hq nano_raw_reads/1059_filt.fastq  -t 8 -o flye_1059_filt_01
```
I chose to run flye with the flag -nano-hq because these genomes were sequenced in 2021. Likely the basecalling used at the time was prior to Q20 but maybe used Guppy or something of that sort. the -nano-hq assumes an error rate of <5% so that seems like a safe call. Newer sequencing that uses Q20 should use the flag --nano-hq --read-error 0.03 . 

##### Assembly QC
Using Quast I checked for misassemblies, using DSM507 as a reference genome. Its a recently sequenced, complete genome with a Unicycler hybrid assembly of Illumina and Nanopore MinION reads. 

To start I compared one flye and one canu assembly of MJM1059. Both are non-deterministic assemblers so each time I assemble it will be different. Eventually I will run each 3xs to feed into Trycycler. For now I just wanted to compare metrics to decide whether its worth doing both. 

```
quast -r DSM507.fna -o quast_1059flye_out flye_out_1059/00-assembly/draft_assembly.fasta

quast -r DSM507.fna -o quast_1059canu_out 1059_canu/1059.contigs.fasta
```
Surprisingly flye produced 0 missasseblies while canu produced 157 relocations, which is rather concerning. If this were an  Illumina sequenced assembly we were referencing I wouldn't be as concerned but given this difference I may drop the use of canu entirely. To proceed I'm going to run canu a few times and see how different each assembly is.

Running flye 3xs for each genome revealed misassmblies with flye as well. It appears to be stochastic depending on what read subset they start with. All the more reason to use Trycycler. Will try Trycycler with flye run 3xs. Then run Trycycler with flye 3xs and canu 3xs for a handful isolates to see if it improves anything. 

##### Consensus assembly

##### Annotation