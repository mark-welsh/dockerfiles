FROM ubuntu:18.04
LABEL maintainer="Mark Welsh <welshm3@email.chop.edu>"

RUN apt update && apt install -y bcftools bedtools wget && \
apt autoclean -y && apt autoremove -y

RUN wget https://github.com/dellytools/delly/releases/download/v0.7.9/delly_v0.7.9_parallel_linux_x86_64bit && chmod +x ./delly_v0.7.9_parallel_linux_x86_64bit && ln -s ./delly_v0.7.9_parallel_linux_x86_64bit ./delly
