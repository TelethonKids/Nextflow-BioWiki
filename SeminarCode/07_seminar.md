# Seminar 7 Coding Material


## [`nf-core/ampliseq`](https://nf-co.re/atacseq/2.6.1)

### Basic run command
```bash 
nextflow run 'https://github.com/nf-core/ampliseq' \
         --outdir results-ampliseq-test-profile \
		 -r 2.6.1 \
         -profile docker,test
```
## --input

### Samplesheet (.csv) 

```csv
sampleID	forwardReads	reverseReads	run
SRR10070130	ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR100/030/SRR10070130/SRR10070130_1.fastq.gz	ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR100/030/SRR10070130/SRR10070130_2.fastq.gz	1
SRR10070131	ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR100/031/SRR10070131/SRR10070131_1.fastq.gz	ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR100/031/SRR10070131/SRR10070131_2.fastq.gz	2
SRR10070132	ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR100/032/SRR10070132/SRR10070132_1.fastq.gz	ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR100/032/SRR10070132/SRR10070132_2.fastq.gz	2
```

### Metadata (.csv)

```csv
ID	condition
sample1	control
sample2	treatment
sample3	control
sample4	treatment
```

## Rclone: Rclone syncs your files to cloud (remote) storage



### Configuring a remote using the `config` command

https://rclone.org/commands/rclone_config/


### `listremotes` command

```console
rclone listremotes
```


### `lsd` and `lsl` commands

```console
rclone lsd ssh-tki-nimbus:/home/ubuntu/_scratch/
```

```console
rclone lsl ssh-tki-nimbus:/home/ubuntu/_scratch/
```

### `md5sum` command

```console
echo "Hello, rclone!" >> test.txt
rclone md5sum test.txt
```

### `copy` command

> **NOTE**: Verbose output:
Add `-vv` at the end of the command to execute rclone in verbose mode


```console
rclone copy test.txt ssh-tki-nimbus:/home/ubuntu/_scratch/ -v

rclone copy ssh-tki-nimbus:/home/ubuntu/_scratch/results-ampliseq-test-profile/fastqc ./results-ampliseq-test-profile/fastqc -vv

```

### `tree` command

```console
rclone tree ssh-tki-nimbus:/home/ubuntu/_scratch 
```

### `ncdu` command

```console
rclone ncdu ssh-tki-nimbus:/home/ubuntu/_scratch 
```
