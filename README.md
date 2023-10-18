# SMM-tset
try to build a pipeline for smm-seq
# Data processing and variant calling
Raw sequence reads were adapter- and quality-trimmed, aligned to human reference genome, realigned, and recalibrated on the basis of known indels as we described previously (7) except that deduplication step was omitted.
For variant calling, we developed a set of filters that were applied to each position in SMM-seq data. Only reads in proper pairs, with mapping quality not less than 60 and without secondary alignments, were taken in consideration. Positions in SMM-seq data were considered as qualified for variant calling if it is covered by UMI family containing not less than seven reads from each strand and this position is covered at least 20× in regular sequencing data. The qualified position was considered as a potential variant if all the reads within a given UMI family reported the same base at this position and this base was different from the corresponding reference genome. Next, to filter out germline variants, we checked if a found potential variant is in a list of SNPs of this DNA sample as well as in dbSNP. A list of sample specific germline SNPs was prepared by analysis of conventional sequencing data with Genome Analysis Toolkit (GATK) HaplotypeCaller. Last, a variant was rejected if one or more reads of a different UMI family in SMM data or in conventional data contained the same variant. SNV frequency was calculated as a ratio of the number of identified variants to the total number of qualified positions.
# step1. download data
Data may be accessed using the following link: https://dataview.ncbi.nlm.nih.gov/object/PRJNA758911.  
We use the SMM-seq raw data of ENU 50 sample and their control to build this pipeline.
Download data and tansfer data into fastq file.
# step2. nfcore pipline
nf-core
This pipline includ fastQC, trimgalore, mapping and sort.
Use hapllotype caller call germline mutation, also preformed BQSR, bamQC.
