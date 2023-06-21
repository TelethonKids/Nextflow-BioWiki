![Overview]()

<br>

## Seed

### Custom `Configurations`



**References:**
- []()

<br>

## Seedling

### [`nfcore/methylseq`](https://nf-co.re/methylseq)

<br>

`nfcore/methylseq` is a Nextflow bioinformatic pipeline used for the analysis of methylation (bisulphite) sequencing data. The `nfcore/methylseq` pipeline is able to preprocess the raw data from raw fastq files, align the reads, and do further quality control analysis on the results.

`nfcore/methylseq` has multiple different workflows from which users can specify in the `config` file, these being Bismark, or bwa/meth and MethylDackel. The specfication for which workflow to use comes under the `--aligner` tag.

`nfcore/methylseq` requires pipeline parameters to be provided by either the command line, or through a Nextflow `-params-file`. Custom `config` files can be used to provide any specific confirgurations _except for parameters_.

<br>

#### **Usage**
`nfcore/methylseq` essentially contains two pipelines in one:
> - Default: Bismark with Bowtie2 as the alignment tool. HISAT2 can also be used through specifying in the command line.
> - Other: BWA-Meth and MethylDackel. For this pipeline the appropriate flag in command line must be used.

<br>

`nfcore/methylseq` requires the use of specific sample sheets created by the user containing their input fastq data as a .csv file with the headers sample, fastq_1, and fastq_2. `nfcore/methylseq` accepts both paired end and single end data input, and is able to recognise whether the input data is single end or paired end through the samplesheet alone (no specification required).

>Samplesheet:
>
>sample,fastq_1,fastq_2
>

<br>

To run the pipeline (as launched with docker):

```

nextflow run nf-core/methylseq --input samplesheet.csv --outdir <OUTDIR> --genome GRCh37 -profile <CONTAINER>

```
The directories created:

```

work                # Directory containing the nextflow working files
<OUTDIR>            # Finished results in specified location (defined with --outdir)
.nextflow_log       # Log file from Nextflow
# Other nextflow hidden files, eg. history of pipeline runs and old logs.

```


<br>

#### **Parameters**


#### **Output**

<br>

**References:**
- [`nfcore/methylseq`](https://nf-co.re/methylseq)
- [`nfcore/methylseq` usage documents](https://nf-co.re/methylseq/2.4.0/usage)
- 

<br>

## Plant

### `Configuration` training and resources

Training resources: 
- [Nextflow Training](https://github.com/nextflow-io/training/tree/master) 
- [Nextflow Configuration](https://training.nextflow.io/basic_training/config/)
- [Introduction to Bioinformatics workflows with Nextflow and nf-core: Nextflow configuration](https://carpentries-incubator.github.io/workflows-nextflow/08-configuration/index.html)

**References:**
- []()

