# Clinical Variant Interpretation Workflow

This repository documents a reproducible workflow for identifying, annotating, and classifying clinically relevant genetic variants using public databases and standardized interpretation guidelines. The project simulates a clinical genomics pipeline, starting from variant selection and ending with ACMG/AMP-based pathogenicity classification.

<img width="3980" height="944" alt="image" src="https://github.com/user-attachments/assets/28d79046-2977-4040-8f6b-6601ecae49d1" />

---

## Repository Structure

assignment.xlsx – Structured evidence table containing variant details, phenotype data, computational predictions, and ACMG classification  

unannotated.vcf – Simulated raw variant file formatted in VCF v4.2 (GRCh38)  

annotated.vcf – ClinVar-annotated output file  

README.md – Project documentation  

---

## Workflow Overview

1. Variant selection using ClinVar  
2. Phenotype verification using OMIM  
3. Coordinate standardization to GRCh38  
4. VCF construction  
5. Functional annotation using Ensembl VEP  
6. Pathogenicity scoring (AlphaMissense and RAVEL, where applicable)  
7. ACMG/AMP 2015 evidence-based classification  
8. Generation of final annotated VCF  

---

## How to Reproduce

### 1. Select a Variant

- Search ClinVar for a pathogenic or likely pathogenic variant.  
- Use filters to narrow by variant type and clinical significance.  
- Verify phenotype and inheritance information in OMIM.  
- Record relevant details in `assignment.xlsx`.

---

### 2. Create a VCF File

Use VCF version 4.2 format:

```vcf
##fileformat=VCFv4.2
##reference=GRCh38
#CHROM POS ID REF ALT QUAL FILTER INFO
<chr> <position> . <REF> <ALT> . PASS .
```

Ensure:
- The genome build is GRCh38.  
- The REF allele matches the reference genome.  

---

### 3. Functional Annotation (VEP)

Upload the VCF to Ensembl Variant Effect Predictor:

- Select GRCh38.  
- Enable SIFT.  
- Enable PolyPhen.  
- Include gnomAD allele frequencies.  

Record:
- Variant consequence  
- Amino acid change  
- Population frequency  
- In-silico predictions  

---

### 4. Retrieve Pathogenicity Scores

Using UCSC Genome Browser:

- Retrieve AlphaMissense score (missense variants only).  
- Retrieve RAVEL score (single nucleotide variants only).  
- Document scores in `assignment.xlsx`.  

Note: Repeat expansions and structural variants are not evaluated by these tools.

---

### 5. Apply ACMG/AMP Classification

Assign evidence codes based on:

- Variant type (loss-of-function, missense, splice-site, etc.)  
- Population frequency  
- Computational evidence  
- Established disease mechanism  

Combine the evidence to determine the final classification (Pathogenic, Likely Pathogenic, etc.).

---

## Notes

- All coordinates were standardized to GRCh38 to avoid genome build inconsistencies.  
- Computational predictions provide supporting evidence, not definitive proof.  
- Population frequency interpretation depends on disease prevalence and inheritance model.  
- Final classification requires integration of multiple evidence categories.

---

## Summary

This project demonstrates a streamlined, reproducible variant interpretation workflow consistent with clinical genomics practice. It integrates database evidence, computational prediction, standardized variant formatting, and ACMG/AMP guideline-based classification.
