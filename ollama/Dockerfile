FROM nvidia/cuda:12.6.3-cudnn-devel-ubuntu24.04 AS build

RUN apt update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends ca-certificates git golang-go \
    && git clone --depth 1 https://github.com/ollama/ollama.git /app \
    && cd /app \
    && make CUDA_12_PATH=/usr/local/cuda CUDA_12_COMPILER=/usr/local/cuda/bin/nvcc

FROM ubuntu:24.04

RUN apt update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends ca-certificates \
    && rm -rf /var/lib/apt/lists/*

COPY --from=build /app/ollama /usr/bin/ollama
COPY --from=build /app/llama/build/linux-amd64/runners /usr/bin/llama/build/linux-amd64/runners

ENV OLLMA_HOST=0.0.0.0
ENV OLLAMA_DEBUG=0
ENV OLLAMA_KEEP_ALIVE=-1
ENV GIN_MODE=release

EXPOSE 11434
ENTRYPOINT ["/usr/bin/ollama"]
CMD ["serve"]