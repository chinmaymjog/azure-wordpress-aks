# 🎨 Static Assets (Themes & Plugins)

A standardized way to manage the common pool of WordPress themes and plugins - part of the [azure-wordpress-aks](../../README.md) repo.

## 🔗 Related Components

* [../docker-base](../docker-base/README.md) - the base WordPress runtime image this pool layers onto.
* [../../charts](../../charts/README.md) - the Helm chart and site-specific Dockerfile that select which of these plugins/themes a given site actually ships.

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