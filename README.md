# AI Tools Docker Collection

Production-ready Docker images for machine learning and deep learning frameworks, optimized for performance and ease of use in Docker or Kubernetes environment.

### Overview

This repository contains Dockerfiles and configuration files for running popular AI tools in containerized environments. Each image is optimized for performance and ease of use, with sensible defaults and clear documentation.

### Available Images

**FastSD CPU** - Faster Stable Diffusion CPU version  
Size: 1.09 GiB  
See [fastsdcpu/README.md](https://github.com/z-george-ma/ai-tools/blob/main/fastsdcpu/README.md) for deployment instructions.

**stable-diffusion.cpp (CUDA)** - Stable Difffusion with CUDA support and Web UI  
See [sd-cpp-webui/README.md](https://github.com/z-george-ma/ai-tools/blob/main/sd-cpp-webui/README.md) for deployment instructions.

**Ollama CPU** - Minimal CPU-only Ollama runtime  
See [ollama-cpu/README.md](https://github.com/z-george-ma/ai-tools/blob/main/ollama-cpu/README.md) for deployment instructions.

**Ollama (CUDA runner)** - Ollama with CUDA runner  
See [ollama-cuda/README.md](https://github.com/z-george-ma/ai-tools/blob/main/ollama-cuda/README.md) for deployment instructions.

**Open WebUI** - Open WebUI front-end for Ollama  
See [open-webui/README.md](https://github.com/z-george-ma/ai-tools/blob/main/open-webui/README.md) for deployment instructions.

### License

This project is licensed under the MIT License - see the LICENSE file for details.

### Acknowledgments

This project builds upon the following open-source projects:

- [Fastsdcpu](https://github.com/rupeshs/fastsdcpu)
- [alpine/ollama](https://hub.docker.com/r/alpine/ollama)
- [open-webui](https://github.com/open-webui/open-webui)
- [stable-diffusion.cpp](https://github.com/leejet/stable-diffusion.cpp)
- [sd.cpp-webui](https://github.com/daniandtheweb/sd.cpp-webui)
