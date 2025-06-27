# Description
* This is a bulkRNA-seq pipeline base on [snakemake](https://snakemake.readthedocs.io/en/stable/) workflow that able to complete primary analysis.
* [Singularity](https://sylabs.io/singularity/) is supported in this pipeline.
* If you use pipeline in your paper don't forget citing the URL of this repository,thanks!<br>
# Graph of jobs
![pipeline](pipeline.png)
# Usage
## Clone project
```shell
git clone https://github.com/BioinfoCSM/BulkRNA_pipeline.git
cd BulkRNA_pipeline
#Tips:you need to set current directory to work_dir when change parameters in subsequent step!
```
## Deployment
```shell
#copy your reference genome fasta and gtf annotation file to BulkRNA_pipeline/ref and rename genome.fa/genes.gtf separately
mkdir ref
cp path/you_reference.fa ref/genome.fa
cp path/you_annotation.gtf ref/genes.gtf
#pull a singularity container to BulkRNA_pipeline/image
mkdir image
cd image
singularity pull --arch amd64 library://bioinfocsm/share/bulkrna:v1.0
or
singularity pull --arch amd64 library://bioinfocsm/share/bulkrna:sha256.5d3b05d0f6021dacea1d5bd2a411f5c411466feb36fb7a6ff8bed0a2800c6d43
cd ../
#replace example rawdata/sample_name.fastq.gz with your project`s fastq file
rm rawdata/*
cp path/youfastq.fastq.gz rawdata/
#prepare samples.txt and contrasts.txt
samples.txt:group_name\tsample_name
contrasts.txt:case_name\tcontrol_name
#Tips:\t represent tab separate
```
# Usage
## Change parameter
* `vi main.sh`
* change config.py command-line argument according your project requirement,write and quit
## Check the pipeline by dry run
```shell
snakemake --dry run -s Snakefile
```
## Run the main program
```shell
nohup sh main.sh &
```
## Check the log file when tasks completed
```shell
less snakemake.log
#Tips:you can view the information screenshot below after all of tasks completed
```
![1751007007795](https://github.com/user-attachments/assets/b411912b-ad13-4ff2-a747-5c4f0fdd0db3)
# Info
* Author:BioinfoCSM(Siming Cheng)
* Email:simoncheng158@gmail.com


