FROM ghcr.io/taffish-org/debian:12

LABEL maintainer="taffish@163.com"

WORKDIR /root

RUN apt-get update && apt-get install -y curl git gcc g++ make

RUN apt-get update && apt-get install -y libboost-all-dev swig python3-dev python3-pip python3-venv && \
    cd / && python3 -m venv vinaenv && . /vinaenv/bin/activate && \
    pip install --upgrade pip && pip install -U numpy scipy rdkit vina meeko gemmi prody

RUN cd / && curl -LO https://github.com/ccsb-scripps/AutoDock-Vina/releases/download/v1.2.7/vina_1.2.7_linux_$(uname -m) && \
    curl -LO https://github.com/ccsb-scripps/AutoDock-Vina/releases/download/v1.2.7/vina_split_1.2.7_linux_$(uname -m) && \
    chmod +x /vina_1.2.7_linux_$(uname -m) && chmod +x /vina_split_1.2.7_linux_$(uname -m) && \
    mv /vina_1.2.7_linux_$(uname -m) /usr/local/bin/vina && mv /vina_split_1.2.7_linux_$(uname -m) /usr/local/bin/vina_split

ENV TAFFISH_ENV=TAFFISH
ENV TAFFISH_NAME=autodock-vina
