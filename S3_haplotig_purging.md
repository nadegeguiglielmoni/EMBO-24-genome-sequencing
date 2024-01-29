# Haplotig purging

## Mapping reads to the assembly

### PacBio HiFi reads

[minimap2](https://github.com/lh3/minimap2)

![minimap2_hifi](s3_pic/minimap2_hifi.png)
![minimap2_out](s3_pic/minimap2_output.png)

```sh
minimap2 -x map-hifi --q-occ-frac 0.01 assembly.fasta hifi.fastq.gz > minimap2_hifi.paf
```

### Nanopore reads

[minimap2](https://github.com/lh3/minimap2)

![minimap2_ont](s3_pic/minimap2_ont.png)
![minimap2_out](s3_pic/minimap2_output.png)

```sh
minimap2 -x map-ont --q-occ-frac 0.01 assembly.fasta hifi.fastq.gz > minimap2_ont.paf
```

## Splitting and self-mapping the assembly

[purge_dups](https://github.com/dfguan/purge_dups)

![purge_dups_split](s3_pic/purge_dups_split.png)

```sh
split_fa assembly.fasta > split.fa
```

[minimap2](https://github.com/lh3/minimap2)

![minimap2_self](s3_pic/minimap2_self.png)
![minimap2_out](s3_pic/minimap2_output.png)

```sh
minimap2 -x asm5 --q-occ-frac 0.01 split.fa split.fa > minimap2_self.paf
```

## Calculating cutoffs

## Purging duplications

## Getting the purged assembly sequence
