# Seminar 6 Coding Material


## [`nf-core/atacseq`](https://nf-co.re/atacseq/2.1.2)

### Basic run command
```bash 
nextflow run nf-core/atacseq /
    --input samplesheet.csv /
    --outdir <OUTDIR>
    --genome GRCh37 /
    --read_length <50> /
    -profile <docker> /
    -r <2.1.1>
```
## --input

### Samplesheet (.csv) 

#### Biological Replicates

```
sample,fastq_1,fastq_2,replicate
CONTROL,AEG588A1_S1_L002_R1_001.fastq.gz,AEG588A1_S1_L002_R2_001.fastq.gz,1
CONTROL,AEG588A1_S1_L003_R1_001.fastq.gz,AEG588A1_S1_L003_R2_001.fastq.gz,2
CONTROL,AEG588A1_S1_L004_R1_001.fastq.gz,AEG588A1_S1_L004_R2_001.fastq.gz,3
```

#### Technical replicates
```
sample,fastq_1,fastq_2,replicate
CONTROL,AEG588A1_S1_L002_R1_001.fastq.gz,AEG588A1_S1_L002_R2_001.fastq.gz,1
CONTROL,AEG588A1_S1_L003_R1_001.fastq.gz,AEG588A1_S1_L003_R2_001.fastq.gz,1
CONTROL,AEG588A1_S1_L004_R1_001.fastq.gz,AEG588A1_S1_L004_R2_001.fastq.gz,1
```

#### Controls for peak calling
```
sample,fastq_1,fastq_2,replicate,control,control_replicate
CONTROL,AEG588A1_S1_L002_R1_001.fastq.gz,,1,,
CONTROL,AEG588A2_S2_L002_R1_001.fastq.gz,,2,,
CONTROL,AEG588A3_S3_L002_R1_001.fastq.gz,,3,,
TREATMENT,AEG588A4_S4_L003_R1_001.fastq.gz,,1,CONTROL,1
TREATMENT,AEG588A5_S5_L003_R1_001.fastq.gz,,2,CONTROL,2
TREATMENT,AEG588A6_S6_L003_R1_001.fastq.gz,,3,CONTROL,3
```