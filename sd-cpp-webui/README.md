# stable-diffusion.cpp with GRadio Web UI

[stable-diffusion.cpp](https://github.com/leejet/stable-diffusion.cpp) with CUDA support and [Web UI](https://github.com/daniandtheweb/sd.cpp-webui).

### Get Started

#### Web UI

1. Ensure your container environment is configured with [NVIDIA GPU](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html).
2. Put your downloaded model file into `/app/models/checkpoints` mountpoint, and other files into corresponding mountpoints.
3. Run the following command to bring up the container

```bash
docker run --gpus all -d -p 7860:7860 -v ~/sd-model:/app/models/checkpoints --name stable-diffusion ghcr.io/z-george-ma/ai-tools/sd-cpp-webui:latest
```

GRadio Web UI is hosted on http://localhost:7860/.

#### Mount points

- `/app/models/checkpoints`  
  Stable diffusion models

- `/app/models/controlnet`  
  ControlNet models

- `/app/models/embeddings`  
  Embeddings models

- `/app/models/photomaker`  
  PhotoMaker models

- `/app/models/unet`  
  UNet models

- `/app/models/vae`  
  VAE (Variational Autoencoder) models

- `/app/models/loras`  
  LoRA models

- `/app/models/taesd`  
  TAESD (Tiny AutoEncoder for Stable Diffusion) models

- `/app/models/upscale_models`  
  Upscaling models

- `/app/outputs`  
  Output images

### Kubernetes deployment

Refer to [k8s.yaml](https://github.com/z-george-ma/ai-tools/blob/main/sd-cpp-webui/k8s.yaml) for Kubernetes deployment.
