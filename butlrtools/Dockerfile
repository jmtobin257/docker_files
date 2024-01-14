FROM jmt257/biobase:latest as app
ARG DEBIAN_FRONTEND=noninteractive

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="BUTLRtools for converting HiC matrices to BUTLR format installed on jmt257/biobase"
LABEL description="https://github.com/yuelab/BUTLRTools"

#Install BUTLRTools
RUN cd bioinformatics &&\
	git clone https://github.com/yuelab/BUTLRTools &&\
	chmod +x BUTLRTools/*

#Perl scripts in BUTLRTools use a different path than where perl is installed here
RUN ln -s /usr/bin/perl /usr/local/bin/perl

ENV ADDPATH="$ADDPATH:/bioinformatics/BUTLRTools"