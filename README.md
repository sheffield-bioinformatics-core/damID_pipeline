# damID_pipeline

Wrapper for easy installation of the damidseq_pipeline provided at http://owenjm.github.io/damidseq_pipeline/. Includes the damsidseq pipeline, bowtie2 and samtools

## Example usage (on sharc)

```
#create singularity image from the dockerhub entry
cd /shared/bioinformatics_core1/Shared/software/singularity/
singularity pull docker://markdunning/damid-pipeline

# download the reference files and build bowtie2 index
cd /shared/bioinformatics_core1/Shared/reference_files/damID/
wget ftp://ftp.flybase.net/releases/FB2014_03/dmel_r5.57/fasta/dmel-all-chromosome-r5.57.fasta.gz
singularity exec damid-pipeline_latest.sif gunzip dmel-all-chromosome-r5.57.fasta.gz
singularity exec damid-pipeline_latest.sif bowtie2-build dmel-all-chromosome-r5.57.fasta dmel_r5.57

wget https://github.com/owenjm/damidseq_pipeline/raw/gh-pages/pipeline_gatc_files/Dmel_r5.57.GATC.gff.gz
```
Now run from a folder containing fastq.gz files to be analysed

```
singularity exec /shared/bioinformatics_core1/Shared/software/singularity/damid-pipeline_latest.sif damidseq_pipeline --gatc_frag_file=/shared/bioinformatics_core1/Shared/reference_files/damID/Dmel_r5.57.GATC.gff.gz --bowtie2_genome_dir=/shared/bioinformatics_core1/Shared/reference_files/damID/dmel_r5.57
```
