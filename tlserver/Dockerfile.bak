# Dockerfile for TLS server

FROM ubuntu:latest

MAINTAINER itdream "jongsx1203@gmail.com"

# Modified source to aliyun
RUN sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list \
    && apt-get clean \
    && apt-get update \
    && apt-get install gcc git redis curl -y

# Install rust
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs -o rustup-init.sh \
    && sh rustup-init.sh -y

# Cloning TLS-posion
RUN git clone https://github.com/jmdx/TLS-poison.git \
    && cd TLS-poison/client-hello-poisoning/custom-tls \
    && $HOME/.cargo/bin/cargo build

# Exposing 8443 port
EXPOSE 8443

