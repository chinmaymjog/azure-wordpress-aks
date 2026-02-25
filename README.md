# 🎨 Azure WordPress Stack: Tier 3 - Static Assets (Themes & Plugins)

> **Part 3 of the Azure WordPress Stack ecosystem.**

A standardized repository for managing custom WordPress themes and plugins in an enterprise environment. Designed for seamless integration with Kubernetes-based deployment pipelines.

## 🔗 Project Ecosystem Navigation

You are currently at **Step 3: Static Assets**.

* **Previous Step:** [Step 2: Base Docker Image (azure-wp-stack-docker-base)](https://github.com/chinmaymjog/azure-wp-stack-docker-base) - The underlying PHP/Nginx container.
* **Next Step:** [Step 4: Helm Chart Deployment (azure-wp-stack-helm-chart)](https://github.com/chinmaymjog/azure-wp-stack-helm-chart) - Deploy the application using GitOps.
* **Full Ecosystem:**
  * 1️⃣ [Infrastructure](https://github.com/chinmaymjog/azure-wp-stack-infrastructure)
  * 2️⃣ [Base Docker Image](https://github.com/chinmaymjog/azure-wp-stack-docker-base)
  * 3️⃣ **Static Assets** (You are here)
  * 4️⃣ [Helm Chart Deployment & App Boilerplate](https://github.com/chinmaymjog/azure-wp-stack-helm-chart)

---

## 🚀 Key Features

- **Automated Bundling**: Optimized `dockerfile` for building extension-heavy images.
- **Package Management**: Structured `pkg-mgr` directory for handling dependencies.
- **Standardized Layout**: Follows WordPress best practices for folder hierarchy and multi-tenant support.
- **CI/CD Integrated**: Pre-configured for automated testing and registry deployment.

## 📁 Project Structure

```text
.
├── themes/               # Custom WordPress themes
├── plugins/              # Custom WordPress plugins
├── pkg-mgr/              # Dependency management (Composer/NPM)
└── dockerfile            # Optimized build-stage for extensions
```

## 🛡️ License
Distributed under the MIT License. See `LICENSE` for more information.