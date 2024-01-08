# Analysis of DNA sequencing

## NanoPlot on PacBio HiFi reads

[NanoPlot](https://github.com/wdecoster/NanoPlot)

![nanoplot_hifi](s1_pic/nanoplot_hifi.png)

```sh
NanoPlot --tsv_stats --fastq ju765.hifi_reads.3Gb.fastq.gz
```

## NanoPlot on Nanopore reads

[NanoPlot](https://github.com/wdecoster/NanoPlot)

![nanoplot_hifi](s1_pic/nanoplot_ont.png)

```sh
NanoPlot --tsv_stats --fastq duplex.dorado_v0.4.1_dna_r10.4.1_e8.2_400bps_sup_v4.2.0.chopper_default.fastq.gz
```

## GenomeScope on PacBio HiFi reads

[jellyfish](https://github.com/gmarcais/Jellyfish)
[GenomeScope2](https://github.com/tbenavi1/genomescope2.0)

```sh
jellyfish count --mer-len 21 ju765.hifi_reads.3Gb.fastq.gz
jellyfish histo -o jellyfish.histo mer_counts.jf
genomescope2 --input jellyfish.histo --output . --kmer_length 21
```
