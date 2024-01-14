FROM jmt257/biobase:latest as app

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="Common tools used for cutnrun analysis to facilitate using one docker for the entire pipeline. Built from jmt257/biobase docker"

ARG DEBIAN_FRONTEND=noninteractive
ARG BOWTIE2_VER="2.5.2"
ARG FASTQC_VER="0.12.1"
ARG MULTIQC_VER="1.18"
ARG PANDOC_VER="3.1.11"
ARG PICARD_VER="2.21.5"
ARG SUBREAD_VER="2.0.2"
ARG SEACR_VER="1.3"
ARG TRIMGALORE_VER="0.6.10"
ARG MACS2_VER="2.2.9.1"

#Install required R Packages
RUN R -e "install.packages(c('tidyverse', 'plotly', 'ggplot2', 'BiocManager', 'edgeR', 'DESeq2'), dependencies=TRUE, repos='http://cran.rstudio.com/')"

#Install bowtie2
RUN cd bioinformatics &&\
	wget https://github.com/BenLangmead/bowtie2/releases/download/v${BOWTIE2_VER}/bowtie2-${BOWTIE2_VER}-linux-x86_64.zip &&\
	unzip bowtie2-${BOWTIE2_VER}-linux-x86_64.zip &&\
	rm bowtie2-${BOWTIE2_VER}-linux-x86_64.zip &&\
	mv bowtie2-${BOWTIE2_VER}-linux-x86_64 bowtie2 &&\
	chmod +x bowtie2/*

#Install fastqc
RUN cd bioinformatics &&\ 
	wget https://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v${FASTQC_VER}.zip &&\
	unzip fastqc_v${FASTQC_VER}.zip &&\
	rm fastqc_v${FASTQC_VER}.zip &&\
	chmod +x FastQC/fastqc

#Install bedGraphToBigWig
RUN cd bioinformatics &&\ 
	wget -q http://hgdownload.soe.ucsc.edu/admin/exe/linux.x86_64/bedGraphToBigWig &&\
	chmod +x bedGraphToBigWig

#Install subread
RUN cd bioinformatics &&\
	wget -q https://github.com/ShiLab-Bioinformatics/subread/releases/download/${SUBREAD_VER}/subread-${SUBREAD_VER}-Linux-x86_64.tar.gz &&\
	tar -xzvf subread-${SUBREAD_VER}-Linux-x86_64.tar.gz &&\
	rm subread-${SUBREAD_VER}-Linux-x86_64.tar.gz &&\
	mv subread-${SUBREAD_VER}-Linux-x86_64 subread &&\
	chmod +x subread/bin/*

#Install Homer
RUN cd bioinformatics &&\
	mkdir homer &&\
	cd homer &&\
	wget http://homer.ucsd.edu/homer/configureHomer.pl &&\
	perl configureHomer.pl -install

#Create a conda environment and install macsr, seacr, multiqc, and TrimGalore
RUN conda create -n cutnrun -c bioconda -c conda-forge \
	"multiqc=${MULTIQC_VER}" \
	"seacr=${SEACR_VER}" \
	"macs2=${MACS2_VER}" \
	"trim-galore=${TRIMGALORE_VER}"

ENV ADDPATH="$ADDPATH:/bioinformatics:/bioinformatics/bowtie2:/bioinformatics/FastQC:/bioinformatics/subread/bin:/bioinformatics/homer:/bioinformatics/homer/bin:/opt/conda/envs/cutnrun/bin"
