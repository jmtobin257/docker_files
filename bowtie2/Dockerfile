FROM jmt257/biobase:latest as app

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="bowtie2 alignerinstalled on top of the jmt257/biobase docker"
LABEL description="https://bowtie-bio.sourceforge.net/bowtie2/index.shtml"

ARG DEBIAN_FRONTEND=noninteractive
ARG BOWTIE2_VER="2.5.2"

#Install bowtie2
RUN cd bioinformatics &&\
	wget https://github.com/BenLangmead/bowtie2/releases/download/v${BOWTIE2_VER}/bowtie2-${BOWTIE2_VER}-linux-x86_64.zip &&\
	unzip bowtie2-${BOWTIE2_VER}-linux-x86_64.zip &&\
	rm bowtie2-${BOWTIE2_VER}-linux-x86_64.zip &&\
	mv bowtie2-${BOWTIE2_VER}-linux-x86_64 bowtie2 &&\
	chmod +x bowtie2/*

ENV ADDPATH="$ADDPATH:/bioinformatics/bowtie2"