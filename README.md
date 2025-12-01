## Food_Species_Identification 🐟🐟

**16S rRNA Species Identification from Fish Muscle Metagenome (SRA SRR33819363)** 🐠🐠

This repository contains the code and analysis used to identify bacterial species from a 16S rRNA fasta file obtained from fish muscle samples infected with *Hafnia* (luxS mutant).  
Raw sequences were downloaded directly from NCBI SRA:

- **Run:** SRR33819363  
- **Study:** PRJNA1271149  
- **Sample:** SAMN48856362  
- **Source:** Metagenome of fish muscle microbiome after infection  
- **Data:** 16S V3–V4 sequences in fasta format  

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Project Overview: 🥼🥼

This project performs 16S rRNA species identification in fish muscle metagenomes using simple Python scripts and publicly available bioinformatics tools. The dataset analyzed (SRA accession: SRX29040611) contains paired-end 16S rRNA reads from fish muscles infected with Hafnia Z11::luxS. The main goal is to identify different bacterial populations present in the sample and visualize GC content variation, which can reflect species heterogeneity or minor sequence variants.

The project demonstrates:

**1.** Parsing and inspecting large FASTA files using Biopython

**2.** Computing sequence statistics such as length and GC content

**3.** Visualizing GC content distributions with Matplotlib and Seaborn

**4.** Subsetting reads corresponding to distinct GC content peaks

**5.** Preparing sequences for BLAST-based taxonomic assignment

This workflow serves as an educational example of metagenomic sequence analysis using Python.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

##  Workflow: 👨‍🔬👨‍🔬

**1.** Load and inspect sequences:
       - Use Biopython’s SeqIO to parse the downloaded FASTA file containing all reads.
       - Count the total number of reads/spots and confirm sequence lengths (~300 nt, covering V3-V4 regions).

**2.** Quality check / mini FastQC:
       - Verify that all reads have consistent length, indicating no truncation or trimming artifacts.
       - Compute GC content for each sequence to assess compositional variation.

**3.** Visualize GC content:
       - Plot GC content distribution for all reads.
       - Identify multiple peaks, suggesting the presence of distinct bacterial populations or minor sequence variants.
       - Zoom in on the 40–60% GC range for detailed inspection.

**4.** Subset reads by GC content peaks:
       - Divide reads into three peaks based on GC content:
                    Peak 1: <46% GC
                    Peak 2: 49–51% GC
                    Peak 3: >51% GC
       - Randomly select a subset of 5 sequences from each peak for downstream BLAST analysis.

**5.** Prepare sequences for BLAST
       - Save subsets as FASTA files (peak_1_random5.fasta, etc.).
       - These sequences can be uploaded to NCBI BLAST or used in local BLAST to identify species.

**6.** Interpret results
       - GC content peaks correspond to distinct bacterial taxa.
       - Minor peaks may reflect sequence variants, PCR biases, or chimeras.
       - BLAST results allow assignment of reads to specific bacterial species, such as Myroides or Morganella. 

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Python Implementation: 🐍🐍

This project is implemented in Python and uses standard bioinformatics libraries to analyze 16S sequences:
•	**BioPython**: For parsing fasta files, calculating GC content, and handling sequence data. :
•	**Matplotlib / Seaborn**: For visualizing GC content, BLAST results, or sequence distributions.
    Why Python: Python provides a simple, reproducible way to process sequences, calculate statistics, and generate plots for easy interpretation of metagenomic data.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Key Findings: 🧪🧪

**1.** Myroides detected:
       Two extracted sequence peaks (Peak 1 & Peak 2) matched:
            •	Myroides sp. strain WCUF-1Myr (GenBank: MZ067773)
            •	Myroides profundi
            •	Myroides odoratimimus
I      Identity ranged 98–100%, confirming the presence of a Myroides organism.

**2.** Morganella detected. A third peak matched:
            •	Morganella sp. strain A30
            •	Morganella sp. a111-140b
            This genus belongs to **Enterobacteriaceae**, unrelated to Myroides, confirming a mixed-species metagenome.
            
**3.** GC Content:
       - GC content was similar across sequences, consistent with 16S structural constraints.
       - GC% alone cannot determine species identity (BLAST was used for taxonomic assignment).

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Interpretation & GC Content Analysis: ✔️✔️

The sequences analyzed in this project were extracted from a fish muscle metagenome experimentally infected with Hafnia (Z11::luxS). BLAST analysis of representative peaks identified primarily Myroides and Morganella, while Hafnia itself was not detected in the selected sequences.

## Why Hafnia may not appear prominently - Several factors explain why Hafnia sequences were not dominant:

•	**16S rRNA amplification bias**: Primers targeting the V3–V4 region may preferentially amplify certain taxa. Hafnia 16S regions may contain mismatches, reducing its representation.
•	**Relative abundance**: Even after infection, Hafnia may have been present at low abundance compared to naturally occurring bacteria like Myroides or Morganella.
•	**luxS mutation effects**: The luxS knockout may reduce Hafnia growth or quorum-sensing–mediated colonization.
•	**Sample preparation bias**: Freezing and DNA extraction can favor robust bacteria like Myroides, leading to higher recovery.
•	**Limited sequence subset analyzed**: Only a few representative peaks were examined; Hafnia may still exist in the full dataset.

Conclusion: The results reflect the metagenomic nature of the sample. While the fish were infected with Hafnia, the predominant bacterial DNA recovered corresponds to Myroides and Morganella. This highlights both the complexity of the fish muscle microbiome and the limitations of targeted 16S analysis for low-abundance pathogens.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Why the GC content peaks matter 📊📊

The analysis identified distinct GC content peaks across the extracted sequences. These peaks provide evidence for multiple species in the sample.
Technical artifacts considered:

•	**PCR bias**: Can skew relative abundances but does not create new GC content peaks.
•	**Chimeras**: Rare for sequences of identical length; unlikely to explain distinct peaks.
•	**Truncation or trimming artifacts**: Would produce variable read lengths. All sequences here are uniform, so truncation is not responsible.

## Biological explanation:

•	Different species (or strains) naturally have slightly different GC content in their 16S rRNA sequences.
•	Even closely related species can produce distinct GC content peaks.
•	In your dataset, each GC peak corresponds to a distinct taxon identified by BLAST (Myroides, Morganella, etc.), indicating true biological variation rather than technical artifacts.

## Summary:

•	GC content peaks align with distinct taxa.
•	Sequence lengths are consistent, reducing the likelihood of artifacts.
•	PCR bias or chimeras alone cannot explain the observed peaks.
•	This supports the conclusion that multiple bacterial species are present in the fish muscle metagenome sample.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## NOTES: 📔📔

- ## The project is fully Python-based and uses standard libraries: Biopython, Pandas, Matplotlib, and Seaborn.

- ## No trimming or preprocessing was performed; the analysis relies on 16S rRNA reads downloaded directly from NCBI.

- ## This project is intended for educational purposes only and provides a simple, reproducible workflow for small-scale metagenomic analyses. It is by no means a research standard

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 

                                                                                              #END OF PROJECT# 
