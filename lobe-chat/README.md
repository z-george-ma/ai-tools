# Lobe-chat

Lobe-chat Docker Image from [lobe-chat](https://hub.docker.com/r/lobehub/lobe-chat)

### Get Started

#### Web UI

```bash
docker run -d -p 3210:3210 -e OPENAI_API_KEY=sk-xxxx -e ACCESS_CODE=lobe66 --name lobe-chat --restart always lobehub/lobe-chat
```

Visit http://localhost:3210 for the web UI.

### Kubernetes deployment

Refer to [k8s.yaml](https://github.com/z-george-ma/ai-tools/blob/main/lobe-chat/k8s.yaml) for Kubernetes deployment.
