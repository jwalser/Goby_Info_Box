#### Round Goby Transcriptome

---
Data: 444,944,147 Illumina 81bp paired-end reads<br>
Number of RNAseq libraries: 15<br>
Tissue: embryonic tissue (1 cell to 64 cell stage plus a few larva cells)<br>
Transcriptome file: RoundGoby_Transcritome_Assembly_V1_160507.fasta
ORFs file name: RoundGoby_Transcritome_Assembly_V1_160507_ORFs_c98.fasta
___

#### Trancriptome V1 (160507)

1. Quality control with FastQC (v0.11.2)
2. Quality filtering with PrinSeq (v0.20.4)
3. De novo assembly with Trinity (v2.1.1)

```
Total sequences              176,474
Total bases               92,502,216 (~92.5Mb)
Min sequence length              101
Max sequence length           23,082
Average sequence length          524.1
Median sequence length           170.0
N25 length                     3,541
N50 length                     1,787
N75 length                       407
N90 length                       153
As                               26.9%
Ts                               26.6%
Gs                               23.5%
Cs                               23.0%
(A + T)s                         53.5%
(G + C)s                         46.5%
Ns                                0.0%
```

4. Transdecoder was used to find and extract possible ORFs with a minimum length of 150nt (50aa).
5. De-replication with PrinSeq (v0.20.4)
6. Clustering with USEARCH (v8.1.1812_i86linux64)
7. Completness estimate with BUSCO (v1.1b1)

```
Number of total ORFs          265,080
Unique ORFs                   204,608 (77.2%)
Clustered (id:100%, cov:100%) 128,956 (48.6%)
Clustered (id:99%, cov:100%)  125,495 (47.3%)
Clustered (id:98%, cov:100%)  122,843 (46.3%)
Completness                        74.6%
```



