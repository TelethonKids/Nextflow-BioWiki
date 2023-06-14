# Seminar 4 Coding Material


## [`nf-core/smrnaseq`](https://nf-co.re/smrnaseq)

### Run command from Introduction

```console
nextflow run nf-core/smrnaseq \
    -profile <docker/singularity/.../institute> \
    --input samplesheet.csv \
    --genome 'GRCh37' \
    --mirtrace_species 'hsa' \
    --protocol 'illumina' \
    --outdir <OUTDIR>
```

### Sample sheet (samplesheet.csv)
```console
sample,fastq_1
Clone1_N1,s3://ngi-igenomes/test-data/smrnaseq/C9-N1-R1_S7_L001_R1_001.fastq.gz
Clone1_N2,s3://ngi-igenomes/test-data/smrnaseq/C9-N2-R1_S8_L001_R1_001.fastq.gz
Control_N1,s3://ngi-igenomes/test-data/smrnaseq/Ctl-N1-R1_S1_L001_R1_001.fastq.gz
Control_N2,s3://ngi-igenomes/test-data/smrnaseq/Ctl-N2-R1_S2_L001_R1_001.fastq.gz
```

### Parameters (myParams.json)

```console
{
    "max_cpus": 4,
    "max_memory": "12.GB",
    "max_time": "6.h",
    "input": "https://github.com/nf-core/test-datasets/raw/smrnaseq/samplesheet/v2.0/samplesheet.csv",
    "fasta":"https://github.com/nf-core/test-datasets/raw/smrnaseq/reference/genome.fa",
    "mature": "https://github.com/nf-core/test-datasets/raw/smrnaseq/reference/mature.fa",
    "hairpin": "https://github.com/nf-core/test-datasets/raw/smrnaseq/reference/hairpin.fa",
    "mirna_gtf": "https://github.com/nf-core/test-datasets/raw/smrnaseq/reference/hsa.gff3",
    "mirtrace_species": "hsa",
    "protocol": "illumina",
    "skip_mirdeep": true  
}
```

### Run command
```console
nextflow run smrnaseq/ -profile docker --input samplesheet.csv -params-file myParams.json --outdir results
```

## [`Tower`](https://cloud.tower.nf/)

> ### Instructions
>
>Tutorial [here](https://training.nextflow.io/basic_training/tower/#usage).
>
>Follow the instructions in the [`Tower` documentation](https://tower.nf/docs/launching-pipelines) to launch the pipeline.

```
export TOWER_ACCESS_TOKEN=<token>
```

```
export TOWER_WORKSPACE_ID=<id>
```

Can store in `$HOME/.nextflow/config`

```
tower {
  enabled = true
  accessToken = '<token>'
  workspaceId = '<id>'
}
```

>Notes found [here](https://www.nextflow.io/docs/latest/config.html).