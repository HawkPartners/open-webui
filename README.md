# HawkGPT Open WebUI

## Docker Build Commands

### Development
```bash
docker buildx build --no-cache \
  --platform linux/amd64,linux/arm64 \
  -t jasongraydon01/hawkgpt-openwebui:dev \
  -f Dockerfile.custom \
  --push .
```

### Production
```bash
docker buildx build --no-cache \
  --platform linux/amd64,linux/arm64 \
  -t jasongraydon01/hawkgpt-openwebui:latest \
  -f Dockerfile.custom \
  --push .
```

## Development Tips
- Use the `:dev` tag for testing and development purposes
- Use the `:latest` tag for production deployments
- The build supports both AMD64 and ARM64 architectures