# Notebook Log

### Maximum Likelihood Homework (2024-03-21)
Script information contained in [maximum_likelihood_HW.md](scripts/maximum_likelihood_HW.md). 

Instructions:
1. Choose a maximum likelihood method that you like the best on your project dataset (it does not have to be RAxML or IQ-Tree, but you should read the paper and tutorial of whichever method you choose)
   1. Don't forget to include in your reproducible script a short description of the chosen algorithm, its assumptions and limitations (see the software cheatsheet Links to an external site.)
2. Make sure to keep notes in your reproducible script and keep the most updated version on github (it is important to push your work to github since this allows me to check what you are doing and offer suggestions)
3. Submit the link to your github commit in canvas
4. Note: did not generate real output, but instead detailed the commands I would use, as I still need to clean up earlier data to get a good msa file. 


### Distance & Parsimony Homework
Script information detailed in [distance_parsimony_HW.md](scripts/distance_parsimony_HW.md). 

Instructions: 
1. Estimate a distance-based tree and a parsimony-based tree for bacterial isolate data using the `ape` and `phangorn` R packages.
  - Don't forget to include in your reproducible script a short description of the chosen algorithm, its assumptions and limitations (see the [software cheatsheet](https://github.com/crsl4/phylogenetics-class/blob/master/exercises/software-cheatsheet.md))
2. Keep notes in your reproducible script and keep the most updated version on github (it is important to push your work to github since this allows me to check what you are doing and offer suggestions)
3. Submit the link to the github commit in canvas
4. Note: I tried to provide the programs the berryiisolatesall.xmfa from the Mauve alignment, but this generated an error and did not run to completion. I'm still troubleshooting the use of MUSCLE and ClustalW to generate an alignment, so the hypothetical entry of my own data is detailed in the file. 

### Aligning Data Homework (2024-02-20)
* Ran progressiveMauve to align 2022_Eberryi_WGSeqPconsensusfnas folder sequences as detailed in [aligning_DNA.md](scripts/aligning_DNA.md) scripts file. Initial alignment is to explore what is present among these bacterial isolates and determine if further analysis is best spent on *Vibrio fischeri* strain-specific differences among the isolates or a broader *Vibrio* multispecies comparison, depending on diversity within the sequences. 

### Adding Data Homework (2024-02-12)
* Uploaded datasets to data folder
  * 2024_Vfischeri_genbankref_files folder contains reference *V. fischeri* genomes downloaded from Genbank. 3 strains were downloaded (ES114, MJ11, and SR5) with a minimum of chromosome 1 and chromosome 2 of the genome assembled. 
  * 2024_Vfischeri_MillerAssemblies folder contains the flye assemblies for 12 *V. fischeri* strains used in the squid-vibrio model system for the traditional squid host *Euprymna scolopes* as downloaded on 2024-02-12. The quality control and processing for these assemblies is detailed in the [data/ReadME.md](data/README.md) file. 
  * 2022_Eberryi_WGSeq_consensusfnas folder contains nanopore whole genome sequencing fasta files for 11 bacterial isolates processed by me from *Euprymna berryi* squid sources in 2022. Plasmidsaurus processing is detailed in the [data/ReadME.md](data/README.md) file. 
* Notes on data upload 
  * The 2022 E. berryi isolate sequences are highly fragmented and unable to circularize as chromosomes. I aim to resequence these bacterial isolates within the month and reprocess the raw reads to generate higher quality genomic data. 
  * The 2024 Miller assemblies are in triplicate at the moment, to be further processed in TriCycler to synthesize the three assemblies for each strain. 