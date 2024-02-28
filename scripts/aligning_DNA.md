# Aligning Own DNA (2024-02-20)

Note: the ClustalW and MUSCLE alignment programs do not run to completion on my machine as of 2024-02-20. To circumvent this, I plan to run more alignment methods on a desktop lab computer that already has a conda environment set up and more computing power, but that computer has been having some other issues that have made it inaccessible the past few days. To fulfill the homework requirement, I've detailed a Mauve alignment, a method that does run on my machine and I've detailed the first steps of, but will require some more refinement for the final project output.

### Alignment method 1: Mauve 
1. [Mauve](https://darlinglab.org/mauve/mauve.html) chosen for initial alignment of *E. berryi* bacterial isolate fasta files. I am initially only running my own isolates as an early evaluation to see what is present, and determine if I want to spend more time and analysis on *V. fischeri* strain specific details or focus on broader *Vibrio* phylogenetics. 
   1. Description: Mauve is a multiple genome aligner best used for large-scale evolutionary events such as rearrangement and inversion. The progressiveMauve algorithm is meant to use modest computational resources, but the computation time scales cubically with the number of genomes and is unsuitable for more than 50-100 genomes (varies by divergence between the genomes). 
   2. Note: Mauve identifies conserved segments internally free from genome rearrangements called Locally Collinear Blocks (LCBs). A first alignment must be ran using the default parameters, but the default minimum LCB weight of 3 is typically too low to be accurate, but is manually determined by information provided in the first alignment to run a second more accurate alignment. 
      1. progressiveMauve is included among the WGA tools tested in the [Alignathon](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4248324/) paper.
   3. Strengths: modest computation power that readily identifies and visualizes genome changes among closely related organisms by applying ClustalW or MUSCLE progressive global alignment algorithms to each LCB. 
   4. Limitations: Mauve works best on closely related organisms, may not align large regions shared by subsets of the genomes, rearranged regions shared by genome subsets will not be identified, minimum LCB must be manually calculated after first alignment, algorithm has difficulty aligning genomes with many segmental duplications. 
2. Downloaded [Mauve for Mac OS X 10.7+](https://darlinglab.org/mauve/download.html) which runs as an application. 
   1. Documentation on how to operate Mauve found in [Mauve User's Guide](https://darlinglab.org/mauve/user-guide/introduction.html) and command-line tools detailed [here](https://darlinglab.org/mauve/user-guide/progressivemauve.html) within user guide. Program can be run through command line or through the Mauve app user interface. 
   2. Relative to the Mauve.app, the path to the progressiveMauve aligner will be ../Mauve.app/Contents/MacOS/progressiveMauve
3. Align the whole genome DNA sequences of *E. berryi* bacterial isolates as found in [2022_Eberryi_WGSeq_Consensusfnas](../data/Vfischeri_genomes/2022_Eberryi_WGSeq_consensusfnas) folder by running `progressiveMauve`.
   1. These files are all in .fna format 
   2. Input following commands to generate output file berryiisolates.xmfa, which is aligning the listed .fna input genome files. 
```shell
cd data/Vfischeri_genomes/2022_Eberryi_WGSeq_consensusfnas

/Applications/Mauve.app/Contents/MacOS/progressiveMauve --output=berryiisolates.xmfa BH1.fna BH2.fna BW1.fna BW2.fna BW3.fna BW4.fna BW5.fna BW6.fna BW7.fna BW8.fna BW9.fna
```


### Prepare files for alignment 
1. Compile sequence data from BW3, BW8, and BW2 fna files into one fasta file. This file contains all DNA sequences as contigs for the 3 bacterial isolates from *E. berryi* squid. These files were chosen due to their highest quality among the isolates and lowest number of contigs. 
   1. File labeled as [BW3+BW8+BW2.fasta](/Users/aimes/Temp/PhyloGen563/data/large_files/genome_processing/BW3+BW8+BW2.fasta) in genome_processing data folder. 
2. Use this compiled file for MUSCLE and ClustalW

### Alignment method 2: MUSCLE

### MUSCLE
Note: retrying Muscle on a lab mac desktop computer. 
1. Download [MUSLCE](https://github.com/rcedgar/muscle/releases/tag/5.1.0) with file [muscle5.1.macos_intel64](https://github.com/rcedgar/muscle/releases/download/5.1.0/muscle5.1.macos_intel64). 
   1. Make sure this executable file has permissions to read and execute by using: 
```shell
chmod +x /Users/mandellab/Desktop/Avery/Software/muscle5.1.macos_intel64
  ```
2. Run MUSCLE on E. berryi bacterial isolate data with commands:
```shell
cd /Users/mandellab/Desktop/Avery/
/Users/mandellab/Desktop/Avery/Software/muscle5.1.macos_intel64 -in BW3+BW8+BW2.fasta -out berryi3isolatesDNA-aligned-muscle.fasta
  ```


### Alignment method 3:ClustalW - not updated
1. Download ClustalW file clustalw-2.1-macosx.dmg as modified on 2010-11-17. 
   1. Link to download file: http://www.clustal.org/download/current/clustalw-2.1-macosx.dmg
2. Downloaded primatesAA.fasta file from Phylogenetic class repo [data folder](https://github.com/crsl4/phylogenetics-class/tree/master/data).
   1. primatesAA.fasta file is in data/class_exercises folder within Phylogen563 repo. Must be in class_exercises folder to work on the file. 
   2. Running commands for Clustal 2.0.12 are found in the [docs](http://www.clustal.org/download/clustalw_help.txt).
   3. Check functionality: enter the command below to check the number of sequences in the file, which should return the answer 22
      1. grep ">" primatesAA.fasta | wc -l
3. Run the command to align sequences
   1. /Users/aimes/Temp/clustalw-2.1-macosx/clustalw2 -ALIGN -INFILE=primatesAA.fasta -OUTFILE=primatesAA-aligned.fasta -OUTPUT=FASTA
   2. Generates error: zsh: bad CPU type in executable: /Users/aimes/Temp/clustalw-2.1-macosx/clustalw2
      1. Meaning: clustal is likely incompatible with my operating system, recommended by crsl4 to move to MUSCLE program instead. 