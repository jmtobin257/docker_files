FROM jmt257/biobase:latest as app

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="minimap2 alignerinstalled on top of the jmt257/biobase docker"
LABEL description="https://github.com/lh3/minimap2"

ARG DEBIAN_FRONTEND=noninteractive

RUN git clone https://github.com/lh3/minimap2 &&\
	cd minimap2 &&\
	make 

ENV ADDPATH="${ADDPATH}:/minimap2:/picard"

