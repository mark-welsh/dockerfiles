FROM ubuntu:18.04
LABEL maintainer="Mark Welsh <welshm3@email.chop.edu>"

RUN apt update && apt install -y bcftools bedtools python-pip git && \
apt autoclean -y && apt autoremove -y

RUN pip install --upgrade pip
RUN pip install pandas

RUN mkdir -p /usr/local/bin && chmod 777 /usr/local/bin
