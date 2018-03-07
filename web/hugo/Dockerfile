FROM debian:stretch-slim

MAINTAINER ysicing

ENV TZ Asia/Shanghai

RUN echo 'APT::Install-Recommends 0;' >> /etc/apt/apt.conf.d/01norecommends \
    && echo 'APT::Install-Suggests 0;' >> /etc/apt/apt.conf.d/01norecommends \
    && apt update \
    && apt install -y hugo curl \
    && apt-get autoremove \
    && apt-get clean all \
    && rm -rf /var/lib/apt/lists/* /usr/share/doc/* /usr/share/man/* 

RUN mkdir -p /opt/Gowo

COPY . /opt/Gowo

WORKDIR ./opt/Gowo

ENTRYPOINT [ "hugo","server","-b","0.0.0.0","-p","21313","-w"]