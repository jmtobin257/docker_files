FROM jmt257/biobase:latest as app
MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="DROP pipeline installed on jmt257/biobase docker"
LABEL description="https://github.com/gagneurlab/drop"

ARG DEBIAN_FRONTEND=noninteractive
ARG DROP_VER="1.3.3"

RUN conda create -y -c conda-forge -c bioconda -n drop \
  "drop=${DROP_VER}" \
  snakemake

ENV ADDPATH="/opt/conda/envs/drop/bin"

