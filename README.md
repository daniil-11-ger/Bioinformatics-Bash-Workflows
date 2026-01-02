# Bioinformatics-Bash-Workflows
#!/bin/bash
# Pipeline for Bacterial Genome Assembly

# 1. Download data
fasterq-dump --split-files SRR35523993

# 2. Quality Control & Trimming
conda activate fastp
fastp -i SRR35523993_1.fastq -I SRR35523993_2.fastq \
      -o SRR35523993_1.trimmed.fastq -O SRR35523993_2.trimmed.fastq \
      -q 20 -u 30 -l 50 -w 10
conda deactivate
