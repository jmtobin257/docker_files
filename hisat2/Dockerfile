FROM jmt257/biobase:latest as app

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="Hisat2 Aligner installed on top of the jmt257/biobase docker"
LABEL description="https://github.com/alexdobin/STAR"

ARG DEBIAN_FRONTEND=noninteractive
ARG HISAT2_VER="2.2.1"

RUN cd bioinformatics &&\
	curl -s https://cloud.biohpc.swmed.edu/index.php/s/oTtGWbWjaxsQ2Ho/download > hisat2-${HISAT2_VER}-Linux_x86_64.zip &&\
	unzip hisat2-${HISAT2_VER}-Linux_x86_64.zip &&\
	mv hisat2-${HISAT2_VER} hisat2 &&\
	rm hisat2-${HISAT2_VER}-Linux_x86_64.zip

ENV ADDPATH="${ADDPATH}:/bioinformatics/hisat2"
ENV HISAT2_BUILD=/bioinformatics/hisat2/hisat2-build
