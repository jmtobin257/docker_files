FROM jmt257/biobase:latest as app
ARG DEBIAN_FRONTEND=noninteractive

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="Homer pipeline for HiC and/or ChiPseq installed on jmt257/biobase docker"
LABEL description="http://homer.ucsd.edu/homer/"

ARG BIOCONDUCTOR_VERSION=3.19
ENV BIOCONDUCTOR_USE_CONTAINER_REPOSITORY=FALSE

#Install R Packages Necessary for Homer
RUN R -e "install.packages(c('BiocManager'), dependencies=TRUE, repos='http://cran.rstudio.com/')" &&\
	R -e "BiocManager::install(c('edgeR', 'DESeq2'))"

#Install Homer
RUN cd bioinformatics &&\
	mkdir homer &&\
	cd homer &&\
	wget http://homer.ucsd.edu/homer/configureHomer.pl &&\
	perl configureHomer.pl -install

ENV ADDPATH="$/bioinformatics/homer:/bioinformatics/homer/bin"