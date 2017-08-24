FROM ubuntu:latest
MAINTAINER Adam Liter <io@adamliter.org>

ARG PSITURK_VERSION
ENV PSITURK_VERSION=${PSITURK_VERSION:-2.2.3} \
    PSITURK_GLOBAL_CONFIG_LOCATION=/psiturk/

RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y \
        python \
        python-pip \
    && pip install --upgrade \
        pip \
        setuptools \
        wheel \
    && pip install --upgrade \
        psiturk==${PSITURK_VERSION} \
    && rm -rf /var/lib/apt

WORKDIR /psiturk

EXPOSE 22362
