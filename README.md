# Swarming_project

This is a repository with bioinformatic tools used for a project describing changes in microbial composition and abundances
in honey bees during swarming preparation.

Below, please find information about the bioinformatic steps we have undertaken to analyse our data.

We started with R1 and R2 fastq files outputted by a sequencing machine.
Next, we used our custom scripts:

## [MultiSPLIT](https://github.com/MikeCollasa/Swarming_project/blob/main/MultiSplit.py):
- Splits reads of marker genes into separate subdirectories,
- Passes only reads with tags expected for a given sample.

## [LSD](https://github.com/MikeCollasa/Swarming_project/blob/main/LSD.py):
- Analyses each library (sample) separately,
- Merges R1 and R2 reads, passes only high-quality reads,
- Converts fastq to fasta files,
- Dereplicates and denoises samples,
- Assigns taxonomy affiliation to reads,
- Produces zOTU/OTU tables used by other scripts.

## [Quack](https://github.com/MikeCollasa/Swarming_project/blob/main/QUACK.py)
Uses as an input:
- 16S zOTU table (produced by LSD),
- otus.tax (produced by LSD),
- list of blanks,
- list of spikeins,
- Decontaminates 16S data based on negative controls,
Creates:
- Table with zOTUs assigned as: symbiont or contaminants,
- Decontaminated zOTU and OTU tables,
- Statistics table.
