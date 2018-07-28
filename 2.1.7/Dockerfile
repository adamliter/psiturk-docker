FROM ubuntu:latest
MAINTAINER Adam Liter <io@adamliter.org>

ARG PSITURK_VERSION
ENV PSITURK_VERSION=${PSITURK_VERSION:-2.1.7} \
    PSITURK_GLOBAL_CONFIG_LOCATION=/psiturk/

RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y \
        python-dev \
        python-pip \
        libmysqlclient-dev \
    && test ${PSITURK_VERSION} = "dev" \
    && apt-get install -y \
        git \
    && pip install \
           git+https://github.com/NYUCCL/psiTurk.git@master \
           PyMySQL \
    || pip install --upgrade \
           psiturk==${PSITURK_VERSION} \
           mysql-python \
    && apt-get clean autoclean \
    && apt-get autoremove -y \
    && rm -rf /var/lib/{apt,dpkg,cache,log}/

WORKDIR /psiturk

EXPOSE 22362
