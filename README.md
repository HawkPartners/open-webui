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

SSL Error 1: SSLEOFError: [SSL: UNEXPECTED_EOF_WHILE_READING] EOF occurred in violation of protocol (Hugging Face Download)

Cause: This error typically indicates that the secure connection to Hugging Face Hub was abruptly closed during the SSL/TLS handshake process. It's often due to transient network issues, firewalls, or network security groups blocking or interfering with the connection on port 443.
Resolution: Primarily involves ensuring clear network path and stable connectivity to Hugging Face Hub. This includes checking firewall rules, network security groups, and potentially trying the operation again to rule out temporary network glitches. Installing hf_xet might improve performance but doesn't directly resolve the underlying SSL connection interruption.
SSL Error 2: SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed: Hostname mismatch, certificate is not valid for 'hawkgptstorageprod.privatelink.blob.core.windows.net' (Azure Blob Storage Upload)

Cause: This error occurs when an application configured to use Azure Private Endpoints attempts to connect to the storage account using the specific private link FQDN (e.g., storagename.privatelink.blob.core.windows.net) instead of the standard public FQDN (e.g., storagename.blob.core.windows.net). The SSL certificate provided by Azure Blob Storage is for the public FQDN, leading to a hostname mismatch validation failure.
Resolution: Ensure your application's configuration for Azure Blob Storage uses the standard public FQDN. A correctly configured Azure Private Endpoint and linked Private DNS Zone will ensure that this standard FQDN resolves to the Private Endpoint's private IP address when accessed from within the associated virtual network, allowing the SSL certificate validation to succeed. Do not use the .privatelink suffix in your application's connection string or endpoint configuration.