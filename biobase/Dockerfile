FROM jmt257/base:latest as app
ARG DEBIAN_FRONTEND=noninteractive

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="Built from jmt257/base. I have added some common bioinformatics tools that i use with mose of my dockers."


ARG BEDTOOLS_VER="2.31.1"
ARG IGV_VER="2.16.2"
ARG PICARD_VER="3.1.1"
ARG SAMTOOLS_VER="1.19"

RUN mkdir /bioinformatics

#Install Samtools
RUN cd bioinformatics &&\
	wget https://github.com/samtools/samtools/releases/download/${SAMTOOLS_VER}/samtools-${SAMTOOLS_VER}.tar.bz2 &&\
	tar -xjf samtools-${SAMTOOLS_VER}.tar.bz2 &&\
	rm samtools-${SAMTOOLS_VER}.tar.bz2 &&\
	mv samtools-${SAMTOOLS_VER} samtools &&\
	cd samtools &&\
	./configure &&\
	make &&\
	make install

#Install Bedtools
RUN cd bioinformatics &&\
	wget -q https://github.com/arq5x/bedtools2/archive/refs/tags/v${BEDTOOLS_VER}.tar.gz &&\
  	tar -xzf v${BEDTOOLS_VER}.tar.gz &&\
  	rm v${BEDTOOLS_VER}.tar.gz &&\
  	mv bedtools2-${BEDTOOLS_VER} bedtools &&\
	cd bedtools &&\
	make &&\
	make install

#Install picard
RUN cd bioinformatics &&\ 
	mkdir picard &&\
	cd picard &&\
	curl -SL https://github.com/broadinstitute/picard/releases/download/${PICARD_VER}/picard.jar \
	> picard.jar &&\
	chmod +x /bioinformatics/picard/picard.jar

#Install SRAToolkit
RUN cd bioinformatics &&\
	wget https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/current/sratoolkit.current-ubuntu64.tar.gz &&\
	tar -xzvf sratoolkit.current-ubuntu64.tar.gz &&\
	rm sratoolkit.current-ubuntu64.tar.gz &&\
	mv sratoolkit*ubuntu64 sratoolkit &&\
	chmod +x sratoolkit/bin/*

#Install IGV
RUN cd bioinformatics &&\
	wget https://data.broadinstitute.org/igv/projects/downloads/2.16/IGV_${IGV_VER}.zip &&\
	unzip IGV_${IGV_VER}.zip &&\
	rm IGV_${IGV_VER}.zip &&\
	mv IGV_${IGV_VER} IGV

ENV ADDPATH="/bioinformatics:/bioinformatics/fastp:/bioinformatics/IGV:/bioinformatics/sratoolkit:/bioinformatics/sratoolkit/bin"
ENV PICARD=/bioinformatics/picard/picard.jar






