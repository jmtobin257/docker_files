FROM jmt257/bowtie2:latest as app

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="HiCUP pipeline installed on top of the jmt257/bowtie2 docker"
LABEL description="https://www.bioinformatics.babraham.ac.uk/projects/hicup/"

ARG DEBIAN_FRONTEND=noninteractive
ARG HICUP_VER="0.9.2"

#Install R Package Dependencies
RUN R -e "install.packages(c('tidyverse', 'plotly'), dependencies=TRUE, repos='http://cran.rstudio.com/')"

#Install HiCUP
RUN cd bioinformatics &&\
	wget https://github.com/StevenWingett/HiCUP/archive/refs/tags/v${HICUP_VER}.tar.gz &&\
	tar -xzf v${HICUP_VER}.tar.gz &&\
	rm v${HICUP_VER}.tar.gz &&\
	mv HiCUP-${HICUP_VER} HiCUP &&\
	chmod +x HiCUP/*

ENV ADDPATH="$ADDPATH:/bioinformatics/HiCUP"