## ChangeLog

This repo has made the following modifications to the original [nf-core scrnaseq](https://github.com/nf-core/scrnaseq) workflow

- Allows multiple barcode whitelist files to be provided to accommodate multiple barcode segments.
- Add protocol for Singleron rna kit: scopeV3.0.1. Please note scopeV3.0.1 currently only support `--aligner star`.
- Change the default value of STARsolo `star_feature` parameter to "GeneFull_Ex50pAS". Using the `GeneFull_Ex50pAS` parameter can effectively count reads mapped to intron.
- Remove the default parameter `--twopassMode Basic` as it is not compatible with `GeneFull_Ex50pAS`.
- Add `soloCellFilter` parameter and set default value "EmptyDrops_CR".
- Update the STAR version from 2.7.10b to the lastest version 2.7.11b as 2.7.11b fix some bugs.

## Usage

Run the pipeline with test data using

```
nextflow run zhouyiqi91/scrnaseq -profile test,docker --outdir ./outs
```

This is equivalent to the following command

```
nextflow run zhouyiqi91/scrnaseq -profile docker \
 --outdir ./outs \
 --input 'https://github.com/zhouyiqi91/nf_test_data/raw/main/scRNA/scopeV3.0.1/test.csv' \
 --fasta 'https://github.com/nf-core/test-datasets/raw/scrnaseq/reference/GRCm38.p6.genome.chr19.fa' \
 --gtf 'https://github.com/nf-core/test-datasets/raw/scrnaseq/reference/gencode.vM19.annotation.chr19.gtf' \
 --protocol scopeV3.0.1 \
 --aligner star \
 --max_memory '6.GB' \
 --max_cpus 2 \
 --max_time '6.h'
```

For detailed documentation, please refer to the nf-core scrnaseq doc: https://nf-co.re/scrnaseq/2.5.1
