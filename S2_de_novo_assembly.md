# *De novo* assembly

Goals:
* generate draft assemblies using PacBio HiFi and Nanopore reads, separately and combined
* investigate the assembly graph

## hifiasm (PacBio HiFi only)

[hifiasm](https://github.com/chhylp123/hifiasm)

![hifiasm_hifi](s2_pic/hifiasm_hifi.png)

```sh
hifiasm -o output -f 37 -l 3 --primary ju765.hifi_reads.3Gb.fastq.gz
```

## hifiasm (PacBio HiFi + Nanopore)

[hifiasm](https://github.com/chhylp123/hifiasm)

![hifiasm_hifi_ont](s2_pic/hifiasm_hifi_ont.png)

```sh
hifiasm -o output -f 37 -l 3 --ul duplex.dorado_v0.4.1_dna_r10.4.1_e8.2_400bps_sup_v4.2.0.chopper_default.fastq.gz --ul-rate 0.2 --ul-tip 6 --primary ju765.hifi_reads.3Gb.fastq.gz
```

## Flye (HiFi)

[Flye](https://github.com/fenderglass/Flye)

![flye_hifi](s2_pic/flye_hifi.png)

```sh
flye --pacbio-hifi ju765.hifi_reads.3Gb.fastq.gz -o out_dir -i 1
```

## Flye (Nanopore)

[Flye](https://github.com/fenderglass/Flye)

![flye_ont](s2_pic/flye_ont.png)

```sh
flye --nano-hq duplex.dorado_v0.4.1_dna_r10.4.1_e8.2_400bps_sup_v4.2.0.chopper_default.fastq.gz -o out_dir -i 1
```

## Converting graphical fragment assembly (GFA) to fasta file

![gfatofasta](s2_pic/gfatofasta_hifiasm.png)

```sh
awk '/^S/{print ">"$2;print $3}' assembly.gfa > assembly.fasta
```

## Checking the graphical fragment assembly (GFA)

[Bandage](https://rrwick.github.io/Bandage/)

### Bandage info

![bandage_info](s2_pic/bandage_info.png)

```sh
Bandage info input.gfa 
```

![bandage_info_result](s2_pic/bandage_info_result.png)

### Bandage image

![bandage_image](s2_pic/bandage_image.png)

```sh
Bandage image input.gfa 
```

![bandage_image_result](s2_pic/bandage_image_result.jpg)
