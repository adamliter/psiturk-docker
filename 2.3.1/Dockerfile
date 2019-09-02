FROM ubuntu:latest
MAINTAINER Adam Liter <io@adamliter.org>

ARG PSITURK_VERSION
ENV PSITURK_VERSION=${PSITURK_VERSION:-2.3.1} \
    PSITURK_GLOBAL_CONFIG_LOCATION=/psiturk/

RUN echo $PSITURK_VERSION && apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y \
        git \
    && if [ "${PSITURK_VERSION}" = "2.3.1" ] || [ "${PSITURK_VERSION}" = "2.3.0" ] ; then \
           apt-get install -y \
               python \
               python-pip \
           && pip install --upgrade \
                  psiturk==${PSITURK_VERSION} \
                  pymysql ; \
       else \
           apt-get install -y \
               python3 \
               python3-pip \
           && if [ "${PSITURK_VERSION}" = "dev" ] ; then \
                  pip3 install --upgrade \
                      git+https://github.com/NYUCCL/psiTurk.git@master ; \
              else \
                  pip3 install --upgrade \
                      psiturk==${PSITURK_VERSION} ; \
              fi \
           && pip3 install --upgrade pymysql ; \
       fi \
    && apt-get clean autoclean \
    && apt-get autoremove -y \
    && rm -rf /var/lib/{apt,dpkg,cache,log}/

WORKDIR /psiturk

EXPOSE 22362
