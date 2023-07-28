# Hello World

In this example, we demonstrate how to run a hello world WASM application from the command line.

## Build with docker

```bash
docker buildx build --push --platform wasi/wasm -t hydai/wasm-image-demo:hello .
```

## Run with docker

```bash
docker run \
  --runtime=io.containerd.wasmedge.v1 \
  --platform=wasi/wasm \
  hydai/wasm-image-demo:hello
```

### Expected output

```
Hello WasmEdge from the container
```
