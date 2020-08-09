FROM rust

WORKDIR /app

# Install tlserver
RUN apt-get update \
    && apt-get install git gcc -y \
    && git clone https://github.com/jmdx/TLS-poison.git . \
    && cd TLS-poison/client-hello-poisoning/custom-tls \
    && cargo build \
    && cargo install --path .

WORKDIR /app/client-hello-poisoning/custom-tls

EXPOSE 8443

CMD ["/usr/local/cargo/bin/custom-tls", "--verbose", "--certs", "/app/rustls/test-ca/rsa/end.fullchain", "--key", "/app/rustls/test-ca/rsa/end.rsa", "-p", "8443", "http"]
