# Ollama CPU

Minimal CPU-only Ollama Docker Image from [alpine/ollama](https://hub.docker.com/r/alpine/ollama)

### Get Started

#### Web UI

```bash
docker run -d -p 11434:11434 -v ~/.ollama/root/.ollama --name ollama alpine/ollama
```

API is hosted on http://localhost:11434/.

#### Mount points

- `/root/.ollama`
  Storage for ollama models

### Kubernetes deployment

Refer to [k8s.yaml](https://github.com/z-george-ma/ai-tools/blob/main/ollama-cpu/k8s.yaml) for Kubernetes deployment.
