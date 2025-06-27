# Description
* This is a bulkRNA-seq pipeline base on snakemake workflow that able to complete primary analysis!
* if you use pipeline in your papaer don`t forget citing the URL of this repository,thanks!<br>
# Graph of jobs
![pipeline](pipeline.png)
# Usage
## Clone project
```shell
git clone https://github.com/BioinfoCSM/BulkRNA_pipeline.git
cd BulkRNA_pipeline
```
## Deployment
```shell
#copy your reference genome fasta and gtf annotation file to BulkRNA_pipeline/ref and rename genome.fa genes.gtf separately
mkdir ref
cp path/you_reference.fa ref/genome.fa
cp path/you_annotation.gtf ref/genes.gtf
#pull a singularity container to BulkRNA_pipeline/image
mkdir image
cd image
singularity pull --arch amd64 library://bioinfocsm/share/bulkrna:v1.0
cd ../
#replace example rawdata/sample_name.fastq.gz with your project`s fastq file
rm rawdata/*
cp path/youfastq.fastq.gz rawdata/
```
