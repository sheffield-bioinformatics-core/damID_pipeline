FROM ubuntu:18.04
MAINTAINER Mark Dunning<m.j.dunning@sheffield.ac.uk>
RUN rm -rf /var/lib/apt/lists/*
ENV DEBIAN_FRONTEND=noninteractive 
RUN apt-get update  && apt-get install --fix-missing -y git wget unzip bowtie2 samtools
WORKDIR /opt
RUN git clone https://github.com/owenjm/damidseq_pipeline.git
WORKDIR damidseq_pipeline
RUN chmod +x damidseq_pipeline
RUN ln -s /opt/damidseq_pipeline/damidseq_pipeline /usr/bin
WORKDIR /opt
RUN git clone https://github.com/owenjm/find_peaks.git
WORKDIR find_peaks
RUN chmod +x find_peaks
RUN ln -s /opt/find_peaks/find_peaks /usr/bin
RUN git clone https://github.com/owenjm/polii.gene.call.git
WORKDIR polii.gene.call
RUN chmod +x polii.gene.call
RUN ln -s /opt/polii.gene.call/polii.gene.call /usr/bin
RUN git clone https://github.com/owenjm/damid_misc.git
WORKDIR damid_misc
RUN mkdir /data
WORKDIR /data
RUN wget ftp://ftp.flybase.net/releases/FB2014_03/dmel_r5.57/fasta/dmel-all-chromosome-r5.57.fasta.gz 
RUN gunzip dmel-all-chromosome-r5.57.fasta.gz
RUN bowtie2-build dmel-all-chromosome-r5.57.fasta dmel_r5.57
RUN wget https://github.com/owenjm/damidseq_pipeline/raw/gh-pages/pipeline_gatc_files/Dmel_r5.57.GATC.gff.gz
WORKDIR /home