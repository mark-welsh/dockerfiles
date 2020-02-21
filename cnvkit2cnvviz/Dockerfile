FROM alpine:latest as intermediate
LABEL maintainer="Mark Welsh <welshm3@email.chop.edu>"

RUN apk add git openssh

ARG SSH_PRIVATE_KEY
ARG SSH_PUBLIC_KEY

RUN mkdir /root/.ssh/
RUN echo "${SSH_PRIVATE_KEY}" > /root/.ssh/id_rsa
RUN chmod 600 /root/.ssh/id_rsa
RUN echo "${SSH_PUBLIC_KEY}" > /root/.ssh/id_rsa.pub
RUN ssh-keyscan github.research.chop.edu > /root/.ssh/known_hosts

RUN git clone git@github.research.chop.edu:DGD/cancer-whole-genome.git

FROM ubuntu:18.04
LABEL maintainer="Mark Welsh <welshm3@email.chop.edu>"
COPY --from=intermediate /cancer-whole-genome/tools/make_panels.py /usr/bin/make_panels.py
COPY --from=intermediate /cancer-whole-genome/tools/cnvkit2cnvviz.sh /usr/bin/cnvkit2cnvviz.sh

RUN apt update && apt install -y bcftools bedtools python-pip && \
apt autoclean -y && apt autoremove -y

RUN pip install --upgrade pip
RUN pip install pandas
