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

Having a capacity to write scripts or utilise pre-existing packages in Python and/or R greatly benefits us! Both languages are very popular in (and outside of) the bioinformatics sphere, and online communities that serve to help troubleshoot disfunctional scripts and suggest programming solutions to data problems, such as [Stack Overflow](www.stackoverflow.com/), are very helpful in our thirst for programming skills and know-how.


Resources for learning Python and/or R:
* [Datacamp](https://www.datacamp.com)
* [Coursera](https://www.coursera.org/)
* [EdX](https://www.edx.org/)


At the very least, basic knowledge of Python is required for the use of ARIBA, the scripts we use to process the outcoming data, and other pieces of software we use to analyse our sequences of interest.

Currently, our pipelines for the generation of heatmaps and other figures utilise the R programming language.

# Software

Below is a list of software that we frequently use for genotyping (characterising genetic content), annotating regions of DNA and various other applications

## Assemblers

### A5

### Shovill

### Unicycler

### FALCON

## Sequence Aligners

### ARIBA

As mentioned, [ARIBA](https://github.com/sanger-pathogens/ariba) is a major tool in our genome analysis pipeline. ARIBA stands for Antimicrobial Resistance Identification By Assembly, and while its name implies it may only be used for analysis of antimicrobial resistance genes it is not limited therein. ARIBA can be used to check for the presence of VAGs, plasmid-associated genes, custom gene databases and can even perform multi-locus sequence typing, serotyping and phylogrouping can be performed, though for the later two functionalities some custom scripts available at [ARIBAlord](https://github.com/maxlcummins/ARIBAlord) are recommended.

### BLASTn

BLASTn is a sequence aligner that has been around since 1990. There are [command-line](https://www.ncbi.nlm.nih.gov/books/NBK279680/) and [web-based](https://blast.ncbi.nlm.nih.gov/Blast.cgi?PAGE_TYPE=BlastSearch) applications available, and depending on what kind of analysis you are interested in doing you might use either. Prior to running BLASTn you must first assemble your sequences using one of the tools mentioned in the assembly section above.

#### Genotyping
BLASTn is useful for genotyping, however it is unsuitable for determining the carriage of IS elements and other genetic elements that may have repeat regions or sequences above a certain length which appear in the genome of a sample in multiple locations, as these entities often are not assembled properly by short-read assemblers. On that note, while ARIBA runs on raw reads, BLAST requires assembled DNA sequence. To determine carriage rates of such elements a read-mapping tool like ARIBA, ISfinder or SRST2 is preferred, though it may be useful to validate genotypic data generated using read-mapping approaches.

#### Genetic Epidemiology
The web-based BLASTn portal hosted by NCBI is a useful tool in searching for sequences of interest that have been deposited in the NCBI nucleotide database by other researchers around the world. If you have a region of DNA that is of interest you can search to see if this sequence, or one similar to it, has been identified, and if so, where and when the sequence was isolated.

#### Annotation
BLASTn can be used to determine the genetic context of genes of interest. It is important to know whether AMR and VAGs are carried chromosomally or on a plasmid, for example, and we are usually also interested in how such elements are arranged. BLASTn is best employed with long-read sequence data, which better allows the determination of genetic arrangement and context.

### 



### SRST2



##


# Job Submission and data processing

## ARIBA

To submit an ARIBA job you will need access to first download and prepare your databases of interest. The databases can be found below, though it is recommended to undertake these steps using ARIBA where possible. Information on how to do this can be found on the [ARIBA github wiki](https://github.com/sanger-pathogens/ariba). For custom databases, you will need to run ARIBA's prepareref step with the option --all_coding no. All supported databases should be run without this option.

ARIBA jobs require relatively large computing resources, particularly if you are screening many samples for hundreds or thousands of genes. Therefore a PBS job submission script can be used for the UTS HPC, which you can access [here](https://github.com/maxlcummins/Bioinformatics/blob/master/new_ariba.qsub). Clone the Bioinformatics repository to your home directory and you should be able to run the following job submission without any issue.

Note: it is important that the paths in "READ_PATH" and "REF" are pathed to as if you are accessing them from your home directory, or the job will fail. Also, the "OUT" designation is required to avoid overwriting your read files and should be informative of the database being used.

```
qsub -v READ_PATH=<your_path_to_reads_here>,REF=<your_path_to_ARIBA_prepared_DB_here>,OUT=<informative_append_here> ~/qsub/new_ariba.qsub
```

Screen for your genes of interest. We have set up support for phylogrouping and serotyping, but it is also recommended to screen for resistance genes (via Resfinder), virulence genes (via Virulencefinder), plasmid genes (via Plasmidfinder), Custom genes (via E_coli_customDB), and MLST (via ARIBAs MLST pipeline \[we recommend the Achtman scheme\]).

Once all of your ARIBA output is prepared (this may take some time), we recommend using ARIBAlord to combine the resulting data into a spreadsheet with which you can summarise your data for further analysis. Check the [github page](https://github.com/maxlcummins/ARIBAlord) for information on how to use it.

## BLASTn

BLAST is a very useful piece of software which we can use to try to answer a number of different research questions. Primarily, this section will focus on using BLAST on the command line to identify genes of interest and to retreive the scaffolds on which they are identified as well as the coordinates where they are specifically located. The latter is particularly useful when it comes to annotation of regions of DNA, particularly when annotating long-read sequence assemblies.

BLAST is natively accessible to all users on the UTS HPC, so you should not need to install anything to use it. You will, however, need a qsub file for job submission, particularly if you are running BLAST with a large number of genes/samples. If you clone this github you can use the one called blast.qsub contained within the qsub folder, however first be sure to edit the qsub file using vim and replace any appropriate fields flagged with \*\*Your_student_number_here\*\* or \*\*Your_email_here\*\*.

Upon downloading your database/s of interest, the first step required is to prepare your BLASTn database for use. You can use this command, substituting in the name of your database file. Note your database file may end in .fasta, .fa or .fsa - make sure you get the name right!


```
makeblastdb -in ***DB_name_here.fa*** -dbtype nucl
```

Once this is done you can run BLAST. Note that BLAST can only be run on assemblies, not on read files. You can use the following command, but be sure to change the bits flagged between three asterisks; "path_to_your_genomes", "path_to_BLAST_DB" and "Informative_append". The asterisks should be deleted, however be sure not to delete the asterisk in "\*.fasta"

```
for genome in `ls ***path_to_your_genomes***/*.fasta`; do qsub -v DB=***path_To_BLAST_DB***,INPUT=${input_genome},OUTPUT=${input_genome}.***Informative_append***.csv ./blast.qsub; done
```

The job should finish quickly. Repeat the above two steps for all databases you wish to screen your samples for (typically just Resfinder, Virulencefinder, Plasmidfinder and a Custom database). Be sure to change the "informative append" such that i) it is different between job runs so that the output files for one screen aren't overwritten by the output files from the subsequent screen, and ii) that you know which file is which.

All the blast output files will land in the folder containing your genome assemblies, ie the path you designated in
\`ls \*\*\*path_to_your_genomes\*\*\*/\*.fasta\`. Navigate to this folder.

Each BLAST output file consists of a delimited file. We want to concatenate them together for ease of processing, but first we must provide a sample ID for each of the BLAST hits detected. This command will do the trick:

```for f in *.csv; do paste $f <(yes $f | head -n $(cat $f | wc -l)) > $f.new; done```

Next, we can concatenate the BLAST output files into a single file we can work with more easily. Use this command to do so, but be sure to alter the name of the resulting output file to something informative that reflects the samples under investigation, the date, and any other important info.

``` cat *.new > ***informative_name***.txt```

Now all of your BLAST data will be in a single file. From here, we recommend filtering of your results using [BLASTlord](https://github.com/maxlcummins/BLASTlord/). BLAST data can be quite noisy, particularly because the settings we run it on are relatively unstringent. BLASTlord allows you to set cutoffs for nucleotide ID and coverage and will filter the hits appropriately, providing you with a table of hits which met the criteria and those that did not. While it originally was used for creating tables that summarised the genes present and absent in a sample, this purpose has been largely superceded by ARIBAlord and therefore using BLASTlord for this purpose is at this time not recommended. At some point I plan to update BLASTlord such that it can be used for this purpose again, but for the time being this role is unlikely to work very well without being used with a purpose built BLAST database being used for screening.

To use BLASTlord, download it as a zip file and open the file appended in '.R' in R studio.





# Resources

## Databases

Nucleotide databases can be used in combination with BLAST and/or read mapping tools to genotype samples. There are many publicly available databases that may be of use. Typically, we in the Djordjevic Lab use the following:

### Center for Genomic Epidemiology

While the links below are for the most common databases we use, there are many others provided at the centre for genomic epidemiology.
Click [here](https://cge.cbs.dtu.dk/services/) for a link to see what is on offer, and [here]( to navigate to a downloadable copy a database through bitbucket. To do so click the downloads tab on the left hand side of the page that will pop up after clicking the database of interest and then click 'Download repository'.
* [Virulencefinder](https://bitbucket.org/genomicepidemiology/virulencefinder_db/get/0dd7f3105233.zip)
* [Resfinder](https://bitbucket.org/genomicepidemiology/resfinder_db/get/a409b844aa2c.zip)
* [Plasmidfinder](https://bitbucket.org/genomicepidemiology/plasmidfinder_db/get/591948ee56dc.zip)

### ISfinder

Note that [this](https://isfinder.biotoul.fr/) database can unfortunately not be downloaded, but sequences of interest can be found via searching the online database. Click 'Tools' and then 'Search' to search for a particular IS, or you can use the BLAST function
to search for IS elements in a DNA sequence of interest.

### Custom Database

We also use a custom database which is available [here](https://github.com/maxlcummins/E_coli_customDB)

### Other Databases:
* CARD
* VFDB





# References and Acknowledgements
Some images have been scavenged from the internet to give this page some flare! If you are the owner of any images contained herein and would like me to remove them, please ask and I will do so. I have attempted, wherever possible, to give credit to the owners and authors of borrowed content.
* One Health Image attributed to [LiLongWe Wildlife Trust](https://www.lilongwewildlife.org/clinical-project-one-health/)

