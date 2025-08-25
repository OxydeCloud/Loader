FROM buildpack-deps:trixie

LABEL org.opencontainers.image.source=https://github.com/OxydeCloud/Loader

ENV RUSTUP_HOME=/usr/local/rustup \
    CARGO_HOME=/usr/local/cargo \
    PATH=/usr/local/cargo/bin:$PATH \
    RUST_VERSION=nightly

RUN set -eux; \
    url="https://raw.githubusercontent.com/rust-lang/rustup/refs/heads/master/rustup-init.sh"; \
    wget "$url"; \
    chmod +x rustup-init.sh; \
    ./rustup-init.sh -y --no-modify-path --profile minimal --default-toolchain $RUST_VERSION --allow-downgrade --default-host ${rustArch}; \
    rm rustup-init.sh; \
    chmod -R a+w $RUSTUP_HOME $CARGO_HOME; \
    rustup --version; \
    cargo --version; \
    rustc --version; \
    rustup target add wasm32-unknown-unknown \
    cargo install cargo-leptos --locked
