# OpenClaw Docker Building Guide

This guide provides instructions for building OpenClaw Docker images, including the main application image and various sandbox images for isolated code execution.

## Building the Local Image

Build and run OpenClaw locally using Docker Compose:

```bash
# docker compose run --rm openclaw-cli onboard
# docker compose up -d openclaw-gateway
docker build -t openclaw:local -f Dockerfile .
docker tag openclaw:local craftslab/openclaw:local
docker push craftslab/openclaw:local
```

## Building Sandbox Images

### Default Sandbox Image

Build the default sandbox image (`openclaw-sandbox:bookworm-slim`):

```bash
./scripts/sandbox-setup.sh
docker tag openclaw-sandbox:bookworm-slim craftslab/openclaw-sandbox:bookworm-slim
docker push craftslab/openclaw-sandbox:bookworm-slim
```

### Sandbox Common Image

Build the sandbox common image (`openclaw-sandbox-common:bookworm-slim`):

```bash
# Using script (recommended for local development)
./scripts/sandbox-common-setup.sh
docker tag openclaw-sandbox-common:bookworm-slim craftslab/openclaw-sandbox-common:bookworm-slim
docker push craftslab/openclaw-sandbox-common:bookworm-slim

# Or using Dockerfile directly (requires openclaw-sandbox:bookworm-slim base image)
docker build -t openclaw-sandbox-common:bookworm-slim -f Dockerfile.sandbox-common .
docker tag openclaw-sandbox-common:bookworm-slim craftslab/openclaw-sandbox-common:bookworm-slim
docker push craftslab/openclaw-sandbox-common:bookworm-slim
```

### Sandbox Browser Image

Build the sandbox browser image (`openclaw-sandbox-browser:bookworm-slim`):

```bash
./scripts/sandbox-browser-setup.sh
docker tag openclaw-sandbox-browser:bookworm-slim craftslab/openclaw-sandbox-browser:bookworm-slim
docker push craftslab/openclaw-sandbox-browser:bookworm-slim
```

## References

- [Docker Installation Guide](https://docs.openclaw.ai/install/docker)
- [Sandboxing Documentation](https://docs.openclaw.ai/gateway/sandboxing)
