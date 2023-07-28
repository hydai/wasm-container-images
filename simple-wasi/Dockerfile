# syntax=docker/dockerfile:1

FROM --platform=$BUILDPLATFORM rust:latest AS buildbase
WORKDIR /
RUN <<EOT bash
	set -ex
	apt-get update
	apt-get install -y \
		git \
		wget
	rustup target add wasm32-wasi
EOT

FROM buildbase AS build
RUN mkdir -p /simple-wasi
WORKDIR /simple-wasi
COPY Cargo.toml /simple-wasi
COPY src /simple-wasi/src
RUN cargo build --release --target wasm32-wasi

FROM scratch
ENTRYPOINT ["/simple_wasi.wasm", "Hello from", "WasmEdge"]
COPY --link --from=build /simple-wasi/target/wasm32-wasi/release/simple_wasi.wasm /simple_wasi.wasm
