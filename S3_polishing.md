# Polishing

## Mapping the PacBio HiFi reads to the Nanopore assembly

[minimap2](https://github.com/lh3/minimap2)

![minimap2_hifi](s3_pic/minimap2_hifi_polish.png)

```sh
minimap2 -ax map-hifi --q-occ-frac 0.01 assembly.fasta hifi.fastq.gz > minimap2_hifi.bam
```

## Polishing the assembly

[HyPo](https://github.com/kensung-lab/hypo)

![hypo](s3_pic/hypo.png)

```sh
echo ju765.hifi_reads.3Gb.fastq.gz >>  short_reads.txt &&
hypo --reads-short @short_reads.txt --draft assembly.fasta --bam-sr minimap2_hifi.bam --coverage-short 60 --size-ref '50m' --kind-sr ccs \
  --match-sr 5 --mismatch-sr -4 --gap-sr -8 --match-lr 3 --mismatch-lr -5 --gap-lr -4 --ned-th 20 --qual-map-th 2 -o polished.fasta
```
