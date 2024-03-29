---
title: "About"
layout: single
author_profile: true
permalink: "/about/"
---


I am a PhD student at Department of Statistics, University of Wisconsin-Madison. My research focuses on designing statistical methods to detect non-coding risk variants in neurodevelopmental disorder.

Email: <khuang82@wisc.edu> \
CV: [CV](/assets/docs/KHuangCV.pdf)


## Education

- **University of Wisconsin-Madison**  
*Doctor of philosophy in Statistics*                                   
Advisor: Dr. Qiongshi Lu ([Lu lab](https://qlu-lab.org/))
\
Dissertation: “Statistical methods for linking noncoding genetic variations to target genes with application in neurodevelopmental disorders”

## Skills
- Operation system: Linux/Unix
- Programming languages: R, Python, Java
- Database tools: MySQL

## Projects

### Transcriptome-wide transmission disequilibrium analysis identifies novel risk genes for autism spectrum disorder

- Conducted a large-scale transcriptome-wide association study on autism spectrum disorder (ASD) genetics data
- Developed and optimized pipeline using R libraries tidyverse and data.table ([project code](https://github.com/qlu-lab/TITANS))
- Designed parallel computing strategy on high-performance computing environment HTCondor
- Implemented pseudo sibling matching and conditional logistic regression models for analyzing ASD trios
- Specified and confirmed the epigenetic role of transcription factor gene [*POU3F2*](https://www.ncbi.nlm.nih.gov/gene/5454) on ASD risk
- Performed DNase-I network analysis and demonstrated excess damaging de novo variants in known ASD genes regulated by *POU3F2*
- Identified heritability enrichments in *POU3F2* binding sites using LD score regression
- Evaluated the differential expression in adult and fetal brain for *POU3F2*

### Integrating enhancer-promoter interaction with ASD GWAS signals
- Constructed variance tests for Hi-C enhancer-promoter interaction on GWAS scores to pinpoint genes distantly regulating ASD risks
- Adapted variance quantitative loci (vQTL) methods to denoise the Hi-C interaction data and achieved model robustness
- Processed the Hi-C raw data to interpretable format using Fit-Hi-C
- Integrated and curated resources from NCBI and UCSC
- Provided high throughput computing and human genetics trainings to undergraduate students


### Modelling prenatal and postnatal brain eQTLs together via fused LASSO
- Modelled expression quantitative loci (eQTL) in adult and fetal brain together to boost power in fetal studies using fused LASSO model
- Designed a fast coordinate descent algorithm taking eQTL summary statistics in each developmental stage as input
- Implemented the algorithm as a python scikit-learn compatible module

### Genome-wide association study for congenital heart disease
- Curated next generation sequencing (NGS) data using Plink and bcftools
- Combined the association results between microarray and NGS studies using meta-analysis tool METAL and R

### Identifying ovarian cancer biomarkers with different disease progress
- Collected RNA-seq data and ovarian cancer progress information using Bioconductor on R
- Performed gene expression cluster analysis using weighted correlation network analysis (WGCNA) and Gene Ontology (GO)
- Validated the cancer biomarkers using survival models in different patient groups


