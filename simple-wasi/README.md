# Simple WASI application

In this example, we demonstrate how to run a standalone WASI application from the command line.

## Build with docker

```bash
docker buildx build --push --platform wasi/wasm -t hydai/wasm-image-demo:simple-wasi .
```

## Run with docker

```bash
docker run \                                                                                              130 ↵  5008  16:05:30
  --runtime=io.containerd.wasmedge.v1 \
  --platform=wasi/wasm \
  hydai/wasm-image-demo:simple-wasi
```

### Expected output

```
Random number: -150444377
Random bytes: [71, 181, 182, 205, 90, 197, 107, 29, 111, 128, 178, 181, 31, 61, 0, 130, 151, 89, 5, 182, 107, 129, 33, 159, 60, 47, 130, 147, 110, 65, 41, 58, 200, 81, 114, 202, 166, 54, 90, 134, 233, 185, 228, 37, 93, 196, 148, 1, 192, 176, 203, 86, 110, 164, 89, 221, 50, 208, 152, 154, 112, 73, 212, 95, 138, 93, 101, 96, 179, 212, 205, 209, 181, 156, 219, 109, 76, 218, 123, 157, 127, 120, 70, 199, 162, 67, 236, 210, 242, 106, 38, 251, 193, 15, 74, 252, 51, 243, 177, 110, 207, 230, 202, 42, 236, 14, 180, 199, 252, 57, 15, 253, 10, 227, 202, 27, 48, 74, 119, 12, 183, 165, 237, 129, 251, 244, 255, 171]
Printed from wasi: This is from a main function
This is from a main function
The env vars are as follows.
PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
HOSTNAME: bb244dd586cd
The args are as follows.
/simple_wasi.wasm
Hello from
WasmEdge
File content is This is in a file
```
