# 🎡 Azure WordPress Stack: Tier 4 - Application Boilerplate & Helm Chart

> **Part 4 of the Azure WordPress Stack ecosystem.**

This repository provides a production-ready boilerplate and Helm chart for deploying WordPress at scale on the Azure Kubernetes Service (AKS).

## 🔗 Project Ecosystem Navigation

You are currently at **Step 4: Application Boilerplate & Helm Chart**.

* **Previous Step:** [Step 3: Static Assets (azure-wp-stack-static-assets)](https://github.com/chinmaymjog/azure-wp-stack-static-assets) - Dependency management for themes and plugins.
* **Full Ecosystem:**
  * 1️⃣ [Infrastructure](https://github.com/chinmaymjog/azure-wp-stack-infrastructure)
  * 2️⃣ [Base Docker Image](https://github.com/chinmaymjog/azure-wp-stack-docker-base)
  * 3️⃣ [Static Assets (Themes & Plugins)](https://github.com/chinmaymjog/azure-wp-stack-static-assets)
  * 4️⃣ **Helm Chart Deployment** (You are here)

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