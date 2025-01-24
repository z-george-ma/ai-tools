FROM nvidia/cuda:12.6.3-cudnn-devel-ubuntu24.04 AS build

# change -DCMAKE_CUDA_ARCHITECTURES=75 to your GPU architecture
RUN apt update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends ca-certificates git cmake python3 python3-venv \
    && git clone --recursive --depth 1 https://github.com/leejet/stable-diffusion.cpp.git /app \
    && mkdir -p /app/build && cd /app/build \
    && cmake .. -DSD_CUDA=ON -DCMAKE_CUDA_ARCHITECTURES=75 \
    && cmake --build . --config Release

RUN git clone --depth 1 https://github.com/daniandtheweb/sd.cpp-webui /web \
    && cp /app/build/bin/sd /web/ \
    && cd /web \
    && rm -rf .git \
    && python3 -m venv env \
    && ( . env/bin/activate; \
      pip install -r requirements.txt; \
    )

FROM nvidia/cuda:12.6.3-cudnn-runtime-ubuntu24.04
RUN apt update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends ca-certificates python3
COPY --from=build /web /app

ENV PYTHONUNBUFFERED=1
ENV GRADIO_SERVER_NAME=0.0.0.0
ENV GRADIO_ANALYTICS_ENABLED=False

WORKDIR /app

VOLUME [ \
    "/app/models/checkpoints", \
    "/app/models/controlnet", \
    "/app/models/embeddings", \
    "/app/models/photomaker", \
    "/app/models/unet", \
    "/app/models/vae", \
    "/app/models/loras", \
    "/app/models/taesd", \
    "/app/models/upscale_models" \
]

EXPOSE 7860
ENTRYPOINT ["/app/env/bin/python3"]
CMD ["/app/sdcpp_webui.py"]
