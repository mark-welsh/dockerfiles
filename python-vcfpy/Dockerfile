FROM ubuntu:18.04
MAINTAINER Mark Welsh (welshm3@email.chop.edu)

RUN apt update && apt install -y build-essential python3.8 python3-pip git wget zlib1g-dev libncurses5-dev libbz2-dev liblzma-dev
RUN /usr/bin/python3.8 -m pip install --upgrade pip
RUN /usr/bin/python3.8 -m pip install pysam vcfpy
#RUN pip3 install --upgrade pip 
#RUN pip3 install pysam vcfpy

RUN wget -O /usr/local/bin/htslib-1.10.2.tar.bz2 https://github.com/samtools/htslib/releases/download/1.10.2/htslib-1.10.2.tar.bz2 
RUN tar -xjf /usr/local/bin/htslib-1.10.2.tar.bz2 
RUN cd htslib-1.10.2 && ./configure && make

RUN mkdir -p /usr/local/bin && chmod 777 /usr/local/bin
