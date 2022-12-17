FROM mcr.microsoft.com/devcontainers/rust:0-1-bullseye

RUN apt update && apt install binaryen -y

RUN rustup default stable
RUN rustup target add wasm32-unknown-unknown
RUN rustup update && rustup component add clippy rustfmt
# Check cargo version
RUN cargo --version

# cargo template plugin and sccache
RUN cargo install sccache
RUN cargo install cargo-generate --features vendored-openssl

# Check sccache version
RUN sccache --version

# Use sccache. Users can override this variable to disable caching.
ENV RUSTC_WRAPPER=sccache