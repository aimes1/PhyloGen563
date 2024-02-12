# Data Description

# Vfischeri_genomes
* 2024_Vfischeri_genbankref_files: folder contains the genbank (.gb) files for V. fischeri strains ES114, MJ11, and SR5 as downloaded on 2024-02-12. 
* 2024_Vfischeri_MillerAssemblies: folder contains the flye assemblies in triplicate for 12 *V. fischeri* strains commonly used in the Mandel lab for study in the squid-vibrio system. The DNA extraction and sequencing was performed years prior by lab member Katherine Bultman, and current processing of the raw read fasta files has been performed in 2024 by Delaney Miller as detailed in [bacterialgenome_assemblyworkflow.md](bacterialgenome_assemblyworkflow.md).
* 2022_Eberryi_WGSeq_consensusfnas: folder contains the consensus FASTA file sequences for 11 bacterial isolates I processed from *Euprymna berryi* squid in 2022. This exact isolation is detailed in my private lab notebook for the Mandel lab. These are whole genome sequences processed by Plasmidsaurus, as detailed below:
  * Sample sequencing: 
    * Oxford Nanopore
    * Construct an amplification-free long-read sequencing library using the newest v14 library prep chemistry, including minimal fragmentation of the genomic input DNA in a sequence independent-manner.
    * Sequence the library primer-free using the most accurate R10.4.1 flow cells (raw data is >99% accurate and is delivered in .fastq format).
    * Produce a high-accuracy genome assembly (delivered in .fasta format) with Flye for assembly and medaka for polishing.
    * Produce a set of bacterial genome annotations with Bakta (delivered in various file formats).
  * Assembly generation
    * Remove the bottom 5% worst fastq reads via Filtlong v0.2.1 (default parameters)
    * Downsample the reads to 250 Mb via Filtlong to create a rough sketch of the assembly with Miniasm v0.3
    * Using information acquired from the Miniasm assembly, re-downsample the reads to ~100x coverage (do nothing if there isn't at least 100x coverage) with heavy weight applied to removing low quality reads (helps small plasmids stick around)
    * Run a Flye v2.9.1 assembly with parameters selected for high quality ONT reads
    * Polish Flye assembly via Medaka v1.8.0 using the reads generated in step 3
    * Run several analyses:
      * annotation: Bakta v1.6.1
      * contig analysis: Bandage v0.8.1
      * genome completeness and contamination: CheckM v1.2.2
      * species / plasmid identification: Mash v2.3 against RefSeq genomes+plasmids, Sourmash v4.6.1 against GenBank, CheckM v1.2.2