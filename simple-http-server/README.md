# WasmEdge WASI Socket Http Server Demo

This demo runs an echo server on `localhost`.

## Build

```shell
docker buildx build --push --platform wasi/wasm -t hydai/wasm-image-demo:simple-http-server .
```

## Run

```shell
docker run \
  -dp 1234:1234 \
  --runtime=io.containerd.wasmedge.v1 \
  --platform=wasi/wasm \
  hydai/wasm-image-demo:simple-http-server
```

## Test

```shell
curl -X POST http://localhost:1234 -d "Hello=WasmEdge"
echo: Hello=WasmEdge
```
