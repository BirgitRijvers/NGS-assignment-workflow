# NGS assignment workflow
Repository of the NGS workflow building assignment of Yke Stockman, Isabelle Sewsahai, Mathijs Schouten en Birgit Rijvers.

## Goal
The goal of this Galaxy workflow is to perform a hybrid assembly of Nanopore and paired Illumina sequence data, identify the species and detect antibiotic resistance genes. The data quality is also checked and visualized, and the raw reads are trimmed. 

## Workflow 
Find the .ga file of the workflow in the files list, or click [here](Workflow_NGS_assignment_YS_IS_MS_BR.ga). Upload this file to Galaxy.

Our workflow includes:
* fastp for raw reads QC and trimming
* MultiQC for summarizing and visualizing al quality reports of fastp
* Unicycler for creating assemblies with long and short read data
* Quast for QC of the assemblies
* Bandage image for visualizing the assemblies
* Busco for assessing the completeness of assemblies
* staramr to find resistance gene and plasmid sequences in assemblies
* Kraken2 for species identification of assemblies
* Prokka to annotate genes in assemblies
* Roary to generate a core gene alignment
* Phylogenetic reconstruction with RaXML to create phylogenetic tree
* Phandago to visualize pan/core genome and phylogenetic tree

## Input data
One fastq file is required with long reads sequenced with technology from Nanopore, two fastq files are required with short reads (forward and reverse). Upload the files individually (and not as collection) to Galaxy.

## Please note
All steps untill phylogenetic reconstruction with RaXML are included in the galaxy workflow (.ga file), but additional steps are required to visualize the results with Phandago:
1. Download the gene_presence_absence.csv output file of Roary and save it locally.
2. Download the Result.nhx output file of Phylogenetic reconstruction with RaXML and save it locally.
3. Rename the Result.nhx file with the .tree extension.
4. Drag and drop the files on https://jameshadfield.github.io/phandango/#/.

## Flowchart
![image](https://user-images.githubusercontent.com/126883391/228933911-d5149fe1-ba0b-4c3a-80da-7538edbdbb71.png)
