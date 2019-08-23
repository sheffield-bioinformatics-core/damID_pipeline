FROM ubuntu:18.04
MAINTAINER Mark Dunning<m.j.dunning@sheffield.ac.uk>
RUN rm -rf /var/lib/apt/lists/*
ENV DEBIAN_FRONTEND=noninteractive 
RUN apt-get update  && apt-get install --fix-missing -y git wget unzip bowtie2 samtools build-essential python-dev 
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
WORKDIR /opt
RUN git clone https://github.com/owenjm/polii.gene.call.git
WORKDIR polii.gene.call
RUN chmod +x polii.gene.call
RUN ln -s /opt/polii.gene.call/polii.gene.call /usr/bin
WORKDIR /opt
RUN git clone https://github.com/owenjm/damid_misc.git
WORKDIR damid_misc
RUN chmod +x *
RUN ln -s /opt/damid_misc/* /usr/bin
WORKDIR /opt
RUN wget http://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v0.11.3.zip -P /opt
RUN unzip fastqc_v0.11.3.zip
RUN chmod 755 FastQC/fastqc
RUN ln -s /opt/FastQC/fastqc /usr/bin/fastqc
WORKDIR /opt
RUN wget https://bootstrap.pypa.io/get-pip.py
RUN python get-pip.py
RUN pip install multiqc
WORKDIR /home