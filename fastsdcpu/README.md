# Fast Stable Diffusion CPU Docker Image

Fastsdcpu is a CPU inference implementation of Stable Diffusion. This image provides a pre-built environment for running Stable Diffusion on CPUs.

### Get Started

#### GRadio Web UI

```bash
docker run -p 7860:7860 ghcr.io/z-george-ma/ai-tools/fastsdcpu:latest
```

Visit http://localhost:7860 for the GRadio web UI.

#### Web API

```bash
docker run -p 8000:8000 ghcr.io/z-george-ma/ai-tools/fastsdcpu:latest /app/start-webserver.sh
```

Web API is hosted on http://localhost:8000/api. Documentation is located at http://localhost:8000/api/docs.

#### Mount points

- `/app/lora_models`
  Storage for LoRA models

- `/app/controlnet_models`
  Storage for ControlNet models

- `/root/.cache/huggingface`
  HuggingFace models cache

### Kubernetes deployment

Refer to [k8s.yaml](https://github.com/z-george-ma/ai-tools/blob/main/fastsdcpu/k8s.yaml) for Kubernetes deployment.
