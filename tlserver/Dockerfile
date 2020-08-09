FROM rust

WORKDIR /usr/src/app

# Install tlserver
RUN apt-get update \
    && apt-get install git gcc -y \
    && git clone https://github.com/jmdx/TLS-poison.git . \
    && cd client-hello-poisoning/custom-tls \
    && cargo build \
    && cargo install --path .

WORKDIR /usr/src/app/client-hello-poisoning/custom-tls

EXPOSE 8443

CMD ["custom-tls", "--verbose", "--certs", "/usr/src/app/rustls/test-ca/rsa/end.fullchain", "--key", "/usr/src/app/rustls/test-ca/rsa/end.rsa", "-p", "8443", "http"]
