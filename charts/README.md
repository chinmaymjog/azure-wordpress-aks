# 🎡 Application Boilerplate & Helm Chart

This directory provides a production-ready boilerplate and Helm chart for deploying WordPress at scale on Azure Kubernetes Service (AKS) - part of the [azure-wordpress-aks](../README.md) repo.

## 🔗 Related Components

* [Infrastructure (Terraform)](https://github.com/chinmaymjog/azure-wordpress-aks-infra) - the companion repo that provisions the AKS cluster, ACR, and database this deploys onto.
* [../containers/docker-base](../containers/docker-base/README.md) - the base WordPress runtime image this chart's `Dockerfile` builds on.
* [../containers/static-assets](../containers/static-assets/README.md) - the common plugins/themes pool this chart's `Dockerfile` pulls from.

---

## ✨ Key Features

- **Dockerized WordPress**: Optimized PHP-FPM and Nginx configuration for high-traffic sites.
- **Enterprise CI/CD**: Comprehensive GitLab CI/CD pipeline covering:
  - Secret Detection
  - Automated Database Migrations & Search-Replace
  - Asset Synchronization via Azure FileShare
  - Blue/Green style deployments via Helm
- **Stateless Architecture**: Engineered for Kubernetes with externalized storage and database.
- **Developer Workflow**: Built-in support for Development, Staging, and Production environments.

## 📁 Project Structure

```text
.
├── src/                  # WordPress source code (themes, plugins)
├── deploy/               # Helm charts and Kubernetes manifests
├── dockerfile            # Optimized WordPress Docker image
├── docker-compose.yml    # Local development environment
└── .gitlab-ci.yml        # Enterprise deployment pipeline
```

## 🚀 How to Use

1. **Local Dev**: Run `docker-compose up` to start a local instance.
2. **Cloud Deploy**: Configure your Azure/GitLab variables and push to the `main` branch for Staging deployment. Create a version tag (e.g., `v1.0.0`) for Production.

## 🛡️ License
Distributed under the MIT License. See `LICENSE` for more information.