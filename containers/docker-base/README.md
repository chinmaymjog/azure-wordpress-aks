# 📦 Docker Base Image

A highly optimized and hardened base image for enterprise WordPress deployments - part of the [azure-wordpress-aks](../../README.md) repo.

## 🔗 Related Components

* [Infrastructure (Terraform)](https://github.com/chinmaymjog/azure-wordpress-aks-infra) - provisions the AKS cluster/ACR this image gets pushed to and pulled onto.
* [../static-assets](../static-assets/README.md) - the common plugins/themes pool.
* [../../charts](../../charts/README.md) - the Helm chart and site-specific Dockerfile that build on this base image.

---

## 🚀 Technical Highlights

- **PHP 8.x Optimized**: Fine-tuned for performance and security.
- **Hardened**: Removed unnecessary packages and configured secure defaults.
- **Build-ready**: Includes essential tools like `wp-cli` for automated management.
- **Cloud Native**: Pre-configured for Azure/AWS persistent storage mounting.

## 🛠️ Usage

Use this image as the `FROM` instruction in your application Dockerfile:

```dockerfile
FROM <your-acr-name>.azurecr.io/docker-base:latest
COPY ./src /var/www/html
```

## 🛡️ License
Distributed under the MIT License. See `LICENSE` for more information.