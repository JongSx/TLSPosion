FROM ubuntu:latest

MAINTAINER itdream "jongsx1203@gmail.com"
WORKDIR $HOME

ENV DOMAIN testing.com
ENV TARGET_IP 127.0.0.1
ENV TLSERVER_IP 

RUN apt-get update \
    && apt-get install python3 python3-pip git -y \
    && git clone https://github.com/jmdx/TLS-poison.git \
    && cd TLS-poison/client-hello-poison/custom-dns \
    && pip install -r requirements.txt \
    && python3 alternate-dns.py 
