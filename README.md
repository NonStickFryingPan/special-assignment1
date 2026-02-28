# Clinical Variant Interpretation Workflow

This repository documents a reproducible workflow for identifying, annotating, and classifying clinically relevant genetic variants using public databases and standardized interpretation guidelines. The project simulates a clinical genomics pipeline, starting from variant selection and ending with ACMG/AMP-based pathogenicity classification.

<img width="3980" height="944" alt="image" src="https://github.com/user-attachments/assets/28d79046-2977-4040-8f6b-6601ecae49d1" />

---

## Repository Structure

- [`assignment.xlsx`](https://docs.google.com/spreadsheets/d/1bKZsR481E2k683q5QbTzLJn8DGj020nKFDmSF3KP6_Q/edit?usp=sharing) – Structured evidence table containing variant details, phenotype data, computational predictions, and ACMG classification  

- `unannotated.vcf` – Simulated raw variant file formatted in VCF v4.2 (GRCh38)  

- `annotated.vcf` – ClinVar-annotated output file  
---

## Workflow Overview

1.  **Variant Selection:** Identification of pathogenic variants using [ClinVar](https://www.ncbi.nlm.nih.gov/clinvar/).
2.  **Phenotype Verification:** Confirmation of clinical symptoms and inheritance patterns via [OMIM](https://www.omim.org/).
3.  **Coordinate Standardization:** Ensuring all positions are mapped to the **GRCh38** assembly.
4.  **VCF Construction:** Generating a machine-readable variant file.
5.  **Functional Annotation:** Predicting biological impact using [Ensembl VEP](https://www.ensembl.org/Homo_sapiens/Tools/VEP).
6.  **Pathogenicity Scoring:** Extracting AlphaMissense and REVEL scores for computational evidence.
7.  **Evidence Synthesis:** Applying [ACMG/AMP 2015 Guidelines](https://www.acmg.net/ACMG/Medical-Genetics-Practice-Resources/Practice-Guidelines.aspx).
8.  **Output:** Generation of the final annotated VCF and clinical verdict.

---

## How to Reproduce

### 1. Select a Variant

- Search ClinVar for a pathogenic or likely pathogenic variant.  
- Use filters to narrow by variant type and clinical significance.  
- Verify phenotype and inheritance information in OMIM.  
- Record relevant details in `assignment.xlsx`.
<img width="1260" height="555" alt="{78B94717-7D83-42A4-86BA-DFAC8684DE25}" src="https://github.com/user-attachments/assets/d974e942-2a7b-49cb-bec6-dae34bb69b44" />


---

### 2. Create a VCF File

Use VCF version 4.2 format:

```vcf
##fileformat=VCFv4.2
##reference=GRCh38
#CHROM POS ID REF ALT QUAL FILTER INFO
<chr> <position> . <REF> <ALT> . PASS .
```

---

### 3. Functional Annotation (VEP)

Upload the VCF to Ensembl Variant Effect Predictor:

- Select GRCh38.  
- Enable SIFT.  
- Enable PolyPhen.  
- Include gnomAD allele frequencies.
<img width="1278" height="632" alt="{281B3BE1-3915-483A-B5FE-162E9B7F0404}" src="https://github.com/user-attachments/assets/a92d6a59-942c-41d7-96bc-811ed8ecffa9" />


---

### 4. Retrieve Pathogenicity Scores

Using UCSC Genome Browser:

- Retrieve AlphaMissense score (missense variants only).  
- Retrieve RAVEL score (single nucleotide variants only).  
- Document scores in `assignment.xlsx`.  

Note: Repeat expansions and structural variants are not evaluated by these tools.
<img width="2560" height="1159" alt="image" src="https://github.com/user-attachments/assets/9a46f04d-60d1-42cb-ac2e-a16827580e9b" />


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
