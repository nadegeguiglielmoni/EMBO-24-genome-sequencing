# Analysis of DNA sequencing

## NanoPlot on PacBio HiFi reads

[NanoPlot](https://github.com/wdecoster/NanoPlot)

![nanoplot_hifi](s1_pic/nanoplot_hifi.png)

```sh
NanoPlot --tsv_stats --fastq ju765.hifi_reads.3Gb.fastq.gz
```

![nanoplot_hifi](s1_pic/nanoplot_hifi_result.png)

## NanoPlot on Nanopore reads

[NanoPlot](https://github.com/wdecoster/NanoPlot)

![nanoplot_hifi](s1_pic/nanoplot_ont.png)

```sh
NanoPlot --tsv_stats --fastq duplex.dorado_v0.4.1_dna_r10.4.1_e8.2_400bps_sup_v4.2.0.chopper_default.fastq.gz
```

![nanoplot_hifi](s1_pic/nanoplot_ont_result.png)

## GenomeScope on PacBio HiFi reads

[jellyfish](https://github.com/gmarcais/Jellyfish)
[GenomeScope2](https://github.com/tbenavi1/genomescope2.0)

![jellyfish_count](s1_pic/jellyfish_count_hifi.png) 

![jellyfish_hist](s1_pic/jellyfish_hist_hifi.png) 

![genomescope](s1_pic/genomescope_hifi.png) 

```sh
jellyfish count --mer-len 21 ju765.hifi_reads.decont.3Gb.fastq.gz
jellyfish histo -o jellyfish.histo mer_counts.jf
genomescope2 --input jellyfish.histo --output . --kmer_length 21
```

## Smudgeplot on PacBio HiFi reads

[Smudgeplot](https://github.com/KamilSJaron/smudgeplot)

![smudgeplot](s1_pic/smudgeplot.png)

```sh
mkdir tmp_smudge
ls ju765.hifi_reads.decont.3Gb.fastq.gz > FILES
kmc -k21 -ci1 -cs10000 @FILES kmcdb tmp_smudge
kmc_tools transform kmcdb histogram kmcdb_k21.hist -cx10000

L=$(smudgeplot.py cutoff kmcdb_k21.hist L)
U=$(smudgeplot.py cutoff kmcdb_k21.hist U)
echo $L $U

kmc_tools transform kmcdb -ci"$L" -cx"$U" dump -s kmcdb_L"$L"_U"$U".dump
smudgeplot.py hetkmers -o kmcdb_L"$L"_U"$U" < kmcdb_L"$L"_U"$U".dump

smudgeplot.py plot kmcdb_L"$L"_U"$U"_coverages.tsv
```
