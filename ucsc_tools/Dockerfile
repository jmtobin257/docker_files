FROM jmt257/biobase:latest as app
ARG DEBIAN_FRONTEND=noninteractive

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="Useful tools from UCSC to manipulate annotation files downloaded onto the jmt257/biobase docker"

#Install UCSC Aplications and Tools
RUN cd bioinformatics &&\ 
	mkdir UCSC_Tools &&\
	rsync -aP rsync://hgdownload.soe.ucsc.edu/genome/admin/exe/linux.x86_64/ UCSC_Tools/ &&\
	chmod +x UCSC_Tools/*

ENV ADDPATH="$ADDPATH:/bioinformatics/UCSC_Tools"