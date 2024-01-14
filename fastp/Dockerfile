FROM jmt257/biobase:latest as app
ARG DEBIAN_FRONTEND=noninteractive

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="fastp adapter and QC trimming for NGS data installed on top of the jmt257/biobase docker"
LABEL description="https://github.com/OpenGene/fastp"

ARG FASTP_VER="0.23.4"

RUN cd bioinformatics &&\
	mkdir fastp && \
  	cd fastp && \ 
 	wget http://opengene.org/fastp/fastp.${FASTP_VER} && \
 	mv fastp.${FASTP_VER} fastp && \
  	chmod +x ./fastp 

ENV ADDPATH="$ADDPATH:/bioinformatics/fastp"