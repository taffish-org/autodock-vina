FROM ghcr.io/taffish-org/debian:12

LABEL maintainer="taffish@163.com"

WORKDIR /root

RUN apt-get update && apt-get install -y curl git gcc g++ make cmake build-essential libboost-all-dev swig python3-dev python3-pip python3-venv

RUN cd / && python3 -m venv vinaenv && . /vinaenv/bin/activate && \
    pip install --upgrade pip && pip install -U numpy scipy rdkit vina meeko gemmi prody

ENV PATH=/vinaenv/bin:${PATH}

RUN cd / && . /vinaenv/bin/activate && \
    curl -LO https://github.com/ccsb-scripps/AutoDock-Vina/archive/refs/tags/v1.2.7.tar.gz && \
    tar -zxvf /v1.2.7.tar.gz && cd /AutoDock-Vina-1.2.7/build/linux/release/ && make && \
    cp vina /usr/local/bin/ && cp vina_split /usr/local/bin/ && rm /v1.2.7.tar.gz

ENV TAFFISH_ENV=TAFFISH
ENV TAFFISH_NAME=autodock-vina
