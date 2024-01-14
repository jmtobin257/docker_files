FROM jmt257/biobase:latest as app

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="STAR Aligner installed on top of the jmt257/biobase docker"
LABEL description="https://github.com/alexdobin/STAR"

ARG DEBIAN_FRONTEND=noninteractive
ARG STAR_VER="2.7.11a"

RUN cd bioinformatics &&\
	wget https://github.com/alexdobin/STAR/releases/download/${STAR_VER}/STAR_${STAR_VER}.zip &&\
	unzip STAR_${STAR_VER}.zip &&\
	mv STAR_${STAR_VER}/Linux_x86_64 STAR &&\
	rm -rf STAR_2.7.11a &&\
	rm STAR_2.7.11a.zip

ENV ADDPATH="${ADDPATH}:/bioinformatics/STAR"