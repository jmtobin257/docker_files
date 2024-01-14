FROM jmt257/biobase:latest as app

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="Salmon, a quasi-mapper for RNAseq quantification installed on top of the jmt257/biobase docker"
LABEL description="https://combine-lab.github.io/salmon/getting_started/"

ARG DEBIAN_FRONTEND=noninteractive

RUN conda update conda &&\
	conda create -y -n salmon -c bioconda -c conda-forge salmon

ENV ADDPATH="${ADDPATH}:/opt/conda/envs/salmon/bin"
