FROM jmt257/biobase:latest as app

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="subread package, which includes featureCounts for quantifying RNAseq data installed on top of the jmt257/biobase docker"
LABEL description="https://github.com/ShiLab-Bioinformatics/subread"

ARG DEBIAN_FRONTEND=noninteractive
ARG SUBREAD_VER="2.0.6"

RUN cd bioinformatics &&\
	wget https://sourceforge.net/projects/subread/files/subread-${SUBREAD_VER}/subread-${SUBREAD_VER}-source.tar.gz &&\
	tar -xzvf subread-${SUBREAD_VER}-source.tar.gz &&\
	rm subread-${SUBREAD_VER}-source.tar.gz &&\
	cd subread-${SUBREAD_VER}-source/src &&\
	make -f Makefile.Linux &&\
	mv /bioinformatics/subread-${SUBREAD_VER}-source/bin/ /bioinformatics/subread

ENV ADDPATH="${ADDPATH}:/bioinformatics/subread"
