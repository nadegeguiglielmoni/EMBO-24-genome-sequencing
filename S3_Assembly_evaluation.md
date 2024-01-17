# Assembly evaluation

## Assembly statistics



## Ortholog completeness

[BUSCO](https://busco.ezlab.org/)

![busco](s3_pic/busco.png)

```sh
busco --in assembly.fasta --mode genome --out busco_out --evalue 0.001 --limit 3 --contig_break 10 --auto-lineage
```

## *k*-mer completeness
