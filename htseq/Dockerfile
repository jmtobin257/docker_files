FROM jmt257/biobase:latest as app

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="Htseq, a program to generate RNAseq counts installed on top of the jmt257/biobase docker"
LABEL description="https://htseq.readthedocs.io/en/latest/"

ARG DEBIAN_FRONTEND=noninteractive

RUN conda update conda &&\
	conda create -y -n htseq -c bioconda -c conda-forge htseq

ENV ADDPATH="${ADDPATH}:/opt/conda/envs/htseq/bin"
