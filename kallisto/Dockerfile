FROM jmt257/biobase:latest as app

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="Kallisto, a pseudo-aligner for RNAseq quantification installed on top of the jmt257/biobase docker"
LABEL description="https://github.com/pachterlab/kallisto#"

ARG DEBIAN_FRONTEND=noninteractive

RUN conda update conda &&\
	conda create -y -n kallisto -c bioconda -c conda-forge kallisto

ENV ADDPATH="${ADDPATH}:/opt/conda/envs/kallisto/bin"
