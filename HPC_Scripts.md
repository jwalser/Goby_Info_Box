### Script


```HPC
### =================================
### Project Goby
### Scripts for sciCORE
### trinity_qsub_across.sh
### 11/03/16
### =================================

#!/bin/bash
#$ -N trinity_across
#$ -S /bin/bash
#$ -pe smp 16
#$ -l membycore=14G
#$ -l runtime=120:00:00
#$ -o /scicore/home/holmp/GROUP/1_Gopy_RNAseq/z_log/trinity_qsub_across.stdout
#$ -e /scicore/home/holmp/GROUP/1_Gopy_RNAseq/z_log/trinity_qsub_across.error
#$ -m beas -M jean-claude.walser@unibas.ch

## --------------------------
## load your required modules
## --------------------------

module load Trinity/2.1.1-goolf-1.4.10 EMBOSS/6.6.0-goolf-1.4.10 

## --------------------------
## set paths
## --------------------------

wd=/scicore/home/holmp/walser/Goby/2_RNASeq
gp=/scicore/home/holmp/GROUP/1_Gopy_RNAseq
N50=/scicore/home/holmp/walser/bin/N50Stat.pl

## Data sets:

f2R1=/scicore/home/holmp/GROUP/1_Gopy_RNAseq/b_qf/B1_2_qf_1.fastq
f2R2=/scicore/home/holmp/GROUP/1_Gopy_RNAseq/b_qf/B1_2_qf_2.fastq

f70R1=/scicore/home/holmp/GROUP/1_Gopy_RNAseq/b_qf/F1_70_qf_1.fastq
f70R2=/scicore/home/holmp/GROUP/1_Gopy_RNAseq/b_qf/F1_70_qf_2.fastq

f132R1=/scicore/home/holmp/GROUP/1_Gopy_RNAseq/b_qf/C2_132_qf_1.fastq
f132R2=/scicore/home/holmp/GROUP/1_Gopy_RNAseq/b_qf/C2_132_qf_2.fastq

f141R1=/scicore/home/holmp/GROUP/1_Gopy_RNAseq/b_qf/A1_141_qf_1.fastq
f141R2=/scicore/home/holmp/GROUP/1_Gopy_RNAseq/b_qf/A1_141_qf_2.fastq


## ---------------------------------------------------------------------------------------
## De-novo Transcriptome Assembly ()
## --------------------------------------------------------------------------------------

mkdir -p $gp/c_assembly/trinity_across

Trinity --seqType fq --min_contig_length 100 --min_glue 4 --group_pairs_distance 300 --path_reinforcement_distance 85 --min_kmer_cov 4 --max_memory 50G --CPU 16 --bflyCalculateCPU --left $f2R1,$f70R1,$f132R1,$f141R1 --right $f2R2,$f70R2,$f132R2,$f141R2 --output $gp/c_assembly/trinity_across | tee $gp/c_assembly/trinity_across.log

## Summary
$N50 -i $gp/c_assembly/trinity_across/Trinity.fasta -o $gp/c_assembly/trinity_across/Trinity.stats
## Length and %GC report for R import
infoseq -only -length -pgc $gp/c_assembly/trinity_acorss/Trinity.fasta | sed '1d' > $gp/c_assembly/trinity_across/Trinity_l_gc.txt

```
