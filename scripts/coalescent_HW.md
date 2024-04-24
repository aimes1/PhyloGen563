# Coalescent - Astral 

Astral is a Java program for estimating a species tree given a set of unrooted gene trees. A strength of the program is the statistical consistency under the multi-species coalescent model. The software does assume the presence of some gene tree discordance and will automatically remove branches with the lowest branch support. 

I will not be using Astral on my dataset, but will reflect below the tutorial and toy data set as provided on the ASTRAL github tutorial page found [here](https://github.com/smirarab/ASTRAL/blob/master/astral-tutorial.md)

## ASTRAL Script 

1. Download ASTRAL 
   A. Download the linked [zip file](https://github.com/smirarab/ASTRAL/raw/master/Astral.5.7.8.zip) and extract the contents into the Software folder for the project. 
   B. Note: Java must be installed in order for ASTRAL to run. 
   C. To test the installation, within the directory where ASTRAL has been put, run the command: 
```shell
 java -jar astral.5.7.8.jar -i test_data/song_primates.424.gene.tre
```
2. Run ASTRAL on the sample mammalian dataset 
   A. Run the command
```shell
java -jar astral.5.7.8.jar -i test_data/song_mammals.424.gene.tre
java -Djava.library.path=./lib/ -jar astralmp.5.7.8.jar -i test_data/song_mammals.424.gene.tre
```
   B. The results will be put in a standard output. To save the results, use the -o option: 
```shell
java -jar astral.5.7.8.jar -i test_data/song_mammals.424.gene.tre -o test_data/song_mammals.tre
java -Djava.library.path=./lib/ -jar astralmp.5.7.8.jar -i test_data/song_mammals.424.gene.tre -o test_data/song_mammals.tre
```
Note: the output is an unrooted tree.
3. To view ASTRAL results, open the Newick format tree output in [FigTree](http://tree.bio.ed.ac.uk/software/figtree/)