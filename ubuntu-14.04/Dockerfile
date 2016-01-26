FROM ubuntu:14.04

MAINTAINER Mark Stillwell <mark@stillwell.me>

RUN \
  apt-get update && \
  apt-get upgrade -y && \
  apt-get install -y \
  build-essential \
  git \
  libseccomp2 \
  libseccomp-dev 

RUN mkdir -p /usr/src && \
    cd /usr/src && \
    git clone https://github.com/marklee77/lkl-linux.git && \
    cd lkl-linux && \
    git checkout franken && \
    cd /usr/src && \
    git clone https://github.com/marklee77/musl.git && \
    cd musl && \
    git checkout franken && \
    cd /usr/src && \
    git clone https://github.com/marklee77/frankenlibc.git && \
    git checkout lkl-musl 

ENV SUDO_UID=1000
ENV FRANKEN_VERBOSE=1

RUN ./build.sh -d /usr/local -b /usr/local/bin clean && \
    cp rumpobj/tests/hello /usr/local/bin/franken.hello && \
    make clean
