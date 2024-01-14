FROM ubuntu:jammy as app

MAINTAINER Joshua Tobin <joshua.tobin@wustl.edu>
LABEL description="base docker for Ubuntu:jammy with common linux packages and software used in my other dockers. Notable packages include R, perl, python3, miniconda"
LABEL description="Built for compatibility with LSF. Variable ADDPATH is to facilitate easily adding executables to path when a new shell is made with LSF."

ARG DEBIAN_FRONTEND=noninteractive
ARG JAVA_VER="11"

ENV PACKAGES \
	apt-transport-https \
	apt-utils \
	aria2 \
	axel \
	build-essential \
	bzip2 \
	bc \
	bzip2 \
	ca-certificates \
	default-jdk \
	dirmngr \
	emacs \
	curl \
	gawk \
	g++ \
	gcc \
	git \
   	gnuplot \
	gnupg \
	less \
	libbz2-dev \
	libcurl4-gnutls-dev \
 	liblzma-dev \
	libncurses5-dev \
	libssl-dev \
	libxml2-dev \
	locales \
	make \
	nano \
	openjdk-${JAVA_VER}-jre \
	perl \
	pigz \
	procps \
	python3 \ 
   	python3-pip \
   	python3-dev \
   	rsync \
   	software-properties-common \
   	tar \
   	unzip \
   	vim  \
   	wget \
   	zip \
   	zlib1g-dev 

#Install package dependencies
RUN apt-get update && \
	apt-get install -y --no-install-recommends \
	${PACKAGES} &&\
	apt-get autoclean && rm -rf /var/lib/apt/lists/*

#Set Locale
RUN echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen \
	&& locale-gen en_US.utf8 \
	&& /usr/sbin/update-locale LANG=en_US.UTF-8

#Set shortcut to activate python with "python" 
RUN ln -s /usr/bin/python3 /usr/bin/python

#Install latest version of R and give access to different R libraries to install packages
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9 &&\
	add-apt-repository "deb https://cloud.r-project.org/bin/linux/ubuntu jammy-cran40/" &&\
	apt-get install -y --no-install-recommends r-base r-base-dev &&\
	chmod -R a+rwx /usr/lib/R/library /usr/local/lib/R/site-library /usr/lib/R/site-library /usr/share/R

#Install conda 
RUN mkdir miniconda &&\
	cd miniconda &&\
	wget -O miniconda.sh https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh &&\
	bash miniconda.sh -b -p /opt/conda &&\
	rm miniconda.sh &&\
	/opt/conda/bin/conda update conda

ENV ADDPATH /opt/conda:/opt/conda/bin
ENV PATH "$PATH:$ADDPATH"