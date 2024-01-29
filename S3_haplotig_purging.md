# Haplotig purging

## Mapping reads to the assembly

### PacBio HiFi reads

![minimap2_hifi](s3_pic/minimap2_hifi.png)
![minimap2_out](s3_pic/minimap2_output.png)

### Nanopore reads

![minimap2_ont](s3_pic/minimap2_ont.png)
![minimap2_out](s3_pic/minimap2_output.png)

## Splitting and self-mapping the assembly

[purge_dups](https://github.com/dfguan/purge_dups)

![purge_dups_split](s3_pic/purge_dups_split.png)

```sh
split_fa assembly.fasta > split.fa
```

![minimap2_out](s3_pic/minimap2_output.png)

## Calculating cutoffs

## Purging duplications

## Getting the purged assembly sequence
