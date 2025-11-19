# Variant-Calling-Pipeline-for-Human-Genome-Analysis-Using-GSE131027
Variant Calling Pipeline for Human Genome Analysis Using GSE131027
# 🧬 GATK Variant Calling Pipeline (GSE131027 Subset)

This repository contains a comprehensive **Jupyter Notebook** pipeline that demonstrates the key steps of the **Genome Analysis Toolkit (GATK) Best Practices** workflow for identifying **Single Nucleotide Polymorphisms (SNPs)** and **Indels** in human sequencing data.

The workflow uses a small, publicly available RNA-Seq sample (**SRR8416805** from GSE131027) and a subset of the reference genome (Chromosome 22) for rapid execution, focusing on the foundational GATK steps: indexing, sorting, marking duplicates, and variant calling.

## 🚀 Key Features

* **GATK Best Practices Implementation:** Executes the critical steps of the GATK workflow, including HaplotypeCaller.
* **Targeted Analysis:** Uses a small read accession (**SRR8416805**) and a reduced reference (**Human Chromosome 22**) for efficient demonstration and learning.
* **Toolchain Setup:** Automatically installs necessary bioinformatics tools: **sra-toolkit**, **Picard**, **GATK4**, and **BWA**.
* **Preprocessing & QC:** Covers essential alignment file preparation steps:
    1.  **Alignment** (BWA-MEM)
    2.  **Sorting and Indexing** (samtools/Picard)
    3.  **Read Group Tagging** (Picard)
    4.  **Marking Duplicates** (Picard)
    5.  **Base Quality Score Recalibration (BQSR)** (GATK)
* **Variant Calling:** Executes **GATK HaplotypeCaller** to produce a final Variant Call Format (**VCF**) file.

---

## 🔬 Workflow Steps

The notebook is structured into the following executable steps:

1.  **Setup and Installation:** Installs BWA, GATK4, Picard, and the SRA Toolkit.
2.  **Data Download:** Fetches and converts the **SRR8416805** reads to paired-end FASTQ.
3.  **Reference Preparation:** Downloads the FASTA file for **Human Chromosome 22** (GRCh38) and creates BWA/GATK indices.
4.  **Alignment (BWA-MEM):** Aligns reads and converts SAM to BAM format.
5.  **Picard Preprocessing:** Adds Read Groups, sorts the BAM file, and marks PCR duplicates.
6.  **GATK Base Recalibration (BQSR):** Builds the recalibration model (BaseRecalibrator).
7.  **Final Variant Calling:** Executes **GATK HaplotypeCaller** to generate the final **VCF** output.

## ⚠️ Note on Data

The analysis uses **RNA-Seq data** (GSE131027) for a **variant calling** demonstration. While this allows for rapid execution of the pipeline, **germline variant calling is typically performed on Whole Genome (WGS) or Exome (WES) sequencing data** for optimal results.

---

## 🛠️ Prerequisites and Execution

### Requirements

To run this pipeline, you need a Python environment (like Google Colab) with access to a Linux terminal and the following tools (which the script installs):

* **`sra-toolkit`**
* **`BWA`**
* **`samtools`**
* **`Picard`**
* **`GATK4`**

### How to Run

1.  Open the **`Variant Calling Pipeline for Human Genome Analysis Using GSE131027.ipynb`** file in Google Colab or a Jupyter environment.
2.  Execute all cells sequentially.

---

## 📁 Output Files

The pipeline generates the following key files in the execution directory:

| Filename | Format | Description |
| :--- | :--- | :--- |
| `SRR8416805_aligned_sorted.bam` | BAM | Final alignment file used for variant calling. |
| `SRR8416805_marked_duplicates.txt` | Text | Metrics file from Picard MarkDuplicates. |
| `recal_data.table` | Text | Output of the BaseRecalibrator, containing the recalibration model. |
| `SRR8416805_variants.vcf` | VCF | **The final output:** Contains the list of identified SNPs and Indels. |
