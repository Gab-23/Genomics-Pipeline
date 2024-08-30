## BRIEF PROGRAM OUTLINE

The program excecutes a complete pipeline of genomics analysis of a family 
The aim is variant prioritization and potential discovery of mendellian diseases

All the provided files are stored in a specific folder inside a server. The starting materials include:

- The **original FASTQ files**, coming from a exome sequencing experiment
- The **reference genome** and its indexing
- The **target sequences**, according to the exons in the reference genome

The main steps excecuted by this program, according to the usual pipeline will be:

- **BAM files generation**
  - Reads, coming from a sequencing procedure are aligned against an already indexed reference genome
  - BAM files are obtained

- **Quality Control step**
  - FASTQC to assess the quality of the reads
  - BAMQC to assess the quality of the alignment
  - MULTIQC to obtain a unique summary

- **Variant Calling**
  - Using the freebayes tools a VCF file containing called variants is generated
  - The file is then filtrated in order to obtain only the variants with the right pattern of transmission
  - The file is intersected with respect to the target regions of the reference exome
  - The file is then sorted to keep a coherent ordering of the genotypes
 
- **BG files generation**, for subsequent variant visualization on the UCSC Genome Browser

The **output** of the program will be a directory, named as the family number, containing **17 directories and 157 files** 

## HOW TO INITIALIZE THE PROGRAM


- The program will first ask for the target directory, where the output will be stored
  
  NOTE: If the specified directory is NOT found, the program will create it
  
- By further editing the program, other path-containing variables may be changed  
- The program can hold up to 10 arguments, since the project asked for a 10 families analysis
- If you want to compute less than 10 arguments, mind typing STOP as a last argument, an error is raised otherwise

- Arguments MUST be composed in this way: **<family_number> _ <disease_model>** 
  
  NOTE: Disease models either are Autosomic Recessive (AR), or Autosomic Dominant (AD)
  EXAMPLE: 452_AR, 468_AD ...
