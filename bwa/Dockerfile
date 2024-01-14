FROM jmt257/biobase:latest as app

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="BWA installed on top of the jmt257/biobase docker"
LABEL description="https://github.com/lh3/bwa"

ARG DEBIAN_FRONTEND=noninteractive
ARG BWA_VER="0.7.17"

RUN apt-get update && \
	apt-get install -y --no-install-recommends bwa  &&\
	apt-get autoclean && rm -rf /var/lib/apt/lists/*
