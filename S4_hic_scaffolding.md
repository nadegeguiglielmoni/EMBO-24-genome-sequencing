# Hi-C scaffolding

Goals:
* scaffold our contigs using Hi-C data
* evaluate the Hi-C contact maps

## BWA MEM2 (mapping R1 and R2 reads separately)

[bwa mem2](https://github.com/bwa-mem2/bwa-mem2)

![hifiasm_hifi](s2_pic/hifiasm_hifi.png)

```sh
hifiasm -o output -f 37 -l 3 --primary ju765.hifi_reads.3Gb.fastq.gz
```
