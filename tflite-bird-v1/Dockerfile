FROM scratch
ADD libtensorflowlite_c.so /
ADD libwasmedgePluginWasiNN.so /
ADD wasmedge-wasinn-example-tflite-bird-image.wasm /
ADD lite-model_aiy_vision_classifier_birds_V1_3.tflite /
ADD bird.jpg /
CMD ["/wasmedge-wasinn-example-tflite-bird-image.wasm", "lite-model_aiy_vision_classifier_birds_V1_3.tflite", "bird.jpg"]
