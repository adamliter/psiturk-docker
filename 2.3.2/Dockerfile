FROM ubuntu:latest
MAINTAINER Adam Liter <io@adamliter.org>

ARG PSITURK_VERSION
ENV PSITURK_VERSION=${PSITURK_VERSION:-2.3.2} \
    PSITURK_GLOBAL_CONFIG_LOCATION=/psiturk/

RUN apt-get update -y \
    && apt-get install -y \
        python-dev \
        python-pip \
        libmysqlclient-dev \
        git \
    && test ${PSITURK_VERSION} = "dev" \
    && pip install \
           git+https://github.com/NYUCCL/psiTurk.git@master \
           PyMySQL \
    || pip install --upgrade \
           psiturk==${PSITURK_VERSION} \
           mysql-python \
           certifi \
    && apt-get clean autoclean \
    && apt-get autoremove -y \
    && rm -rf /var/lib/{apt,dpkg,cache,log}/

WORKDIR /psiturk

EXPOSE 22362
