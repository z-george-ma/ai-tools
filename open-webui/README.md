# Open WebUI

Open WebUI Docker Image from [open-webui](https://github.com/open-webui/open-webui)

### Get Started

#### Web UI

```bash
docker run -d -p 8080:8080 -e OLLAMA_BASE_URL=https://example.com -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

Visit http://localhost:8080 for the web UI.

#### Mount points

- `/app/backend/data`
  Storage for Open WebUI.

### Kubernetes deployment

Refer to [k8s.yaml](https://github.com/z-george-ma/ai-tools/blob/main/open-webui/k8s.yaml) for Kubernetes deployment.
