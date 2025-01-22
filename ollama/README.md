# Ollama

Minimal Ollama Docker Image with GPU support

### Get Started

#### API

```bash
docker run -d -p 11434:11434 -v ~/.ollama/root/.ollama --name ollama ghcr.io/z-george-ma/ai-tools/ollama:latest
```

API is hosted on http://localhost:11434/.

#### Mount points

- `/root/.ollama`
  Storage for ollama models

### Kubernetes deployment

Refer to [k8s.yaml](https://github.com/z-george-ma/ai-tools/blob/main/ollama/k8s.yaml) for Kubernetes deployment.
