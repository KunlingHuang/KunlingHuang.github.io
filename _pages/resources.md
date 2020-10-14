---
layout: single
classes: narrow
title: "Resources"
permalink: "/resources/"
path: "/resources/"
toc: true
toc_icon: "fas fa-compass"

toc_label: #""
toc_sticky: true
author_profile: true
#sidebar: 
#    nav: docs
---
## Conducting reproducible research


Conducting reproducible research is important for large projects and error checking. Reproducible research allows people reproducing your published results easily and it is commonly required for publishing. Large-scale reproducible research includes an organized pipeline suitable for high-throughput computing and clear documentation. Keeping your pipeline and folders organized improves efficiency and helps avoiding potential confusion in the future. Documenting your work is like leaving messages to yourself in the future. Having a clear and up-to-date documentation allows you to keep track of your work and eliminate the hustle and bustle. Finally, making your pipeline suitable for high throughput computing greatly improves the speed of the analysis but you should be very careful about the errors. Handling a huge batch of tasks may cause error, performing [defensive programming](https://en.wikipedia.org/wiki/Defensive_programming) and designing an efficient error detection protocol help you eliminate the errors.

Here, I am going to provide some general advice on organizing the pipeline, documenting the work, and scaling up the pipeline. The advice is based on my research experience at UW-Madison and focuses on genome-wide association studies (GWAS). Those are the things I wish I knew when I joined the lab, and I hope the advice is helpful for you.


### 1. Organizing your pipeline

### 2. Keeping your documentation

### 3. Working on high throughput clusters


## Software

### TITANS

![TITANS workflow](/assets/images/TWAS_workflow_B.png)

[**TITANS**](https://github.com/qlu-lab/TITANS) (TrIo-based Transcriptome-wide AssociatioN Study) is a statistical framework to conduct transcription-wide associaiton study in proband-parent trios. TITANS quantifies the transmission disequilibrium of genetically regulated gene expression from parents to probands using pseudosibling matching and conditional logistic regression. 

