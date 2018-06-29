# How to Bioinformatics (In Development)

Contained within this repo is some information about the Djordjevic Genomics Lab, what we do and why we think its important. It also contains some links to videos and other resources that should help in your quest toward Bioinformatic prowess!

I hope you find it useful...


# Background and Context


We undertake microbial genetic epidemiological investigations that aim to elucidate the genetic characteristics and phylogenetic structure of microbial populations from agricultural, clinical and environmental settings. We have short-read sequence data on around a thousand or so E. coli isolates, and this number is growing fast. We also are expanding into other microbial Genera, such as Klebsiella and Proteus.


Such investigations are important because it is increasingly recognised that animal, human and environmental microbiota are in a state of flux - many mechanisms allow for the transfer of bacteria and other microbes between these different contexts, and because of this, human, animal and evironmental health are intrinsically linked. This concept is referred as the One Health Initiative; a framework or lens through which one can approach investigations that involve the study, treatment and prevention of infectious disease. According to the One Health Initiative's webpage:



> *The One Health Initiative is a movement to forge co-equal, all inclusive collaborations between physicians, osteopathic physicians,
> veterinarians, dentists, nurses and other scientific-health and environmentally related disciplines.*

![alt text](https://github.com/maxlcummins/Bioinformatics/blob/master/One%20Health%20Logo.png "Image sourced from Lilongwe Wildlife Trust")


For more information on One Health see the following links:
* [One Health Initiative](http://www.onehealthinitiative.com/)
* [Antimicrobial resistance: a One Health perspective](https://academic.oup.com/trstmh/article/111/6/255/4554993)

# Our Goal and Our Approach

Essentially, the aim of the game is to characterise the genetic contents of the strains under study, as well as use various approaches to classify them into phylogenetic groups that reflect their relatedness. We can then compare these attributes of bacteria from different environments to identify potential reservoirs of antimicrobial resistance (AMR), virulence-associated genes (VAGs) and potential zoonotic pathogens.

Our current workhorse for genotyping is a piece of software called [ARIBA](https://github.com/sanger-pathogens/ariba). This allows the mapping of short-read sequence data to a file of reference sequences - typically these references sequences are involved in AMR, experimentally or epidemiologically associated with disease (VAGs), or those that encode, or are associated, with mobile DNA elements that play an important role in the spread of such genes. We also use ARIBA, in combination with some custom scripts, to perform Multi-locus sequence typing, e-serotyping and phylogroup classification. These are various classification schemes we can use to assess the relatedness of different strains of E. coli. More on ARIBA later...

After generating the above data, we typically want to generate some sort of phylogenetic tree that allows a visualisation of relatedness of the samples under study. Typically our approaches to this involve use of Phylosift or software that allows detection and comparison of single nucleotide polymorphisms (SNPS), the latter of which detects mutations that have accumulated within the core genome, over time, of the samples under investigation, thus inferring how related they may be. Subsequently we can generate the tree using FastTree2, and visualise the tree in iTOL, figtree, or more recently, in R (with a bit of help from ggtree and friends). We then can combine this tree with figures that visualise the genotype of each sample in the tree.

# Skills Required

## Bash and the terminal

The first order of business, in regard to preparing for undertaking *in silico* analysis of our DNA sequence data, should be to familiarise yourself with the terminal, aka the command line. Working in the terminal allows us a great deal more flexibility than can be offered through the use of a graphical user interface (GUI), and in fact much of the software used in bioinformatics is not available in the form of a GUI and/or do not lend themself to the high-throughput analysis that often we are interested in undertaking. En-masse manipulations of file names and/or contents and bulk processing of DNA analysis pipelines are two major reasons that the terminal serves us as a useful tool.

If you're running MacOS or Linux you will have an in-built terminal, while if you're running Windows I would suggest downloading MobaXterm. Note that while [MobaXterm](https://mobaxterm.mobatek.net/) users have the luxury of an inbuilt file transfer system, allowing you to natively upload or download from a computer cluster, Mac and Linux users will have to download a FTP client such as [FileZilla](https://filezilla-project.org/).



Here is a link to a video that will get you started on the command line and teach you some important basics of navigating and beginning to utilise the command line.

[Joe Collins - Intro to linux/bash](https://www.youtube.com/watch?v=oxuRxtrO2Ag)

## Python and/or R

Having a capacity to write scripts or utilise pre-existing packages in Python and/or R greatly benefits us! Both languages are very popular in (and outside of) the bioinformatics sphere, and online communities that serve to help troubleshoot disfunctional scripts and suggest programming solutions to data problems, such as [Stack Overflow](www.stackoverflow.com/), are very helpful in our thirst for programming knowledge and know-how.


Resources for learning Python and/or R:
* [Datacamp](https://www.datacamp.com)
* [Coursera](https://www.coursera.org/)
* [EdX](https://www.edx.org/)


At the very least, basic knowledge of Python is required for the use of ARIBA, the scripts we use to process the outcoming data, and other pieces of software we use to analyse our sequences of interest.

Currently, our pipelines for the generation of heatmaps and other figures utilise the R programming language.


# Resources


# References and Acknowledgements
Some images have been scavenged from the internet to give this page some flare! If you are the owner of any images contained herein and would like me to remove them, please ask and I will do so. I have attempted, wherever possible, to give credit to the owners and authors of borrowed content.
* One Health Image attributed to [LiLongWe Wildlife Trust](https://www.lilongwewildlife.org/clinical-project-one-health/)

