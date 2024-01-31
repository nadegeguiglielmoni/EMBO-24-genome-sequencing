# Hi-C scaffolding

Goals:
* scaffold our contigs using Hi-C data
* evaluate the Hi-C contact maps

## BWA MEM2 (mapping R1 and R2 reads *separately*)

[bwa mem2](https://github.com/bwa-mem2/bwa-mem2)

![bwa mem](s4_pic/bwa_mem.png)

Note that we are treating the paired reads as separate, unpaired files. We need to get a name-sorted BAM (instead of the usual coordinate-sorted ones), because we will need to find pairs later on, and due to the nature of Hi-C sequencing, these pairs should have their R1 and R2 reads at distant coordinates from each other. 

```sh
bwa-mem2 index assembly.fasta
bwa-mem2 mem assembly.fasta R1_subseq_10pct.fastq.gz | samtools sort -n -O bam -o R1.bam
```

Repeat this with the R2 data to create a `R2.bam`.

## Bellerophon (Arima mapping pipeline)

[arima mapping pipeline](https://github.com/ArimaGenomics/mapping_pipeline/tree/master)

[bellerophon conda wrapper](https://bioconda.github.io/recipes/bellerophon/README.html)

![bellerophon](s4_pic/bellerophon.png)

Bellerophon is a conda wrapper for the Arima mapping pipeline. This step finds pairs and filters them to remove pairs with chimeric reads (reads that cover the ligation junction, thus artifically connecting two distant parts of the sequence).

```sh
bellerophon --forward R1.bam --reverse R2.bam --quality 20 --output merged.bam
samtools sort --no-PG -O bam -o merged_sorted.bam merged.bam
```

