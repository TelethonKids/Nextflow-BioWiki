# Seminar 3 coding material

 ## 1. Folder structure
    
``` 
    ├── data
    ├── params
    │   ├── exp1
    │   │   ├── diffabun.yml
    │   │   ├── fetchngs.yml
    │   │   └── rnaseq.yml
    │   └── exp2
    ├── results
    │   ├── exp1
    │   └── exp2
    └── samplesheets
        ├── fetchngs_sample_ids.txt
        └── rnaseq.100samples.csv

```
    
<br>

 ## 2. Pipeline specific options should be kept in a `yml` files for each experiment, for example:  
 <br>

 ### [`nf-core/fetchngs`](https://nf-co.re/fetchngs)
     
```yaml
    #---------------------
    # fetchngs
    #---------------------
    outdir: data/
    input: samplesheets/fetchngs_sample_ids.txt
    max_memory: 6.GB
    force_sratools_download: true
    nf_core_pipeline: rnaseq

```
<br>

### [`nf-core/rnaseq`](https://nf-co.re/rnaseq)

```yaml
    #---------------------
    # rnaseq
    #---------------------

    input: rnaseq.100samples.csv
    outdir: results/exp1/rnaseq
    genome: GRCh37
```
<br>

### [`nf-core/differentialabundance`](https://nf-co.re/differentialabundance)

```yaml
    #---------------------
    # differentialabundance
    #---------------------

    shinyngs_deploy_to_shinyapps_io: true
    shinyngs_shinyapps_account: abhi18av
    shinyngs_shinyapps_app_name: diffabun-1
```
<br>

## 3. Nextflow specific options should be kept in the command line
<br>

 ### [`nf-core/fetchngs`](https://nf-co.re/fetchngs)     
```bash
    #---------------------
    # fetchngs
    #---------------------

   
    nextflow run nf-core/fetchngs \
        -r 1.9 \
        -profile docker \
        -resume \
        -params-file params/exp1/fetchngs.yml

```
<br>

### [`nf-core/rnaseq`](https://nf-co.re/rnaseq)
```bash
    #---------------------
    # rnaseq
    #---------------------

    nextflow run nf-core/rnaseq \
        -r 3.11.2 \
        -profile docker \
        -resume \
        --params-file params/exp1/rnaseq.yml

```
<br>

### [`nf-core/differentialabundance`](https://nf-co.re/differentialabundance)

```bash 
    #---------------------
    # differentialabundance
    #---------------------

    nextflow run nf-core/differentialabundance \
        -r 1.2.0 \
        -profile rnaseq,docker \
        -resume \
        --params-file params/exp1/diffabun.yml

```