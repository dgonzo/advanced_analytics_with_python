FROM ubuntu:14.04

MAINTAINER Gonzo "gonzo@ziff.io"

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && apt-get install -y wget bzip2 ca-certificates && apt-get clean
RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
RUN echo 'export PATH=/opt/anaconda/bin:$PATH' > /etc/profile.d/conda.sh
RUN wget --quiet https://repo.continuum.io/miniconda/Miniconda-latest-Linux-x86_64.sh && \
    /bin/bash /Miniconda-latest-Linux-x86_64.sh -b -p /opt/anaconda && \
    rm Miniconda-latest-Linux-x86_64.sh
ENV PATH /opt/anaconda/bin:$PATH
ADD requirements.txt /src/requirements.txt
RUN cd /src; conda create -c https://conda.anaconda.org/gonzo --yes --file \
    src/requirements.txt
