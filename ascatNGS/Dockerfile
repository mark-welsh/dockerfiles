FROM ubuntu:16.04
LABEL maintainer="Mark Welsh <welshm3@email.chop.edu>"

ARG DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y build-essential libbz2-dev libcurl4-gnutls-dev libgnutls-dev liblzma-dev libncurses5-dev libssl-dev locales nettle-dev wget zlib1g-dev curl libexpat1-dev libgoogle-perftools-dev lsof time libgd-perl psmisc moreutils git r-base perl libgd-perl && \
apt autoclean -y && apt autoremove -y

RUN mkdir -p /usr/local/bin/ascat-ngs

# setup cpgBigwig dependency
RUN cd /usr/local/bin/ascat-ngs && \
wget https://github.com/cancerit/cgpBigWig/archive/1.2.0.tar.gz && \
tar -zxf 1.2.0.tar.gz && cd cgpBigWig-1.2.0 && ./setup.sh ..

ENV PATH="/usr/local/bin/ascat-ngs/bin:${PATH}"

# setup PCAP dependency
RUN cd /usr/local/bin/ascat-ngs && \
wget https://github.com/cancerit/PCAP-core/archive/5.0.3.tar.gz && \
tar -zxf 5.0.3.tar.gz && cd PCAP-core-5.0.3 && ./setup.sh ..

ENV PATH="/usr/local/bin/ascat-ngs/biobambam2/bin:/usr/local/bin/ascat-ngs/bin:${PATH}"
ENV PERL5LIB="/usr/local/bin/ascat-ngs/lib/perl5:${PERL5LIB}"

RUN cd /usr/local/bin/ascat-ngs && \
wget https://github.com/cancerit/cgpVcf/archive/v2.2.1.tar.gz && \
tar -zxf v2.2.1.tar.gz && cd cgpVcf-2.2.1 && ./setup.sh ..

RUN cd /usr/local/bin/ascat-ngs && \
wget https://github.com/cancerit/alleleCount/archive/4.1.0.tar.gz && \
tar -zxf 4.1.0.tar.gz && cd alleleCount-4.1.0 && ./setup.sh ..

RUN mkdir -p /usr/local/bin/ascat-ngs/R

ENV R_LIBS="/usr/local/bin/ascat-ngs/R"

RUN cd /usr/local/bin/ascat-ngs/R && Rscript -e 'install.packages("RColorBrewer", repos = "https://cloud.r-project.org")'

RUN cd /usr/local/bin/ascat-ngs && \
wget https://github.com/cancerit/ascatNgs/archive/4.3.3.tar.gz && \
tar -zxf 4.3.3.tar.gz && cd ascatNgs-4.3.3 && ./setup.sh ..
