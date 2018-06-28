# How to Bioinformatics

Contained within this repo is some information about the Djordjevic Genomics Lab, what we do and why we think its important. It also contains some links to videos and other resources that should help in your quest toward Bioinformatic prowess!

I hope you find it useful...


# Background and Context


Currently we undertake microbial genetic epidemiological investigations that aim to elucidate the genetic characteristics and phylogenetic structure of microbial populations from agricultural, clinical and environmental settings. We have short-read sequence data on around a thousand or so E. coli isolates, and this number is growing fast. We also are expanding into other microbial Genera, such as Klebsiella and Proteus.


Such investigations are important because it is increasingly recognised that animal, human and environmental microbiota are in a state of flux - many mechanisms allow for the transfer of bacteria and other microbes between these different contexts, and because of this, human, animal and evironmental health are intrinsically linked. This concept is referred as the One Health Initiative; a framework or lens through which one can approach investigations that involve the study, treatment and prevention of infectious disease. According to the One Health Initiative's webpage:



> *The One Health Initiative is a movement to forge co-equal, all inclusive collaborations between physicians, osteopathic physicians,
> veterinarians, dentists, nurses and other scientific-health and environmentally related disciplines.*


For more information on One Health see the following links:
* [One Health Initiative](http://www.onehealthinitiative.com/)
* [Antimicrobial resistance: a One Health perspective](https://academic.oup.com/trstmh/article/111/6/255/4554993)

# The Goal 

Essentially, the aim of the game is to characterise the genetic contents of the strains understudy, as well as use various approaches to classifying them into phylogenetic groups that reflect their phylogenetic relatedness.

The current workhorse for our genotyping is a piece of software called ARIBA. This allows the mapping of short-read sequence data to a file of reference sequences - typically these references sequences are involved in antimicrobial resistance, experimentally or epidemiologically associated with disease, or those that encode, or are associated, with mobile DNA elements that play an important role in the spread of such genes. We also use ARIBA, in combination with some custom scripts, to perform Multi-locus sequence typing, e-serotyping and phylogroup classification. These are various classification schemes we can use to assess the relatedness of different strains of E. coli. More on ARIBA later...

After generating the above data, we typically want to generate some a phylogenetic tree that allows a visualisation of relatedness of the samples under study. Typically our approaches to this involve use of Phylosift or software that allows detection and comparison of single nucleotide polymorphisms (SNPS), which you can think of as the extent to which mutations have accumulated within the core genome, over time, of the samples under investigation

# Resources


