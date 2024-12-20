ARG BUILD_DATE
ARG FASTSDCPU_VERSION=1.0.0-beta.100

FROM ubuntu:24.04 AS build
ARG FASTSDCPU_VERSION

RUN apt update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends ca-certificates python3 ffmpeg

ADD . /patch
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends git python3-venv \
    && git clone https://github.com/rupeshs/fastsdcpu.git /app \
    && cd /app \
    && git checkout -b build v$FASTSDCPU_VERSION \
    && git apply /patch/v$FASTSDCPU_VERSION.patch \
    && rm -rf .git \
    && python3 -m venv env \
    && ( . env/bin/activate; \
      pip install webp==0.4.0; \
      pip install torchvision==0.20.1+cpu --index-url https://download.pytorch.org/whl/cpu; \
      pip install -r requirements.txt; \
    ) \
    && rm -rf /var/lib/apt/lists/* \
    && chmod +x start.sh start-webui.sh start-webserver.sh

FROM ubuntu:24.04
ARG BUILD_DATE
ARG FASTSDCPU_VERSION

LABEL org.opencontainers.image.title="FastSD CPU Image" \
      org.opencontainers.image.authors='George Ma' \
      org.opencontainers.image.url='https://github.com/z-george-ma/ai-tools/' \
      org.opencontainers.image.documentation='https://github.com/z-george-ma/ai-tools/blob/main/fastsdcpu/README.md'

RUN apt update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends ca-certificates python3 ffmpeg

COPY --from=build /app /app
ENV GRADIO_ANALYTICS_ENABLED=False

WORKDIR /app

VOLUME /app/lora_models
VOLUME /app/controlnet_models
VOLUME /root/.cache/huggingface

EXPOSE 7860
EXPOSE 8000
CMD ["/app/start-webui.sh"]
