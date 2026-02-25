# 📦 Azure WordPress Stack: Tier 2 - Docker Base Image

> **Part 2 of the Azure WordPress Stack ecosystem.**

A highly optimized and hardened base image for enterprise WordPress deployments. Designed to be used in conjunction with a Kubernetes-based hosting platform.

## 🔗 Project Ecosystem Navigation

You are currently at **Step 2: Base Docker Image**.

* **Previous Step:** [Step 1: Infrastructure (azure-wp-stack-infrastructure)](https://github.com/chinmaymjog/azure-wp-stack-infrastructure) - Provision the AKS environment.
* **Next Step:** [Step 3: Static Assets (azure-wp-stack-static-assets)](https://github.com/chinmaymjog/azure-wp-stack-static-assets) - Manage custom plugins and themes.
* **Full Ecosystem:**
  * 1️⃣ [Infrastructure](https://github.com/chinmaymjog/azure-wp-stack-infrastructure)
  * 2️⃣ **Base Docker Image** (You are here)
  * 3️⃣ [Static Assets (Themes & Plugins)](https://github.com/chinmaymjog/azure-wp-stack-static-assets)
  * 4️⃣ [Helm Chart Deployment & App Boilerplate](https://github.com/chinmaymjog/azure-wp-stack-helm-chart)

---

## 🚀 Technical Highlights

- **PHP 8.x Optimized**: Fine-tuned for performance and security.
- **Hardened**: Removed unnecessary packages and configured secure defaults.
- **Build-ready**: Includes essential tools like `wp-cli` for automated management.
- **Cloud Native**: Pre-configured for Azure/AWS persistent storage mounting.

## 🛠️ Usage

Use this image as the `FROM` instruction in your application Dockerfile:

```dockerfile
FROM chinmaymjog/wp-base:latest
COPY ./src /var/www/html
```

## 🛡️ License
Distributed under the MIT License. See `LICENSE` for more information.