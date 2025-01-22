FROM ubuntu:24.04 AS build

RUN apt update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends ca-certificates git golang-go build-essential \
    && git clone --depth 1 https://github.com/ollama/ollama.git /app \
    && cd /app \
    && CGO_ENABLED=1 go build .

FROM ubuntu:24.04

RUN apt update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends ca-certificates \
    && rm -rf /var/lib/apt/lists/*

COPY --from=build /app/ollama /usr/bin/ollama

ENV OLLMA_HOST=0.0.0.0
ENV OLLAMA_DEBUG=0
ENV OLLAMA_KEEP_ALIVE=-1
ENV GIN_MODE=release

EXPOSE 11434
ENTRYPOINT ["/usr/bin/ollama"]
CMD ["serve"]