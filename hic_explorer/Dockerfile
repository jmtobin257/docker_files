FROM jmt257/biobase:latest as app

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="HiC Explorer installed on the jmt257/biobase docker"
LABEL description="https://hicexplorer.readthedocs.io/en/latest/index.html"

ARG DEBIAN_FRONTEND=noninteractive

#Install HiC Explorer
RUN conda create -y -n hicexplorer -c bioconda -c conda-forge  \
	hicexplorer

ENV ADDPATH="$ADDPATH:/opt/conda/envs/hicexplorer/bin"


