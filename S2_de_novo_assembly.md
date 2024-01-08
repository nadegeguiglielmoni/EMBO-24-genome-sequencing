# *De novo* assembly

## hifiasm (PacBio HiFi only)

[hifiasm](https://github.com/chhylp123/hifiasm)

![hifiasm_hifi](s2_pic/hifiasm_hifi.png)

```sh
hifiasm -o output -f 37 --primary ju765.hifi_reads.3Gb.fastq.gz
```

## hifiasm (PacBio HiFi + Nanopore)

[hifiasm](https://github.com/chhylp123/hifiasm)

![hifiasm_hifi_ont](s2_pic/hifiasm_hifi_ont.png)

```sh
hifiasm -o output -f 37 --ul duplex.dorado_v0.4.1_dna_r10.4.1_e8.2_400bps_sup_v4.2.0.chopper_default.fastq.gz --ul-rate 0.2 --ul-tip 6 --primary ju765.hifi_reads.3Gb.fastq.gz
```

## Flye (HiFi)

![flye_hifi](s2_pic/flye_hifi.png)

```sh
flye --pacbio-hifi ju765.hifi_reads.3Gb.fastq.gz -o out_dir -i 1
```

## Flye (Nanopore)

![flye_ont](s2_pic/flye_ont.png)

```sh
flye --nano-hq duplex.dorado_v0.4.1_dna_r10.4.1_e8.2_400bps_sup_v4.2.0.chopper_default.fastq.gz -o out_dir -i 1
```