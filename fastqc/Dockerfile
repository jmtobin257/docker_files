FROM jmt257/biobase:latest as app

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="FastQC and MultiQC installed on top of the jmt257/biobase docker"
LABEL description="https://www.bioinformatics.babraham.ac.uk/projects/fastqc/"
LABEL description="https://github.com/MultiQC/MultiQC"


ARG DEBIAN_FRONTEND=noninteractive
ARG FASTQC_VER="0.12.1"
ARG MULTIQC_VER="1.19"

#Install fastqc
RUN cd bioinformatics &&\ 
	wget https://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v${FASTQC_VER}.zip &&\
	unzip fastqc_v${FASTQC_VER}.zip &&\
	rm fastqc_v${FASTQC_VER}.zip &&\
	chmod +x FastQC/fastqc

#Install MultiQC
RUN conda create -y -c bioconda -c conda-forge -n multiqc \
	"multiqc==${MULTIQC_VER}"

ENV ADDPATH="$ADDPATH:/bioinformatics/FastQC"