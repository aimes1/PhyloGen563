# Aligning Own DNA (2024-02-13)

**Instructions:** Run and compare the results of all three MSA software on the toy dataset of primates (see the class repo [data folder](https://github.com/crsl4/phylogenetics-class/tree/master/data)). You can use my reproducible script as guideline: [notebook-log.md](https://github.com/crsl4/phylogenetics-class/tree/master/exercises/notebook-log.md).

**ClustalW**

1. Download [ClustalW](http://www.clustal.org/clustal2/)
2. Download the `primatesAA.fasta` file from the Phylogenetic Handbook website (22 primate aminoacid sequences). The website stopped working at some point, so we have the file in the class repo [data folder](https://github.com/crsl4/phylogenetics-class/tree/master/data).
3. Run `ClustalW`, see [docs](http://www.clustal.org/download/clustalw_help.txt)

**T-Coffee**

1. Download [T-Coffee](http://www.tcoffee.org/Projects/tcoffee/index.html#DOWNLOAD)
2. Run `T-Coffee` on the same `primatesAA.fasta` data. See the [docs](http://www.tcoffee.org/Projects/tcoffee/documentation/index.html#quick-start-t-coffee)

**MUSCLE**

1. Download [MUSCLE](https://www.drive5.com/muscle/downloads.htm)
2. Run `MUSCLE` on the same `primatesAA.fasta` data. See the [docs](https://www.drive5.com/muscle/manual/basic_alignment.html)

# Alignment method documentation (2024-02-13)
### ClustalW
1. Downloaded ClustalW file clustalw-2.1-macosx.dmg as modified on 2010-11-17. 
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

### MUSCLE
1. Download [MUSLCE](https://github.com/rcedgar/muscle/releases/tag/5.1.0) with file [muscle5.1.macos_arm64](https://github.com/rcedgar/muscle/releases/download/5.1.0/muscle5.1.macos_arm64). 
   1. Make sure this executable file has permissions to read and execute. 
   2. Use command: chmod +x /Users/aimes/Temp/Software/muscle5.1.macos_arm64
2. Run MUSCLE on primate data with commands
   1. cd /Users/aimes/Temp/PhyloGen563/data/class_exercises
   2. /Users/aimes/Temp/Software/muscle5.1.macos_arm64 -in primatesAA.fasta -out primatesAA-aligned-muscle.fasta
   3. Killed due to mac not being able to scan for malware 