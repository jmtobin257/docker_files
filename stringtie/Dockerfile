FROM jmt257/biobase:latest as app

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="Stringtie2: transcript assembly and quantification for RNA-seq installed on jmt257/biobase Docker"
LABEL description="GFFcompare and ballgown are also included to facilitate downstream analyses"
LABEL description="https://github.com/skovaka/stringtie2"

ARG DEBIAN_FRONTEND=noninteractive
ARG STRINGTIE_VER="2.2.1"
ARG GFF_COMPARE_VER="0.12.6"

#Install Stringtie
RUN cd bioinformatics &&\
	wget http://ccb.jhu.edu/software/stringtie/dl/stringtie-${STRINGTIE_VER}.Linux_x86_64.tar.gz &&\
	tar -xzvf stringtie-${STRINGTIE_VER}.Linux_x86_64.tar.gz &&\
	mv stringtie-${STRINGTIE_VER}.Linux_x86_64 stringtie &&\
	rm stringtie-2.2.1.Linux_x86_64.tar.gz

#Install GFFCompare
RUN cd bioinformatics &&\
	wget http://ccb.jhu.edu/software/stringtie/dl/gffcompare-${GFF_COMPARE_VER}.Linux_x86_64.tar.gz &&\
	tar -xzvf gffcompare-${GFF_COMPARE_VER}.Linux_x86_64.tar.gz &&\
	rm gffcompare-${GFF_COMPARE_VER}.Linux_x86_64.tar.gz &&\
	mv gffcompare-${GFF_COMPARE_VER}.Linux_x86_64 gffcompare

#Install ballgown
RUN R -e "install.packages(c('BiocManager'), dependencies=TRUE, repos='http://cran.rstudio.com/')" &&\
	R -e "BiocManager::install(c('ballgown'))"

ENV ADDPATH="$ADDPATH:/bioinformatics/stringtie:/bioinformatics/gffcompare"