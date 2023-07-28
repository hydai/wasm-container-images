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
RUN mkdir -p /simple-http-server
WORKDIR /simple-http-server
COPY Cargo.toml /simple-http-server
COPY src /simple-http-server/src
RUN cargo build --release --target wasm32-wasi

FROM scratch
ENTRYPOINT ["/http_server.wasm", "Hello from", "WasmEdge"]
COPY --link --from=build /simple-http-server/target/wasm32-wasi/release/http_server.wasm /http_server.wasm
